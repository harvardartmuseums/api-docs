# Harvard Art Museums API Documentation

The Harvard Art Museums API is a REST-style service designed for developers who wish to explore and integrate the museums’ collections in their projects. The API provides direct access to [JSON](http://json.org) formatted data that powers the [museums' website](http://www.harvardartmuseums.org) and many other aspects of the museums. 

## Access to the API

All requests to the API begin with: 

```shell
http://api.harvardartmuseums.org
```

The API uses keys to authenticate requests. Every request must be accompanied by the `apikey` parameter and an API key. 

```shell
http://api.harvardartmuseums.org?apikey=00000000-0000-0000-0000-000000000000
```

[Send a request](https://docs.google.com/forms/d/1Fe1H4nOhFkrLpaeBpLAnSrIMYvcAxnYWm0IU9a6IkFA/viewform) to obtain your key.

## Responses and data format

All data comes out in [JSON](http://json.org) format. Here is a typical response:

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 224111,
        "pages": 22412,
        "page": 1
    },
    "records": [

    ],
    "facets": [

    ]
}
```

## Paging through data

By default, requests return 10 records at a time. You can increase the number of records per page up to a maximum of 100 by setting the `size` parameter. Use the `page` parameter to page through large record sets.

```shell
http://api.harvardartmuseums.org/object?size=5&page=42
```

## Images

Some of the datasets include URLs to images in JPEG format. Our images are served to you by an image delivery service that is capable of resizing images on the fly. Append `height` and `width` parameters to image URLs to get an image sized to fit to the supplied dimensions. For example, if you want an image scaled to 150 pixels on the longest side construct the URL as follows.

```shell
http://nrs.harvard.edu/urn-3:HUAM:OCP16703_dynmc?height=150&width=150
```

Please note that URLs for images of objects that have rights restrictions are excluded for most API users. This means images for many 20th and 21st century works of art will not be available to you at the present time. We are working on a solution to this.

## Resources that are available

Several primary museum resources are accessible in this API. They include the following:

* [Object](https://github.com/harvardartmuseums/api-docs/blob/master/object.md)
* [Person](https://github.com/harvardartmuseums/api-docs/blob/master/person.md)
* [Exhibition](https://github.com/harvardartmuseums/api-docs/blob/master/exhibition.md)
* [Publication](https://github.com/harvardartmuseums/api-docs/blob/master/publication.md)
* [Gallery](https://github.com/harvardartmuseums/api-docs/blob/master/gallery.md)
* [Spectrum](https://github.com/harvardartmuseums/api-docs/blob/master/spectrum.md)
* [Classification](https://github.com/harvardartmuseums/api-docs/blob/master/classification.md)
* [Century](https://github.com/harvardartmuseums/api-docs/blob/master/century.md)
* Color
* [Culture](https://github.com/harvardartmuseums/api-docs/blob/master/culture.md)
* Group
* Medium
* [Period](https://github.com/harvardartmuseums/api-docs/blob/master/period.md)
* Place
* [Technique](https://github.com/harvardartmuseums/api-docs/blob/master/technique.md)
* [Worktype](https://github.com/harvardartmuseums/api-docs/blob/master/worktype.md)

## Example projects

You can do a lot with the API. Here are few examples. 

> [Art Explorer](http://apps.harvardartmuseums.org/art-explorer/)  
> A different approach to browsing through the collections.  
>  
> [Suns Explorer](http://apps.harvardartmuseums.org/suns-explorer/)  
> A simple abstract use of the color information supplied with some of the object records.  
>   
> [Spectrum Explorer](http://apps.harvardartmuseums.org/spectrum-explorer)  
> The color spectrum that is part of the branding of the Harvard Art Museums.

## Feedback

Have you tried the API? [Let us know what you think.](https://docs.google.com/forms/d/118WjSPgKEYBjLU3B3iUkELwHbgeWryVb_5hw3o6_3K8/viewform)

## Terms of use
- If you make a request to this service you are deemed to have accepted the terms and conditions listed here.

- You may not use the Harvard Art Museums logo on your website without the specific written permission of Harvard Art Museums.

- You may not use the Harvard Art Museums name or any derivative phrases (such as "ham", "harvard", "harvardmuseum" or "harvardartmuseums") in the hostname of your website or application.

- Harvard Art Museums is constantly updating the data provided by the API. You will not cache or store any content returned by the Harvard Art Museums API for more than two weeks unless specific written permission has been given by the museums.

- If you display images in your website or application you must use the image URL returned by our API rather than create a copy on your local web server.

- We reserve the right to turn off or modify the API service at any time.

- We reserve the right to block or cancel your access to the API service without prior notice.

- We require at all times free access to and a description of any applications that include Harvard Art Museums content via the API.

- The API is for non-commercial use only.

- All Harvard Art Museums API content that is located on your website must include a link back to the location of the content on the Harvard Art Museums website.

- You must identify all Harvard Art Museums content on your website as originating from the Harvard Art Museums.

- You must not use the API or Harvard Art Museums content in any context that is obscene, indecent, pornographic, illegal or defamatory of any nature, or otherwise inappropriate.

- The Harvard Art Museums reserves the right to extend or alter these terms and conditions at any time.

- Respect other users of the API by limiting the number of API calls to 2500 per day.

- Respect the works of art.