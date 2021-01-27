# Create AssetBusiness 

An AssetBusiness represents the relationship between a particular Business within your CMMS and the associated Assets with this Business. It contains information about the Business Role Type, such as Customer/Client, Manufacturer, Owner, Service Provider, or Supplier

Create an AssetBusiness if  AssetBusiness does not already exist.

**URL** : `/api/assetbusiness`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intBusinessID |  Integer    | An integer that uniquely identifies the Business (used in conjunction with AssetID).|
|  intBusinessRoleTypeID |  Integer    | An integer that uniquely identifies the Business Role Type (used in conjunction with BusinessRoleType).|
|  intAssetID |  Integer    | An integer that uniquely identifies the Asset that is associated with the Business (used in conjunction with BusinessID).|
|  bolSendRFQs |  Boolean    | If set to true, indicates that RFQs should be sent when stock is low for for an asset (usually parts/supplies).|
|  bolPreferredVendor |  Boolean    | If set to true, indicates that the vendor is the Preferred Vendor for the associated asset (usually parts/supplies).|
|  qtyEconomicBatchQuantity |  Integer    | The minimum quantity when re-ordering an asset (usually parts/supplies).|
|  strBusinessAssetNumber |  String    | A string that represents an asset's part number from the business (usually parts/supplies).|
|  intBusinessGroupID |  Integer    ||

** Success Response: **
**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
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
    "msg": "Create failed"
}
```

# Read Get AssetBusiness list

Get the all registered AssetBusiness list by Business Id .

**URL** : `/api/assetbusiness/:businessId`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the AssetBussiness.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": [
        {
            bolPreferredVendor: false
            bolSendRFQs: false
            intAssetID: {_id: 137, strName: "New Facility # 137", intCategoryKind: 1,  …}
            intBusinessID: 9
            intBusinessRoleTypeID: 5
            strBusinessAssetNumber: "ss"
            strCategory: "xx"
            _id: 5
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

# Update AssetBusiness

Update the AssetBusiness by Id

**URL** : `/api/assetbusiness/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the assetbusiness.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intBusinessID |  Integer    | An integer that uniquely identifies the Business (used in conjunction with AssetID).|
|  intBusinessRoleTypeID |  Integer    | An integer that uniquely identifies the Business Role Type (used in conjunction with BusinessRoleType).|
|  intAssetID |  Integer    | An integer that uniquely identifies the Asset that is associated with the Business (used in conjunction with BusinessID).|
|  bolSendRFQs |  Boolean    | If set to true, indicates that RFQs should be sent when stock is low for for an asset (usually parts/supplies).|
|  bolPreferredVendor |  Boolean    | If set to true, indicates that the vendor is the Preferred Vendor for the associated asset (usually parts/supplies).|
|  qtyEconomicBatchQuantity |  Integer    | The minimum quantity when re-ordering an asset (usually parts/supplies).|
|  strBusinessAssetNumber |  String    | A string that represents an asset's part number from the business (usually parts/supplies).|
|  intBusinessGroupID |  Integer    ||


** Success Response: **

**Code** : `200 success`

*  Resonse example

```json
{
   "msg": "Updated successfully!"
    }
```

** Error Responses: **

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

*  Resonse example

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

# Delete AssetBusiness 

Delete an AssetBusiness by Id

**URL** : `/api/assetbusiness/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the AssetBussiness.

** Success Response: **

**Code** : `200 success`

*  Resonse example

```json
{
    "msg": "Deleted successfully!",
    data: null
}
```

** Error Responses **

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

*  Resonse example

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
