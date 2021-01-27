
# MoveBackAsset

This object is used to include assets in a return move. A MoveBack object should always be created with the status "Draft" and then MoveBackAsset objects should be created for each asset that is part of the return move. Once all the assets are attached to the return move, its status can be changed to "Requested".

Create an MoveBackAsset if  MoveBackAsset does not already exist.


**URL** : `/api/movebackasset`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intAssetID |  Integer    | The ID of the asset to attach to the return move. See Asset.|
|  intMoveBackID |  Integer    | The ID of the return move. See MoveBack.|
|  intOriginalMoveAssetID |  Integer    | The ID of the MoveAsset object that was used to initially put the asset away from its location.|
|  bolPending |  Boolean    | A boolean that indicates if the return move is currently pending confirmation by and administrator or move manager.|
|  bolSetBackOnline |  Boolean    | If set to true, then the asset will be put back online when the return move is confirmed.|
|  intReasonOnlineID |  Integer    | If bolSetOnline is set to true, then this property can be used to specify a reason to set the asset online. Please refer to ReasonToSetAssetOnline.|
|  bolSetBackOffline |  Boolean    | If set to true, then the asset will be put back offline when the return move is confirmed.|
|  intReasonOfflineID |  Integer    | If bolSetOffline is set to true, then this property can be used to specify a reason to set the asset offline. Please refer to ReasonToSetAssetOffline.|
|  strToAisle	 |  String    | The aisle the asset is put back in. This will be defaulted to the original aisle of the asset.|
|  strToBin |  String    | The bin the asset is put back in. This will be defaulted to the original bin of the asset.|
|  strToRow |  String    | The row the asset is put back in. This will be defaulted to the original row of the asset.|
|  intSiteID |  Integer    | The ID of the site where the asset is put back. This has to be consistent with the site ID of the MoveBack object and other MoveBackAsset objects associated to it. See Asset.|
|  strNotes |  String    | Some additional notes about the asset being part of the return move.|
|  bolExclude |  Boolean    | If set to true, the asset is excluded from the move back from the temporary location.|


* Data example 

```json
{
    "intAssetID": 23,
    "intMoveBackID": 4,
    "intOriginalMoveAssetID": 7,
    "bolPending": false,
    "bolSetBackOnline": false,
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

**URL** : `/api/movebackasset`

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
            "intMoveBackID": 4,
            "intOriginalMoveAssetID": 7,
            "bolPending": false,
            "bolSetBackOnline": false,
            "intReasonOnlineID": 23,
            "bolSetBackOffline": true,
            "intReasonOfflineID": 7,
            "strToAisle": "strToAisle",
            "strToBin": "strToBin",
            "strToRow": "strToRow",
            "intSiteID": 4,
            "strNotes": "strNotes",
            "bolExclude": false,
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

**URL** : `/api/movebackasset/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intAssetID |  Integer    | The ID of the asset to attach to the return move. See Asset.|
|  intMoveBackID |  Integer    | The ID of the return move. See MoveBack.|
|  intOriginalMoveAssetID |  Integer    | The ID of the MoveAsset object that was used to initially put the asset away from its location.|
|  bolPending |  Boolean    | A boolean that indicates if the return move is currently pending confirmation by and administrator or move manager.|
|  bolSetBackOnline |  Boolean    | If set to true, then the asset will be put back online when the return move is confirmed.|
|  intReasonOnlineID |  Integer    | If bolSetOnline is set to true, then this property can be used to specify a reason to set the asset online. Please refer to ReasonToSetAssetOnline.|
|  bolSetBackOffline |  Boolean    | If set to true, then the asset will be put back offline when the return move is confirmed.|
|  intReasonOfflineID |  Integer    | If bolSetOffline is set to true, then this property can be used to specify a reason to set the asset offline. Please refer to ReasonToSetAssetOffline.|
|  strToAisle	 |  String    | The aisle the asset is put back in. This will be defaulted to the original aisle of the asset.|
|  strToBin |  String    | The bin the asset is put back in. This will be defaulted to the original bin of the asset.|
|  strToRow |  String    | The row the asset is put back in. This will be defaulted to the original row of the asset.|
|  intSiteID |  Integer    | The ID of the site where the asset is put back. This has to be consistent with the site ID of the MoveBack object and other MoveBackAsset objects associated to it. See Asset.|
|  strNotes |  String    | Some additional notes about the asset being part of the return move.|
|  bolExclude |  Boolean    | If set to true, the asset is excluded from the move back from the temporary location.|


* Data example 

```json
{
    "intAssetID": 23,
    "intMoveBackID": 4,
    "intOriginalMoveAssetID": 7,
    "bolPending": false,
    "bolSetBackOnline": false,
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

**URL** : `/api/movebackasset/:movebackassetid`

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
            "intMoveBackID": 4,
            "intOriginalMoveAssetID": 7,
            "bolPending": false,
            "bolSetBackOnline": false,
            "intReasonOnlineID": 23,
            "bolSetBackOffline": true,
            "intReasonOfflineID": 7,
            "strToAisle": "strToAisle",
            "strToBin": "strToBin",
            "strToRow": "strToRow",
            "intSiteID": 4,
            "strNotes": "strNotes",
            "bolExclude": false,
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

**URL** : `/api/movebackasset/:movebackassetid`

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
