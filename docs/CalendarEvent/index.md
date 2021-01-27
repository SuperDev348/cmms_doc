
# CalendarEvent

A CalendarEvent represents a certain Maintenance object such as a Work Order that is assigned to a User on a specific Date for a ScheduleTrigger or ScheduledMaintenance. The CalendarEvent is associated with your CMMS. It contains information about the timestamp Date for the CalendarEvent and the associated ScheduleTrigger. An Example Scenario: You have an Asset in the CMMS. The Asset is of type Facility. The Facility has a Work Order attached to it. The Work Order has certain Labor Tasks for certain users attached to it. For a certain Date, a CalendarEvent can be created for this Work Order where a ScheduleTrigger and ScheduledMaintenance can be assigned to a User. See the WorkOrder object for more details. You can have multiple CalendarEvents associated in your CMMS.

Create an CalendarEvent if  CalendarEvent does not already exist.


**URL** : `/api/calendarevent`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intScheduledMaintenanceID |  Integer    | An integer that uniquely identifies the ScheduledMaintenance.|
|  intScheduleTriggerID |  Integer    | An integer that uniquely identifies the ScheduleTrigger.|
|  dtmDate |  Timestamp    | A datetime stamp that identifies the the Date for the CalendarEvent.|

* Data example 

```json
{
    "intScheduledMaintena": 12,
    "intScheduleTriggerID": 12,
    "dtmDate": 2020-11-26T09:00:36.285+00:00 
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

**URL** : `/api/calendarevent`

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
            "intScheduledMaintena": 12,
            "intScheduleTriggerID": 12,
            "dtmDate": 2020-11-26T09:00:36.285+00:00 
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

**URL** : `/api/calendarevent/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intScheduledMaintenanceID |  Integer    | An integer that uniquely identifies the ScheduledMaintenance.|
|  intScheduleTriggerID |  Integer    | An integer that uniquely identifies the ScheduleTrigger.|
|  dtmDate |  Timestamp    | A datetime stamp that identifies the the Date for the CalendarEvent.|

* Data example 

```json
{
    "intScheduledMaintena": 12,
    "intScheduleTriggerID": 12,
    "dtmDate": 2020-11-26T09:00:36.285+00:00 
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

**URL** : `/api/calendarevent/:calendareventid`

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
            "intScheduledMaintena": 12,
            "intScheduleTriggerID": 12,
            "dtmDate": 2020-11-26T09:00:36.285+00:00 
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

**URL** : `/api/calendarevent/:calendareventid`

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
