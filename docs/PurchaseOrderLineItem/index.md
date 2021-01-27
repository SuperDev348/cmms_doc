# Create PurchaseOrderLineItem

A PurchaseOrderLineItem represents a Maintenance job that is to be done and executed by the assigned user. It contains information about the PurchaseOrderLineItem Maintenance Type, Date created, Priority level, Site it resides in, Asset(s) involved, and assigned User.
See the MaintennaceType, SheduledMaintenaceUser, SheduledMaintenancePart, and PurchaseOrderLineItemAsset objects for more details and information. You can have multiple PurchaseOrderLineItem associated in your CMMS.

Create a PurchaseOrderLineItem if  PurchaseOrderLineItem does not already exist.

**URL** : `/api/purchaseorderlineitem`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  bolAddedDirectlyToPurchaseOrder |  boolean    | A boolean that indicates if the purchase order line item is added directly to the purchase order. If set to false, it means it was added through the Purchase Planning Board.|
|  bolProductionEquipmentDownWhileOnOrder |  boolean    | A boolean that indicates if the production equipment is down while on order or not. This will determine if the purchase of the item is critical or not.|
|  dblRemoteOrgUnitPrice |  double    | The original unit price.|
|  dblTaxRate |  double    | The tax rate applied to the purchase order line item.|
|  dblUnitPrice |  double    | The price for a unit of the item.|
|  dtmDateCreated |  date    | A date that represents when the item was created.|
|  dtmRequiredByDate |  date    | The item purchased will be required by this date.|
| intAccountID|  integer    | An integer uniquely identifying the account used to purchase the item. Please refer to Account|
| intAssetID|  integer    | An integer that uniquely identifies the asset linked to the purchased item. Please refer to Asset|
| intChargeDepartmentID|  integer    | An integer that uniquely defines the Charge Department|
| intPurchaseOrderID|  integer    | The ID of the purchase order which the purchase order line item is part of.|
| intRequestedByUserID|  integer    | The ID of the user who requested the purchase order. Please refer to User.|
| intShipToLocationID|  integer    | The reference to the location where the purchased item will be shipped. Please refer to Location|
| intSiteID|  integer    | The ID of the site where the purchase order will be shipped. A site is an asset itself, so for possible values, please refer to the Asset|
| intSourceAssetID|  integer    | The ID of the asset that represents the source asset of the purchase order item. Please refer to Asset|
| intSourceWorkOrderID|  integer    | The ID of the source work order to which the purchase order line item is related. Please refer to WorkOrder|
| intStockHistoryID|  integer    | The ID of the stock history record related to the purchase order item.|
| intStockID|  integer    | The ID of the stock related to the purchase order item. Please refer to Stock|
| intSupplierID|  integer    | The ID of the business that fulfills the purchased order item. Please refer to Business|
| qtyOnOrder|  integer    | The quantity requested on the purchase order line item.|
| qtyRecieved|  integer    | The quantity received on the purchase order line item.|
| strBusinessAssetNumber|  string    | The description for the business asset related to the purchase order line item.|
| strDescription|  string    | As string that represents the description on the Purchase order line item.|
| intUpdated|  integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|

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

# Get all PurchaseOrderLineItem list

Get the all registered PurchaseOrderLineItem list.

**URL** : `/api/purchaseorderlineitem`

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
            "intUserID":Integer,
            "bolAddedDirectlyToPurchaseOrder":boolean,
            "dblRemoteOrgUnitPrice":double,
            "dblTaxRate":2.8,
            "dblUnitPrice":45,
            "dtmDateCreated":date,
			"dtmRequiredByDate":2020-11-09T07:35:22.052+00:00,
			"intAccountID":Integer,
			"intAssetID":2,
			"intChargeDepartmentID":3,
			"intPurchaseOrderID":4,
			"intRequestedByUserID":55,
			"intShipToLocationID":23,
			"intSiteID":345,
			"intSourceAssetID":5,
			"intSourceWorkOrderID":1,
			"intStockHistoryID":23,
			"intStockID":44,
			"intSupplierID":54,
			"qtyOnOrder":21,
			"qtyRecieved":22,
			"strBusinessAssetNumber":string,
			"strDescription":"this is description...",
			"intUpdated":Integer,
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

# Get Single PurchaseOrderLineItem By Id

Get a single PurchaseOrderLineItem by id if current PurchaseOrderLineItem was registered on it.

**URL** : `/api/purchaseorderlineitem/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrderLineItem.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "5",           
            "intUserID":Integer,
            "bolAddedDirectlyToPurchaseOrder":boolean,
            "dblRemoteOrgUnitPrice":double,
            "dblTaxRate":2.8,
            "dblUnitPrice":45,
            "dtmDateCreated":date,
			"dtmRequiredByDate":2020-11-09T07:35:22.052+00:00,
			"intAccountID":Integer,
			"intAssetID":2,
			"intChargeDepartmentID":3,
			"intPurchaseOrderID":4,
			"intRequestedByUserID":55,
			"intShipToLocationID":23,
			"intSiteID":345,
			"intSourceAssetID":5,
			"intSourceWorkOrderID":1,
			"intStockHistoryID":23,
			"intStockID":44,
			"intSupplierID":54,
			"qtyOnOrder":21,
			"qtyRecieved":22,
			"strBusinessAssetNumber":string,
			"strDescription":"this is description...",
			"intUpdated":Integer
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

**Condition** : If PurchaseOrderLineItem does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Update PurchaseOrderLineItem

Update the PurchaseOrderLineItem by Id

**URL** : `/api/purchaseorderlineitem/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrderLineItem.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  bolAddedDirectlyToPurchaseOrder |  boolean    | A boolean that indicates if the purchase order line item is added directly to the purchase order. If set to false, it means it was added through the Purchase Planning Board.|
|  bolProductionEquipmentDownWhileOnOrder |  boolean    | A boolean that indicates if the production equipment is down while on order or not. This will determine if the purchase of the item is critical or not.|
|  dblRemoteOrgUnitPrice |  double    | The original unit price.|
|  dblTaxRate |  double    | The tax rate applied to the purchase order line item.|
|  dblUnitPrice |  double    | The price for a unit of the item.|
|  dtmDateCreated |  date    | A date that represents when the item was created.|
|  dtmRequiredByDate |  date    | The item purchased will be required by this date.|
| intAccountID|  integer    | An integer uniquely identifying the account used to purchase the item. Please refer to Account|
| intAssetID|  integer    | An integer that uniquely identifies the asset linked to the purchased item. Please refer to Asset|
| intChargeDepartmentID|  integer    | An integer that uniquely defines the Charge Department|
| intPurchaseOrderID|  integer    | The ID of the purchase order which the purchase order line item is part of.|
| intRequestedByUserID|  integer    | The ID of the user who requested the purchase order. Please refer to User.|
| intShipToLocationID|  integer    | The reference to the location where the purchased item will be shipped. Please refer to Location|
| intSiteID|  integer    | The ID of the site where the purchase order will be shipped. A site is an asset itself, so for possible values, please refer to the Asset|
| intSourceAssetID|  integer    | The ID of the asset that represents the source asset of the purchase order item. Please refer to Asset|
| intSourceWorkOrderID|  integer    | The ID of the source work order to which the purchase order line item is related. Please refer to WorkOrder|
| intStockHistoryID|  integer    | The ID of the stock history record related to the purchase order item.|
| intStockID|  integer    | The ID of the stock related to the purchase order item. Please refer to Stock|
| intSupplierID|  integer    | The ID of the business that fulfills the purchased order item. Please refer to Business|
| qtyOnOrder|  integer    | The quantity requested on the purchase order line item.|
| qtyRecieved|  integer    | The quantity received on the purchase order line item.|
| strBusinessAssetNumber|  string    | The description for the business asset related to the purchase order line item.|
| strDescription|  string    | As string that represents the description on the Purchase order line item.|
| intUpdated|  integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|

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

# Delete PurchaseOrderLineItem

Delete a PurchaseOrderLineItem by Id

**URL** : `/api/purchaseorderlineitem/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrderLineItem.

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
