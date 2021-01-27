
# Create AssetUser

An AssetUser represents the relationship between a particular User within your CMMS and the associated Assets with this User. It contains information about the Date Added, and the Asset User Type, such as Manager, Technician, Operator, and Consumer. See the Asset object for more details and the User object for more information. You can have multiple Assets associated with one User. You can have multiple AssetUsers associated in your CMMS.

Create an AssetUser if  AssetUser does not already exist.


**URL** : `/api/assetuser`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intAssetUserTypeID |  Integer    | An integer that uniquely identifies the AssetUserType (used in conjunction with AssetUserType).|
|  dtmDateAdded |  Timestamp    | The date time stamp for when the Asset was added in the CMMS by the User.|
|  intUserID | Integer    | An integer that uniquely identifies the User.|
|  intAssetID |  Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|


* Data example 

```json
{
    "intAssetUserTypeID": 3,
    "dtmDateAdded": 2020-10-30T20:26:49.518+00:00,
    "intUserID": 5,
    "intAssetID": 4
}
```
** Success Response: **

**Code** : `200 success`

* Resonse example

```json
{
   "msg": "Asset added successfully!",
    "data": {id: "4rt8a89c24753232419483c"}
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

**URL** : `/api/assetuser`

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
            "intAssetUserTypeID": 3,
            "dtmDateAdded": 2020-10-30T20:26:49.518+00:00,
            "intUserID": 5,
            "intAssetID": 4
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

**URL** : `/api/assetuser/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intAssetUserTypeID |  Integer    | An integer that uniquely identifies the AssetUserType (used in conjunction with AssetUserType).|
|  dtmDateAdded |  Timestamp    | The date time stamp for when the Asset was added in the CMMS by the User.|
|  intUserID | Integer    | An integer that uniquely identifies the User.|
|  intAssetID |  Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|

* *Data example 

```json
{
    "intAssetUserTypeID": 3,
    "dtmDateAdded": 2020-10-30T20:26:49.518+00:00,
    "intUserID": 5,
    "intAssetID": 4
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

**URL** : `/api/assetuser/:assetuserid`

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
            "intAssetUserTypeID": 3,
            "dtmDateAdded": 2020-10-30T20:26:49.518+00:00,
            "intUserID": 5,
            "intAssetID": 4
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

**URL** : `/api/assetuser/:assetuserid`

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
