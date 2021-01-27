
# MoveAsset

This object is used to include assets in a move. A Move object should always be created with the status "Draft" and then MoveAsset objects should be created for each asset that is part of the move. Once all the assets are attached to the move, its status can be changed to "Requested".

Create an MoveAsset if  MoveAsset does not already exist.


**URL** : `/api/moveasset`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intAssetID |  Integer    | The ID of the asset. Please refer to Asset.|
|  intMoveID |  Integer    | The ID of the move. Please refer to Move.|
|  intSiteID |  Integer    | This ID must be the same as the intSiteID of the move. Please refer to Asset.|
|  bolAway |  Boolean    | A boolean that indicates if the asset is currently away from its original location.|
|  bolPending |  Boolean    | A boolean that indicates if the move is currently pending confirmation by and administrator or move manager.|
|  intReasonOfflineID |  Integer    | If bolSetOffline is set to true, then this property can be used to specify a reason to set the asset offline. Please refer to ReasonToSetAssetOffline.|
|  bolSetOnline |  Boolean    | If set to true, then the asset will be put online when the move is confirmed.|
|  bolPending |  Boolean    | A boolean that indicates if the move is currently pending confirmation by and administrator or move manager.|
|  intReasonOnlineID	 |  Integer    | If bolSetOnline is set to true, then this property can be used to specify a reason to set the asset online. Please refer to ReasonToSetAssetOnline.|
|  dtmReturnDate |  Date    | The date when the asset should be checked back in to its original location. If the asset is moved to a destination of type "site/location/equipment", then the asset will be considered "away" from its original location only if a return date was set.|
|  dtmDateReturned |  Date    | The date when the asset was effectively returned to its original location.|
|  intMovedFromID |  Integer    | The ID of the original location of the asset.|
|  strFromAisle |  String    | The aisle where the asset was originally located.|
|  strFromRow |  String    | The row where the asset was originally located.|
|  strFromBin |  String    | The bin where the asset was originally located.|
|  strNotes |  String    | Some additional notes about the asset being part of the move.|
|  bolExclude |  Boolean    | If set to true, the asset is excluded from the move from the original location.|


* Data example 

```json
{
    "intAssetID": 23,
    "intMoveID": 4,
    "intSiteID": 7,
    "bolAway": false,
    "bolPending": true,
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

**URL** : `/api/moveasset`

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
            "intAssetID": 23,
            "intMoveID": 4,
            "intSiteID": 7,
            "bolAway": false,
            "bolPending": true,
            "bolSetOffline": true,
            "intReasonOfflineID": 3,
            "bolSetOnline": true,
            "intReasonOnlineID": 5,
            "dtmReturnDate": 2020-11-26T09:00:36.285+00:00,
            "dtmDateReturned": 2020-11-26T09:00:36.285+00:00,
            "intMovedFromID": 3,
            "strFromAisle": "strFromAisle",
            "strFromRow": "strFromRow",
            "strFromBin": "strFromBin",
            "strNotes": "strNotes",
            "bolExclude": true,
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

**URL** : `/api/moveasset/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intAssetID |  Integer    | The ID of the asset. Please refer to Asset.|
|  intMoveID |  Integer    | The ID of the move. Please refer to Move.|
|  intSiteID |  Integer    | This ID must be the same as the intSiteID of the move. Please refer to Asset.|
|  bolAway |  Boolean    | A boolean that indicates if the asset is currently away from its original location.|
|  bolPending |  Boolean    | A boolean that indicates if the move is currently pending confirmation by and administrator or move manager.|
|  intReasonOfflineID |  Integer    | If bolSetOffline is set to true, then this property can be used to specify a reason to set the asset offline. Please refer to ReasonToSetAssetOffline.|
|  bolSetOnline |  Boolean    | If set to true, then the asset will be put online when the move is confirmed.|
|  bolPending |  Boolean    | A boolean that indicates if the move is currently pending confirmation by and administrator or move manager.|
|  intReasonOnlineID	 |  Integer    | If bolSetOnline is set to true, then this property can be used to specify a reason to set the asset online. Please refer to ReasonToSetAssetOnline.|
|  dtmReturnDate |  Date    | The date when the asset should be checked back in to its original location. If the asset is moved to a destination of type "site/location/equipment", then the asset will be considered "away" from its original location only if a return date was set.|
|  dtmDateReturned |  Date    | The date when the asset was effectively returned to its original location.|
|  intMovedFromID |  Integer    | The ID of the original location of the asset.|
|  strFromAisle |  String    | The aisle where the asset was originally located.|
|  strFromRow |  String    | The row where the asset was originally located.|
|  strFromBin |  String    | The bin where the asset was originally located.|
|  strNotes |  String    | Some additional notes about the asset being part of the move.|
|  bolExclude |  Boolean    | If set to true, the asset is excluded from the move from the original location.|


* Data example 

```json
{
    "intAssetID": 23,
    "intMoveID": 4,
    "intSiteID": 7,
    "bolAway": false,
    "bolPending": true,
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

**URL** : `/api/moveasset/:moveassetid`

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
            "intAssetID": 23,
            "intMoveID": 4,
            "intSiteID": 7,
            "bolAway": false,
            "bolPending": true,
            "bolSetOffline": true,
            "intReasonOfflineID": 3,
            "bolSetOnline": true,
            "intReasonOnlineID": 5,
            "dtmReturnDate": 2020-11-26T09:00:36.285+00:00,
            "dtmDateReturned": 2020-11-26T09:00:36.285+00:00,
            "intMovedFromID": 3,
            "strFromAisle": "strFromAisle",
            "strFromRow": "strFromRow",
            "strFromBin": "strFromBin",
            "strNotes": "strNotes",
            "bolExclude": true,
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

**URL** : `/api/moveasset/:moveassetid`

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
