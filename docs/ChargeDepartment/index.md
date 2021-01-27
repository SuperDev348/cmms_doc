# Create ChargeDepartment
This object is used to access the Charge Department lookup table.

Create an ChargeDepartment if  ChargeDepartment does not already exist.

**URL** : `/api/chargedepartment`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Required | Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  strCode | Yes |String    | A unique code for referencing the charge department.|
|  strDescription | Yes |String    | A short text describing the charge department.|
|  intFacilityID |  |Integer    | An integer that can be used to linked the charge department with the facility it is located at.|
|  intFacilityID |  |Integer    | An integer that can be used to linked the charge department with the facility it is located at.|

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "4"}
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
    "msg": "strCode is required"
}
```
```json
{
    "msg": "Create failed"
}
```

# Get all ChargeDepartment list 

Get the all registered ChargeDepartment list.

**URL** : `/api/chargedepartment`

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
            "_id": "6",
            "strCode": "String",
            "strDescription": "String",
            "intFacilityID": Object,
            "intUpdated":2020-10-16T18:12:30.433+00:00
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

# Get Single ChargeDepartment By Id

Get a single ChargeDepartment by id if current ChargeDepartment was registered on it.

**URL** : `/api/chargedepartment/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the chargedepartment.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "7",
            "strCode":"String",
            "strDescription":"String",
            "intFacilityID":"Integer",
            "intUpdated":2020-10-16T18:12:30.433+00:00
            
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

**Condition** : If chargedepartment does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Update ChargeDepartment

Update the ChargeDepartment by Id

**URL** : `/api/chargedepartment/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ChargeDepartment.

| Param       | Required | Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  strCode | Yes |String    | A unique code for referencing the charge department.|
|  strDescription | Yes |String    | A short text describing the charge department.|
|  intFacilityID |  |Integer    | An integer that can be used to linked the charge department with the facility it is located at.|
|  intFacilityID |  |Integer    | An integer that can be used to linked the charge department with the facility it is located at.|

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

# Delete ChargeDepartment

Delete a ChargeDepartment by Id

**URL** : `/api/chargedepartment/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the chargedepartment.

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

