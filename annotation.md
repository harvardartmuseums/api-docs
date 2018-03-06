# Annotation

Contains information on the annotations in the Harvard Art Museums collections.

An annotation indicates a region of interest in an image in our dataset. We annotate two types of regions. One, a region that contains a persons face. Two, a region that contains words. 

Annotations come from a number of different sources. Some of the annotations are created by humans. Some of the data is a result of machine processing images through two external services: [Google Vision](https://cloud.google.com/vision/) and [Microsoft Cognitive Services](https://www.microsoft.com/cognitive-services). We are using the services to perform face detection and text detection. We have not created training sets for these services. We are feeding in our images and data as-is to see what comes out.  

## Get Annotations

`GET /annotation` will get all annotations.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| usedby | FIELD NAME:ID |

#### Examples

> https://api.harvardartmuseums.org/annotation  
> Returns all of the annotations. 

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 2,
        "totalrecords": 63196,
        "pages": 31598,
        "page": 1
    },
    "records": [
        {
            "id": 9174,
            "body": "<p>surprise: VERY_UNLIKELY<br/>anger: VERY_UNLIKELY<br/>sorrow: VERY_UNLIKELY<br/>joy: VERY_UNLIKELY<br/>headwear: VERY_UNLIKELY<br/>blurred: VERY_UNLIKELY</p>",
            "lastupdate": "2018-02-17T15:12:47-0500",
            "annotationid": 9174,
            "selectors": [
                {
                    "value": "xywh=2003,221,234,271",
                    "type": "FragmentSelector"
                }
            ],
            "target": "https://ids.lib.harvard.edu/ids/iiif/435166560/full/full/0/native.jpg",
            "idsid": 435166560,
            "fileid": 5014334,
            "imageid": 480833
        },
        {
            "id": 9329,
            "body": "Düsseldorf",
            "lastupdate": "2018-02-20T10:18:13-0500",
            "annotationid": 9329,
            "selectors": [
                {
                    "value": "xywh=1068,2005,268,77",
                    "type": "FragmentSelector"
                }
            ],
            "target": "https://ids.lib.harvard.edu/ids/iiif/400098359/full/full/0/native.jpg",
            "idsid": 400098359,
            "fileid": 4967858,
            "imageid": 441393
        }
    ]
}
```

## Get annotation

`GET /annotation/ANNOTATION_ID` will get the full record of the specified annotation.

**annotationid** describes the numeric unique identifier for a record  

**imageid** describes the numeric identifier for the image on which the annotation occurs   

**body** describes the actual annotation  

**selectors** describes the region of the image where the annotation occurs  
Selectors take many forms. By default all of our selectors will conform to the Media Fragment Specification as documented in the [W3C's Web Annotation Data Model](https://www.w3.org/TR/annotation-model/#fragment-selector).  

#### Examples

> https://api.harvardartmuseums.org/annotation/9329   
> Returns the full record for the annotation with the ID number 9329.  

#### Response

```json
{
    "imageid": 441393,
    "annotationid": 9329,
    "fileid": 4967858,
    "idsid": 400098359,
    "target": "https://ids.lib.harvard.edu/ids/iiif/400098359/full/full/0/native.jpg",
    "body": "Düsseldorf",
    "id": 9329,
    "selectors": [
        {
            "type": "FragmentSelector",
            "value": "xywh=1068,2005,268,77"
        }
    ],
    "lastupdate": "2018-02-20T10:18:13-0500"
}
```