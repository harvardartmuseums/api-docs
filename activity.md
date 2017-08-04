# Activity

Contains information on activities specific to objects in the Harvard Art Museums collections.

## Get Activities

`GET /activity` will get all activities.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/1.4/search-aggregations.html#_structuring_aggregations) |
| object | OBJECT ID |
| type | "edits", "pageviews", "uniquepageviews", "moves", "conservation", "studycenterviews" |

Several types of activites are available via this endpoint. They are described in the `activitytype` field. 

**Edits** refers to the number of times the descriptive data for an object has changed on a given day. This gives you no indication of what specifically has changed. 

**Pageviews** refers to the number of times an object was visited on the [museum's public website](http://www.harvardartmuseums.org) on a given day.

**Unique Pageviews** refers to the number of unique times an object was visited on the [museum's public website](http://www.harvardartmuseums.org) on a given day. This number is equal to or lower than pageviews.

**Conservation** refers to the number of times an object had a conservation report written about on a given day.

**Moves** refers to the number of times an object was physically moved on a given day. A move could be from one storage to location to another storage location. It could be storage to a gallery and so on.

**Study Center Views** refers to the number of times an object was viewed in the [Art Study Center](http://www.harvardartmuseums.org/teaching-and-research/art-study-center) on a given day.

#### Examples

> https://api.harvardartmuseums.org/activity?object=299843  
> Returns all of the activity for the [Van Gogh's Self-Portrait](www.harvardartmuseums.org/collections/object/299843).  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 3424,
        "pages": 343,
        "page": 1
    },
    "records": [
        {
            "date": "2009-05-16",
            "objectid": 299843,
            "activitytype": "pageviews",
            "activitycount": 2
        },
        {
            "date": "2009-06-06",
            "objectid": 299843,
            "activitytype": "pageviews",
            "activitycount": 1
        },
        {
            "date": "2009-06-22",
            "objectid": 299843,
            "activitytype": "pageviews",
            "activitycount": 2
        },
        {
            "date": "2009-07-05",
            "objectid": 299843,
            "activitytype": "pageviews",
            "activitycount": 4
        }
    ]
}
```