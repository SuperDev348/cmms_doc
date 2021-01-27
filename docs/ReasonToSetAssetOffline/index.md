# Create ReasonToSetAssetOffline

A ReasonToSetAssetOffline represents a Maintenance job that is to be done and executed by the assigned user. It contains information about the ReasonToSetAssetOffline Maintenance Type, Date created, Priority level, Site it resides in, Asset(s) involved, and assigned User.
See the MaintennaceType, SheduledMaintenaceUser, SheduledMaintenancePart, and ReasonToSetAssetOfflineAsset objects for more details and information. You can have multiple ReasonToSetAssetOffline associated in your CMMS.

Create a ReasonToSetAssetOffline if  ReasonToSetAssetOffline does not already exist.

**URL** : `/api/reasontosetassetoffline`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  strName |  string     | A string that identifies the name of the ReasonToSetAssetOffline.|
|  intUpdated |  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|

**Success Response: **

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
    "msg": "Create failed"
}
```

# Get all ReasonToSetAssetOffline list

Get the all registered ReasonToSetAssetOffline list.

**URL** : `/api/reasontosetassetoffline`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": [
        {
            "_id": "5",
            "strName":"name ...",
            "intUpdated":Integer,      
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

# Get Single ReasonToSetAssetOffline By Id

Get a single ReasonToSetAssetOffline by id if current ReasonToSetAssetOffline was registered on it.

**URL** : `/api/reasontosetassetoffline/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ReasonToSetAssetOffline.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "5",
            "strName":"name ...",
            "intUpdated":Integer          
        }
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

** Or **

**Condition** : If ReasonToSetAssetOffline does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Update ReasonToSetAssetOffline

Update the ReasonToSetAssetOffline by Id

**URL** : `/api/reasontosetassetoffline/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ReasonToSetAssetOffline.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  strName |  string     | A string that identifies the name of the ReasonToSetAssetOffline.|
|  intUpdated |  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Updated successfully!"
    }
```

** Error Responses:**

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

# Delete ReasonToSetAssetOffline

Delete a ReasonToSetAssetOffline by Id

**URL** : `/api/reasontosetassetoffline/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ReasonToSetAssetOffline.

**  Success Response: **

**Code** : `200 success`

* Resonse example

```json
{
    "msg": "Deleted successfully!",
    data: null
}
```

** Error Responses : **

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
