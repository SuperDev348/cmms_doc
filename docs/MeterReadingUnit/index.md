# Create MeterReadingUnit

This object is used to represent units for the meter readings. Meter reading units can be added and deleted but a unit cannot be deleted if it is already referred somewhere in the CMMS.

Create a MeterReadingUnit if  MeterReadingUnit does not already exist.

**URL** : `/api/meterreadingunit`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Required | Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  strName |  Yes|String    | The display name of the meter reading unit. For example : "Kilowatts","Cycles" or "Gallons"|
|  strSymbol | Yes |String    | The symbol of the meter reading unit. For example "kw", "kPa" or "g"|
|  intPrecision |  |Integer    | The number of digits to be displayed after the point when rendering the value of a meter reading with this unit. With a precision of 3, example values will be "13.654","9.111"|


** Success Response:**

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "1"}
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
    "msg": "strName is required"
}
```
```json
{
    "msg": "Create failed"
}
```

# Get all MeterReadingUnit list 

Get the all registered MeterReadingUnit list.

**URL** : `/api/meterreadingunit/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the MeterReadingUnit.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": [
        {
            "_id": "6",
            "strName": "Kilowatts",
            "strSymbol": "Kw",
            "intPrecision": 13.654,         
            "intUpdated":2020-10-16T18:12:30.433+00:00,
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

# Update MeterReadingUnit

Update the MeterReadingUnit by Id

**URL** : `/api/meterreadingunit/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the MeterReadingUnit.

| Param       | Required | Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  strName |  Yes|String    | The display name of the meter reading unit. For example : "Kilowatts","Cycles" or "Gallons"|
|  strSymbol | Yes |String    | The symbol of the meter reading unit. For example "kw", "kPa" or "g"|
|  intPrecision |  |Integer    | The number of digits to be displayed after the point when rendering the value of a meter reading with this unit. With a precision of 3, example values will be "13.654","9.111"|


** Success Response:**

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

# Delete MeterReadingUnit

Delete a MeterReadingUnit by Id

**URL** : `/api/meterreadingunit/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the MeterReadingUnit.

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
    "msg": "Deleted successfully!",
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
