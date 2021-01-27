# Create AssetEvent
This object represents an event that has occurred on an asset. The type of events that can occur are stored in the AssetEventType object and are defined by each tenant.

Create an AssetEvent if  AssetEvent does not already exist.

**URL** : `/api/assetevent`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param      | Required  | Type     | Description     | 
| :------------- | :----------- |:----------- |----------- |
|  dtmDateSubmitted | Yes  |timestamp     | The date and time when the event was submitted (UNIX epoch milliseconds).|
|  intAssetEventTypeID | Yes | Integer     | An integer that represents the id of an AssetEventType.|
|  intAssetID | Yes | Integer     |An integer that represents the id of an Asset.|
|  intSubmittedByUserID |  | Integer     |An integer that represents the id of a User who submitted the event.|
|  intWorkOrderID |  | Integer     |An integer that represents the id of a WorkOrder, if this event originated from a Work Order. This can be null.|
|  strAdditionalDescription |  | String     |A string that represents description of the event.|

** Success Response:**

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "5"}
    }
```

** Error Responses: **

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
    "msg": "dtmDateSubmitted is required"
}
```
```json
{
    "msg": "Create failed"
}
```
# Get all AssetEvent list

Get the all registered AssetEvent list by AssetId.

**URL** : `/api/assetevent/:assetId`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

** Success Response: **

**Code** : `200 success`

* Resonse example


```json
{
    "msg": "Found!",
    "data": [
        {
            "_id": "5",
            "dtmDateSubmitted": 2020-10-30T20:26:49.518+00:00,
            "intAssetEventTypeID": 4,
            "intAssetID": 3,
            "intSubmittedByUserID":5,
            "intWorkOrderID":6,
            "strAdditionalDescription":"String"
            "__v": 0
        },
        ...
    ]
}
```

** Error Responses: **

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

# Update AssetEvent

Update the AssetEvent by Id

**URL** : `/api/assetevent/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the AssetEvent.

| Param      | Required  | Type     | Description     | 
| :------------- | :----------- |:----------- |----------- |
|  dtmDateSubmitted | Yes  |timestamp     | The date and time when the event was submitted (UNIX epoch milliseconds).|
|  intAssetEventTypeID | Yes | Integer     | An integer that represents the id of an AssetEventType.|
|  intAssetID | Yes | Integer     |An integer that represents the id of an Asset.|
|  intSubmittedByUserID |  | Integer     |An integer that represents the id of a User who submitted the event.|
|  intWorkOrderID |  | Integer     |An integer that represents the id of a WorkOrder, if this event originated from a Work Order. This can be null.|
|  strAdditionalDescription |  | String     |A string that represents description of the event.|

** Success Response **

**Code** : `200 success`

* Resonse example

```json
{
   "msg": "Updated successfully!"
    }
```

** Error Responses: **

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

# Delete AssetEvent

Delete a AssetEvent by Id

**URL** : `/api/assetevent/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the assetevent.

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
    "msg": "Deleted successfully!",
    data: null
}
```

** Error Responses: **

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
