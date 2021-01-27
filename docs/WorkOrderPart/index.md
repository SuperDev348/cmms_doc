# Create WorkOrderPart

This object is used to represent work orders. A work order is a set of maintenance tasks that have to be executed by some assigned users on a given asset. 

Create an WorkOrderPart if  WorkOrderPart does not already exist.

**URL** : `/api/workorderpart`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intWorkOrderID |  Integer    | The ID of the work order the part will be needed for.|
|  intAssetID |  Integer    | The ID of the asset the part will be needed for. For getting possible values, please refer to the Asset section.|
|  intStockID |  Integer    | The ID of the stock representing the part. For getting possible values, please refer to the Stock section.|
|  intPartID |  Integer    | The ID of the asset associated with the stock that represents the part. For getting possible values, please refer to the Asset section.|
|  qtySuggestedQuantity |  Integer    | This field can be used to indicate the quantity that is going to be used for this part to perform the work order.|
|  qtyActualQuantityUsed |  integer    | This field can be used to indicate the quantity that was actually used to performed the work order.|
|  intUpdated |  integer     | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|
|  dv_intWorkOrderID |  string    |The code of the work order. For example : "WO 2009-09-01.0010.00048.Any". For more details, please refer to the WorkOrder section.|
|  dv_intPartID |  String    |The name and the code of the asset associated with the stock that represents the part.|
|  dv_intAssetID |  String    |The name and the code of the asset the part will be used to perform the work order on.|
|  dv_intStockID |  String    |The display value for the stock associated with the part. For example "Asset (asset code) at facility x aisle y row z".|

* Data example 

```json
{
    "intPriorityID": 4156,
    "intSiteID": 9,
    "strCode": "2009-02-05.0004.00004",
    "strCompletionNotes": "strCompletionNotes",
    "intRCACauseID": 4
    ... ...
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "WorkOrderPart added successfully!",
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


# Get all workorderpart list

Get the all registered workorderpart list.

**URL** : `/api/workorderpart`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "WorkOrderPart list found!",
    "data": [
        {
            "_id": "5f6a6f90d9741d152c754178",
            "intWorkOrderID": 11,
            "intAssetID": 22,
            "intStockID": 33,
            "intPartID": null,
            "qtySuggestedQuantity": "",
            "qtyActualQuantityUsed": "",
            "intUpdated": "",
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

# Get Single WorkOrderPart By Id

Get a single WorkOrderPart by id if current workorderpart was registered on it.

**URL** : `/api/workorderpart/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the workorderpart.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Workorderpart found!",
    "data": 
        {
            "_id": "5f6896897b9884253cf6bdb6",
            "intWorkOrderID": 1234,
            "intAssetID": 5678,
            "intStockID": 1111,
            "intPartID": 3434,
            "qtySuggestedQuantity": 2,
            "qtyActualQuantityUsed": 4
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

**Condition** : If WorkOrderPart does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "WorkOrderPart not found", 
   "data":null
}
```

# Update WorkOrderPart

Update the WorkOrderPart by Id

**URL** : `/api/workorderpart/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the workorder.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intWorkOrderID |  Integer    | The ID of the work order the part will be needed for.|
|  intAssetID |  Integer    | The ID of the asset the part will be needed for. For getting possible values, please refer to the Asset section.|
|  intStockID |  Integer    | The ID of the stock representing the part. For getting possible values, please refer to the Stock section.|
|  intPartID |  Integer    | The ID of the asset associated with the stock that represents the part. For getting possible values, please refer to the Asset section.|
|  qtySuggestedQuantity |  Integer    | This field can be used to indicate the quantity that is going to be used for this part to perform the work order.|
|  qtyActualQuantityUsed |  integer    | This field can be used to indicate the quantity that was actually used to performed the work order.|
|  intUpdated |  integer     | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|
|  dv_intWorkOrderID |  string    |The code of the work order. For example : "WO 2009-09-01.0010.00048.Any". For more details, please refer to the WorkOrder section.|
|  dv_intPartID |  String    |The name and the code of the asset associated with the stock that represents the part.|
|  dv_intAssetID |  String    |The name and the code of the asset the part will be used to perform the work order on.|
|  dv_intStockID |  String    |The display value for the stock associated with the part. For example "Asset (asset code) at facility x aisle y row z".|

* Data example 

```json
{
    "intWorkOrderID": 556,
    "intAssetID": 789,
    "intStockID": 98786,
    "intPartID": 8564,
    "qtySuggestedQuantity":545"
    ... ...
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example

```json
{
   "msg": "WorkOrderPart updated successfully!"
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

# Delete WorkOrderPart

Delete a WorkOrderPart by Id

**URL** : `/api/workorderpart/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the workorderpart.

** Success Response:**

**Code** : `200 success`

* Resonse example 

```json
{
    "msg": "WorkOrderPart deleted successfully!",
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
