# Read all WorkOrderTask list Api

Get the all registered WorkOrderTask list.

**URL** : `/api/workordertask`

**Method** : `GET`

**Auth required** : `YES`

**Header**  : `Authorization:{jwt-token}`


## Success Response

**Code** : `200 success`

**Resonse example**


```json
{
    "msg": "Found!",
    "data": [
        {
            "_id": "11",
           "intWorkOrderID": 1234,
            "dtmDateCompleted": 2020-11-26T09:00:36.285+00:00, 
            "intCompletedByUserID": 9876,
            "dblTimeSpentHours": 4,
            "intMeterReadingUnitID": 9010,
            "strTaskNotesCompletion": "The meter reading is over 9000",
            ...
            "__v": 0
        },
        ...
    ]
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
**Condition** : Internal Server Error.

**Code** : `500`

**Resonse example**

```json
{
    "msg": "Internal Server error"
}
```