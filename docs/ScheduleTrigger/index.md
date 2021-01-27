# Create ScheduleTrigger

A ScheduleTrigger represents a trigger that is created on a ScheduledMaintenance for scheduling a WorkOrder. A WorkOrder can be scheduled for a ScheduledMaintenance when any of the ScheduleTriggers fire or when all of the ScheduleTriggers are fired depending on the configuration specified on ScheduledMaintenance.

Create an ScheduleTrigger  if  ScheduleTrigger  does not already exist.

**URL** : `/api/scheduletrigger`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  bolTSWFriday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Friday.|
|  bolTSWMonday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Monday.|
|  bolTSWSaturday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Saturday.|
|  bolTSWSunday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Sunday.|
|  bolTSWThursday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Thursday.|
|  bolTSWTuesday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Tuesday.|
|  bolTSWWednesday |  boolean     |If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Wednesday.|
|  strDatLogicHourly |  String     | For a Time Schedule trigger, this field shows the logic of the hourly setting. It is set to x (fixed) or t (floating).|
|  strDatLogicDaily |  String     | For a Time Schedule trigger, this field shows the logic of the daily setting. It is set to x (fixed) or t (floating).|
|  strDatLogicMonthly |  String     | For a Time Schedule trigger, this field shows the logic of the monthly setting. It is set to x (fixed) or t (floating).|
|  strDatLogicYearly |  String     | For a Time Schedule trigger, this field shows the logic of the yearly setting. It is set to x (fixed) or t (floating).|
|  dblLastMeterReading |  double| For a Meter Reading trigger, this field identifies the last meter reading recorded.|
|  dblRMeterReading |  double | For a Meter Reading trigger, this field specifies the interval in which it should be triggered (Ex: Every 90 hours).|
|  dblROMeterReading |  double  | For a Meter Reading trigger, this field specifies the value when it should be triggered (Ex: When Hours (h) Reading is greater than 10).|
|  dblRREndBy |  double  | For a Meter Reading trigger, this field specifies the End By Reading configured for the trigger. If no End By is configured, it defaults to 0.|
|  dblRRStart |  double  | For a Meter Reading trigger, this field specifies the Start At Reading configured for the trigger. If no Start At is configured, it defaults to 0.|
|  dtmLastTriggered |  timestamp  | The date and time which the trigger was triggered last.|
|  intAssetEventTypeID |  Integer  | For an Event trigger, this field specifies the ID of the AssetEventType associated with the trigger.|
|  intRMeterReadingUnitID |  Integer  |For a Meter Reading trigger, this field specifies ID of MeterReadingUnit associated with the trigger when the trigger is configured for Every reading of the unit.|
|  intROMeterReadingUnitID |  Integer  |For a Meter Reading trigger, this field specifies ID of MeterReadingUnit associated with the trigger when the trigger is configured based on a condition.|
|  intRREndAfter |  Integer  |For Meter Reading trigger, it specifies the reading after which to stop the trigger.|
|  intScheduledMaintenanceID |  Integer  |The ID of the ScheduledMaintenance associated with the trigger.|
|  intTREndAfter |  Integer  |This field is used to determine after how many occurrences the trigger should be stopped.|
|  intTSDEveryDays |  Integer  |For a Time Schedule trigger that is configured to be daily, it denotes the daily rate of repetition associated with the trigger.|
|  intTSHEveryHours |Integer |   For a Time Schedule trigger that is configured to be hourly, it denotes the hourly rate of repetition associated with the trigger.|
|  intTSMDayOfMonth |Integer | For a Time Schedule trigger that is configured to be monthly, it denotes the day of the month associated with the trigger.|
|  intTSMEveryMonths |Integer | For Time Schedule trigger that is configured to be monthly, it denotes the monthly rate of repetition associated with the trigger.|
|  intTSWEveryWeeks |Integer | For a Time Schedule trigger that is configured to be weekly, it denotes the weekly rate of repetition associated with the trigger.|
|  intTSYDayOfMonth |Integer | For a Time Schedule trigger that is configured to be yearly, it denotes the day of the month associated with the trigger.|
|  intTSYEveryYears |Integer |For a Time Schedule trigger that is configured to be yearly, it denotes the yearly rate of repetition associated with the trigger.|
|  intTSYMonthOfYear |Integer |For a Time Schedule trigger that is configured to be yearly, it denotes the month of the year associated with the trigger. Do note that the months start at 0. For eg: The year starts at January (0) and ends with December (11).|
|  strROType |String |For a Meter Reading trigger, this field is the Trigger Meter (When) Comparison. It is set to l (less than), g (greater than), or empty if not meter reading based.|
|  strRRType |String |It is the Trigger Schedule No End Date. It is set to empty if not time based, n (no end date), b (has a end date).|
|  strRType |String |For a Meter Reading trigger, this field is the Trigger Meter Type. It is set to e (every), o (other), empty if not meter reading based.|
|  strTRType |String |It is the Trigger Reading End type. It is set to n (no end reading), b (end by reading).|
|  strTSType |String |It is the Trigger Schedule Type. It is set to h (hourly), d (daily), w (weekly), m (monthly), y (yearly).|
|  strType |String |This field denotes the type of the Schedule Trigger. It is set to t for Time Schedule trigger, r for Meter Reading Trigger and e for an Event Trigger.|
|  strMrLogic |String |For a Meter Reading trigger, this field is used to determine the logic of the schedule. It is set x (fixed) or t (floating).|
|  bolMrByWOClosed |boolean |If set to true, the Meter Reading trigger should check the reading when the WO is closed.|
|  bolCreateWorkOrderOnStartDate |boolean |If set to true, it indicates that a WorkOrder be created on the start date when the trigger is scheduled.|
|  intAssetID |Integer |Indicates the ID for an Asset associated with the ScheduledMaintenance that creates the trigger. For a Meter Reading trigger, this field needs to be populated with the Asset id of one of the ScheduledMaintenance Assets.|
|  strScheduleDescription |String |The description for the Schedule Trigger.|
|  intTRTriggerTime |Integer |For all the Time Schedule triggers except an hourly trigger, this field specifies time at which it will be triggered. It can have a value between 0 and 23.|

** Success Response: **

**Code** : `200 success`

* Resonse example 

```json
{
   "msg": "Created successfully!",
    "data": {id: "71"}
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
    "msg": "Create failed"
}
```

# Get all ScheduleTrigger list

Get the all registered ScheduleTrigger list.

**URL** : `/api/scheduletrigger`

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
            "_id": "32",
            "strAssignedUserIds":" 13 8 9 "
            "intPriorityID": 4156,
            "intWorkOrderStatusID": 4,
            "strAssets":"ASSET ABC (0010), ASSET DEF (0011)"
            "intSiteID": 3345,
             "strAssignedUsers": "John Doe, Samuel Smith",
            "intRequestedByUserID": 667, 
            strEmailUserGuest:"",
            dtmDateCreated:"",
            strAssetIds:" 9 78 675 ",
            dtmDateCompleted:"",
            intCompletedByUserID:555
            ...
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

# Update ScheduleTrigger

Update the ScheduleTrigger by Id

**URL** : `/api/scheduletrigger/:Id`

**Method** : `PUT`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ScheduleTrigger.

| Param       | Type     | Description     | 
| :------------- |  :----------- |----------- |
|  bolTSWFriday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Friday.|
|  bolTSWMonday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Monday.|
|  bolTSWSaturday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Saturday.|
|  bolTSWSunday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Sunday.|
|  bolTSWThursday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Thursday.|
|  bolTSWTuesday |  boolean     | If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Tuesday.|
|  bolTSWWednesday |  boolean     |If set to true, this field indicates that the Time Schedule trigger is configured to run weekly on every Wednesday.|
|  strDatLogicHourly |  String     | For a Time Schedule trigger, this field shows the logic of the hourly setting. It is set to x (fixed) or t (floating).|
|  strDatLogicDaily |  String     | For a Time Schedule trigger, this field shows the logic of the daily setting. It is set to x (fixed) or t (floating).|
|  strDatLogicMonthly |  String     | For a Time Schedule trigger, this field shows the logic of the monthly setting. It is set to x (fixed) or t (floating).|
|  strDatLogicYearly |  String     | For a Time Schedule trigger, this field shows the logic of the yearly setting. It is set to x (fixed) or t (floating).|
|  dblLastMeterReading |  double| For a Meter Reading trigger, this field identifies the last meter reading recorded.|
|  dblRMeterReading |  double | For a Meter Reading trigger, this field specifies the interval in which it should be triggered (Ex: Every 90 hours).|
|  dblROMeterReading |  double  | For a Meter Reading trigger, this field specifies the value when it should be triggered (Ex: When Hours (h) Reading is greater than 10).|
|  dblRREndBy |  double  | For a Meter Reading trigger, this field specifies the End By Reading configured for the trigger. If no End By is configured, it defaults to 0.|
|  dblRRStart |  double  | For a Meter Reading trigger, this field specifies the Start At Reading configured for the trigger. If no Start At is configured, it defaults to 0.|
|  dtmLastTriggered |  timestamp  | The date and time which the trigger was triggered last.|
|  intAssetEventTypeID |  Integer  | For an Event trigger, this field specifies the ID of the AssetEventType associated with the trigger.|
|  intRMeterReadingUnitID |  Integer  |For a Meter Reading trigger, this field specifies ID of MeterReadingUnit associated with the trigger when the trigger is configured for Every reading of the unit.|
|  intROMeterReadingUnitID |  Integer  |For a Meter Reading trigger, this field specifies ID of MeterReadingUnit associated with the trigger when the trigger is configured based on a condition.|
|  intRREndAfter |  Integer  |For Meter Reading trigger, it specifies the reading after which to stop the trigger.|
|  intScheduledMaintenanceID |  Integer  |The ID of the ScheduledMaintenance associated with the trigger.|
|  intTREndAfter |  Integer  |This field is used to determine after how many occurrences the trigger should be stopped.|
|  intTSDEveryDays |  Integer  |For a Time Schedule trigger that is configured to be daily, it denotes the daily rate of repetition associated with the trigger.|
|  intTSHEveryHours |Integer |   For a Time Schedule trigger that is configured to be hourly, it denotes the hourly rate of repetition associated with the trigger.|
|  intTSMDayOfMonth |Integer | For a Time Schedule trigger that is configured to be monthly, it denotes the day of the month associated with the trigger.|
|  intTSMEveryMonths |Integer | For Time Schedule trigger that is configured to be monthly, it denotes the monthly rate of repetition associated with the trigger.|
|  intTSWEveryWeeks |Integer | For a Time Schedule trigger that is configured to be weekly, it denotes the weekly rate of repetition associated with the trigger.|
|  intTSYDayOfMonth |Integer | For a Time Schedule trigger that is configured to be yearly, it denotes the day of the month associated with the trigger.|
|  intTSYEveryYears |Integer |For a Time Schedule trigger that is configured to be yearly, it denotes the yearly rate of repetition associated with the trigger.|
|  intTSYMonthOfYear |Integer |For a Time Schedule trigger that is configured to be yearly, it denotes the month of the year associated with the trigger. Do note that the months start at 0. For eg: The year starts at January (0) and ends with December (11).|
|  strROType |String |For a Meter Reading trigger, this field is the Trigger Meter (When) Comparison. It is set to l (less than), g (greater than), or empty if not meter reading based.|
|  strRRType |String |It is the Trigger Schedule No End Date. It is set to empty if not time based, n (no end date), b (has a end date).|
|  strRType |String |For a Meter Reading trigger, this field is the Trigger Meter Type. It is set to e (every), o (other), empty if not meter reading based.|
|  strTRType |String |It is the Trigger Reading End type. It is set to n (no end reading), b (end by reading).|
|  strTSType |String |It is the Trigger Schedule Type. It is set to h (hourly), d (daily), w (weekly), m (monthly), y (yearly).|
|  strType |String |This field denotes the type of the Schedule Trigger. It is set to t for Time Schedule trigger, r for Meter Reading Trigger and e for an Event Trigger.|
|  strMrLogic |String |For a Meter Reading trigger, this field is used to determine the logic of the schedule. It is set x (fixed) or t (floating).|
|  bolMrByWOClosed |boolean |If set to true, the Meter Reading trigger should check the reading when the WO is closed.|
|  bolCreateWorkOrderOnStartDate |boolean |If set to true, it indicates that a WorkOrder be created on the start date when the trigger is scheduled.|
|  intAssetID |Integer |Indicates the ID for an Asset associated with the ScheduledMaintenance that creates the trigger. For a Meter Reading trigger, this field needs to be populated with the Asset id of one of the ScheduledMaintenance Assets.|
|  strScheduleDescription |String |The description for the Schedule Trigger.|
|  intTRTriggerTime |Integer |For all the Time Schedule triggers except an hourly trigger, this field specifies time at which it will be triggered. It can have a value between 0 and 23.|


** Success Response: **

**Code** : `200 success`

**Resonse example**

```json
{
   "msg": "Updated successfully!"
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
    "msg": "update failed"
}
```

# Delete ScheduleTrigger

Delete a ScheduleTrigger by Id

**URL** : `/api/scheduletrigger/:Id`

**Method** : `DELETE`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the ScheduleTrigger.

** Success Response: **

**Code** : `200 success`

**Resonse example**

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

