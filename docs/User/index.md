# Create User

This object represents a user that can access and use the CMMS or a user group. Note: Only inactive users can be added through the API (with intUserStatusID set to 0). The user has to be activated using the CMMS.

Create an User if  User does not already exist.

**URL** : `/api/users/register`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Required     | Type     | Description     | 
| :------------- | :----------: | -----------: |----------- |
|  strFullName | yes   | String    | The full name of the user or user group.   |
|  intUserStatusID | optional   | Integer    |This can take the value `0` or `1`. A status `1` means that the user is active, whereas a status 0 means that the user is currently not activated and cannot access and use the CMMS.   |
|  strTelephone2 | optional   | String    | Secondary phone number.    |
|  strEmailAddress | yes   | String    | Email address.   |
|  strUserTitle | optional   | String    | The title of the user. For example : `"Head of Operations" or "Program Director"`.   |
|  strPersonnelCode | optional   | String    | Field that can be used to store a personnel code associated to this user.   |
|  strUserName | yes   | String    | The username that will be used by the user to access the CMMS. |
|  strTelephone | yes   | String    | Primary phone number.    |
|  strNotes | optional   | String    | This fied can contain technical notes about the user. For example : `"Data imported from V2: language=English"`.   |
|  strRequestNotes | optional   | String    | Contains a string stating when the account was created. For example : `"Wed Nov 23 09:43:49 EST 2011: Account created."`.   |
|  bolGroup | optional   | boolean    | This can take the value 0 or 1 or null. A value of 1 means the object represents a user group.    |
|  bolApiManaged | optional   | boolean    | The boolean value represents if the user is created through the API, in an external system. User information is managed in the Originating system.    |
|  strPreferences | optional   | String    | Technical string defining the user's preferences.    |
|  password | yes   | String    | user's password.    |
|  passwordconfirm | yes   | String    | password confirm.    |



**Data example** All fields must be sent.

```json
{
    "strFullName": "first last",
    "strTelephone": "5141257",
    "strEmailAddress": "test@gmai.com",
    "bolGroup":true,
    "password": "test!@3",
    "passwordconfirm": "test!@3",
    ... ...
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "User added successfully!!!",
    "data": {id: "5f68a89c247532232419483c"}
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

**Condition** : If fields are missed.

**Code** : `400 BAD REQUEST`

* Content example 

```json
{
    "msg": "Email is required"
}
```
 
** Or **

**Condition** : Internal Server Error.

**Code** : `500`

* Content example 

```json
{
    "msg": "Internal Server error",
}
```

# Get all user list

Get the all registered user list.

**URL** : `/api/users/userlist`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


** Success Response: ** 

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": null,
    "data": [
        {
            "_id": "5f6212d8ed7daa16dcbf44ca",
            "strFullName": "test demo",
            "strEmailAddress": "pavel@gmail.com",
            "strTelephone": "123456",
            "strTelephone2": "1",
            "intUserStatusID": 1,
            "strUserTitle": "2",
            "strPersonnelCode": "",
            "strUserName": "3",
            "strNotes": "4",
            "strRequestNotes": "sdfddd",
            "bolGroup": true,
            "bolApiManaged": true,
            "strPreferences": "6",
            "__v": 0
        },
        {
            "_id": "5f68a89c247532232419483c",
            "strFullName": "ttest pavel",
            "strEmailAddress": "olga@gmail.com",
            "strTelephone": "45789",
            "strTelephone2": "",
            "intUserStatusID": 0,
            "strUserTitle": "",
            "strPersonnelCode": "",
            "strUserName": "",
            "strNotes": "",
            "strRequestNotes": "",
            "bolGroup": false,
            "bolApiManaged": false,
            "strPreferences": "",
            "__v": 0
        }
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
    "msg": "Internal Server error",
    "data":null
}
```

# Get Single User By Id

Get a single User by id if current user was registered on it.

**URL** : `/api/users/:uid`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the user.

** Success Response: **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": null,
    "data": {
        "user": {
            "_id": "5f6212d8ed7daa16dcbf44ca",
            "strFullName": "test demo",
            "password": "$2b$10$jIqho0m8oHKsXTNIk6xFcu0kSBme4zNieLyrm.cFDLYMCpVzRcKPq",
            "strEmailAddress": "test@gmail.com",
            "strTelephone": "strTelephone",
            "strTelephone2": "",
            "intUserStatusID": 1,
            "strUserTitle": "strUserTitle",
            "strPersonnelCode": "",
            "strUserName": "3",
            "strNotes": "strNotes",
            "strRequestNotes": "strRequste notes",
            "bolGroup": true,
            "bolApiManaged": true,
            "strPreferences": "6",
            "__v": 0
        }
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

**Condition** : If user does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "User not found", 
   "data":null
}
```

# Update User

Update the User by Id

**URL** : `/api/users/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the user.

| Param       | Required     | Type     | Description     | 
| :------------- | :----------: | -----------: |----------- |
|  strFullName | yes   | String    | The full name of the user or user group.   |
|  intUserStatusID | optional   | Integer    |This can take the value `0` or `1`. A status `1` means that the user is active, whereas a status 0 means that the user is currently not activated and cannot access and use the CMMS.   |
|  strTelephone2 | optional   | String    | Secondary phone number.    |
|  strEmailAddress | yes   | String    | Email address.   |
|  strUserTitle | optional   | String    | The title of the user. For example : `"Head of Operations" or "Program Director"`.   |
|  strPersonnelCode | optional   | String    | Field that can be used to store a personnel code associated to this user.   |
|  strUserName | yes   | String    | The username that will be used by the user to access the CMMS. |
|  strTelephone | yes   | String    | Primary phone number.    |
|  strNotes | optional   | String    | This fied can contain technical notes about the user. For example : `"Data imported from V2: language=English"`.   |
|  strRequestNotes | optional   | String    | Contains a string stating when the account was created. For example : `"Wed Nov 23 09:43:49 EST 2011: Account created."`.   |
|  bolGroup | optional   | boolean    | This can take the value 0 or 1 or null. A value of 1 means the object represents a user group.    |
|  bolApiManaged | optional   | boolean    | The boolean value represents if the user is created through the API, in an external system. User information is managed in the Originating system.    |
|  strPreferences | optional   | String    | Technical string defining the user's preferences.    |
|  password | yes   | String    | user's password.    |
|  passwordconfirm | yes   | String    | password confirm.    |



**Data example**  `All fields must be sent.`

```json
{
    "strFullName": "first last",
    "strTelephone": "5141257",
    "strEmailAddress": "test@gmai.com",
    "bolGroup":true,
    "password": "test!@3",
    "passwordconfirm": "test!@3",
    ... ...
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
    "msg": "User updated successfully!",
    data: "user": {
            "_id": "5f6212d8ed7daa16dcbf44ca",
            "strFullName": "first last",
             "strEmailAddress": "test@gmail.com",
            "strTelephone": "5141257",
            "strTelephone2": "",
            "intUserStatusID": 1,
            "strUserTitle": "strUserTitle",
            "strPersonnelCode": "",
            "strUserName": "3",
            "strNotes": "strNotes",
            "strRequestNotes": "strRequste notes",
            "bolGroup": true,
            "bolApiManaged": true,
            "strPreferences": "6",
            "__v": 0
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

**Condition** : If fields are missed.

**Code** : `400 BAD REQUEST`

* Content example 

```json
{
    "msg": "Update failed",
    "data":null
}
```

** Or **

**Condition** : Internal Server Error.

**Code** : `500`

* Content example 

```json
{
    "msg": "Internal Server error",
    "data":null
}
```

# Delete User

Delete the User by Id

**URL** : `/api/users/:uid`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the user.

** Success Response: **

**Code** : `200 success`

* Resonse example

```json
{
    "msg": "User deleted successfully!",
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

**Condition** : If there was no User available to delete.

**Code** : `400 BAD REQUEST`

* Content example 

```json
{
    "msg": "Delete failed",
    "data":null
}
```
