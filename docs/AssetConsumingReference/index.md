
# Create AssetConsumingReference 

An AssetConsumingReference represents the relationship between a particular Bill Of Materials (BOM) Group within your CMMS and the associated Asset(s) with this CMMS. It contains information about the associated BOM (Control and Part). One example scenario: Bill Of Materials (BOM) Group is setup under Supplies. Once setup, an Asset can use this BOM by tieing one or more Assets to the BOM. This will setup an Asset to consume or take in your BOM and Parts. Alternatively, an Asset can be created first and then assigned a BOM Group (under Parts/BOM). See the Asset object for more details and information. You can have multiple AssetConsumingReference associated in your CMMS.

Create an AssetConsumingReference if  AssetConsumingReference does not already exist.


**URL** : `/api/assetconsumingreference`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intConsumesAssetID |  Integer    | An integer that uniquely identifies the associated Asset.|
|  intBOMControlID |  Integer    | An integer that uniquely identifies the associated BOMControl.|
|  intAssetID | Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|
|  intBOMPartControlID | Integer    | An integer that uniquely identifies the associated BOMPart.|
|  qtyMaxConsumption | Integer    | |
|  intUpdated | Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|


* Data example 

```json
{
    "intConsumesAssetID": 3,
    "intBOMControlID": 5,
    "intAssetID": 2,
    "intBOMPartControlID": 4,
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

**URL** : `/api/assetconsumingreference`

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
            "intConsumesAssetID": 3,
            "intBOMControlID": 5,
            "intAssetID": 2,
            "intBOMPartControlID": 4,
            "qtyMaxConsumption": 3,
            "intUpdated": 231,
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

**URL** : `/api/assetconsumingreference/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intConsumesAssetID |  Integer    | An integer that uniquely identifies the associated Asset.|
|  intBOMControlID |  Integer    | An integer that uniquely identifies the associated BOMControl.|
|  intAssetID | Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|
|  intBOMPartControlID | Integer    | An integer that uniquely identifies the associated BOMPart.|
|  qtyMaxConsumption | Integer    | |
|  intUpdated | Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|


* Data example 

```json
{
    "intConsumesAssetID": 3,
    "intBOMControlID": 5,
    "intAssetID": 2,
    "intBOMPartControlID": 4,
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

**URL** : `/api/assetconsumingreference/:assetconsumingreferenceid`

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
            "intConsumesAssetID": 3,
            "intBOMControlID": 5,
            "intAssetID": 2,
            "intBOMPartControlID": 4,
            "qtyMaxConsumption": 3,
            "intUpdated": 231,
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

**URL** : `/api/assetconsumingreference/:assetconsumingreferenceid`

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
