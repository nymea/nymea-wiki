#guh REST API Documentation

Http Protocol version: `HTTP/1.1`

Allowed methods:
* GET
* PUT
* POST
* DELETE

API prefix: `/api/v1/`



=====================================================
# Devices resource
=====================================================

-----------------------------------------------------
## GET /api/v1/devices
-----------------------------------------------------
* JSON RPC method: Devices.GetConfiguredDevices
* Description: Returns the list of configured devices
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:Device"
        ]
             

-----------------------------------------------------
## GET /api/v1/devices/{deviceId}
-----------------------------------------------------
* JSON RPC method: -
* Description: Returns the map of the device with the given `{deviceId}`
* Response:
         
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
           
        "$ref:Device"
        

-----------------------------------------------------
## GET /api/v1/devices/{deviceId}/states
-----------------------------------------------------
* JSON RPC method: Devices.GetStateValues
* Description: Returns the list of the states from the device with the given `{deviceId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:State"
        ]
        

-----------------------------------------------------
## GET /api/v1/devices/{deviceId}/states/{stateTypeId}
-----------------------------------------------------
* JSON RPC method: Devices.GetStateValue
* Description: Returns the value of the state with the given `{stateTypeId}` from the device with the given `{deviceId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        {
            "value": "Variant"
        }
        

-----------------------------------------------------
## POST /api/v1/devices
-----------------------------------------------------
* JSON RPC method: Devices.AddConfiguredDevice
* Description: Add a new device (CreateMethodUser)
* Request:
        
        POST /api/v1/devices
        Content-Type: application/json; charset="utf-8";

        {
            "deviceParams": [
                "$ref:Param"
             ]    
        }
        
    Add a discovered device request (CreateMethodDiscovery):
            
        POST /api/v1/devices
        Content-Type: application/json; charset="utf-8";
        
        {
            "deviceDescriptorId": "Uuid"
        }
        
* Response:
    
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
    
        {
            "deviceId": "Uuid"
        }


-----------------------------------------------------
## PUT /api/v1/devices/{deviceId}
-----------------------------------------------------
* JSON RPC method: Devices.EditDevice
* Description: Edit the device with the given `{deviceId}` (CreateMethodUser)
* Request:
        
        PUT /api/v1/devices/{deviceId}
        Content-Type: application/json; charset="utf-8";
        
        {
            "deviceParams": [
                "$ref:Param"
             ]    
        }
        
    Edit a device with the given {deviceId} (CreateMethodDiscoverys):
            
        PUT /api/v1/devices/{deviceId}
        Content-Type: application/json; charset="utf-8";
        
        {
            "deviceDescriptorId": "db43c4a8-1b79-4006-ae89-c12661bc20b0"
        }
        
* Response:
    
        HTTP/1.1 200 Ok
    

-----------------------------------------------------
## DELETE /api/v1/devices/{deviceId}
-----------------------------------------------------
* JSON RPC method: Devices.RemoveConfiguredDevice
* Description: Remove the device with the given `{deviceId}`
* Response:
    
        HTTP/1.1 200 Ok





=====================================================
# DeviceClasses resource
=====================================================

-----------------------------------------------------
## GET /api/v1/deviceclasses?vendorId="{vendorId}"
-----------------------------------------------------
* JSON RPC method: Devices.GetSupportedDevices
* Description: Returns the list of supported devices
* Optional parameters:
    
        vendorId -> filter DeviceClasses for the given `{vendorId}`

* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:DeviceClass"
        ]
     

-----------------------------------------------------
## GET /api/v1/deviceclasses/{deviceClassId}"
-----------------------------------------------------
* JSON RPC method: -
* Description: Returns the DeviceClass for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:DeviceClass"
        ]
             

-----------------------------------------------------
## GET /api/v1/deviceclasses/{deviceClassId}/actiontypes"
-----------------------------------------------------
* JSON RPC method: Devices.GetActionTypes
* Description: Returns the list of ActionTypes for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:ActionType"
        ]
        

-----------------------------------------------------
## GET /api/v1/deviceclasses/{deviceClassId}/actiontypes/{actionTypeId}"
-----------------------------------------------------
* JSON RPC method: Actions.GetActionType
* Description: Returns the ActionType for the given `{actionTypeId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        "$ref:ActionType"
        

-----------------------------------------------------
## GET /api/v1/deviceclasses/{deviceClassId}/statetypes"
-----------------------------------------------------
* JSON RPC method: Devices.GetStateTypes
* Description: Returns the list of StateTypes for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:StateType"
        ]
        

-----------------------------------------------------
## GET /api/v1/deviceclasses/{deviceClassId}/statetypes/{stateTypeId}"
-----------------------------------------------------
* JSON RPC method: States.GetStateType
* Description: Returns the StateType for the given `{stateTypeId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        "$ref:StateType"
     

-----------------------------------------------------
## GET /api/v1/deviceclasses/{deviceClassId}/eventtypes"
-----------------------------------------------------
* JSON RPC method: Devices.GetEventTypes
* Description: Returns the list of EventTypes for the given `{deviceClassId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:EventType"
        ]
        

-----------------------------------------------------
## GET /api/v1/deviceclasses/{deviceClassId}/eventtypes/{eventTypeId}"
-----------------------------------------------------
* JSON RPC method: Events.GetEventType
* Description: Returns the EventType for the given `{eventTypeId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        "$ref:EventType"
     

-----------------------------------------------------
## GET /api/v1/deviceclasses/{deviceClassId}/discover?name=paramName&value=paramValue
-----------------------------------------------------
* JSON RPC method: Devices.GetDiscoveredDevices
* Description: Get discovered devices for the given `{deviceClassId}`
* Parameters: 
    
        name -> name of the discovery parameter
        value -> value of the discovery paramter

* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:DeviceDescriptor"
        ]





=====================================================
# Vendors resource
=====================================================

-----------------------------------------------------
## GET /api/v1/vendors"
-----------------------------------------------------
* JSON RPC method: Devices.GetSupportedVendors
* Description: Returns the list of supported vendors
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:Vendor"
        ]
     

-----------------------------------------------------
## GET /api/v1/vendors/{vendorId}"
-----------------------------------------------------
* JSON RPC method: -
* Description: Returns the vendor with the given `{vendorId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        
        "$ref:Vendor"




=====================================================
# Plugins resource
=====================================================

-----------------------------------------------------
## GET /api/v1/plugins"
-----------------------------------------------------
* JSON RPC method: Devices.GetPlugins
* Description: Returns the list of loaded plugins
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "$ref:Plugin"
        ]
     

-----------------------------------------------------
## GET /api/v1/plugins/{pluginId}"
-----------------------------------------------------
* JSON RPC method: -
* Description: Returns the vendor with the given `{vendorId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        
        "$ref:Plugin"

-----------------------------------------------------
## GET /api/v1/plugins/{pluginId}/configuration"
-----------------------------------------------------
* JSON RPC method: Devices.GetPluginConfiguration
* Description: Returns the plugin configuration of the given `{pluginId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        {
            configuration": [
                "$ref:Param"
            ]
        }


-----------------------------------------------------
## PUT /api/v1/plugins/{pluginId}/configuration"
-----------------------------------------------------
* JSON RPC method: Devices.SetPluginConfiguration
* Description: Set the configuration of the plugin with the given `{pluginId}`
* Request:
        
        PUT /api/v1/plugins/{pluginId}/configuration
        Content-Type: application/json; charset="utf-8";

        {
            configuration": [
                "$ref:Param"
            ]
        }

* Response:
        
        HTTP/1.1 200 Ok

        
        

=====================================================
# Rules resource
=====================================================
     
-----------------------------------------------------
## GET /api/v1/rules=deviceId={deviceId}"
-----------------------------------------------------
* JSON RPC method: Rules.GetRules
* Description: Returns the list of rule descriptions 
* Optional parameters:
    
        deviceId -> filter rules with the given deviceId in it 

* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        [
            "ref:RuleDescription"
        ]
     

-----------------------------------------------------
## GET /api/v1/rules/{ruleId}"
-----------------------------------------------------
* JSON RPC method: Rules.GetRuleDetails
* Description: Returns the details of the rule with the given `{ruleId}`
* Response:
        
        HTTP/1.1 200 Ok
        Content-Type: application/json; charset="utf-8";
        
        "ref:Rule"




