# Create ScheduledMaintenance

A ScheduledMaintenance represents a Maintenance job that is to be done and executed by the assigned user. It contains information about the ScheduledMaintenance Maintenance Type, Date created, Priority level, Site it resides in, Asset(s) involved, and assigned User.
See the MaintennaceType, SheduledMaintenaceUser, SheduledMaintenancePart, and ScheduledMaintenanceAsset objects for more details and information. You can have multiple ScheduledMaintenance associated in your CMMS.

Create a ScheduledMaintenance if  ScheduledMaintenance does not already exist.

**URL** : `/api/scheduledmaintenance`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intPriorityID |  Integer    | The ID of the priority level for this scheduled maintenace. For getting possible values, please refer to the Priority section.|
|  intSiteID |  Integer    | For multi-sites tenants, the ID of the site where the maintenace is taking place at. A site is an asset itself, so for possible values, please refer to the Asset section.|
|  intStartAsWorkOrderStatusID |  Integer    | An Integer that represents the id of a WorkOrderStatus|
|  intScheduledMaintenanceStatusID |  Integer    | An integer that represents the status of the ScheduledMaintenance. Possible values STATUS_PAUSED=0, STATUS_PLAYING=1|
|  intSuggestedCompletion |  Integer    | The estimated number of days that the generated work order should be completed by.|
|  dtmUpdatedDate |  timestamp    | The date and time when the ScheduledMaintenace was updated(UNIX epoch miliseconds).|
| strCode|  String    | A code that represents the ScheduledMaintenace|
| intProjectId|  Integer   | The ID of the Project.|
| strCompletionNotes|  String   | A string that represents the completion notes on this ScheduledMaintenace.|
| dtmCreateDate|  timestamp   | The date and time when the ScheduledMaintenance was created (UNIX epoch milliseconds).|
| intMaintenanceTypeID|  Integer   | An integer that represents the id of the MaintenaceType|
| intRequestorUserID|  Integer   |An integer that represents the id of a User who requested the scheduled maintenace.|
| strDescription|  String   |As string that represents the description on the ScheduledMaintenance.|
| bolCanFireSMwithOpenWO|  boolean   |If set to true, a new work order will be created even if there are existing work orders taht are not closed from this scheduled maintenace.|
| bolWORequiresSignature|  boolean   |If set to true, indicates that the Work Orders generated from the ScheduledMaintenance need to be signed. A Work Order generated from the ScheduledMaintenace does not need to be signed if this is set to false.|

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

# Get all ScheduledMaintenace list

Get the all registered ScheduledMaintenace list.

**URL** : `/api/scheduledmaintenace`

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
            "intPriorityID":"Integer",
            "intSiteID":Object,
            "intStartAsWorkOrderStatusID":3,
            "intScheduledMaintenanceStatusID":"Integer",
            "intSuggestedCompletion":"Integer",
            "dtmUpdatedDate":2020-11-09T07:35:22.052+00:00,
            "strCode":"String",
            "intProjectID":Object,
            "strCompletionNotes":"String",
            "dtmCreateDate":2020-11-09T07:35:22.052+00:00,
            "intMaintenanceTypeID":"Integer",
            "intRequestorUserID":"Integer",
            "strDescription":"String",
            "bolCanFireSMWithOpenWO":true,
            "bolWORequiresSignature":true,
            "intAccountID":Object,
            "intChargeDepartmentID":Object,
            "intAssignedToUserID":Object,
            "strWorkInstruction":"String",
			"dblTimeEstimatedHours":2.5
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

# Get Single ScheduledMaintenace By Id

Get a single ScheduledMaintenace by id if current ScheduledMaintenace was registered on it.

**URL** : `/api/scheduledmaintenance/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ScheduledMaintenace.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "5",
            "intPriorityID":"Integer",
            "intSiteID":Object,
            "intStartAsWorkOrderStatusID":3,
            "intScheduledMaintenanceStatusID":"Integer",
            "intSuggestedCompletion":"Integer",
            "dtmUpdatedDate":2020-11-09T07:35:22.052+00:00,
            "strCode":"String",
            "intProjectID":Object,
            "strCompletionNotes":"String",
            "dtmCreateDate":2020-11-09T07:35:22.052+00:00,
            "intMaintenanceTypeID":"Integer",
            "intRequestorUserID":"Integer",
            "strDescription":"String",
            "bolCanFireSMWithOpenWO":true,
            "bolWORequiresSignature":true,
            "intAccountID":Object,
            "intChargeDepartmentID":Object,
            "intAssignedToUserID":Object,
            "strWorkInstruction":"String",
			"dblTimeEstimatedHours":2.5
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

**Condition** : If ScheduledMaintenace does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Update ScheduledMaintenace

Update the ScheduledMaintenace by Id

**URL** : `/api/scheduledmaintenance/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ScheduledMaintenace.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intPriorityID |  Integer    | The ID of the priority level for this scheduled maintenace. For getting possible values, please refer to the Priority section.|
|  intSiteID |  Integer    | For multi-sites tenants, the ID of the site where the maintenace is taking place at. A site is an asset itself, so for possible values, please refer to the Asset section.|
|  intStartAsWorkOrderStatusID |  Integer    | An Integer that represents the id of a WorkOrderStatus|
|  intScheduledMaintenanceStatusID |  Integer    | An integer that represents the status of the ScheduledMaintenance. Possible values STATUS_PAUSED=0, STATUS_PLAYING=1|
|  intSuggestedCompletion |  Integer    | The estimated number of days that the generated work order should be completed by.|
|  dtmUpdatedDate |  timestamp    | The date and time when the ScheduledMaintenace was updated(UNIX epoch miliseconds).|
| strCode|  String    | A code that represents the ScheduledMaintenace|
| intProjectId|  Integer   | The ID of the Project.|
| strCompletionNotes|  String   | A string that represents the completion notes on this ScheduledMaintenace.|
| dtmCreateDate|  timestamp   | The date and time when the ScheduledMaintenance was created (UNIX epoch milliseconds).|
| intMaintenanceTypeID|  Integer   | An integer that represents the id of the MaintenaceType|
| intRequestorUserID|  Integer   |An integer that represents the id of a User who requested the scheduled maintenace.|
| strDescription|  String   |As string that represents the description on the ScheduledMaintenance.|
| bolCanFireSMwithOpenWO|  boolean   |If set to true, a new work order will be created even if there are existing work orders taht are not closed from this scheduled maintenace.|
| bolWORequiresSignature|  boolean   |If set to true, indicates that the Work Orders generated from the ScheduledMaintenance need to be signed. A Work Order generated from the ScheduledMaintenace does not need to be signed if this is set to false.|

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

# Delete ScheduledMaintenace

Delete a ScheduledMaintenace by Id

**URL** : `/api/scheduledmaintenance/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ScheduledMaintenace.

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
