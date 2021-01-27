
# MoveBack

This object represents a return move to put an asset back to its original location after it was put away as part of a Move. A return move should always be created with a "Draft" status and MoveBackAsset objects should then be attached to it. The status of the MoveBack object should then be changed to "Requested" in order to trigger notification sending to the site's move managers (see MoveSiteManager). The site's move managers or an administrator will then be able to confirm the move by updating its status to "Confirmed", which will trigger the move to be effectively performed. If a move manager or an administrator changes the status of a move to "Requested", the status will be changed automatically to "Confirmed" and the move will be performed straight away

Create an MoveBack if  MoveBack does not already exist.


**URL** : `/api/moveback`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intMovedBackByUserID |  Integer    | The ID of the user who will actually be performing the return move, if different from the one requesting the return move. See User.|
|  dtmMoveBackDate |  Date    | The date when the return move will physically happen.|
|  intRequestedByID |  Integer    | The ID of the user who requested the return move. See User.|
|  dtmDateRequested |  Date    | The date when the return move was requested.|
|  intConfirmedByID |  Integer    | It he return move was accepted, the ID of the user who accepted it. See User.|
|  dtmDateConfirmed |  Date    | If the return move was accepted, the date when it happened.|
|  intRejectedByID |  Integer    | If the return move was rejected, the ID of the user who rejected it. See User.|
|  dtmDateCanceled |  Date    | If the return move was rejected, the date when it happened.|
|  intMoveStatusID	 |  Integer    | The status of the return move. A return move should be created as a "Draft". See MoveStatus.|
|  intFromSiteID |  Integer    | The ID of the site where the assets were temporarily moved. See Asset.|
|  intSiteID |  Integer    | The ID of the site where the assets are checked back in. See Asset.|
|  strNotes |  String    | Some additional notes about the return move.|


* Data example 

```json
{
    "intMovedBackByUserID": 23,
    "dtmMoveBackDate": 2020-11-26T09:00:36.285+00:00,
    "intRequestedByID": 7,
    "dtmDateRequested": 2020-11-26T09:00:36.285+00:00,
    "intConfirmedByID": 4,
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

**URL** : `/api/moveback`

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
            "intMovedBackByUserID": 23,
            "dtmMoveBackDate": 2020-11-26T09:00:36.285+00:00,
            "intRequestedByID": 7,
            "dtmDateRequested": 2020-11-26T09:00:36.285+00:00,
            "intConfirmedByID": 4,
            "dtmDateConfirmed": 2020-11-26T09:00:36.285+00:00,
            "intRejectedByID": 4,
            "dtmDateCanceled": 2020-11-26T09:00:36.285+00:00,
            "intMoveStatusID": 4,
            "intFromSiteID": 2,
            "intSiteID	": 5,
            "strNotes": "strNotes",
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

**URL** : `/api/moveback/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intMovedBackByUserID |  Integer    | The ID of the user who will actually be performing the return move, if different from the one requesting the return move. See User.|
|  dtmMoveBackDate |  Date    | The date when the return move will physically happen.|
|  intRequestedByID |  Integer    | The ID of the user who requested the return move. See User.|
|  dtmDateRequested |  Date    | The date when the return move was requested.|
|  intConfirmedByID |  Integer    | It he return move was accepted, the ID of the user who accepted it. See User.|
|  dtmDateConfirmed |  Date    | If the return move was accepted, the date when it happened.|
|  intRejectedByID |  Integer    | If the return move was rejected, the ID of the user who rejected it. See User.|
|  dtmDateCanceled |  Date    | If the return move was rejected, the date when it happened.|
|  intMoveStatusID	 |  Integer    | The status of the return move. A return move should be created as a "Draft". See MoveStatus.|
|  intFromSiteID |  Integer    | The ID of the site where the assets were temporarily moved. See Asset.|
|  intSiteID |  Integer    | The ID of the site where the assets are checked back in. See Asset.|
|  strNotes |  String    | Some additional notes about the return move.|


* Data example 

```json
{
    "intMovedBackByUserID": 23,
    "dtmMoveBackDate": 2020-11-26T09:00:36.285+00:00,
    "intRequestedByID": 7,
    "dtmDateRequested": 2020-11-26T09:00:36.285+00:00,
    "intConfirmedByID": 4,
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

**URL** : `/api/moveback/:movebackid`

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
            "intMovedBackByUserID": 23,
            "dtmMoveBackDate": 2020-11-26T09:00:36.285+00:00,
            "intRequestedByID": 7,
            "dtmDateRequested": 2020-11-26T09:00:36.285+00:00,
            "intConfirmedByID": 4,
            "dtmDateConfirmed": 2020-11-26T09:00:36.285+00:00,
            "intRejectedByID": 4,
            "dtmDateCanceled": 2020-11-26T09:00:36.285+00:00,
            "intMoveStatusID": 4,
            "intFromSiteID": 2,
            "intSiteID	": 5,
            "strNotes": "strNotes",
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

**URL** : `/api/moveback/:movebackid`

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
