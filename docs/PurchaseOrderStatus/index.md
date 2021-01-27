# Create PurchaseOrderStatus

A PurchaseOrderStatus represents a Maintenance job that is to be done and executed by the assigned user. It contains information about the PurchaseOrderStatus Maintenance Type, Date created, Priority level, Site it resides in, Asset(s) involved, and assigned User.
See the MaintennaceType, SheduledMaintenaceUser, SheduledMaintenancePart, and PurchaseOrderStatusAsset objects for more details and information. You can have multiple PurchaseOrderStatus associated in your CMMS.

Create a PurchaseOrderStatus if  PurchaseOrderStatus does not already exist.

**URL** : `/api/purchaseorderstatus`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intSysCode |  Integer    | The system codes are used to identify statuses with a special meaning for the CMMS. Possible values are 1 for Draft, 3 for Waiting For Approval, 4 for Approved, 5 for On order, 6 for Order Fulfilled, 7 for Order Not Fulfilled and 8 for Cancelled.|
|  intControlID |  Integer    | The control ID identifies statuses that can be added by the system or the users to introduce new behavior for the system statuses. The Possible values are 100 for Draft, 101 for Waiting For Approval, 102 for Approved, 103 for On order, 104 for Order Fulfilled, 104 for Order Not Fulfilled and 104 for Cancelled.|
|  strDefaultLabel |  string    | Default labels to be displayed for the possible statuses. For example, "Draft", "Waiting For Approval", "Approved", "On order", "Order Fulfilled", "Order Not Fulfilled" and "Cancelled".|
|  strName |  string    | The names of the purchase order statuses. Possible values are "Draft", "Waiting For Approval", "Approved", "On order", "Order Fulfilled", "Order Not Fulfilled" and "Cancelled".|
|  intUpdated |  integer     | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|

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

# Get all PurchaseOrderStatus list

Get the all registered PurchaseOrderStatus list.

**URL** : `/api/purchaseorderstatus`

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
            "intSysCode":"Integer",
            "intControlID":4,
            "strDefaultLabel":string,
            "strName":"name wirte",
            "intUpdated":3,   
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

# Get Single PurchaseOrderStatus By Id

Get a single PurchaseOrderStatus by id if current PurchaseOrderStatus was registered on it.

**URL** : `/api/purchaseorderstatus/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrderStatus.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "5",
            "intSysCode":"Integer",
            "intControlID":4,
            "strDefaultLabel":string,
            "strName":"name wirte",
            "intUpdated":3           
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

**Condition** : If PurchaseOrderStatus does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Update PurchaseOrderStatus

Update the PurchaseOrderStatus by Id

**URL** : `/api/purchaseorderstatus/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrderStatus.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intSysCode |  Integer    | The system codes are used to identify statuses with a special meaning for the CMMS. Possible values are 1 for Draft, 3 for Waiting For Approval, 4 for Approved, 5 for On order, 6 for Order Fulfilled, 7 for Order Not Fulfilled and 8 for Cancelled.|
|  intControlID |  Integer    | The control ID identifies statuses that can be added by the system or the users to introduce new behavior for the system statuses. The Possible values are 100 for Draft, 101 for Waiting For Approval, 102 for Approved, 103 for On order, 104 for Order Fulfilled, 104 for Order Not Fulfilled and 104 for Cancelled.|
|  strDefaultLabel |  string    | Default labels to be displayed for the possible statuses. For example, "Draft", "Waiting For Approval", "Approved", "On order", "Order Fulfilled", "Order Not Fulfilled" and "Cancelled".|
|  strName |  string    | The names of the purchase order statuses. Possible values are "Draft", "Waiting For Approval", "Approved", "On order", "Order Fulfilled", "Order Not Fulfilled" and "Cancelled".|
|  intUpdated |  integer     | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|


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

# Delete PurchaseOrderStatus

Delete a PurchaseOrderStatus by Id

**URL** : `/api/purchaseorderstatus/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrderStatus.

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
