# Video

Contains information on the videos produced by and associated with the Harvard Art Museums.

## Get Videos

`GET /video` will get all videos.

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

#### Examples

> https://api.harvardartmuseums.org/video/
> Returns all of the video records

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 2,
        "totalrecords": 43,
        "pages": 22,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/video?size=2&page=2",
        "responsetime": "5 ms"
    },
    "records": [
        {
            "copyright": "President and Fellows of Harvard College",
            "description": "Installation of Recent Acquisitions, Part III: Kerry James Marshall",
            "videoid": 417000,
            "id": 417000,
            "lastupdate": "2020-08-01T05:31:09-0400",
            "fileid": 4919212,
            "primaryurl": "https://vimeo.com/52099684"
        },
        {
            "copyright": "President and Fellows of Harvard College",
            "description": "Re-creation of a Medieval Ceramic Sweetmeat Dish from Iran",
            "videoid": 427454,
            "id": 427454,
            "lastupdate": "2020-08-01T05:31:09-0400",
            "fileid": 4948387,
            "primaryurl": "https://vimeo.com/58571319"
        }
    ]
}
```

## Get Video

`GET /video/VIDEO_ID` will get the full record of the specified video.

#### Examples

> https://api.harvardartmuseums.org/video/451379    
> Returns the full record for video 451379 which is a time-lapse of the construction of the Museumss

#### Response

```json
{
    "id": 451379,
    "videoid": 451379,
    "fileid": 4979919,
    "description": "Harvard Art Museums Construction Time-Lapse",
    "copyright": "President and Fellows of Harvard College",
    "primaryurl": "https://vimeo.com/111057446",
    "lastupdate": "2020-08-01T05:31:09-0400"
}
```
