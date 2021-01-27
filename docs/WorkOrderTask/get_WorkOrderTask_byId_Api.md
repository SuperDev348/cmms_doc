# Get Single WorkOrderTask By Id Api

Get a single WorkOrderTask by id if current WorkOrderTask was registered on it.

**URL** : `/api/workordertask/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the WorkOrderTask.

## Success Response

**Code** : `200 success`

**Resonse example**


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": 11,
            "intWorkOrderID": 1234,
            "dtmDateCompleted": 2020-11-26T09:00:36.285+00:00, 
            "intCompletedByUserID": 9876,
            "dblTimeSpentHours": 4,
            "intMeterReadingUnitID": 9010,
            "strTaskNotesCompletion": "The meter reading is over 9000",
            ...
        
        }
}
```

## Error Responses

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

**Resonse example**

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

### Or

**Condition** : If workordertask does not exist on server.

**Code** : `404 Not Found`

**Content example**

```json
{
   "msg": "Not found", 
   "data":null
}
```