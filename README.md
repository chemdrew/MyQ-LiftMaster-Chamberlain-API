# MyQ API

> the liftmaster/chamberlain apps kinda suck (slow, incorrect states, no touchid login - issue since it always kicks me out, and no geofencing)<br> So these were the api calls I needed to make a useable app 

protocol=https<br>
domain=myqexternal.myqdevice.com

## `POST /api/v4/User/Validate`

<b>headers</b>
```
{
  "MyQApplicationId": "NWknvuBd7LoFHfXmKNMBcgajXtZEgKUh4V7WNzMidrpUUluDpVYVZx+xT4PCM5Kx",
  "Content-Type": "application/json"
}
```

<b>body</b>
```
{
    "username": "string",
    "password": "string"
}
```

<b>response</b>
```
{
    "SecurityToken": "uuid",
    "ReturnCode": "int string",
    "ErrorMessage": "string",
    "CorrelationId": "uuid"
}
```

## `GET /api/v4/userdevicedetails/get`

<b>headers</b>
```
{
  "MyQApplicationId": "NWknvuBd7LoFHfXmKNMBcgajXtZEgKUh4V7WNzMidrpUUluDpVYVZx+xT4PCM5Kx",
  "SecurityToken": "uuid",
  "Content-Type": "application/json"
}
```

<b>response</b>
```
{
    "Devices": [
        {
            "MyQDeviceId": integer,
            "ParentMyQDeviceId": integer,
            "MyQDeviceTypeId": integer,
            "MyQDeviceTypeName": "string",
            "RegistrationDateTime": "iso timestamp",
            "SerialNumber": "string",
            "UserName": "string",
            "UserCountryId": integer,
            "Attributes": [
                {
                    "MyQDeviceTypeAttributeId": integer,
                    "Value": "string",
                    "UpdatedTime": "epoch string",
                    "IsDeviceProperty": boolean,
                    "AttributeDisplayName": "string",
                    "IsPersistent": boolean,
                    "IsTimeSeries": boolean,
                    "IsGlobal": boolean,
                    "UpdatedDate": "iso string"
                }
            ],
            "ChildrenMyQDeviceIds": "string",
            "UpdatedBy": "string",
            "UpdatedDate": "iso string",
            "ConnectServerDeviceId": "string"
        }
    ],
    "ReturnCode": "string",
    "ErrorMessage": "string",
    "CorrelationId": "uuid"
}
```

## `GET /api/v4/deviceattribute/getdeviceattribute?AttributeName=name&MyQDeviceId=id`

<b>headers</b>
```
{
  "MyQApplicationId": "NWknvuBd7LoFHfXmKNMBcgajXtZEgKUh4V7WNzMidrpUUluDpVYVZx+xT4PCM5Kx",
  "SecurityToken": "uuid",
  "Content-Type": "application/json"
}
```

<b>response</b>
```
{
    "MyQDeviceTypeAttributeId": integer,
    "Value": "string",
    "UpdatedTime": "epoch string",
    "IsDeviceProperty": boolean,
    "AttributeDisplayName": "string",
    "IsPersistent": boolean,
    "IsTimeSeries": boolean,
    "IsGlobal": boolean,
    "UpdatedDate": "iso string"
}
```

## `PUT /api/v4/deviceattribute/putdeviceattribute`

<b>headers</b>
```
{
  "MyQApplicationId": "NWknvuBd7LoFHfXmKNMBcgajXtZEgKUh4V7WNzMidrpUUluDpVYVZx+xT4PCM5Kx",
  "SecurityToken": "uuid",
  "Content-Type": "application/json"
}
```

<b>body</b>
```
{
  "MyQDeviceId": integer,
  "AttributeName": "desireddoorstate",
  "AttributeValue": Enum[
    "0" = close
    "1" = open
  ]
}
```

<b>response</b>
```
{
  "UpdatedTime": "epoch string",
  "ReturnCode": "string integer",
  "ErrorMessage": "string",
  "CorrelationId": "uuid"
}
