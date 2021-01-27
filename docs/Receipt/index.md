
# Receipt

Upon receiving a purchase order, a Receipt object is created in the CMMS.

Create an Receipt if  Receipt does not already exist.


**URL** : `/api/receipt`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intSiteID |  Integer  |For multi-sites tenants, the ID of the site where the receipt arrived. A site is an asset itself, so for possible values, please refer to the Asset section.|
|  dtmDateReceived |  TimeStamp    | The date and time when the receipt has arrived.|
|  dtmDateOrdered |  TimeStamp    | The date and time when the purchase was ordered.|
|  intReceiptStatusID |  Integer    | The ID of the status of the receipt. For getting possible values, please refer to the ReceiptStatus section.|
|  intPurchaseCurrencyID |  Integer    | The ID of the currency that was used for the purchase order. For getting possible values, please refer to the Currency section.|
|  intPurchaseOrderID |  Integer    | The ID of the purchase order which the receipt refers to.|
|  intCode |  Integer    | An integer that represents the code of the Receipt object e.g. For receipt R#31, code = 31 |
|  intSupplierID |  Integer    | An integer that represents the id of the Business|
|  intUpdated |  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|
|  strPackingSlip |  String    | The user can add alphanumeric values denoting packing slip numbers using this field. Max length: 255.|


* Data example 

```json
{
    "intSiteID": 1,
    "dtmDateReceived": 2020-11-26T09:00:36.285+00:00,
    "dtmDateOrdered": 2020-11-26T09:00:36.285+00:00,
    "intReceiptStatusID": 3
    "intPurchaseCurrencyID": 3,
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

**URL** : `/api/receipt`

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
            "intSiteID": 1,
            "dtmDateReceived": 2020-11-26T09:00:36.285+00:00,
            "dtmDateOrdered": 2020-11-26T09:00:36.285+00:00,
            "intReceiptStatusID": 3
            "intPurchaseCurrencyID": 3,
            "intPurchaseOrderID": 3,
            "intCode": 3,
            "intSupplierID": 3,
            "intUpdated": 321,
            "strPackingSlip": "strPackingSlip",
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

**URL** : `/api/receipt/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intSiteID |  Integer  |For multi-sites tenants, the ID of the site where the receipt arrived. A site is an asset itself, so for possible values, please refer to the Asset section.|
|  dtmDateReceived |  TimeStamp    | The date and time when the receipt has arrived.|
|  dtmDateOrdered |  TimeStamp    | The date and time when the purchase was ordered.|
|  intReceiptStatusID |  Integer    | The ID of the status of the receipt. For getting possible values, please refer to the ReceiptStatus section.|
|  intPurchaseCurrencyID |  Integer    | The ID of the currency that was used for the purchase order. For getting possible values, please refer to the Currency section.|
|  intPurchaseOrderID |  Integer    | The ID of the purchase order which the receipt refers to.|
|  intCode |  Integer    | An integer that represents the code of the Receipt object e.g. For receipt R#31, code = 31 |
|  intSupplierID |  Integer    | An integer that represents the id of the Business|
|  intUpdated |  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|
|  strPackingSlip |  String    | The user can add alphanumeric values denoting packing slip numbers using this field. Max length: 255.|


* Data example 

```json
{
    "intSiteID": 1,
    "dtmDateReceived": 2020-11-26T09:00:36.285+00:00,
    "dtmDateOrdered": 2020-11-26T09:00:36.285+00:00,
    "intReceiptStatusID": 3
    "intPurchaseCurrencyID": 3,
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

**URL** : `/api/receipt/:receiptid`

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
            "intSiteID": 1,
            "dtmDateReceived": 2020-11-26T09:00:36.285+00:00,
            "dtmDateOrdered": 2020-11-26T09:00:36.285+00:00,
            "intReceiptStatusID": 3
            "intPurchaseCurrencyID": 3,
            "intPurchaseOrderID": 3,
            "intCode": 3,
            "intSupplierID": 3,
            "intUpdated": 321,
            "strPackingSlip": "strPackingSlip",
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

**URL** : `/api/receipt/:receiptid`

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
