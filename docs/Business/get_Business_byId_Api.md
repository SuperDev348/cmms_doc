# Get Single Business By Id Api

Get a single Business by id if current Business was registered on it.

**URL** : `/api/business/:Id`

**Method** : `GET`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

**URL Parameters** :  An integer that uniquely identifies the business.

## Success Response

**Code** : `200 success`

**Resonse example**


```json
{
    "msg": "Found!",
    "data": 
        {
            "_id": "6",
            "strProvince":"String",
            "strPostalCode":"String",
            "strTimezone":"String",
            "strPrimaryEmail":"String",
            "strName":"String",
            "strPhone":"String",
            "strFax":"String",
            "intCountryID":"Integer",
            "strAddress":"String",
            "strPrimaryContact":"String",
            "strNotes":"String",
            "strPhone2":"String",
            "strCode":"String",
            "strCity":"String",
            "strSecondaryEmail":"String"
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

**Condition** : If Business does not exist on server.

**Code** : `404 Not Found`

**Content example**

```json
{
   "msg": "Not found", 
   "data":null
}
```