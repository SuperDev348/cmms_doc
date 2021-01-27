
# File

A File represents a file system object, such as pictures for Assets (facilities, equipment, tools), Supplies (Parts, Businesses), Regions, and Users. It contains information about the size of the File and the name of the File. The File object is associated with your CMMS. The File object is associated with FileContents. See FileContents object for more details. You can have multiple Files associated in your CMMS.

Create an File if  File does not already exist.


**URL** : `/api/file`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intWorkOrderID |  Integer    | An integer that uniquely identifies the Work Order that is associated with this File.|
|  intFileTypeID |  Integer    | An integer that uniquely identifies the File Type.|
|  strName |  String    | A string that identifies the name of the File.|
|  intSize |  Integer    | An integer that identifies the size of the File.|
|  strNotes |  String    | A string that identifies Notes associated with the File.|
|  intFileContentsID |  Integer    | An integer that uniquely identifies the FileContents (used in conjunction with FileContents).|
|  intAssetID |  Integer    | An ID that identifies the Asset associated with the File.|
|  strLink |  String    | A web url, that typically starts with http or https protocol. Network drive paths are not supported, as they are blocked by modern browsers.|
|  intUpdated |  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|
|  strUuid |  String    | A unique identifier for the File.|

* Data example 

```json
{
    "intWorkOrderID": 12,
    "intFileTypeID": 2,
    "strName": "strName",
    "intSize": 7,
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

**URL** : `/api/file`

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
            "intWorkOrderID": 12,
            "intFileTypeID": 2,
            "strName": "strName",
            "intSize": 7,
            "strNotes": "strNotes",
            "intFileContentsID": 3,
            "intAssetID": 2,
            "strLink": "strLink",
            "intUpdated": 123,
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

**URL** : `/api/file/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intWorkOrderID |  Integer    | An integer that uniquely identifies the Work Order that is associated with this File.|
|  intFileTypeID |  Integer    | An integer that uniquely identifies the File Type.|
|  strName |  String    | A string that identifies the name of the File.|
|  intSize |  Integer    | An integer that identifies the size of the File.|
|  strNotes |  String    | A string that identifies Notes associated with the File.|
|  intFileContentsID |  Integer    | An integer that uniquely identifies the FileContents (used in conjunction with FileContents).|
|  intAssetID |  Integer    | An ID that identifies the Asset associated with the File.|
|  strLink |  String    | A web url, that typically starts with http or https protocol. Network drive paths are not supported, as they are blocked by modern browsers.|
|  intUpdated |  Integer    | An integer capturing the most recent write of a resource in UNIX epoch milliseconds, or milliseconds since 1970-01-01 00:00:00 UTC. The field is read-only and will reflect the time a resource was created if it hasn't been updated at all or the time it was most recently updated.|
|  strUuid |  String    | A unique identifier for the File.|

* Data example 

```json
{
    "intWorkOrderID": 12,
    "intFileTypeID": 2,
    "strName": "strName",
    "intSize": 7,
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

**URL** : `/api/file/:fileid`

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
            "intWorkOrderID": 12,
            "intFileTypeID": 2,
            "strName": "strName",
            "intSize": 7,
            "strNotes": "strNotes",
            "intFileContentsID": 3,
            "intAssetID": 2,
            "strLink": "strLink",
            "intUpdated": 123,
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

**URL** : `/api/file/:fileid`

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
