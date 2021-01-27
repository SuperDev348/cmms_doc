
# FileContents

A FileContents represents a more in depth look into a specific file system object, such as pictures for Assets (facilities, equipment, tools), Supplies (Parts, Businesses), Regions, and Users. It contains information about the MimeType of the File. The FileContents object is associated with a File object. See the File object for more details.

Create an FileContents if  FileContents does not already exist.


**URL** : `/api/filecontents`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  strName |  String    | A string that identifies the name of the File.|
|  strMimeType |  String    | A string that identifies the MimeType of the File.|
|  intSize |  Integer    | An integer that identifies the size of the File.|
|  intSysCode |  Integer    | FACILITY = 0,EQUIPMENT = 1,TOOLS = 2,PARTS_SUPPLIES = 3,USER = 4,BUSINESS = 5,SITE = 6|
|  strUuid |  String    | A unique identifier for the FileContents.|


* Data example 

```json
{
    "strName": "strName",
    "strMinmeType": "strMinmeType",
    "intSize": 7,
    "intSysCode": 2,
    "strUuid": "strUuid"
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

**URL** : `/api/filecontents`

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
            "strName": "strName",
            "strMinmeType": "strMinmeType",
            "intSize": 7,
            "intSysCode": 2,
            "strUuid": "strUuid",
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

**URL** : `/api/filecontents/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  strName |  String    | A string that identifies the name of the File.|
|  strMimeType |  String    | A string that identifies the MimeType of the File.|
|  intSize |  Integer    | An integer that identifies the size of the File.|
|  intSysCode |  Integer    | FACILITY = 0,EQUIPMENT = 1,TOOLS = 2,PARTS_SUPPLIES = 3,USER = 4,BUSINESS = 5,SITE = 6|
|  strUuid |  String    | A unique identifier for the FileContents.|

* Data example 

```json
{
    "strName": "strName",
    "strMinmeType": "strMinmeType",
    "intSize": 7,
    "intSysCode": 2,
    "strUuid": "strUuid"
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

**URL** : `/api/filecontents/:filecontentsid`

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
            "strName": "strName",
            "strMinmeType": "strMinmeType",
            "intSize": 7,
            "intSysCode": 2,
            "strUuid": "strUuid",
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

**URL** : `/api/filecontents/:filecontentsid`

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
