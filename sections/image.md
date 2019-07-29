# Image

Contains information on the images produced by and associated with the Harvard Art Museums. 

## Get Images

`GET /image` will get all images.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |

#### Examples

> https://api.harvardartmuseums.org/image?q=width:>2000  
> Finds all images that are wider than 2000 pixels.  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 2,
        "totalrecords": 5274,
        "pages": 1056,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/image?q=width%3A%3E2000&page=2&size=2"
    },
    "records": [
        {
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/400107495",
            "width": 2450,
            "caption": null,
            "fileid": 4968317,
            "copyright": "President and Fellows of Harvard College",
            "date": "2014-06-02",
            "imageid": 441757,
            "renditionnumber": "755709",
            "id": 441757,
            "lastupdate": "2017-12-15T04:37:38-0500",
            "accesslevel": 1,
            "height": 1912,
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:755709",
            "idsid": 400107495
        },
        {
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/400107499",
            "width": 2450,
            "caption": null,
            "fileid": 4968319,
            "copyright": "President and Fellows of Harvard College",
            "date": "2014-06-02",
            "imageid": 441758,
            "renditionnumber": "755710",
            "id": 441758,
            "lastupdate": "2017-12-15T04:37:38-0500",
            "accesslevel": 1,
            "height": 1945,
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:755710",
            "idsid": 400107499
        }
    ]
}
```

## Get Image

`GET /image/IMAGE_ID` will get the full record of the specified image.

A record represents the concept of an image. An image can be represented by one or more files that are accessible via one or more services.

**imageid** describes the numeric unique identifier for a record    

**idsid** describes the unique numeric identifier for a file in the Harvard Digital Repository  

**fileid** describes the unique numeric identifier for a file  

**renditionnumber** describes the unique name for the image; this often takes the form of a prefix + serial number; the prefix can provide hints as to when, why, and how we made the image   

**baseimageurl** describes the primary internet address for the image and is delivered through our [default image delivery service](https://github.com/harvardartmuseums/api-docs#default-service)  

**iiifbaseuri** describes the root of the address for accessing the image through our [IIIF image delivery service](https://github.com/harvardartmuseums/api-docs#iiif)  

**format** describes the [media type/MIME type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the image (typically image/jpeg)  


#### Examples

> https://api.harvardartmuseums.org/image/465905  
> Returns the full record for the image of the object "Untitled [with Anna May Wong]”.  

#### Response

```json
{
    "id": 465905,
    "imageid": 465905,
    "fileid": 4997146,
    "idsid": 423290977,
    "caption": null,
    "copyright": "President and Fellows of Harvard College",
    "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/423290977",
    "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:760994",
    "renditionnumber": "760994",
    "date": "2016-08-04",
    "height": 2550,
    "width": 1955,
    "accesslevel": 1,
    "lastupdate": "2017-12-15T04:38:46-0500"
}
```
