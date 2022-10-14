# Person

Contains information on entities that have some association to works of art in the collection or publications. Associations include artists, sitters, printers, donors, authors, publishers, and more.

## Get people

`GET /person` will get all people affiliated with the museums.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/query-dsl-query-string-query.html) for more options) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/7.17/search-aggregations.html#_structuring_aggregations) |

#### Examples

> https://api.harvardartmuseums.org/person?q=culture:Dutch  
> Finds all of the people that are Dutch.    

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 600,
        "pages": 60,
        "page": 1
    },
    "records": [
        {
            "dateend": 0,
            "alphasort": "Kaap, Gérald Van Der",
            "displaydate": "born 1959",
            "deathplace": null,
            "objectcount": 1,
            "id": 18135,
            "lastupdate": "2015-01-09T04:07:45-0500",
            "datebegin": 1959,
            "birthplace": "Enschede, Netherlands",
            "personid": 18135,
            "gender": "male",
            "culture": "Dutch",
            "displayname": "Gérald Van Der Kaap",
            "url": "http://www.harvardartmuseums.org/collections/person/18135"
        },
        {
            "dateend": 1633,
            "alphasort": "Vinckboons, David",
            "displaydate": "1576 - 1632-1633",
            "deathplace": "Amsterdam",
            "objectcount": 9,
            "id": 18301,
            "lastupdate": "2015-01-09T04:07:45-0500",
            "datebegin": 1576,
            "birthplace": "Mechelen",
            "personid": 18301,
            "gender": null,
            "culture": "Dutch",
            "displayname": "David Vinckboons",
            "url": "http://www.harvardartmuseums.org/collections/person/18301"
        }
    ]
}
```

## Get person

`GET /person/PERSON_ID` will get detailed info about a specific person.

**alphasort** describes the form of the persons name useful for sorting names alphabetically  
This often takes the form of "lastname, firstname" and is our preferred way to sort names.  

**displayname** describes the form of the persons name used for display purposes  
This often takes the form of "firstname lastname" and is our preferred way to display names.  

Some fields contain numeric values that have special meaning and can help connect our records to other data sets. Not all records have these fields because we couldn't always find a match. 

**names** describes the variant names or the person
A person may have one or more names.

`displayname` - is the displayable variant name    
`type` - is the type of variant name, such as 'Original Language Name' or 'Alternate Name'  

**lcnaf_id** contains the identifier for the matching entry in [LCNAF](https://id.loc.gov/authorities/names)

**ulan_id** contains the identifier for the matching entry in the [ULAN](http://www.getty.edu/research/tools/vocabularies/ulan/) vocabulary

**viaf_id** contains the identifier for the matching entry in [VIAF](https://viaf.org/)

**wikidata_id** contains the identifier for the matching entry in [Wikidata](https://www.wikidata.org/)

**wikipedia_id** contains the identifier for the matching entry in [Wikipedia](http://www.wikipedia.org/)

#### Examples

> https://api.harvardartmuseums.org/person/29481  
> Returns the full record for Utagawa Yoshikazu.

#### Response

```json
{
    "personid": 29481,
    "displayname": "Utagawa Yoshikazu",
    "datebegin": 1850,
    "dateend": 1870,
    "displaydate": "active 1850 - 1870",
    "culture": "Japanese",
    "gender": "male",
    "birthplace": null,
    "deathplace": null,
    "alphasort": "Utagawa, Yoshikazu",
    "url": "https://www.harvardartmuseums.org/collections/person/29481",
    "objectcount": 50,
    "id": 29481,
    "lastupdate": "2021-04-24T04:10:32-0400",
    "ulan_id": "500334458",
    "viaf_id": "252063172",
    "wikidata_id": "Q11545174",
    "names": [
        {
            "displayname": "一川芳員",
            "type": "Original Language Name"
        },
        {
            "displayname": "Utagawa Yoshikazu",
            "type": "Primary Name"
        }
    ]
}
```