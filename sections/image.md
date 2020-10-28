# Image

Contains information on the images produced by and associated with the Harvard Art Museums. 

## Get Images

`GET /image` will get all images.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/5.6/query-dsl-query-string-query.html) for more options) |
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
            "id": 130722,
            "imageid": 130722,
            "fileid": 4880475,
            "idsid": 43183146,
            "caption": null,
            "alttext": null,
            "description": null,
            "copyright": "President and Fellows of Harvard College",
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/43183146",
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:48875_dynmc",
            "renditionnumber": "48875",
            "date": "1995-05-01",
            "height": 2550,
            "width": 2154,
            "accesslevel": 1,
            "format": "image/jpeg",
            "technique": "Kodak Ektapan",
            "lastupdate": "2020-07-17T06:22:49-0400"
        },
        {
            "id": 441758,
            "imageid": 441758,
            "fileid": 4968319,
            "idsid": 400107499,
            "caption": null,
            "alttext": null,
            "description": null,
            "copyright": "President and Fellows of Harvard College",
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/400107499",
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:755710",
            "renditionnumber": "755710",
            "date": "2014-06-02",
            "height": 1945,
            "width": 2450,
            "accesslevel": 1,
            "format": "image/jpeg",
            "technique": "Make:Sinar Photography AG;Model:Sinar CMV/ Sinarback eVolution 75H;Orientation:1;Software:Adobe Photoshop CS5 Macintosh;",
            "lastupdate": "2020-07-17T06:30:22-0400"
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

**date** describes either the date of creation of the image record in our collections management system OR the date of creation of the image itself (this is very fuzzy data)  

**baseimageurl** describes the primary internet address for the image and is delivered through our [default image delivery service](https://github.com/harvardartmuseums/api-docs#default-service)  

**iiifbaseuri** describes the root of the address for accessing the image through our [IIIF image delivery service](https://github.com/harvardartmuseums/api-docs#iiif)  

**format** describes the [media type/MIME type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the image (typically image/jpeg)  

**alttext** describes the most relevant, prominent features or general characteristics of the image  
 
**description** describes the image content in detail  

**caption** describes the image, often listing more technical information about the view (recto, verso, profile, 3/4 view)  

**technique** describes the photography equipment and software used during the production of the image  


#### Examples

> https://api.harvardartmuseums.org/image/465905  
> Returns the full record for image 465905 which depicts the object "Untitled [with Anna May Wong]”.  

#### Response

```json
{
    "id": 465905,
    "imageid": 465905,
    "fileid": 4997146,
    "idsid": 423290977,
    "caption": null,
    "alttext": null,
    "description": null,
    "copyright": "President and Fellows of Harvard College",
    "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/423290977",
    "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:760994",
    "renditionnumber": "760994",
    "date": "2016-08-04",
    "height": 2550,
    "width": 1955,
    "accesslevel": 1,
    "format": "image/jpeg",
    "technique": "Make:Hasselblad;Model:Hasselblad H5D-50c MS;Orientation:1;Software:Adobe Photoshop CS6 (Macintosh);",
    "lastupdate": "2020-07-17T06:30:34-0400"
  }
```
