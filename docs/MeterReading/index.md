# Create MeterReading

This object is used to store meter readings for some of the managed assets.

Create a MeterReading if  MeterReading does not already exist.

**URL** : `/api/meterreading`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Required | Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  intWorkOrderID |  |Integer    | The ID of the work order, in case the meter reading was submitted during the completion of a work order. Please refer to the WorkOrder section.|
|  intSubmittedByUserID |  |Integer    | The ID of the user who submitted the meter reading. For getting all possible values, please refer to the User section.|
|  intMeterReadingUnitsID | Yes |Integer    | The ID of the unit used for the meter reading. For getting all possible values, please refer to the MeterReadingUnit section.|
|  dblMeterReading | Yes |Double    | The actual value of the meter reading.|
|  intAssetID | Yes |Integer    | The ID of the asset the meter reading was performed on. For getting all possible values, please refer to the Asset section.|
|  dtmDateSubmitted | Yes |timestamp     | The date and time of the moment when the meter reading was submitted.|

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "1"}
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
    "msg": "intMeterReadingUnitsID is required"
}
```
```json
{
    "msg": "Create failed"
}
```

# Get all MeterReading list

Get the all registered MeterReading list by AssetId.

**URL** : `/api/meterreading/:assetId`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the Asset.

** Success Response: **

**Code** : `200 success`

* Resonse example


```json
{
    "msg": "Found!",
    "data": [
        {
            "_id": "6",
            "intWorkOrderID": "7",
            "intSubmittedByUserID": Object,
            "intMeterReadingUnitsID": Object,
            "dblMeterReading": 0.2,
            "intAssetID": 4,
            "dtmDateSubmitted":2020-10-16T18:12:30.433+00:00,
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

# Update MeterReading

Update the MeterReading by Id

**URL** : `/api/meterreading/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the MeterReading.

| Param       | Required | Type     | Description     | 
| :------------- |  :-----------|  :----------- |----------- |
|  intWorkOrderID |  |Integer    | The ID of the work order, in case the meter reading was submitted during the completion of a work order. Please refer to the WorkOrder section.|
|  intSubmittedByUserID |  |Integer    | The ID of the user who submitted the meter reading. For getting all possible values, please refer to the User section.|
|  intMeterReadingUnitsID | Yes |Integer    | The ID of the unit used for the meter reading. For getting all possible values, please refer to the MeterReadingUnit section.|
|  dblMeterReading | Yes |Double    | The actual value of the meter reading.|
|  intAssetID | Yes |Integer    | The ID of the asset the meter reading was performed on. For getting all possible values, please refer to the Asset section.|
|  dtmDateSubmitted | Yes |timestamp     | The date and time of the moment when the meter reading was submitted.|

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Updated successfully!"
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
    "msg": "Update failed"
}
```

# Delete MeterReading

Delete a MeterReading by Id

**URL** : `/api/meterreading/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the MeterReading.

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

