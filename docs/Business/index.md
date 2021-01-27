# Create Business
A Business represents a particular Business within your CMMS. It contains information about the address of the Business, and the Business Classification, such as Agriculture, Aerospace/Airline, Automotive, Biotechnology, Chemical Processing, Computer, Data Centers, Defense, Education, Electronics, Energy and Utilities, Manufacturing, Software, Technology, and Telecommunications. 

Create an Business if  Business does not already exist.

**URL** : `/api/business`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  strProvince |  String    | A string that identifies the Province of the Business.|
|  strPostalCode |  String    | A string that identifies the Postal Code of the Business.|
|  strTimezone |  String    | A string that identifies the Time Zone of the Business.|
|  strPrimaryEmail |  String    | A string that identifies the Primary Email of the Business.|
|  strName |  String    | A string that identifies the Name of the Business.|
|  strPhone |  String    |A string that identifies the Phone Number of the Business.|
|  strFax |  String    |A string that identifies the Fax Number of the Business.|
|  intCountryID |  Integer    | An integer that uniquely identifies the Country of the Business (used in conjunction with the Country object).|
|  strAddress |  String    | A string that identifies the Address of the Business.|
|  strPrimaryContact |  String    |A string that identifies the Primary Contact of the Business.|
|  strNotes |  String    | A string that identifies Notes of the Business.|
|  strPhone2 |  String    | An additional optional phone number of the Business.|
|  strCode |  String    | The code of the Business.|
|  strCity |  String    |The city of the Business.|
|  strSecondaryEmail |  String    | A string that identifies secondary email of the Business.|

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "6"}
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

# Get Single Business By Id 

Get a single Business by id if current Business was registered on it.

**URL** : `/api/business/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the business.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "6",
            "strProvince":"String",
            "strPostalCode":"String",
            "strTimezone":"String",
            "strPrimaryEmail":"String",
            "strName":"String",
            "strPhone":"String",
            "strFax":"String",
            "intCountryID":"Integer",
            "strAddress":"String",
            "strPrimaryContact":"String",
            "strNotes":"String",
            "strPhone2":"String",
            "strCode":"String",
            "strCity":"String",
            "strSecondaryEmail":"String"
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

**Condition** : If Business does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```
# Update Business

Update the Business by Id

**URL** : `/api/business/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the Business.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  strProvince |  String    | A string that identifies the Province of the Business.|
|  strPostalCode |  String    | A string that identifies the Postal Code of the Business.|
|  strTimezone |  String    | A string that identifies the Time Zone of the Business.|
|  strPrimaryEmail |  String    | A string that identifies the Primary Email of the Business.|
|  strName |  String    | A string that identifies the Name of the Business.|
|  strPhone |  String    |A string that identifies the Phone Number of the Business.|
|  strFax |  String    |A string that identifies the Fax Number of the Business.|
|  intCountryID |  Integer    | An integer that uniquely identifies the Country of the Business (used in conjunction with the Country object).|
|  strAddress |  String    | A string that identifies the Address of the Business.|
|  strPrimaryContact |  String    |A string that identifies the Primary Contact of the Business.|
|  strNotes |  String    | A string that identifies Notes of the Business.|
|  strPhone2 |  String    | An additional optional phone number of the Business.|
|  strCode |  String    | The code of the Business.|
|  strCity |  String    |The city of the Business.|
|  strSecondaryEmail |  String    | A string that identifies secondary email of the Business.|

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Updated successfully!"
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
    "msg": "Update failed"
}
```

# Delete Business

Delete a Business by Id

**URL** : `/api/business/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the business.

** Success Response: **

**Code** : `200 success`

**Resonse example**

```json
{
    "msg": "Deleted successfully!",
    data: null
}
```

** Error Responses: ** 

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

**Resonse example**

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

**Content example**

```json
{
    "msg": "Delete failed",
    "data":null
}
```

