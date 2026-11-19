# Image

Contains information on the images produced by and associated with the Harvard Art Museums. 

## Get Images

`GET /image` will get all images.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY ***required*** |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/docs/reference/query-languages/query-dsl/query-dsl-query-string-query) for more options) |
| semantic | a natural language description of what you are looking for; see the [search section](https://github.com/harvardartmuseums/api-docs/blob/master/sections/search.md) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| aggregation |  see [Elasticsearch aggregations](https://www.elastic.co/docs/explore-analyze/query-filter/aggregations) |
| id | pipe separated list of record IDs |
| keyword | a keyword search string; searches image descriptions and captions |
| match | "all" or "any"; controls how many keyword terms must match; default is "all" |

#### Examples

> https://api.harvardartmuseums.org/image?q=width:>2000  
> Finds all images that are wider than 2000 pixels.  
>   
> https://api.harvardartmuseums.org/image?keyword=seated+figure  
> Finds images whose description or caption mentions a seated figure.  
>   
> https://api.harvardartmuseums.org/image?semantic=a+crowded+street+at+night  
> Finds images matching that description by meaning rather than by words.  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 2,
        "totalrecords": 5274,
        "pages": 1056,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/image?q=width%3A%3E2000&page=2&size=2",
        "responsetime": "5 ms"
    },
    "records": [
        {
            "id": 130722,
            "imageid": 130722,
            "fileid": 4880475,
            "caption": null,
            "alttext": null,
            "description": null,
            "copyright": "President and Fellows of Harvard College",
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
            "caption": null,
            "alttext": null,
            "description": null,
            "copyright": "President and Fellows of Harvard College",
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

**createdate** describes the date and time the record was created in the museum's electronic catalogue system   

**imageid** describes the numeric unique identifier for a record    

**fileid** describes the unique numeric identifier for a file  

**accesslevel** describes the accessibility of a record  
0 – Restricted. Image record is restricted to certain API keys  
1 – Public. Image record is available to all API keys  

**renditionnumber** describes the unique name for the image; this often takes the form of a prefix + serial number; the prefix can provide hints as to when, why, and how we made the image   

**date** describes either the date of creation of the image record in our collections management system OR the date of creation of the image itself (this is very fuzzy data)  

**baseimageurl** describes the primary internet address for the image delivered via a [IIIF image delivery service](https://github.com/harvardartmuseums/api-docs#iiif)  

**format** describes the [media type/MIME type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the image (typically image/jpeg)  

**alttext** describes the most relevant, prominent features or general characteristics of the image  
 
**description** describes the image content in detail  

**caption** describes the image, often listing more technical information about the view (recto, verso, profile, 3/4 view)  

**technique** describes the photography equipment and software used during the production of the image  

**colors** describes the colors programmatically extracted from the image  
An image may have zero or more colors. The color of each pixel is read and then sorted in to buckets. Brightness and gradient variants are reduced so similar colors group together, and to keep the number of buckets under 20. Then those colors are mapped to the [museums' color palette](https://github.com/harvardartmuseums/api-docs/blob/master/sections/spectrum.md), the CSS3 color listing, and hue names.  

`percent` - is the amount, between the range of 0 to 1, of the color found in the image  
`color` - is the color found in the image  
`spectrum` - is the closest match of the color value to the museums' design color [spectrum](https://github.com/harvardartmuseums/api-docs/blob/master/sections/spectrum.md)  
`css3` - is the closest match to the colors listed in the [CSS3 color module specification](https://www.w3.org/TR/css3-color/)  
`hue` - is the color value mapped to the name of a hue (Red, Orange, Yellow, Green, Blue, Violet, Brown, Grey, Black, White)  


#### Examples

> https://api.harvardartmuseums.org/image/465905  
> Returns the full record for image 465905 which depicts the object "Untitled [with Anna May Wong]”.  

#### Response

```json
{
    "id": 465905,
    "imageid": 465905,
    "fileid": 4997146,
    "caption": null,
    "alttext": null,
    "description": null,
    "copyright": "President and Fellows of Harvard College",
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

## Get similar images

`GET /image/IMAGE_ID/similar` will get images that resemble the specified image.

Three signals are returned, each as its own array. An image that lacks the source data for a signal returns an empty array for it.

| Signal | Description |
| :--------- | :----- |
| semantic | Images whose descriptions convey similar content |
| perceptual | Images that look alike, compared pixel to pixel |
| color | Images with a similar distribution of color |

Include one or more of the following parameters.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY ***required*** |
| size | 0-9+; the number of records returned per signal; default is 10, maximum is 1000 |
| fields | comma separated list of data fields you want in the output |

Each record carries a `_score` showing how strong the match is. Scores are comparable within a signal but not across signals. Note that this response has no `info` block and no `records` wrapper.

Use `perceptual` to find duplicate or near-duplicate photography of the same work, and `semantic` to find images of different works that depict similar things.

#### Examples

> https://api.harvardartmuseums.org/image/56/similar  
> Returns images similar to image 56.  
>   
> https://api.harvardartmuseums.org/image/56/similar?size=5&fields=imageid,baseimageurl  
> Returns five images per signal with only the image ID and base URL.  

#### Response

```json
{
    "semantic": [
        {
            "id": 56,
            "imageid": 56,
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:VRS10216",
            "alttext": null,
            "description": null,
            "caption": null,
            "width": 2550,
            "height": 1879,
            "format": "image/jpeg",
            "accesslevel": 1,
            "_score": 14.206
        }
    ],
    "perceptual": [],
    "color": []
}
```
