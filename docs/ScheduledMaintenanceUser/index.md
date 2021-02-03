
# ScheduledMaintenanceUser

A ScheduledMaintenanceUser represents the relationship between a particular ScheduledMaintenance within your CMMS and the associated User in the CMMS. It contains information about the Notification options available to notify the User. See the User and the ScheduledMaintenance objects for more details and information.

Create an ScheduledMaintenanceUser if  ScheduledMaintenanceUser does not already exist.


**URL** : `/api/scheduledmaintenanceuser`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intScheduledMaintenanceID |  Integer  |An integer that uniquely identifies the associated ScheduledMaintenance.|
|  intUserID	 |  Integer    | An integer that uniquely identifies the associated User.|
|  intUserID	 |  Integer    | An integer that uniquely identifies the associated User.|
|  bolNotifyOnAssignment	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified on work order assignment.|
|  bolNotifyOnCompletion	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified on work order completion.|
|  bolNotifyOnOnlineOffline	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified when the asset associated with the work order is set online/offline.|
|  bolNotifyOnStatusChange	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified when the status of the work order changes.|
|  bolNotifyOnTaskCompleted	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified on work order task completion.|


* Data example 

```json
{
    "intScheduledMaintenanceID": 2,
    "intUserID": 12,
    "bolNotifyOnAssignment": false,
    "bolNotifyOnCompletion": true,
    ... ...
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example

```json
{
   "msg": "Created successfully!",
    "data": {id: "5"}
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

**URL** : `/api/scheduledmaintenanceuser`

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
            "intScheduledMaintenanceID": 2,
            "intUserID": 12,
            "bolNotifyOnAssignment": false,
            "bolNotifyOnCompletion": true,
            "bolNotifyOnOnlineOffline": true,
            "bolNotifyOnStatusChange": true,
            "bolNotifyOnTaskCompleted": true,
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

**URL** : `/api/scheduledmaintenanceuser/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intScheduledMaintenanceID |  Integer  |An integer that uniquely identifies the associated ScheduledMaintenance.|
|  intUserID	 |  Integer    | An integer that uniquely identifies the associated User.|
|  intUserID	 |  Integer    | An integer that uniquely identifies the associated User.|
|  bolNotifyOnAssignment	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified on work order assignment.|
|  bolNotifyOnCompletion	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified on work order completion.|
|  bolNotifyOnOnlineOffline	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified when the asset associated with the work order is set online/offline.|
|  bolNotifyOnStatusChange	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified when the status of the work order changes.|
|  bolNotifyOnTaskCompleted	 |  Boolean    | If set to true, when a work order is triggered from the scheduled maintenance, then the user will be notified on work order task completion.|


* Data example 

```json
{
    "intScheduledMaintenanceID": 2,
    "intUserID": 12,
    "bolNotifyOnAssignment": false,
    "bolNotifyOnCompletion": true,
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

**URL** : `/api/scheduledmaintenanceuser/:scheduledmaintenanceuserid`

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
            "intScheduledMaintenanceID": 2,
            "intUserID": 12,
            "bolNotifyOnAssignment": false,
            "bolNotifyOnCompletion": true,
            "bolNotifyOnOnlineOffline": true,
            "bolNotifyOnStatusChange": true,
            "bolNotifyOnTaskCompleted": true,
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

**URL** : `/api/scheduledmaintenanceuser/:scheduledmaintenanceuserid`

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
