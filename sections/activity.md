# Activity

Contains information on activities specific to objects in the Harvard Art Museums collections.

## Get Activities

`GET /activity` will get all activities.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY ***required*** |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/query-dsl-query-string-query.html) for more options) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/7.17/search-aggregations.html#_structuring_aggregations) |
| id | pipe separated list of record IDs |
| object | OBJECT ID |
| type | "edits", "pageviews", "uniquepageviews", "moves", "conservation", "studycenterviews" |

Several types of activities are available via this endpoint. They are described in the `activitytype` field. 

**Edits** refers to the number of times the descriptive data for an object has changed on a given day. This gives you no indication of what specifically has changed. 

**Pageviews** refers to the number of times an object was visited on the [museum's public website](http://www.harvardartmuseums.org) on a given day.

**Unique Pageviews** refers to the number of unique times an object was visited on the [museum's public website](http://www.harvardartmuseums.org) on a given day. This number is equal to or lower than pageviews.

**Conservation** refers to the number of times an object had a conservation report written about on a given day.

**Moves** refers to the number of times an object was physically moved on a given day. A move could be from one storage to location to another storage location. It could be storage to a gallery and so on.

**Study Center Views** refers to the number of times an object was viewed in the [Art Study Center](http://www.harvardartmuseums.org/teaching-and-research/art-study-center) on a given day.

#### Examples

> https://api.harvardartmuseums.org/activity?object=6772  
> Returns all of the activity for the [Marianne Brandt’s "Untitled [with Anna May Wong]"](www.harvardartmuseums.org/collections/object/6772).  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 5,
        "totalrecords": 2387,
        "pages": 478,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/activity?object=6772&size=5&page=2",
        "responsetime": "4 ms"
    },
    "records": [
        {
            "id": 1263375660,
            "objectid": 6772,
            "date": "2023-03-02",
            "activitytype": "pageviews",
            "activitycount": 3,
            "lastupdate": "2023-03-09T14:41:31-0500"
        },
        {
            "id": 105307199,
            "objectid": 6772,
            "date": "2023-03-06",
            "activitytype": "uniquepageviews",
            "activitycount": 2,
            "lastupdate": "2023-03-09T14:41:35-0500"
        },
        {
            "id": 105306334,
            "objectid": 6772,
            "date": "2023-03-02",
            "activitytype": "uniquepageviews",
            "activitycount": 3,
            "lastupdate": "2023-03-09T14:42:03-0500"
        },
        {
            "id": 1263374795,
            "objectid": 6772,
            "date": "2023-03-06",
            "activitytype": "pageviews",
            "activitycount": 2,
            "lastupdate": "2023-03-09T14:42:14-0500"
        },
        {
            "id": 1483504890,
            "objectid": 6772,
            "date": "2022-12-13",
            "activitytype": "pageviews",
            "activitycount": 1,
            "lastupdate": "2022-12-14T12:16:04-0500"
        }
    ]
}
```

## Get Activity

`GET /activity/ACTIVITY_ID` will get the full record of the specified activity.

#### Examples

> https://api.harvardartmuseums.org/activity/1483504890    
> Returns the full record for activity with the ID number 1483504890.

#### Response

```json
    {
        "id": 1483504890,
        "objectid": 6772,
        "date": "2022-12-13",
        "activitytype": "pageviews",
        "activitycount": 1,
        "lastupdate": "2022-12-14T12:16:04-0500"
    }
```
