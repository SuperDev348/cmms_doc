# Create PurchaseOrder

A PurchaseOrder represents a Maintenance job that is to be done and executed by the assigned user. It contains information about the PurchaseOrder Maintenance Type, Date created, Priority level, Site it resides in, Asset(s) involved, and assigned User.
See the MaintennaceType, SheduledMaintenaceUser, SheduledMaintenancePart, and PurchaseOrderAsset objects for more details and information. You can have multiple PurchaseOrder associated in your CMMS.

Create a PurchaseOrder if  PurchaseOrder does not already exist.

**URL** : `/api/purchaseorder`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  dtmDateCreated |  Date    | A date that represents when the purchase order was created.|
|  dtmDateExpectedDelivery |  Date    | A date that represents when the purchase order is expected to be delivered.|
|  dtmDateSubmitted |  Date    | A date that represents when the purchase order was submitted.|
|  intBillingTermID |  Integer    | An integer that uniquely defines a billing term for the purchase order.|
|  intChargeDepartmentID |  Integer    | An integer that uniquely defines the Charge Department. Please refer to ChargeDepartment|
|  intCode |  Integer    | An integer that represents the code of the Purchase Order object e.g. For purchase order PO#33, code = 33|
|  intCreatedByUserID |  Integer    | An integer that uniquely defines the user who created the purchase order record. Please refer to User|
|  intPurchaseOrderStatusID |  Integer    | An integer that uniquely defines the purchase order current status. Please refer to PurchaseOrderStatus.|
| intSendToSupplierMethod|  Integer    | The sending method of the purchase order item. The possible values are 0 for SEND_TO_SUPPLIER_BY_EMAIL, 1 for SEND_TO_SUPPLIER_BY_FAX, 2 for SEND_TO_SUPPLIER_BY_MAIL and 3 for SEND_TO_SUPPLIER_BY_SUPPLIER_WEBSITE|
| intSiteID|  Integer    | The ID of the site where the purchase order will be shipped. A site is an asset itself, so for possible values, please refer to the Asset|
| intSupplierID|  Integer    | The ID of the business that fulfills the purchase order. Please refer to Business|
| intUpdated|  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|
|  dtmDateLastUpdated |  Date    | A date that represent when purchase order was last updated.|
|  dtmDateReceived |  Date    | The date the purchase order was received.|
|  dtmDateRequiredBy |  Date    | The date the purchase order was required.|
|  intAccountID |  integer    | ID of the account that is associated with the purchase order.|
|  intAssetID |  integer    | ID of the asset/site associated with the purchase order.|
|  intBillToCountryID |  integer    | ID of the Country of the facility that is to be billed for the purchase order.|
|  intBillToID |  integer    | ID of the facility to be billed for the purchase order. See Asset|
|  intLastUpdatedUserID |  integer    | ID of the user that performed the last update on the purchase order.|
|  intPurchaseCurrencyID |  integer    | ID of the currency in which the purchase order financial transaction is to be performed.|
|  intShipToCountryID |  integer    | ID of the Country to which the purchase order will be shipped.|
|  intShipToID |  integer    | ID of the facility that will receive shipment of purchase order. See Asset|
|  intSupplierCountryID |  integer    | ID of the Country of the supplier.|
|  intWorkOrderID |  integer    | ID of WorkOrder that is associated with the purchase order.|
|  strBillToAddress |  string    | Address of the facility that is to be billed for the purchase order.|
|  strBillToCity |  string    | City information of the facility that is to be billed for the purchase order.|
|  strBillToPostalCode |  string    | Postal code information of the facility that is to be billed for the purchase order.|
|  strBillToProvince |  string    | Province of the facility that is to be billed for the purchase order.|
|  strPurchaseOrderReference |  string    | Reference number/information for the purchase order.|
|  strShipToAddress |  string    | Address of the facility that is to receive the purchase order items.|
|  strShipToCity |  string    | City of the facility that is to receive the purchase order items.|
|  strShipToPostalCode |  string    | Postal code of the facility that is to receive the purchase order items.|
|  strShipToProvince |  string    | Province of the facility that is to receive the purchase order items.|
|  strSupplierAddress |  string    | Address of the supplier of the purchase order items.|
|  strSupplierCity |  string    | City of the supplier of the purchase order items.|
|  strSupplierPostalCode |  string    | Postal code of the supplier of the purchase order items.|
|  strSupplierProvince |  string    | Province of the supplier of the purchase order items.|
|  intLocationID |  integer     | The id of the location for the PurchaseOrder (Used in conjunction with the Asset object).|

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

# Get all PurchaseOrder list

Get the all registered PurchaseOrder list.

**URL** : `/api/purchaseorder`

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
            "dtmDateCreated":2020-11-09T07:35:22.052+00:00,
            "dtmDateExpectedDelivery":"Date",
            "dtmDateSubmitted":"Date",
            "intBillingTermID":"Integer",
            "intChargeDepartmentID":4,
            "intCode":"Integer",
            "intCreatedByUserID":33,
            "intPurchaseOrderStatusID":"Integer",
            "intSendToSupplierMethod":1,
            "intSiteID":"Integer",
            "intSupplierID":33,
            "intUpdated":"Integer",
			"dtmDateLastUpdated":"Date",
			"dtmDateReceived":2020-11-09T07:35:22.052+00:00,
			"dtmDateRequiredBy":2020-11-09T07:35:22.052+00:00,
            "intAccountID":33,
            "intAssetID":33,
            "intBillToCountryID":33,
            "intBillToID":33,
            "intLastUpdatedUserID":33,
            "intPurchaseCurrencyID":33,
            "intShipToCountryID":33,
            "intShipToID":33,
            "intSupplierCountryID":33,
            "intWorkOrderID":33,			
            "strBillToAddress":"address1",
            "strBillToCity":"city_name",
            "strBillToPostalCode":string,
            "strBillToProvince":string,
            "strPurchaseOrderReference":string,
            "strShipToAddress":string,
            "strShipToCity":string,
            "strShipToPostalCode":"postcode",
            "strShipToProvince":string,
            "strSupplierAddress":string,
            "strSupplierCity":string,
            "strSupplierPostalCode":string,
            "strSupplierProvince":string,		
            "intLocationID":"Integer" , 
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

# Get Single PurchaseOrder By Id

Get a single PurchaseOrder by id if current PurchaseOrder was registered on it.

**URL** : `/api/purchaseorder/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrder.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "5",
            "dtmDateCreated":2020-11-09T07:35:22.052+00:00,
            "dtmDateExpectedDelivery":"Date",
            "dtmDateSubmitted":"Date",
            "intBillingTermID":"Integer",
            "intChargeDepartmentID":4,
            "intCode":"Integer",
            "intCreatedByUserID":33,
            "intPurchaseOrderStatusID":"Integer",
            "intSendToSupplierMethod":1,
            "intSiteID":"Integer",
            "intSupplierID":33,
            "intUpdated":"Integer",
			"dtmDateLastUpdated":"Date",
			"dtmDateReceived":2020-11-09T07:35:22.052+00:00,
			"dtmDateRequiredBy":2020-11-09T07:35:22.052+00:00,
            "intAccountID":33,
            "intAssetID":33,
            "intBillToCountryID":33,
            "intBillToID":33,
            "intLastUpdatedUserID":33,
            "intPurchaseCurrencyID":33,
            "intShipToCountryID":33,
            "intShipToID":33,
            "intSupplierCountryID":33,
            "intWorkOrderID":33,			
            "strBillToAddress":"address1",
            "strBillToCity":"city_name",
            "strBillToPostalCode":string,
            "strBillToProvince":string,
            "strPurchaseOrderReference":string,
            "strShipToAddress":string,
            "strShipToCity":string,
            "strShipToPostalCode":"postcode",
            "strShipToProvince":string,
            "strSupplierAddress":string,
            "strSupplierCity":string,
            "strSupplierPostalCode":string,
            "strSupplierProvince":string,		
            "intLocationID":"Integer"            
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

**Condition** : If PurchaseOrder does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Update PurchaseOrder

Update the PurchaseOrder by Id

**URL** : `/api/purchaseorder/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrder.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  dtmDateCreated |  Date    | A date that represents when the purchase order was created.|
|  dtmDateExpectedDelivery |  Date    | A date that represents when the purchase order is expected to be delivered.|
|  dtmDateSubmitted |  Date    | A date that represents when the purchase order was submitted.|
|  intBillingTermID |  Integer    | An integer that uniquely defines a billing term for the purchase order.|
|  intChargeDepartmentID |  Integer    | An integer that uniquely defines the Charge Department. Please refer to ChargeDepartment|
|  intCode |  Integer    | An integer that represents the code of the Purchase Order object e.g. For purchase order PO#33, code = 33|
|  intCreatedByUserID |  Integer    | An integer that uniquely defines the user who created the purchase order record. Please refer to User|
|  intPurchaseOrderStatusID |  Integer    | An integer that uniquely defines the purchase order current status. Please refer to PurchaseOrderStatus.|
| intSendToSupplierMethod|  Integer    | The sending method of the purchase order item. The possible values are 0 for SEND_TO_SUPPLIER_BY_EMAIL, 1 for SEND_TO_SUPPLIER_BY_FAX, 2 for SEND_TO_SUPPLIER_BY_MAIL and 3 for SEND_TO_SUPPLIER_BY_SUPPLIER_WEBSITE|
| intSiteID|  Integer    | The ID of the site where the purchase order will be shipped. A site is an asset itself, so for possible values, please refer to the Asset|
| intSupplierID|  Integer    | The ID of the business that fulfills the purchase order. Please refer to Business|
| intUpdated|  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|
|  dtmDateLastUpdated |  Date    | A date that represent when purchase order was last updated.|
|  dtmDateReceived |  Date    | The date the purchase order was received.|
|  dtmDateRequiredBy |  Date    | The date the purchase order was required.|
|  intAccountID |  integer    | ID of the account that is associated with the purchase order.|
|  intAssetID |  integer    | ID of the asset/site associated with the purchase order.|
|  intBillToCountryID |  integer    | ID of the Country of the facility that is to be billed for the purchase order.|
|  intBillToID |  integer    | ID of the facility to be billed for the purchase order. See Asset|
|  intLastUpdatedUserID |  integer    | ID of the user that performed the last update on the purchase order.|
|  intPurchaseCurrencyID |  integer    | ID of the currency in which the purchase order financial transaction is to be performed.|
|  intShipToCountryID |  integer    | ID of the Country to which the purchase order will be shipped.|
|  intShipToID |  integer    | ID of the facility that will receive shipment of purchase order. See Asset|
|  intSupplierCountryID |  integer    | ID of the Country of the supplier.|
|  intWorkOrderID |  integer    | ID of WorkOrder that is associated with the purchase order.|
|  strBillToAddress |  string    | Address of the facility that is to be billed for the purchase order.|
|  strBillToCity |  string    | City information of the facility that is to be billed for the purchase order.|
|  strBillToPostalCode |  string    | Postal code information of the facility that is to be billed for the purchase order.|
|  strBillToProvince |  string    | Province of the facility that is to be billed for the purchase order.|
|  strPurchaseOrderReference |  string    | Reference number/information for the purchase order.|
|  strShipToAddress |  string    | Address of the facility that is to receive the purchase order items.|
|  strShipToCity |  string    | City of the facility that is to receive the purchase order items.|
|  strShipToPostalCode |  string    | Postal code of the facility that is to receive the purchase order items.|
|  strShipToProvince |  string    | Province of the facility that is to receive the purchase order items.|
|  strSupplierAddress |  string    | Address of the supplier of the purchase order items.|
|  strSupplierCity |  string    | City of the supplier of the purchase order items.|
|  strSupplierPostalCode |  string    | Postal code of the supplier of the purchase order items.|
|  strSupplierProvince |  string    | Province of the supplier of the purchase order items.|
|  intLocationID |  integer     | The id of the location for the PurchaseOrder (Used in conjunction with the Asset object).|

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

# Delete PurchaseOrder

Delete a PurchaseOrder by Id

**URL** : `/api/purchaseorder/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the PurchaseOrder.

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
