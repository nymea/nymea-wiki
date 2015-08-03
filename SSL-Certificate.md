# Create a SSL certificate
--------------------------------------------

If you want to use guhd webserver with a secure, encrypted connection you need to create a self signed certificate. This certificate will ensure, that the connection you are trying to establish is really your guh server, and not some man in the middle. Creating a certificate is quiet easy, so here we go.

[OpenSSL](http://www.openssl.org/)

[More details](https://help.ubuntu.com/lts/serverguide/certificates-and-security.html)

1. Generate the keys for the Certificate Signing Request (CSR)

        $ openssl genrsa -des3 -out guhd-certificate.key 2048

You need to enter twice a secure password:

        Generating RSA private key, 2048 bit long modulus
                                                                                                          
        ............................................................................+++
        ...............+++
        e is 65537 (0x10001)
        Enter pass phrase for guhd-certificate.key:
        Verifying - Enter pass phrase for guhd-certificate.key:


2. Create the insecure key (without a pass phrase):

        $ openssl rsa -in guhd-certificate.key -out guhd-certificate.key.insecure

Enter the passphrase from step `1`:

        Enter pass phrase for guhd-certificate.key:
        writing RSA key

    Rename the files:

        $ mv guhd-certificate.key guhd-certificate.key.secure
        $ mv guhd-certificate.key.insecure guhd-certificate.key


3. Create the Certificate Signing Request (CSR):

        $ openssl req -new -key guhd-certificate.key -out guhd-certificate.csr
    
    Fill out the requested fields i.e.:

        You are about to be asked to enter information that will be incorporated
        into your certificate request.
        What you are about to enter is what is called a Distinguished Name or a DN.
        There are quite a few fields but you can leave some blank
        For some fields there will be a default value,
        If you enter '.', the field will be left blank.
        -----
        Country Name (2 letter code) [AU]:
        State or Province Name (full name) [Some-State]:Austria
        Locality Name (eg, city) []:Vienna
        Organization Name (eg, company) [Internet Widgits Pty Ltd]:guh
        Organizational Unit Name (eg, section) []:guhIO
        Common Name (e.g. server FQDN or YOUR name) []:guhd
        Email Address []:some.name@example.com

        Please enter the following 'extra' attributes
        to be sent with your certificate request
        A challenge password []:.
        An optional company name []:.

4. Sign the certificate:

        $ openssl x509 -req -days 365 -in guhd-certificate.csr -signkey guhd-certificate.key -out guhd-certificate.crt

        Signature ok
        subject=/C=AU/ST=Austria/L=Vienna/O=guh/OU=guhIO/CN=guhd/emailAddress=simon.stuerz@guh.guru
        Getting Private key


5. Install certificate:

        $ sudo cp guhd-certificate.crt /etc/ssl/certs
        $ sudo cp guhd-certificate.key /etc/ssl/private





