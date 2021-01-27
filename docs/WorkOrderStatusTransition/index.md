# Create WorkOrderStatusTransition

This object is used to represent work orders. A work order is a set of maintenance tasks that have to be executed by some assigned users on a given asset. 

Create an WorkOrderStatusTransition if  WorkOrderStatusTransition does not already exist.

**URL** : `/api/workorderstatustransition`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intFromWorkOrderStatusID |  Integer    | The ID of the previous Work Order status that was changed. For getting possible values, please refer to the WorkOrderStatus section. |
|  intToWorkOrderStatusID |  Integer    | TThe ID of the new Work Order status that was set on the Work Order. For getting possible values, please refer to the WorkOrderStatus section.|
|  intUserID |  Integer    | The ID of the user that made the status transition on a Work Order. For getting possible values, please refer to the User section.|
|  intWorkOrderID |  Integer    | TThe ID of the Work Order on which the status was changed. For getting possible values, please refer to the WorkOrder section.|
|  dtmDate |  Date    | The date and time when the status transition was made.|
|  dv_intFromWorkOrderStatusID |  string    |The name of the WorkOrderStatus associated with intFromWorkOrderStatusID.|
|  dv_intToWorkOrderStatusID |  String    |The name of the WorkOrderStatus associated with intToWorkOrderStatusID.|
|  dv_intUserID |  String    |The name of the User associated with the intUserID.|
|  dv_intWorkOrderID |  String    |The code of the WorkOrder associated with intWorkOrderID.
|

* Data example 

```json
{
    "intFromWorkOrderStatusID": 4156,
    "intToWorkOrderStatusID": 9,
    "intUserID": 9,
    "intWorkOrderID": 9,
    "dtmDate": "2009-02-05.0004.00004",
    ... ...
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "WorkOrderStatusTransition added successfully!",
    "data": {id: "4rt8a89c24753232419483c"}
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
    "msg": "intWorkOrderStatusID is required"
}
```
```json
{
    "msg": "Create failed"
}
```


# Get all WorkOrderStatusTransition list

Get the all registered WorkOrderStatusTransition list.

**URL** : `/api/workorderstatustransition`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "WorkOrderStatusTransition list found!",
    "data": [
        {
            "_id": "5f6a6f90d9741d152c754178",
            "intFromWorkOrderStatusID": 4156,
            "intToWorkOrderStatusID": 9,
            "intUserID": 9,
            "intWorkOrderID": 9,
            "dtmDate": "2009-02-05.0004.00004",
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
    "msg": "Internal Server error."
}
```

# Get Single WorkOrderStatusTransition By Id

Get a single WorkOrderStatusTransition by id if current WorkOrderStatusTransition was registered on it.

**URL** : `/api/workorderstatustransition/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the WorkOrderStatusTransition.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "WorkOrderStatusTransition found!",
    "data": 
        {
            "_id": "5f6896897b9884253cf6bdb6",
            "intFromWorkOrderStatusID": 4156,
            "intToWorkOrderStatusID": 9,
            "intUserID": 9,
            "intWorkOrderID": 9,
            "dtmDate": "2009-02-05.0004.00004",
            ...
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

**Condition** : If WorkOrderStatusTransition does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "WorkOrderStatusTransition not found", 
   "data":null
}
```

# Update WorkOrderStatusTransition

Update the WorkOrderStatusTransition by Id

**URL** : `/api/workorderstatustransition/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the workorder.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intFromWorkOrderStatusID |  Integer    | The ID of the previous Work Order status that was changed. For getting possible values, please refer to the WorkOrderStatus section. |
|  intToWorkOrderStatusID |  Integer    | TThe ID of the new Work Order status that was set on the Work Order. For getting possible values, please refer to the WorkOrderStatus section.|
|  intUserID |  Integer    | The ID of the user that made the status transition on a Work Order. For getting possible values, please refer to the User section.|
|  intWorkOrderID |  Integer    | TThe ID of the Work Order on which the status was changed. For getting possible values, please refer to the WorkOrder section.|
|  dtmDate |  Date    | The date and time when the status transition was made.|
|  dv_intFromWorkOrderStatusID |  string    |The name of the WorkOrderStatus associated with intFromWorkOrderStatusID.|
|  dv_intToWorkOrderStatusID |  String    |The name of the WorkOrderStatus associated with intToWorkOrderStatusID.|
|  dv_intUserID |  String    |The name of the User associated with the intUserID.|
|  dv_intWorkOrderID |  String    |The code of the WorkOrder associated with intWorkOrderID.
|

* Data example 

```json
{
   "intFromWorkOrderStatusID": 4156,
    "intToWorkOrderStatusID": 9,
    "intUserID": 9,
    "intWorkOrderID": 9,
    "dtmDate": "2009-02-05.0004.00004",
    ... ...
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example

```json
{
   "msg": "WorkOrderStatusTransition updated successfully!"
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

# Delete WorkOrderStatusTransition

Delete a WorkOrderStatusTransition by Id

**URL** : `/api/workorderstatustransition/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the WorkOrderStatusTransition.

** Success Response:**

**Code** : `200 success`

* Resonse example 

```json
{
    "msg": "WorkOrderStatusTransition deleted successfully!",
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
