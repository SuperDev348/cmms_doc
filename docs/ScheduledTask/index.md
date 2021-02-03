
# ScheduledTask

A ScheduledTask represents the relationship between a particular ScheduledMaintenance within your CMMS and the associated Task in the CMMS. It contains information about the assigned User, Description, Time estimate (hours), and Task Type. See the User object for more details and information.

Create an ScheduledTask if  ScheduledTask does not already exist.


**URL** : `/api/scheduledtask`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intTaskType |  Integer  |An integer representing the type of the task. Possible values are : 0 for General, 1 for Text Result, 2 for Meter Reading, and 3 for Inspection Task.|
|  dblTimeEstimatedHours	 |  Double    | An estimation of how many hours it should take to perform the task|
|  intAssetID	 |  Integer    | An integer that uniquely identifies the Asset that is associated with the ScheduledTask|
|  intAssignedToUserID	 |  Integer    | An integer that represents the id of a User who the task is assigned to|
|  intMeterReadingUnitID	 |  Integer    | An integer that represents the id of a MeterReadingUnit associated to the task|
|  intOrder	 |  Integer    | An integer representing the relative order in the Scheduled Maintenance of this task. This should be unique to the Scheduled Maintenance|
|  intParentScheduledTaskID	 |  Integer    | An integer that represents the id of the parent scheduled task|
|  intScheduledMaintenanceID	 |  Integer    | An integer that represents the id of a ScheduledMaintenance associated to the task|
|  strDescription	 |  String    | A string that describes the task. E.g. - Replace the air filter|


* Data example 

```json
{
    "intTaskType": 2,
    "dblTimeEstimatedHours": 1.2,
    "intAssetID": 2,
    "intAssignedToUserID": 1,
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

**URL** : `/api/scheduledtask`

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
            "intTaskType": 2,
            "dblTimeEstimatedHours": 1.2,
            "intAssetID": 2,
            "intAssignedToUserID": 1,
            "intMeterReadingUnitID": 1,
            "intOrder": 3,
            "intParentScheduledTaskID": 1,
            "intScheduledMaintenanceID": 2,
            "strDescription": "strDescription",
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

**URL** : `/api/scheduledtask/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intTaskType |  Integer  |An integer representing the type of the task. Possible values are : 0 for General, 1 for Text Result, 2 for Meter Reading, and 3 for Inspection Task.|
|  dblTimeEstimatedHours	 |  Double    | An estimation of how many hours it should take to perform the task|
|  intAssetID	 |  Integer    | An integer that uniquely identifies the Asset that is associated with the ScheduledTask|
|  intAssignedToUserID	 |  Integer    | An integer that represents the id of a User who the task is assigned to|
|  intMeterReadingUnitID	 |  Integer    | An integer that represents the id of a MeterReadingUnit associated to the task|
|  intOrder	 |  Integer    | An integer representing the relative order in the Scheduled Maintenance of this task. This should be unique to the Scheduled Maintenance|
|  intParentScheduledTaskID	 |  Integer    | An integer that represents the id of the parent scheduled task|
|  intScheduledMaintenanceID	 |  Integer    | An integer that represents the id of a ScheduledMaintenance associated to the task|
|  strDescription	 |  String    | A string that describes the task. E.g. - Replace the air filter|


* Data example 

```json
{
    "intTaskType": 2,
    "dblTimeEstimatedHours": 1.2,
    "intAssetID": 2,
    "intAssignedToUserID": 1,
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

**URL** : `/api/scheduledtask/:scheduledtaskid`

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
            "intTaskType": 2,
            "dblTimeEstimatedHours": 1.2,
            "intAssetID": 2,
            "intAssignedToUserID": 1,
            "intMeterReadingUnitID": 1,
            "intOrder": 3,
            "intParentScheduledTaskID": 1,
            "intScheduledMaintenanceID": 2,
            "strDescription": "strDescription",
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

**URL** : `/api/scheduledtask/:scheduledtaskid`

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
