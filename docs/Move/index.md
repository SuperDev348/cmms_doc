
# Move

This object represents one or several assets being moved from their original location to a new location or to a temporary destination. The temporary destination can be a location or site, a user, a business or even a work order. A Move object should be created with the "Draft" status and MoveAsset objects should then be associated with it. The status of the Move object should then be changed to "Requested" in order to trigger notification sending to the site's move managers (see MoveSiteManager). The site's move managers or an administrator will then be able to confirm the move by updating its status to "Confirmed", which will trigger the move to be effectively performed. If a move manager or an administrator changes the status of a move to "Requested", the status will be changed automatically to "Confirmed" and the move will be performed straight away.

Create an Move if  Move does not already exist.


**URL** : `/api/move`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intDestinationTypeID |  Integer    | An integer defining the type of destination for the move. Possible values are 1 for an asset (site, location or equipment), 2 for a user, 3 for a business, 4 for a work order.|
|  intAssetDestinationID |  Integer    | A reference to the Asset, in case the destination is an asset.|
|  strAisle |  String    | In case the destination is a location, the destination aisle can be defined.|
|  strRow |  String    | In case the destination is a location, the destination row can be defined.|
|  strBin |  String    | In case the destination is a location, the destination bin can be defined.|
|  intUserDestinationID |  Integer    | A reference to the User, in case the destination is a user.|
|  intBusinessDestinationID |  Integer    | A reference to the Business, in case the destination is a business.|
|  intWorkOrderDestinationID |  Integer    | A reference to the WorkOrder, in case the destination is an work order.|
|  intProjectDestinationID |  Integer    | A reference to the Project, in case the destination is a project.|
|  intSiteID |  Integer    | The ID of the destination site (see Asset). This has to match the site of the destination.|
|  intFromSiteID |  Integer    | The ID of the site from which the assets are taken. All assets must come from the same site.|
|  intMoveStatusID |  Integer    | The status of the move. A move should be created as a "Draft". See MoveStatus.|
|  intRequestedByID |  Integer    | The ID of the user who requested the move. See User.|
|  dtmDateRequested |  Date    | The date when the move was requested.|
|  intMovedByID |  Integer    | The ID of the user who will be actually performing the move, if different from the one requesting the move. See User.|
|  dtmMoveDate |  Date    | The date when the move will physically happen.|
|  intConfirmedByID |  Integer    | The ID of the user who confirmed the move. See User.|
|  dtmDateConfirmed |  Date    | The date when the move was confirmed by a move manager or an administrator.|
|  intRejectedByID |  Integer    | If the move was rejected, the ID of the user who rejected it. See User.|
|  dtmDateRejected |  Date    | If the move was rejected, the date when it happened.|
|  strNotes |  String    | Some additional notes about the move.|


* Data example 

```json
{
    "intDestinationTypeID": 1,
    "intAssetDestinationID": 5,
    "strAisle": "strAisle",
    "strRow": "strRow",
    "strBin": "strBin",
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

**URL** : `/api/move`

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
            "intDestinationTypeID": 1,
            "intAssetDestinationID": 5,
            "strAisle": "strAisle",
            "strRow": "strRow",
            "strBin": "strBin",
            "intUserDestinationID": 3,
            "intBusinessDestinationID": 2,
            "intWorkOrderDestinationID": 2,
            "intProjectDestinationID": 4,
            "intSiteID": 3,
            "intFromSiteID": 32,
            "intMoveStatusID": 2,
            "intRequestedByID": 2,
            "dtmDateRequested": 2020-11-26T09:00:36.285+00:00,
            "intMovedByID": 4,
            "dtmMoveDate": 2020-11-26T09:00:36.285+00:00,
            "intConfirmedByID": 5,
            "dtmDateConfirmed": 2020-11-26T09:00:36.285+00:00,
            "intRejectedByID": 3,
            "dtmDateRejected": 2020-11-26T09:00:36.285+00:00,
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

**URL** : `/api/move/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intDestinationTypeID |  Integer    | An integer defining the type of destination for the move. Possible values are 1 for an asset (site, location or equipment), 2 for a user, 3 for a business, 4 for a work order.|
|  intAssetDestinationID |  Integer    | A reference to the Asset, in case the destination is an asset.|
|  strAisle |  String    | In case the destination is a location, the destination aisle can be defined.|
|  strRow |  String    | In case the destination is a location, the destination row can be defined.|
|  strBin |  String    | In case the destination is a location, the destination bin can be defined.|
|  intUserDestinationID |  Integer    | A reference to the User, in case the destination is a user.|
|  intBusinessDestinationID |  Integer    | A reference to the Business, in case the destination is a business.|
|  intWorkOrderDestinationID |  Integer    | A reference to the WorkOrder, in case the destination is an work order.|
|  intProjectDestinationID |  Integer    | A reference to the Project, in case the destination is a project.|
|  intSiteID |  Integer    | The ID of the destination site (see Asset). This has to match the site of the destination.|
|  intFromSiteID |  Integer    | The ID of the site from which the assets are taken. All assets must come from the same site.|
|  intMoveStatusID |  Integer    | The status of the move. A move should be created as a "Draft". See MoveStatus.|
|  intRequestedByID |  Integer    | The ID of the user who requested the move. See User.|
|  dtmDateRequested |  Date    | The date when the move was requested.|
|  intMovedByID |  Integer    | The ID of the user who will be actually performing the move, if different from the one requesting the move. See User.|
|  dtmMoveDate |  Date    | The date when the move will physically happen.|
|  intConfirmedByID |  Integer    | The ID of the user who confirmed the move. See User.|
|  dtmDateConfirmed |  Date    | The date when the move was confirmed by a move manager or an administrator.|
|  intRejectedByID |  Integer    | If the move was rejected, the ID of the user who rejected it. See User.|
|  dtmDateRejected |  Date    | If the move was rejected, the date when it happened.|
|  strNotes |  String    | Some additional notes about the move.|


* Data example 

```json
{
    "intDestinationTypeID": 1,
    "intAssetDestinationID": 5,
    "strAisle": "strAisle",
    "strRow": "strRow",
    "strBin": "strBin",
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

**URL** : `/api/move/:moveid`

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
            "intDestinationTypeID": 1,
            "intAssetDestinationID": 5,
            "strAisle": "strAisle",
            "strRow": "strRow",
            "strBin": "strBin",
            "intUserDestinationID": 3,
            "intBusinessDestinationID": 2,
            "intWorkOrderDestinationID": 2,
            "intProjectDestinationID": 4,
            "intSiteID": 3,
            "intFromSiteID": 32,
            "intMoveStatusID": 2,
            "intRequestedByID": 2,
            "dtmDateRequested": 2020-11-26T09:00:36.285+00:00,
            "intMovedByID": 4,
            "dtmMoveDate": 2020-11-26T09:00:36.285+00:00,
            "intConfirmedByID": 5,
            "dtmDateConfirmed": 2020-11-26T09:00:36.285+00:00,
            "intRejectedByID": 3,
            "dtmDateRejected": 2020-11-26T09:00:36.285+00:00,
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

**URL** : `/api/move/:moveid`

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
