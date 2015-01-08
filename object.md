# Object

Contains detailed information on the items in the Harvard Art Museums collections.

## Get objects

`GET /object` will get all objects.


Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| q | FIELD:VALUE |
| size | 0-9+ |
| page | 0-9+ |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| hasimage | 0 or 1 |
| century | CENTURY or pipe separated list of centuries or "any" |
| classification | CLASSIFICATION or pipe separated list of classifications or "any" |
| color | COLOR or pipe separated list of colors or "any" |
| culture | CULTURE or pipe separated list of cultures or "any" |
| exhibition | EXHIBITION ID or "any" |
| gallery | GALLERY NUMBER or pipe separated list of gallery numbers or "any" |
| group | GROUP NAME or "any" |
| keyword | 1 or more terms |
| medium | MEDIUM or pipe separated list of mediums or "any" |
| objectnumber | 1 or more terms |
| period | PERIOD or pipe separated list of periods or "any" |
| person | PERSON ID or PERSON NAME or "any" |
| place | PLACE or pipe separated list of places or "any" |
| relatedto | OBJECT ID |
| technique | TECHNIQUE or pipe separated list of techniques or "any" |
| title | 1 or more terms |
| exact_title | EXACT URL ENCODED TITLE |
| worktype | WORKTYPE or pipe separated list of worktypes or "any" |
| facet | FIELD NAME or comma separated list of fields |
| apikey | YOUR API KEY required |


## Get object

`GET /object/OBJECT_ID` will get the full record of the specified object.

Some fields contain numeric values that have special meaning.

imagepermissionlevel describes the level of image copyright permissions for a record
0 – ok to display images at any size
1 – images have restrictions; display at a maximum pixel dimension of 256px
2 – do not display any images

verificationlevel describes the completeness and vetting status of information in a record
0 - Unchecked. Object information has not been verified for completeness and has not been vetted
1 - Poor. Object information is likely incomplete and has not been vetted
2 - Adequate. Object is adequately described but information may not be vetted
3 - Good. Object is well described and information is vetted
4 - Best. Object is extensively researched, well described and information is vetted

accesslevel describes the accessibility of a record
0 – Restricted. Object record is restricted to certain API keys
1 – Public. Object record is available to all API keys

#### Examples

http://api.harvardartmuseums.org/object/299843
Returns the full record for van Gogh’s "Self-Portrait Dedicated to Paul Gauguin".

#### Response

```json
{
	"id": 123456,
	"objectid": "",
	"accesslevel": 1,
	"accessionyear": 2014,
	"century": "",
	"classification": "",
	"colorcount": 0,
	"colors": [
	{
		"color": "",
		"hue": "",
		"percent": "",
		"css3": "",
		"spectrum": ""
	}],
	"commentary": "",
	"contact": "",
	"contextualtext": [
	{
		"context": "",
		"date": "",
		"text": "",
		"type": ""
	}],
	"contextualtextcount": 0,
	"copyright": "",
	"creditline": "",
	"culture": "",
	"datebegin": "",
	"dated": "",
	"dateend": "",
	"dateoffirstpageview": "",
	"dateoflastpageview": "",
	"department": "",
	"description": "",
	"details": [
		"coins": {
			"dateonobject": "",
			"denomination": "",
			"dieaxis": "",
			"metal": "",
			"obverseinscription": "",
			"reverseinscription": ""
		},
		"technical": [
		{
			"type": "",
			"text": ""
		}]
	],
	"dimensions": "",
	"division": "",
	"edition": "",
	"exhibitioncount": 0,
	"exhibitions": [
	{
		"begindate": "",
		"enddate": "",
		"exhibitionid": "",
		"title": "",
		"citation": ""
	}],
	"gallery": { 
		"gallerynumber": 0,
		"name": "",
		"floor": ""
	},
	"groupcount": 0,
	"groupings": [
	{
		"groupid": "",
		"name": ""
	}],
	"imagecount": 0,
	"imagepermissionlevel": 0,
	"images": [
	{
		"baseimageurl": "",
		"copyright": "",
		"displayorder": "",
		"publiccaption": "",
		"renditionnumber": ""
	}],
	"lastupdate": "",
	"marks": [
	{
		"text": "",
		"type": ""
	}],
	"markscount": 0,
	"media": [
	{
		"filetype": "",
		"fileurl": "",
		"publiccaption": "",
		"renditionnumber": ""
	}],
	"mediacount": 0,
	"medium": "",
	"objectnumber": "",
	"people": [
	{
		"birthplace": "",
		"personid": "",
		"culture": "",
		"deathplace": "",
		"displaydate": "",
		"displayname": "",
		"displayorder": "",
		"name": "",
		"prefix": "",
		"role": ""
	}],
	"peoplecount": 0,
	"period": "",
	"places": [
	{
		"displayname": "",
		"placeid": "",
		"type": ""
	}],
	"primaryimageurl": "",
	"provenance": "",
	"publicationcount": 0,
	"publications": [
	{
		"citation": "",
		"citationremarks": "",
		"format": "",
		"pagenumbers": "",
		"publicationdate": "",
		"publicationid": "",
		"publicationplace": "",
		"publicationyear": "",
		"title": "",
		"volumetitle": "",
		"volumenumber": ""
	}],
	"rank": 12345,
	"related": [
	{
		"accesslevel": "",
		"objectid": "",
		"relationship": ""
	}],
	"relatedcount": 0,
	"signed": "",
	"state": "",
	"standardreferencenumber": "",
	"style": "",
	"tags": [
	{
		"tag": ""
	}],
	"technique": "",
	"terms": [
		"century": [
		{
			"id": "",
			"name": ""
		}],
		"medium": [
		{
			"id": "",
			"name": ""
		}],
		"place": [
		{
			"id": "",
			"name": ""
		}]
	]
	"title": "",
	"titles": [
	{
		"displayorder": "",
		"title": "",
		"titleid": "",
		"titletype": ""
	}],
	"titlescount": 0,
	"totalpageviews": "",
	"totaluniquepageviews": "",
	"url": "",
	"verificationlevel": "",
	"worktypes": [
	{
		"worktype": ""
	}]
}
```

## Get object subsection

`GET /object/OBJECT_ID/SECTION` will get a section of detailed info about the specified object.

#### Examples 

http://api.harvardartmuseums.org/object/299843/publications
Returns an array containing all the publications related to van Gogh’s "Self-Portrait Dedicated to Paul Gauguin".
