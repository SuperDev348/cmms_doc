# Create AssetEventType

This object is used to represent the different types of events that can occur to an asset. The event types are defined by each tenant.

Create an AssetEventType if  AssetEventType does not already exist.

**URL** : `/api/asseteventtype`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  strEventCode |  String    | A string that represents an event code.|
|  strEventDescription |  String    | A string that represents an event description.|
|  strEventName |  String    | A string that represents an event name.|

** Success Response **
 
**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "57"}
    }
```

** Error Responses **

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

* Resonse example 

```json
{
    "msg": "JWT token varified failed!",
    "data":null
}
```

```json
{
    "msg": "JWT token expired!",
    "data":null
}
```

**Condition** : If fields are missed or put the wrong type of value.

**Code** : `400 BAD REQUEST`

* Content example 

```json
{
    "msg": "Create failed"
}
```

# Get all AssetEventType list

Get the all registered AssetEventType list.

**URL** : `/api/asseteventtype`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


** Success Response: **

**Code** : `200 success`

**Resonse example:**


```json
{
    "msg": "Found!",
    "data": [
        {
            "id": 47,
            "strEventCode": "AssetEventType_Code_Name",
            "strEventDescription": "AssetEventType_Desc_Name"
            "__v": 0
        },
        ...
    ]
}
```

** Error Responses **

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

* Resonse example 

```json
{
    "msg": "JWT token varified failed!",
    "data":null
}
```

```json
{
    "msg": "JWT token expired!",
    "data":null
}
```
**Condition** : Internal Server Error.

**Code** : `500`

* Resonse example 

```json
{
    "msg": "Internal Server error"
}
```

# Get Single AssetEventType By Id

Get a single AssetEventType by id if current AssetEventType was registered on it.

**URL** : `/api/asseteventtype/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the AssetEventType.

** Success Response **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Workorder found!",
    "data": 
        {
            "id": 47,
            "strEventCode": "AssetEventType_Code_Name",
            "strEventDescription": "AssetEventType_Desc_Name"
        }
}
```

** Error Responses **

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

* Resonse example 

```json
{
    "msg": "JWT token varified failed!",
    "data":null
}
```

```json
{
    "msg": "JWT token expired!",
    "data":null
}
```

** Or **

**Condition** : If AssetEventType does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```
# Update AssetEventType

Update the AssetEventType by Id

**URL** : `/api/asseteventtype/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the workorder.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  strEventCode |  String    | A string that represents an event code.|
|  strEventDescription |  String    | A string that represents an event description.|
|  strEventName |  String    | A string that represents an event name.|

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Updated successfully!"
    }
```

** Error Responses **

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

* Resonse example 

```json
{
    "msg": "JWT token varified failed!",
    "data":null
}
```

```json
{
    "msg": "JWT token expired!",
    "data":null
}
```

**Condition** : If fields are missed or put the wrong type of value.

**Code** : `400 BAD REQUEST`

* Content example

```json
{
    "msg": "Update failed"
}
```

# Delete AssetEventType

Delete a AssetEventType by Id

**URL** : `/api/asseteventtype/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the AssetEventType.

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
    "msg": "Deleted successfully!",
    data: null
}
```

** Error Responses **

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

* Resonse example 

```json
{
    "msg": "JWT token varified failed!",
    "data":null
}
```

```json
{
    "msg": "JWT token expired!",
    "data":null
}
```

**Condition** : If there was no asset available to delete.

**Code** : `400 BAD REQUEST`

* Content example 

```json
{
    "msg": "Delete failed",
    "data":null
}
```
