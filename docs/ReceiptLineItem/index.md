
# ReceiptLineItem

Upon reception of a purchase order, a Receipt object is created. This object represents the lines of the receipt.

Create an ReceiptLineItem if  ReceiptLineItem does not already exist.


**URL** : `/api/receiptlineitem`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intStockID |  Integer  |The ID of the stock to which the line item refers to. For getting possible values, please refer to the Stock section.|
|  qtyQuantityReceived	 |  Integer    | The quantity that was received.|
|  qtyQuantityOrdered |  Integer    | The quantity that was ordered.|
|  intAssetID |  Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|
|  intReceiptID |  Integer    | The ID of the receipt which this line is part of. For getting possible values, please refer to the Receipt section.|
|  strDescription |  String    | A short text describing the line item.|
|  intParentReceiptLineItemID |  Integer    | An integer representing the id of the parent receipt line item |
|  intPurchaseOrderLineItemID |  Integer    | An integer representing the id of the associated purchase order line item|
|  dtmDateExpiryOfInventoryItems |  TimeStamp    | The date and time when the inventory items would expire|
|  dblPurchasePricePerUnit |  Double    | The price of the received part / item per unit|
|  intReceiveToStockID |  Integer    | An integer that represents the id of a Stock that the part was received to|
|  intReceiveToFacilityID |  Integer    | An integer that represents the id of an Asset (with AssetCategory set to Facility), to which the part was received to|
|  intUpdated |  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|


* Data example 

```json
{
    "intStockID": 1,
    "qtyQuantityReceived": 12,
    "qtyQuantityOrdered": 4,
    "intAssetID": 3
    "intReceiptID": 3,
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

**URL** : `/api/receiptlineitem`

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
            "intStockID": 1,
            "qtyQuantityReceived": 12,
            "qtyQuantityOrdered": 4,
            "intAssetID": 3
            "intReceiptID": 3,
            "strDescription": "strDescription",
            "intParentReceiptLineItemID": 3,
            "intPurchaseOrderLineItemID": 3,
            "dtmDateExpiryOfInventoryItems": 2020-11-26T09:00:36.285+00:00,
            "dblPurchasePricePerUnit": 3.22,
            "intReceiveToStockID": 3,
            "intReceiveToFacilityID": 3,
            "intUpdated": 322,
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

**URL** : `/api/receiptlineitem/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intStockID |  Integer  |The ID of the stock to which the line item refers to. For getting possible values, please refer to the Stock section.|
|  qtyQuantityReceived	 |  Integer    | The quantity that was received.|
|  qtyQuantityOrdered |  Integer    | The quantity that was ordered.|
|  intAssetID |  Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|
|  intReceiptID |  Integer    | The ID of the receipt which this line is part of. For getting possible values, please refer to the Receipt section.|
|  strDescription |  String    | A short text describing the line item.|
|  intParentReceiptLineItemID |  Integer    | An integer representing the id of the parent receipt line item |
|  intPurchaseOrderLineItemID |  Integer    | An integer representing the id of the associated purchase order line item|
|  dtmDateExpiryOfInventoryItems |  TimeStamp    | The date and time when the inventory items would expire|
|  dblPurchasePricePerUnit |  Double    | The price of the received part / item per unit|
|  intReceiveToStockID |  Integer    | An integer that represents the id of a Stock that the part was received to|
|  intReceiveToFacilityID |  Integer    | An integer that represents the id of an Asset (with AssetCategory set to Facility), to which the part was received to|
|  intUpdated |  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|


* Data example 

```json
{
    "intStockID": 1,
    "qtyQuantityReceived": 12,
    "qtyQuantityOrdered": 4,
    "intAssetID": 3
    "intReceiptID": 3,
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

**URL** : `/api/receiptlineitem/:receiptlineitemid`

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
            "intStockID": 1,
            "qtyQuantityReceived": 12,
            "qtyQuantityOrdered": 4,
            "intAssetID": 3
            "intReceiptID": 3,
            "strDescription": "strDescription",
            "intParentReceiptLineItemID": 3,
            "intPurchaseOrderLineItemID": 3,
            "dtmDateExpiryOfInventoryItems": 2020-11-26T09:00:36.285+00:00,
            "dblPurchasePricePerUnit": 3.22,
            "intReceiveToStockID": 3,
            "intReceiveToFacilityID": 3,
            "intUpdated": 322,
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

**URL** : `/api/receiptlineitem/:receiptlineitemid`

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
