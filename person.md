# Person

Contains information on entities that have some association to works of art in the collection.

## Get people

`GET /person` will get all people affiliated with the museums.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| facet | FIELD NAME or comma separated list of fields |

#### Examples

> EX 1  
> EX 2

#### Response

```json
{}
```

## Get person

`GET /person/PERSON_ID` will get detailed info about a specific person.

#### Examples

> http://api.harvardartmuseums.org/person/28241  
> Returns the full record for Rembrandt.

#### Response

```json
{
	"alphasort": "",
	"alternatenames": "",
	"birthplace": "", 
	"personid": ,
	"culture": "",
	"gender": "",
	"deathplace": "",
	"displaydate": "",
	"datebegin": "",
	"dateend": "",
	"displayname": "",
	"id": ,
	"lastupdate": "",
	"objectcount": ,
	"ulan_id": "",
	"viaf_id": "",
	"wikipedia_id": ""
}
```