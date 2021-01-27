# Create WorkOrderStatus

Create a WorkOrderStatus if  WorkOrderStatus does not already exist.

**URL** : `/api/workorderstatus`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       |Required|Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  strName | | String    | The display name of the status.|
|  intControlID | Yes| Integer    | The control ID is used to associated the status with a more general state of the work order workflow. Possible values are :100 for Pending, 101 for Active, 102 for Closed and 103 for Draft.|
|  intSysCode | | Integer    | The system codes are used to identify statuses with a special meaning for the CMMS. Possible values are:2 for Requested, 3 for Assigned, 4 for Open, 5 for Work In Progress, 6 for On Hold, 7 for Closed, Completed,8 for Draft and 9 for Closed, Incomplete.|


** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "12"}
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
    "msg": "intControlID is required"
}
```
```json
{
    "msg": "Create failed"
}
```

# Get all WorkOrderStatus list

Get the all registered WorkOrderStatus list.

**URL** : `/api/workorderstatus`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


** Success Response: ** 

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "WorkOrder list found!",
    "data": [
        {
            "_id": "11",
            "strName":"String"
            "intControlID": 100,
            "intSysCode": 3,
            "intUpdated": 2020-11-09T07:35:22.052+00:00,
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

# Get Single WorkOrderStatus By Id 

Get a single WorkOrderStatus by id if current WorkOrderStatus was registered on it.

**URL** : `/api/workorderstatus/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the workorder.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Workorder found!",
    "data": 
        {
            "_id": "11",
            "strName":"String"
            "intControlID": 100,
            "intSysCode": 3,
            "intUpdated": 2020-11-09T07:35:22.052+00:00,
        
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

**Condition** : If workorderstatus does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Update WorkOrderStatus

Update the WorkOrderStatus by Id

**URL** : `/api/workorderstatus/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the WorkOrderStatus.

| Param       |Required|Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  strName | | String    | The display name of the status.|
|  intControlID | Yes| Integer    | The control ID is used to associated the status with a more general state of the work order workflow. Possible values are :100 for Pending, 101 for Active, 102 for Closed and 103 for Draft.|
|  intSysCode | | Integer    | The system codes are used to identify statuses with a special meaning for the CMMS. Possible values are:2 for Requested, 3 for Assigned, 4 for Open, 5 for Work In Progress, 6 for On Hold, 7 for Closed, Completed,8 for Draft and 9 for Closed, Incomplete.|


** Success Response: **

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
    "msg": "update failed"
}
```

# Delete WorkOrderStatus

Delete a WorkOrderStatus by Id

**URL** : `/api/workorderstatus/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the WorkOrderStatus.

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
