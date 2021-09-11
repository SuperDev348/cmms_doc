# Create AssetCategory
This object is used for representing a category of assets. Main categories are equipment, tools and facilities but more categories can be created under those root categories.
   
Create an AssetCategory if  AssetCategory does not already exist.

**URL** : `/api/assetcategory`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intParentID |  Integer    | The ID of the parent category this category is directly attached to.|
|  strName |  String    | A display name for the category.|
|  intSysCode |  Integer    | System codes are used to define root categories with a significant meaning for the CMMS. There should be only one category with each system code for a given tenant. Possible values are : 0 for Assets, 1 for Locations And Facilities, 2 for Equipment, 3 for Tools, 4 for Parts And Supplies, 5 for Inventory Storage, 6 for Buildings, 7 for Plants, 10 for Regions and 11 for Rotating Spares.|
|  bolOverrideRules |  Boolean    | If set to true, indicates that the associated asset category overrides the rules set.|
|  bolOverrideRules |  Boolean    | If set to true, indicates that the associated asset category overrides the rules set.|

** Success Response:**

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
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
    "msg": "strName is required"
}
```
```json
{
    "msg": "Create failed"
}
```
# Get all AssetCategory list 

Get the all registered AssetCategory list.

**URL** : `/api/assetcategory`

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
            "_id": "5f6a6f90d9741d152c754178",
            "intParentID": 11,
            "strName": "String",
            "intSysCode": 3,
            "bolOverrideRules":true
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

# Get Single AssetCategory By Id

Get a single AssetCategory by id if current AssetCategory was registered on it.

**URL** : `/api/assetcategory/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the assetcategory.

** Success Response **

**Code** : `200 success`

* Resonse example 


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "5f6896897b9884253cf6bdb6",
            "intParentID":"Integer",
            "strName":"String",
            "intSysCode":3,
            "bolOverrideRules":true
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

**Condition** : If AssetCategory does not exist on server.

**Code** : `404 Not Found`

* Content example 

```json
{
   "msg": "Not found", 
   "data":null
}
```

# Update AssetCategory 

Update the AssetCategory by Id

**URL** : `/api/assetcategory/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the AssetCategory.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intParentID |  Integer    | The ID of the parent category this category is directly attached to.|
|  strName |  String    | A display name for the category.|
|  intSysCode |  Integer    | System codes are used to define root categories with a significant meaning for the CMMS. There should be only one category with each system code for a given tenant. Possible values are : 0 for Assets, 1 for Locations And Facilities, 2 for Equipment, 3 for Tools, 4 for Parts And Supplies, 5 for Inventory Storage, 6 for Buildings, 7 for Plants, 10 for Regions and 11 for Rotating Spares.|
|  bolOverrideRules |  Boolean    | If set to true, indicates that the associated asset category overrides the rules set.|
|  bolOverrideRules |  Boolean    | If set to true, indicates that the associated asset category overrides the rules set.|

** Success Response **

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

# Delete AssetCategory

Delete a AssetCategory by Id

**URL** : `/api/assetcategory/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the assetcategory.

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

