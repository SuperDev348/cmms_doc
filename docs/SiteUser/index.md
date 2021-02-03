
# SiteUser

For a multi-sites tenant, this object is used to link a user to a site.

Create an SiteUser if  SiteUser does not already exist.


**URL** : `/api/siteuser`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intSiteID |  Integer  |For multi-site tenants, the ID of the site the work order is related to. A site is an asset itself, so for possible values, please refer to the Asset section.|
|  intUserID	 |  Integer    | The ID of the user. For getting possible values, please refer to the User section.|


* Data example 

```json
{
    "intSiteID": 2,
    "intUserID": 12
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

**URL** : `/api/siteuser`

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
            "intSiteID": 2,
            "intUserID": 12,
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

**URL** : `/api/siteuser/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intSiteID |  Integer  |For multi-site tenants, the ID of the site the work order is related to. A site is an asset itself, so for possible values, please refer to the Asset section.|
|  intUserID	 |  Integer    | The ID of the user. For getting possible values, please refer to the User section.|


* Data example 

```json
{
    "intSiteID": 2,
    "intUserID": 12
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

**URL** : `/api/siteuser/:siteuserid`

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
            "intSiteID": 2,
            "intUserID": 12,
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

**URL** : `/api/siteuser/:siteuserid`

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
