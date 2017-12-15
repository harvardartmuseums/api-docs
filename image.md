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

> [[COMING SOON]]  
>  

#### Response

```json
{
}
```

## Get Image

`GET /image/IMAGE_ID` will get the full record of the specified image.

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
