
# Create AssetOffineTracker 

An AssetOfflineTracker represents the state of an Asset, if the Asset is set to offline. One example scenario: The User sets an Asset to online or offline. By doing so, the state is changed and persisted through this AssetOfflineTracker object. It contains information about the Date when switched to offline and a Reason as to why the state was changed to offline. Note: If an Asset is set to offline, any referenced made to the Asset (example: Bill Of Materials (BOM) Group, WorkOrder, ScheduledMaintenance) will still continue to work.

Create an AssetOfflineTracker if  AssetOfflineTracker does not already exist.


**URL** : `/api/assetofflinetracker`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intReasonOnlineID |  Integer    | An integer that uniquely identifies the associated ReasonOnline (used in conjunction with ReasonToSetAssetOnline).|
|  strOnlineAdditionalInfo |  String    | A string that identifies more additional information associated with the AssetOfflineTracker in online state.|
|  dtmOffLineTo | Timestamp    | A datetime stamp that identifies when the Asset will end its offline state.|
|  intAssetID |  Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|
|  dblProductionHoursAffected |  Double    | An integer that identifies the number of hours the Asset was affected during offline state.|
|  dtmOfflineFrom | Timestamp    | A datetime stamp that identifies when the Asset will begin its offline state.|
|  intReasonOfflineID |Integer    | An integer that uniquely identifies the associated ReasonOffline (used in conjunction with ReasonToSetAssetOffline).|
|  intSetOnlineByUserID |Integer    | An integer that uniquely identifies the User that switched the Asset to online state.|
|  strOfflineAdditionalInfo |String    | A string that identifies more additional information associated with the AssetOfflineTracker in offline state.|
|  intSetOfflineByUserID |Integer    | An integer that uniquely identifies the User that switched the Asset to offline state.|
|  intWorkOrderID |Integer    | The id of the WorkOrder|


* Data example 

```json
{
    "intReasonOnlineID": 3,
    "strOnlineAdditionalInfo": "Online_Additional_Info",
    "dtmOffLineTo": 2020-10-30T20:26:49.518+00:00,
    "intAssetID": 5,
    "dblProductionHoursAffected": 4.432
    ... ...
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

**URL** : `/api/assetofflinetracker`

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
            "intReasonOnlineID": 4,
            "strOnlineAdditionalInfo": "strOnlineAdditionalInfo",
            "dtmOffLineTo": 2020-10-30T20:26:49.518+00:00,
            "intAssetID": 3,
            "dblProductionHoursAffected": 2.3,
            "dtmOfflineFrom": 2020-10-30T20:16:49.518+00:00,
            "intReasonOfflineID": 1,
            "intSetOnlineByUserID": 2,
            "strOfflineAdditionalInfo": "strOfflineAdditionalInfo",
            "intSetOfflineByUserID": 3,
            "intWorkOrderID": 45,
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

**URL** : `/api/assetofflinetracker/:uid`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the asset.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intReasonOnlineID |  Integer    | An integer that uniquely identifies the associated ReasonOnline (used in conjunction with ReasonToSetAssetOnline).|
|  strOnlineAdditionalInfo |  String    | A string that identifies more additional information associated with the AssetOfflineTracker in online state.|
|  dtmOffLineTo | Timestamp    | A datetime stamp that identifies when the Asset will end its offline state.|
|  intAssetID |  Integer    | The ID of the asset. For getting possible values, please refer to the Asset section.|
|  dblProductionHoursAffected |  Double    | An integer that identifies the number of hours the Asset was affected during offline state.|
|  dtmOfflineFrom | Timestamp    | A datetime stamp that identifies when the Asset will begin its offline state.|
|  intReasonOfflineID |Integer    | An integer that uniquely identifies the associated ReasonOffline (used in conjunction with ReasonToSetAssetOffline).|
|  intSetOnlineByUserID |Integer    | An integer that uniquely identifies the User that switched the Asset to online state.|
|  strOfflineAdditionalInfo |String    | A string that identifies more additional information associated with the AssetOfflineTracker in offline state.|
|  intSetOfflineByUserID |Integer    | An integer that uniquely identifies the User that switched the Asset to offline state.|
|  intWorkOrderID |Integer    | The id of the WorkOrder|

* *Data example 

```json
{
    "intReasonOnlineID": 3,
    "strOnlineAdditionalInfo": "Online_Additional_Info",
    "dtmOffLineTo": 2020-10-30T20:26:49.518+00:00,
    "intAssetID": 5,
    "dblProductionHoursAffected": 4.432
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

**URL** : `/api/assetofflinetracker/:assetofflinetrackerid`

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
            "intReasonOnlineID": 4,
            "strOnlineAdditionalInfo": "strOnlineAdditionalInfo",
            "dtmOffLineTo": 2020-10-30T20:26:49.518+00:00,
            "intAssetID": 3,
            "dblProductionHoursAffected": 2.3,
            "dtmOfflineFrom": 2020-10-30T20:16:49.518+00:00,
            "intReasonOfflineID": 1,
            "intSetOnlineByUserID": 2,
            "strOfflineAdditionalInfo": "strOfflineAdditionalInfo",
            "intSetOfflineByUserID": 3,
            "intWorkOrderID": 45,
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

**URL** : `/api/assetofflinetracker/:assetofflinetrackerid`

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
