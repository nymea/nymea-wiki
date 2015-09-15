
--------------------------------------------
# Table of contents

* [Devices](https://github.com/guh/guh/wiki/REST-Api-documentation#devices-resource)
* [DeviceClasses](https://github.com/guh/guh/wiki/REST-Api-documentation#deviceclasses-resource)
* [Vendors](https://github.com/guh/guh/wiki/REST-Api-documentation#vendors-resource)
* [Plugins](https://github.com/guh/guh/wiki/REST-Api-documentation#plugins-resource)
* [Rules](https://github.com/guh/guh/wiki/REST-Api-documentation#rules-resource)
* [Logs](https://github.com/guh/guh/wiki/REST-Api-documentation#logs-resource)

--------------------------------------------
Http Protocol version: `HTTP/1.1`

https://tools.ietf.org/html/rfc7231

In order to get notifications for your client application, 
please take a look at the websocket server.

=====================================================
## Methods

Allowed methods:
* `GET` -> get data from a resource
* `PUT` -> edit a resource
* `POST` -> add a resource / do something with a resource 
* `DELETE` -> delete a resource
* `OPTIONS` -> check if a resource is available (used for CORS)

* Minimal API request path: `/api/v1/{resource}`
* Path for the webinterdace: `/`

# Resources
=====================================================

## Devices resource
-----------------------------------------------------
### `GET /api/v1/devices`

* JSON RPC method: Devices.GetConfiguredDevices
* Description: Returns the list of configured devices
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:Device"
        ]
             

-----------------------------------------------------
### `GET /api/v1/devices/{deviceId}`

* JSON RPC method: -
* Description: Returns the map of the device with the given `{deviceId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
           
        "$ref:Device"
        

-----------------------------------------------------
### `GET /api/v1/devices/{deviceId}/states`

* JSON RPC method: Devices.GetStateValues
* Description: Returns the list of the states from the device with the given `{deviceId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:State"
        ]
        

-----------------------------------------------------
### `GET /api/v1/devices/{deviceId}/states/{stateTypeId}`

* JSON RPC method: Devices.GetStateValue
* Description: Returns the value of the state with the given `{stateTypeId}` from the device with the given `{deviceId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        {
            "value": "Variant"
        }
        

-----------------------------------------------------
### `POST /api/v1/devices`

* JSON RPC method: Devices.AddConfiguredDevice
* Description: Add a new device (CreateMethodUser)
* Request:
        
        POST /api/v1/devices
        Content-Type: application/json; charset="utf-8";

        {
            "deviceClassId": "Uuid",
            "deviceParams": [
                "$ref:Param"
             ]    
        }
        
    Add a discovered device request (CreateMethodDiscovery):
            
        POST /api/v1/devices
        Content-Type: application/json; charset="utf-8";
        
        {
            "deviceClassId": "Uuid",
            "deviceDescriptorId": "Uuid"
        }
        
* Response:
    
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
    
        "$ref:Device"


-----------------------------------------------------
### `PUT /api/v1/devices/{deviceId}`

* JSON RPC method: Devices.EditDevice
* Description: Edit the device with the given `{deviceId}` (CreateMethodUser)
* Request:
        
        PUT /api/v1/devices/{deviceId}
        Content-Type: application/json; charset="utf-8";
        
        {
            "deviceClassId": "Uuid",
            "deviceParams": [
                "$ref:Param"
             ]    
        }
        
    Edit a device with the given `{deviceId}` (CreateMethodDiscoverys):
            
        PUT /api/v1/devices/{deviceId}
        Content-Type: application/json; charset="utf-8";
        
        {
            "deviceClassId": "Uuid",
            "deviceDescriptorId": "Uuid"
        }
        
* Response:
    
        HTTP/1.1 200 Ok
    

-----------------------------------------------------
### `POST /api/v1/devices/pair`

* JSON RPC method: Devices.PairDevice
* Description: Pair a device (CreateMethodUser)
* Request:
        
        POST /api/v1/devices/pair
        Content-Type: application/json; charset="utf-8";

        {
            "deviceClassId": "Uuid",
            "deviceParams": [
                "$ref:Param"
             ]    
        }
        
    Pair a discovered device (CreateMethodDiscovery):
            
        POST /api/v1/devices/pair
        Content-Type: application/json; charset="utf-8";
        
        {
            "deviceClassId": "Uuid",
            "deviceDescriptorId": "Uuid"
        }
        
* Response:
    
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
    
        {
            "displayMessage": "String",
            "pairingTransactionId": "Uuid",
            "setupMethod": "$ref:SetupMethod"
        }

-----------------------------------------------------
### `POST /api/v1/devices/confirmpairing`

* JSON RPC method: Devices.ConfirmPairing
* Description: Confirm the pairing of a device. In case of `SetupMethodEnterPin` or `SetupMethodDisplayPin` also provide the pin in the param `secret`.
* Request:
        
        POST /api/v1/devices/confirmpairing
        Content-Type: application/json; charset="utf-8";

        {
            "pairingTransactionId": "Uuid"
            "o:secret": "String",
        }
                
* Response:
    
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
    
        "$ref:Device"


-----------------------------------------------------
### `POST /api/v1/devices/{deviceId}/execute/{actionTypeId}`

* JSON RPC method: Devices.ExecuteAction
* Description: Execute the action with the given `{actionTypeId}` on device with the given `{deviceId}`
* Request:
        
        POST /api/v1/devices/{deviceId}/execute/{actionTypeId}
        Content-Type: application/json; charset="utf-8";
        
        {
            "params": [
                "$ref:Param"
             ]    
        }

* Response:
    
        HTTP/1.1 200 Ok
    

-----------------------------------------------------
### `DELETE /api/v1/devices/{deviceId}`

* JSON RPC method: Devices.RemoveConfiguredDevice
* Description: Remove the device with the given `{deviceId}`
* Response:
    
        HTTP/1.1 200 Ok





=====================================================
## DeviceClasses resource

-----------------------------------------------------
### `GET /api/v1/deviceclasses?vendorId="{vendorId}"`

* JSON RPC method: Devices.GetSupportedDevices
* Description: Returns the list of supported devices
* Optional parameters:
    
        vendorId -> filter DeviceClasses for the given {vendorId}

* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:DeviceClass"
        ]
     

-----------------------------------------------------
### `GET /api/v1/deviceclasses/{deviceClassId}`

* JSON RPC method: -
* Description: Returns the DeviceClass for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:DeviceClass"
        ]
             

-----------------------------------------------------
### `GET /api/v1/deviceclasses/{deviceClassId}/actiontypes`

* JSON RPC method: Devices.GetActionTypes
* Description: Returns the list of ActionTypes for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:ActionType"
        ]
        

-----------------------------------------------------
### `GET /api/v1/deviceclasses/{deviceClassId}/actiontypes/{actionTypeId}`

* JSON RPC method: Actions.GetActionType
* Description: Returns the `{actionTypeId}` for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        "$ref:ActionType"
        

-----------------------------------------------------
### `GET /api/v1/deviceclasses/{deviceClassId}/statetypes`

* JSON RPC method: Devices.GetStateTypes
* Description: Returns the list of StateTypes for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:StateType"
        ]
        

-----------------------------------------------------
### `GET /api/v1/deviceclasses/{deviceClassId}/statetypes/{stateTypeId}`

* JSON RPC method: States.GetStateType
* Description: Returns the StateType for the given `{stateTypeId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        "$ref:StateType"
     

-----------------------------------------------------
### `GET /api/v1/deviceclasses/{deviceClassId}/eventtypes`

* JSON RPC method: Devices.GetEventTypes
* Description: Returns the list of EventTypes for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:EventType"
        ]
        

-----------------------------------------------------
### `GET /api/v1/deviceclasses/{deviceClassId}/eventtypes/{eventTypeId}`

* JSON RPC method: Events.GetEventType
* Description: Returns the EventType for the given `{eventTypeId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        "$ref:EventType"
     

-----------------------------------------------------
### `GET /api/v1/deviceclasses/{deviceClassId}/discover?params=["$ref:Param"]`

* JSON RPC method: Devices.GetDiscoveredDevices
* Description: Get discovered devices for the given `{deviceClassId}`
* Optional parameters: 
    
        params -> JSON list of discovery params (percent encoding)

* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:DeviceDescriptor"
        ]

* Example:

    Request:

        GET http://localhost:3000/api/v1/deviceclasses/%7B753f0d32-0468-4d08-82ed-1964aab03298%7D/discover?params=[{%22name%22:%22resultCount%22,%20%22value%22:1}]

    Response:

        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";

        [
            {
                "description": "55555",
                "id": "{fbf3bdd7-4ea2-42c3-ac87-a2ab76ae1b3b}",
                "title": "Mock Device 1 (Discovered)"
            }
        ]


=====================================================
## Vendors resource

-----------------------------------------------------
### `GET /api/v1/vendors`

* JSON RPC method: Devices.GetSupportedVendors
* Description: Returns the list of supported vendors
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:Vendor"
        ]
     

-----------------------------------------------------
### `GET /api/v1/vendors/{vendorId}`

* JSON RPC method: -
* Description: Returns the vendor with the given `{vendorId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        
        "$ref:Vendor"




=====================================================
## Plugins resource

-----------------------------------------------------
### `GET /api/v1/plugins`

* JSON RPC method: Devices.GetPlugins
* Description: Returns the list of loaded plugins
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:Plugin"
        ]
     

-----------------------------------------------------
### `GET /api/v1/plugins/{pluginId}`

* JSON RPC method: -
* Description: Returns the vendor with the given `{vendorId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        
        "$ref:Plugin"

-----------------------------------------------------
### `GET /api/v1/plugins/{pluginId}/configuration`

* JSON RPC method: Devices.GetPluginConfiguration
* Description: Returns the plugin configuration of the given `{pluginId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:Param"
        ]
    

-----------------------------------------------------
### `PUT /api/v1/plugins/{pluginId}/configuration`

* JSON RPC method: Devices.SetPluginConfiguration
* Description: Set the configuration of the plugin with the given `{pluginId}`
* Request:
        
        PUT /api/v1/plugins/{pluginId}/configuration
        Content-Type: application/json; charset="utf-8";

        [
            "$ref:Param"
        ]


* Response:
        
        HTTP/1.1 200 Ok

        
        

=====================================================
## Rules resource
     
-----------------------------------------------------
### `GET /api/v1/rules?deviceId={deviceId}`

* JSON RPC method: Rules.GetRules
* Description: Returns the list of rule descriptions 
* Optional parameters:
    
        deviceId -> filter rules with the given `deviceId` in it         

* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "ref:RuleDescription"
        ]
     

-----------------------------------------------------
### `GET /api/v1/rules/{ruleId}`

* JSON RPC method: Rules.GetRuleDetails
* Description: Returns the details of the rule with the given `{ruleId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        "ref:Rule"


-----------------------------------------------------
### `POST /api/v1/rules`

* JSON RPC method: Rules.AddRule
* Description: Add a new rule
* Request:
        
        POST /api/v1/rules
        Content-Type: application/json; charset="utf-8";
        
        {
            "name": "String",
            "o:enabled": "Bool",
            "o:eventDescriptor": "$ref:EventDescriptor",
            "o:stateEvaluator": "$ref:StateEvaluator",
            "actions": [
                "$ref:RuleAction"
            ],
            "o:eventDescriptorList": [
                "$ref:EventDescriptor"
            ],
            "o:exitActions": [
                "$ref:RuleAction"
            ]
        }

* Response:
    
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
    
        "ref:Rule"

-----------------------------------------------------
### `PUT /api/v1/rules/{ruleId}`

* JSON RPC method: Rules.EdidRule
* Description: Edit the rule with the given `{ruleId}`
* Request:
        
        PUT /api/v1/rules/{ruleId}
        Content-Type: application/json; charset="utf-8";
        
        {
            "name": "String",
            "o:enabled": "Bool",
            "o:eventDescriptor": "$ref:EventDescriptor",
            "o:stateEvaluator": "$ref:StateEvaluator",
            "actions": [
                "$ref:RuleAction"
            ],
            "o:eventDescriptorList": [
                "$ref:EventDescriptor"
            ],
            "o:exitActions": [
                "$ref:RuleAction"
            ]
        }

* Response:
    
        HTTP/1.1 200 Ok


-----------------------------------------------------
### `POST /api/v1/rules/{ruleId}/enable`

* JSON RPC method: Rules.EnableRule
* Description: Enable the rule with the given `{ruleId}`
* Request:
        
        POST /api/v1/rules/{ruleId}/enable

* Response:
    
        HTTP/1.1 200 Ok


-----------------------------------------------------
### `POST /api/v1/rules/{ruleId}/disable`

* JSON RPC method: Rules.DisableRule
* Description: Disable the rule with the given `{ruleId}`
* Request:
        
        POST /api/v1/rules/{ruleId}/disable

* Response:
    
        HTTP/1.1 200 Ok





=====================================================
## Logs resource
     
-----------------------------------------------------
### `GET /api/v1/logs?filter={logFilter}`

* JSON RPC method: Logging.GetLogEntries
* Description: Get the LogEntries matching the given filter. 
* Optional parameters:
    
        filter -> JSON map which specifies the filter for the logs (percent encoding)

    Each list element of a given filter will be connected with OR to each other. Each of the given filters will be connected with AND to each other. The filter map looks like this:

        {
            "o:deviceIds": [
                "Uuid"
            ],
            "o:eventTypes": [
                "$ref:LoggingEventType"
            ],
            "o:loggingLevels": [
                "$ref:LoggingLevel"
            ],
            "o:loggingSources": [
                "$ref:LoggingSource"
            ],
            "o:timeFilters": [
                {
                    "o:endDate": "Int",
                    "o:startDate": "Int"
                }
            ],
            "o:typeIds": [
                "Uuid"
            ],
            "o:values": [
                "Variant"
            ]
        }

* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "ref:LogEntry"
        ]
     
* Example request:

    * `filter={"loggingSources": ["LoggingSourceSystem"]}`

            GET http://localhost:3000/api/v1/logs?filter={%22loggingSources%22:%20[%22LoggingSourceSystem%22]}

        



