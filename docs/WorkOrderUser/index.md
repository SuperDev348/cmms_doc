
# Create WorkOrderUser 

This object is used to specify the users who should be notified upon progression of the work order.

Create an WorkOrderUser if  WorkOrderUser does not already exist.


**URL** : `/api/workorderuser`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intWorkOrderID |  Integer    | The ID of the work order. For getting possible values, please refer to the WorkOrder section.|
|  intUserID |  Integer    | The ID of the user. For getting possible values, please refer to the User section.|
|  bolNotifyOnAssignment | Boolean    | If set to true, the user will be notified on assignment.|
|  bolNotifyOnCompletion | Boolean    | If set to true, the user will be notified on completion.|
|  bolNotifyOnOnlineOffline | Boolean    | If set to true, the user will be notified when the asset associated with the work order is set online/offline.|
|  bolNotifyOnStatusChange | Boolean    | If set to true, the user will be notified when the status of the work order changes.|
|  bolNotifyOnTaskCompleted | Boolean    | If set to true, the user will be notified on task completion.|


* Data example 

```json
{
    "intWorkOrderID": 3,
    "intUserID": 5,
    "bolNotifyOnAssignment": false,
    "bolNotifyOnCompletion": false,
    ... ...
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example

```json
{
   "msg": "Asset added successfully!",
    "data": {id: "4rt8a89c24753232419483c"}
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
    "msg": "strFullName is required"
}
```
```json
{
    "msg": "update failed"
}
```

# Get all asset list

Get the all registered asset list.

**URL** : `/api/workorderuser`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


** Success Response: **

** Code ** : `200 success`

* Resonse example 


```json
{
    "msg": "Asset list found!",
    "data": [
        {
            "_id": "5f6896897b9884253cf6bdb6",
            "intWorkOrderID": 3,
            "intUserID": 5,
            "bolNotifyOnAssignment": false,
            "bolNotifyOnCompletion": false,
            "bolNotifyOnOnlineOffline": false,
            "bolNotifyOnStatusChange": false,
            "bolNotifyOnTaskCompleted": false,
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

# Update Asset

Update the Asset by Id

**URL** : `/api/workorderuser/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intWorkOrderID |  Integer    | The ID of the work order. For getting possible values, please refer to the WorkOrder section.|
|  intUserID |  Integer    | The ID of the user. For getting possible values, please refer to the User section.|
|  bolNotifyOnAssignment | Boolean    | If set to true, the user will be notified on assignment.|
|  bolNotifyOnCompletion | Boolean    | If set to true, the user will be notified on completion.|
|  bolNotifyOnOnlineOffline | Boolean    | If set to true, the user will be notified when the asset associated with the work order is set online/offline.|
|  bolNotifyOnStatusChange | Boolean    | If set to true, the user will be notified when the status of the work order changes.|
|  bolNotifyOnTaskCompleted | Boolean    | If set to true, the user will be notified on task completion.|


* Data example 

```json
{
    "intWorkOrderID": 3,
    "intUserID": 5,
    "bolNotifyOnAssignment": false,
    "bolNotifyOnCompletion": false,
    ... ...
}
```
** Success Response **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Asset updated successfully!"
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
    "msg": "update failed"
}
```

# Get Single Asset By Id 

Get a single Asset by id if current asset was registered on it.

**URL** : `/api/workorderuser/:workorderuserid`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": ""Asset found!",
    "data": 
        {
            "_id": "5f6896897b9884253cf6bdb6",
            "intWorkOrderID": 3,
            "intUserID": 5,
            "bolNotifyOnAssignment": false,
            "bolNotifyOnCompletion": false,
            "bolNotifyOnOnlineOffline": false,
            "bolNotifyOnStatusChange": false,
            "bolNotifyOnTaskCompleted": false,
            "__v": 0
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

**Condition** : If asset does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Asset not found", 
   "data":null
}
```

# Delete  Asset 

Delete the Asset by Id

**URL** : `/api/workorderuser/:workorderuserid`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

** Success Response **
**Code** : `200 success` 

* Resonse example 

```json
{
    "msg": "Asset deleted successfully!",
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
