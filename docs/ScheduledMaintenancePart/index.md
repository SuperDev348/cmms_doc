
# ScheduledMaintenancePart

A ScheduledMaintenancePart represents the relationship between a particular ScheduledMaintenance within your CMMS and the associated Parts in the CMMS. It contains information about the Part and Asset that is tied to this ScheduledMaintenance. See the ScheduledMaintenance, Part, and Asset objects for more details and information.

Create an ScheduledMaintenancePart if  ScheduledMaintenancePart does not already exist.


**URL** : `/api/scheduledmaintenancepart`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intScheduledMaintenanceID |  Integer  |An integer that uniquely identifies the ScheduledMaintenance that have associated Parts.|
|  intPartID	 |  Integer    | An integer that uniquely identifies the Part that is associated to a ScheduledMaintenance.|
|  intAssetID	 |  Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|
|  intStockID	 |  Integer    | An integer representing the id of the associated Stock|
|  qtySuggestedQuantity	 |  Integer    | An integer representing the suggested quantity to be used to complete the task|


* Data example 

```json
{
    "intScheduledMaintenanceID": 2,
    "intPartID": 12,
    "intAssetID": 2,
    "intStockID": 12,
    "qtySuggestedQuantity": 2
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

**URL** : `/api/scheduledmaintenancepart`

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
            "intPartID": 12,
            "intAssetID": 2,
            "intStockID": 12,
            "qtySuggestedQuantity": 2,
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

**URL** : `/api/scheduledmaintenancepart/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intScheduledMaintenanceID |  Integer  |An integer that uniquely identifies the ScheduledMaintenance that have associated Parts.|
|  intPartID	 |  Integer    | An integer that uniquely identifies the Part that is associated to a ScheduledMaintenance.|
|  intAssetID	 |  Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|
|  intStockID	 |  Integer    | An integer representing the id of the associated Stock|
|  qtySuggestedQuantity	 |  Integer    | An integer representing the suggested quantity to be used to complete the task|


* Data example 

```json
{
    "intScheduledMaintenanceID": 2,
    "intPartID": 12,
    "intAssetID": 2,
    "intStockID": 12,
    "qtySuggestedQuantity": 2
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

**URL** : `/api/scheduledmaintenancepart/:scheduledmaintenancepartid`

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
            "intPartID": 12,
            "intAssetID": 2,
            "intStockID": 12,
            "qtySuggestedQuantity": 2,
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

**URL** : `/api/scheduledmaintenancepart/:scheduledmaintenancepartid`

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
