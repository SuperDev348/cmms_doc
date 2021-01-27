# Create Account 

This object is used to access the Account lookup table.

Create an Account if  Account does not already exist.

**URL** : `/api/account`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       |Require |Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  strCode |Yes|  String    | A unique code for referencing the account.|
|  strDescription |Yes|  String    | A short text describing the account.|


** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "56"}
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

# Get all Account list 

Get the all registered Account list.

**URL** : `/api/account`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Account list found!",
    "data": [
        {
            "_id": "45",
            "strCode": "A45",
            "strDescription": "String"
            "__v": 0
        },
        ...
    ]
}
```

** Error Responses **

** Code** : `401 Unauthorized`

** Condition** : Missing or incorrect authentication credentials and expired one.

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

# Update Account 

Update the Account by Id

**URL** : `/api/account/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the account.

| Param       |Require |Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  strCode |Yes|  String    | A unique code for referencing the account.|
|  strDescription |Yes|  String    | A short text describing the account.|


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

# Get Single Account By Id 

Get a single Account by id if current Account was registered on it.

**URL** : `/api/account/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the account.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "54",
         "strCode": "34",
         "strDescription": "String"
         "intUpdated":2020-11-26T10:42:25.136+00:00
        }
}
```

**Error Responses: **

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

**Condition** : If workorder does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Delete Account 

Delete a Account by Id

**URL** : `/api/account/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the account.

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

