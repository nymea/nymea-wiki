The *guh* webserver API authentication is by default enabled and can be accessed with the [Basic Authentication Scheme](http://tools.ietf.org/html/rfc1945#section-11.1). Once a client is logged in using the user name and password the server will return an access token. This token can be used for any further API call. This makes sure there is no user name or password saved on the client side. It is highly recommended to use a secure `SSL/TLS` connection for the whole authentication traffic. How to generate a SSL certificate and configure the server using https can be found in the [[Configuration]] wiki.

--------------------------------------------
## Table of contents:

* [Login](https://github.com/guh/guh/wiki/Webserver-authentication#1-login)
* [Using the token](https://github.com/guh/guh/wiki/Webserver-authentication#2-using-the-token)


## 1. Login

> **Note:** if authentication is disabled in the *guh* server, the `/api/v1/authentication` resource will be disabled and cannot be accessed. Each request on this resource will answered with a `403 Forbidden` message.


> **Note:** if you are not using SSL, which is not recommended, you can replace `https` in the url with `http` and skip the `-k` parameter of `curl`. See `man curl`.  


In order to get the API token, the user has to perform a `GET` request on the resource `https://host:3333/api/v1/authentication/login` containing the authentication header i.e.:

#### Request

    $ curl -v -k -u guh:guh https://localhost:3333/api/v1/authentication/login
    ...
    > GET /api/v1/authentication/login HTTP/1.1
    > Host: localhost:3333
    > Authorization: Basic Z3VoOmd1aA==
    > User-Agent: curl/7.43.0
    > Accept: */*

The user name and password will be sent in the `Authorization` header. The keyword `Basic` is required and has to be followed by the Base64 encoded string looking like this:

    username:password

#### Response
If the user name and password are correct the server will return a response like this: 

    < HTTP/1.1 200 Ok
    < Content-Type: text/plain; charset="utf-8";
    < Keep-Alive: timeout=12, max=50
    < Connection: Keep-Alive
    < Cache-Control: no-cache
    < Content-Length: 63
    < Server: guh/0.8.0
    < Date: Mo., 01 Feb. 2016 15:05:56 GMT
    < Access-Control-Allow-Origin: *

    {
        "token": "L_dCf4_EzuulowuysgXr39cTxx6NCtiqK9ZyNh5KbGI"
    }

>**Note:** The token will always be a URL encoded string.

The server saves now this token and knows that this token is from this authorized user and client. As client description the `User-Agent` header will be used. In this example the  client description will be `curl/7.43.0`.  

The returned token can be saved and used for further API calls. 

#### Error response

If the user name or the password are not correct, the server will return an error message like this:

    $ curl -v -k -u guh:wrong-password https://localhost:3333/api/v1/authentication/login

Returns:

    < HTTP/1.1 401 Unauthorized
    < Content-Type: application/json; charset="utf-8";
    < Keep-Alive: timeout=12, max=50
    < Connection: Keep-Alive
    < Cache-Control: no-cache
    < Content-Length: 58
    < Server: guh/0.8.0
    < Date: Mo., 01 Feb. 2016 15:15:36 GMT
    < Access-Control-Allow-Origin: *
    
    {
        "error": "AuthenticationErrorAuthenicationFailed"
    }                               

## 2. Using the token

Once you are logged in successfully and got an access token, you can use the token as user name for every call. The header scheme is the same like in the login procedure. The password is empty.

    curl -v -k -u token: https://localhost:3333/api/v1/devices

#### Request 
If we are using the token from this example, the request would look like this:

    $ curl -v -k -u L_dCf4_EzuulowuysgXr39cTxx6NCtiqK9ZyNh5KbGI: https://localhost:3333/api/v1/devices
    
    ...
    * Server auth using Basic with user 'L_dCf4_EzuulowuysgXr39cTxx6NCtiqK9ZyNh5KbGI'
    > GET /api/v1/devices HTTP/1.1
    > Host: localhost:3333
    > Authorization: Basic TF9kQ2Y0X0V6dXVsb3d1eXNnWHIzOWNUeHg2TkN0aXFLOVp5Tmg1S2JHSTo=
    > User-Agent: curl/7.43.0
    > Accept: */*

#### Response

    < HTTP/1.1 200 Ok
    < Content-Type: application/json; charset="utf-8";
    < Keep-Alive: timeout=12, max=50
    < Connection: Keep-Alive
    < Cache-Control: no-cache
    < Content-Length: 1171
    < Server: guh/0.8.0
    < Date: Mo., 01 Feb. 2016 15:24:22 GMT
    < Access-Control-Allow-Origin: *

    [
        {
            "deviceClassId": "{fbf665fb-9aca-423f-a5f2-924e50ebe6ca}",
            "id": "{08dec017-acec-4b3c-b004-98442f522cad}",
            "name": "Today",
            ....
        }
    ]

#### Error response
If you are trying to use the API without the `Authorization` header or an invalid token, you will get an error response like this:

    < HTTP/1.1 401 Unauthorized
    < Content-Type: application/json; charset="utf-8";
    < Keep-Alive: timeout=12, max=50
    < Connection: Keep-Alive
    < Cache-Control: no-cache
    < Content-Length: 58
    < Server: guh/0.8.0
    < Date: Mo., 01 Feb. 2016 15:34:57 GMT
    < Access-Control-Allow-Origin: *

    {
        "error": "AuthenticationErrorAuthenicationFailed"
    }
