# Audio

Contains information on the audio clips produced by and associated with the Harvard Art Museums.

## Get Audio

`GET /audio` will get all audio clips.

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

> https://api.harvardartmuseums.org/audio   
> Returns all of the audio records

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 2,
        "totalrecords": 9,
        "pages": 5,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/audio?size=2&page=2",
        "responsetime": "3 ms"
    },
    "records": [
        {
            "duration": 0,
            "copyright": "President and Fellows of Harvard College",
            "audioid": 492585,
            "description": "Visual description by Marina Isgro, Nam June Paik Research Fellow, Division of Modern and Contemporary Art. Written August 2018.",
            "id": 492585,
            "lastupdate": "2020-08-01T05:31:10-0400",
            "transcripturl": "https://nrs.harvard.edu/urn-3:HUAM:AUD0170transcript",
            "fileid": 5030413,
            "primaryurl": "http://media.harvardartmuseums.org/audio/alice/total-totality-2.mp3"
        },
        {
            "duration": 0,
            "copyright": "President and Fellows of Harvard College",
            "audioid": 492595,
            "description": "Visual description by Seung Yeon Sang, Henderson Curatorial Fellow in East Asian Art, Division of Asian and Mediterranean Art. Written August 2018.",
            "id": 492595,
            "lastupdate": "2020-08-01T05:31:10-0400",
            "transcripturl": "https://nrs.harvard.edu/urn-3:HUAM:AUD0174transcript",
            "fileid": 5030436,
            "primaryurl": "http://media.harvardartmuseums.org/audio/alice/moon-flask.mp3"
        }
    ]
}
```

## Get Audio

`GET /audio/AUDIO_ID` will get the full record of the specified audio clip.

#### Examples

> https://api.harvardartmuseums.org/audio/492581    
> Returns the full record for audio 492581 which is an visual description of an artwork titled "Leander's Tower on the Bosporus"  

#### Response

```json
{
    "id": 492581,
    "audioid": 492581,
    "fileid": 5030408,
    "description": "Visual description by Jeff Steward, Director of Digital Infrastructure and Emerging Technology. Written April 2018. ",
    "copyright": "President and Fellows of Harvard College",
    "primaryurl": "http://media.harvardartmuseums.org/audio/alice/leanders-tower.mp3",
    "transcripturl": "https://nrs.harvard.edu/urn-3:HUAM:AUD0167transcript",
    "duration": 246,
    "lastupdate": "2020-08-01T05:31:10-0400"
}
```
