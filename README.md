# Harvard Art Museums API Documentation

The Harvard Art Museums API is a REST-style service designed for developers who wish to explore and integrate the museums’ collections in their projects. The API provides direct access to the data that powers the [museums' website](https://www.harvardartmuseums.org) and many other aspects of the museums. 

## Access to the API

All requests to the API begin with: 

```shell
https://api.harvardartmuseums.org
```

And all requests must also specify the [resource](https://github.com/harvardartmuseums/api-docs#resources-that-are-available) you want to retrieve:

```shell
https://api.harvardartmuseums.org/RESOURCE_TYPE
```

And every request must be accompanied by the `apikey` parameter and an API key. The API uses keys to authenticate requests. API keys take the form `00000000-0000-0000-0000-000000000000`. Here is the full structure of a typical request:

```shell
https://api.harvardartmuseums.org/RESOURCE_TYPE?apikey=YOUR_API_KEY
```

[Send a request](https://docs.google.com/forms/d/1Fe1H4nOhFkrLpaeBpLAnSrIMYvcAxnYWm0IU9a6IkFA/viewform) to obtain your key.

## Responses and data format

All data is in [JSON](http://json.org) format. Here is a typical response:

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 224111,
        "pages": 22412,
        "page": 1,
        "next": "",
        "prev": "",
        "responsetime": "5 ms"
    },
    "records": [

    ],
    "aggregations": {

    }
}
```

## Paging through data

Requests that return large numbers of records will be spread across multiple pages. By default, a request returns 10 records per page. You can increase this number (up to 100) by adding the `size` parameter to a request. For example add `&size=100` to get 100 records per page. To move through a large record set, add the `page` parameter and set it some value greater than 1 (i.e. `&page=2`).

```shell
https://api.harvardartmuseums.org/object?size=5&page=42
```

The `next` and `prev` fields in the info block provide a handy shortcut for paging forward and backward through records. They will contain a fully formed URL to the next and previous pages of records. Send a new request to the value in the `next` field to move forward. Check for the existance of the `next` and `prev` fields to determine if you are at the beginning or end of your results.

## Errors

Requests that contain a bad, invalid, or missing API key will return a `401 Unauthorized` error. Remember every request requires the `apikey` parameter with a valid key. See the very top of this document for [more information about keys](https://github.com/harvardartmuseums/api-docs#access-to-the-api). Requests for resources other than those listed in the [resources section below](https://github.com/harvardartmuseums/api-docs#resources-that-are-available) will return a `404 Not Found` error.  

## Images

Some of the datasets include image URLs as part of a block of image information in each record. Our images are served to you by an image server that supports a number of interfaces including [IIIF](http://iiif.io). 

#### Default service

The default service is accessed through the URLs found in the fields `baseimageurl` and `primaryimageurl`. This service is capable of resizing images on the fly. Append `height` and `width` parameters to image URLs to get an image sized to fit to the supplied dimensions. For example, if you want an image scaled to 150 pixels on the longest side construct the URL as follows.

```shell
https://nrs.harvard.edu/urn-3:HUAM:OCP16703_dynmc?height=150&width=150
```

#### IIIF 

Some of the museums' data is accessible through [IIIF](http://iiif.io) image and presentation services.   

The **IIIF image service** is accessed through the data found in the field `iiifbaseuri`. Read more about the capabilities of the IIIF Image API at http://iiif.io/api/image/2.1/. The service we provide adheres to version 2.1 of the API. A typical base URI for an image looks like this:  

```shell
https://ids.lib.harvard.edu/ids/iiif/18483392
```

A fully formed IIIF request for a full resolution JPEG version of that same image looks like this:

```shell
https://ids.lib.harvard.edu/ids/iiif/18483392/full/full/0/default.jpg
```

Please note that URLs for images of objects that have rights restrictions are excluded for most API users. This means images for many 20th and 21st century works of art will not be available to you at the present time. We are working on a solution to this.  

The **IIIF presentation service** is accessed through a separate service. Read more about the capabilities of the IIIF Presentation API at http://iiif.io/api/presentation/2.1/. 

The top level collection is at:

```
https://iiif.harvardartmuseums.org/collections/top
```

The base URL for all presentation manifests begins with:

```
https://iiif.harvardartmuseums.org/manifests
```

You can request a manifest for any object by appending `/object/OBJECT_ID` to the base URL. For example the primary manifest for the object [Self-Portrait Dedicated to Paul Gauguin](https://www.harvardartmuseums.org/collections/object/299843) is at:

```
https://iiif.harvardartmuseums.org/manifests/object/299843
```

At the present a manifest for an object contains one sequence and each image of that object is contained in its own canvas within that sequence.  

Please note that our IIIF presentation service is very much a work in progress. The code for the server is available at https://github.com/harvardartmuseums/iiif-manifest-server and is based on work that was done at HarvardX. If you have any comments, suggestions, or questions about this service feel free to submit them through the feedback links listed below.  

More technical documentation and use cases are described in the [IIIF section](https://github.com/harvardartmuseums/api-docs/blob/master/sections/iiif.md).

## Analysis

Slice and dice the data any way you like at our expense with the `aggregation` parameter. You can ask for aggregations on every resource. They are the best way to gather statistics and analyze the data. The aggregration parameter accepts the structure and syntax of [Elasticsearch aggregations](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/search-aggregations.html#_structuring_aggregations). Output from aggregations will appear as an additional block of data in the response. Learn more about analyizing the data via examples in the [analysis section](https://github.com/harvardartmuseums/api-docs/blob/master/sections/analysis.md) of the API documentation.

## Resources that are available

Several primary museum resources are accessible in this API. They include the following:

* [Object](https://github.com/harvardartmuseums/api-docs/blob/master/sections/object.md)
* [Person](https://github.com/harvardartmuseums/api-docs/blob/master/sections/person.md)
* [Exhibition](https://github.com/harvardartmuseums/api-docs/blob/master/sections/exhibition.md)
* [Publication](https://github.com/harvardartmuseums/api-docs/blob/master/sections/publication.md)
* [Gallery](https://github.com/harvardartmuseums/api-docs/blob/master/sections/gallery.md)
* [Spectrum](https://github.com/harvardartmuseums/api-docs/blob/master/sections/spectrum.md)
* [Classification](https://github.com/harvardartmuseums/api-docs/blob/master/sections/classification.md)
* [Century](https://github.com/harvardartmuseums/api-docs/blob/master/sections/century.md)
* [Color](https://github.com/harvardartmuseums/api-docs/blob/master/sections/color.md)
* [Culture](https://github.com/harvardartmuseums/api-docs/blob/master/sections/culture.md)
* [Group](https://github.com/harvardartmuseums/api-docs/blob/master/sections/group.md)
* [Medium](https://github.com/harvardartmuseums/api-docs/blob/master/sections/medium.md)
* [Support](https://github.com/harvardartmuseums/api-docs/blob/master/sections/support.md)
* [Period](https://github.com/harvardartmuseums/api-docs/blob/master/sections/period.md)
* [Place](https://github.com/harvardartmuseums/api-docs/blob/master/sections/place.md)
* [Technique](https://github.com/harvardartmuseums/api-docs/blob/master/sections/technique.md)
* [Worktype](https://github.com/harvardartmuseums/api-docs/blob/master/sections/worktype.md)
* [Activity](https://github.com/harvardartmuseums/api-docs/blob/master/sections/activity.md)
* [Site](https://github.com/harvardartmuseums/api-docs/blob/master/sections/site.md)
* [Video](https://github.com/harvardartmuseums/api-docs/blob/master/sections/video.md)
* [Image](https://github.com/harvardartmuseums/api-docs/blob/master/sections/image.md)
* [Audio](https://github.com/harvardartmuseums/api-docs/blob/master/sections/audio.md)
* [Annotation](https://github.com/harvardartmuseums/api-docs/blob/master/sections/annotation.md)

## Experimental data

There is a small amount of experimental data available at this endpoint.

* [Experimental](https://github.com/harvardartmuseums/api-docs/blob/master/sections/experimental.md)

## Learning the API

### Introduction to APIs

New to APIs? New to museum data? New to coding? Try out our [beginners guide to APIs and museum data](https://hvrd.art/api-toolkit). 

### Example projects

You can do a lot with the API. Here are a few examples. 

> [Art Explorer](http://apps.harvardartmuseums.org/art-explorer/)  
> A different approach to browsing through the collections.  
>  
> [Suns Explorer](https://hvrd.art/suns)  
> A simple abstract use of the color information supplied with some of the object records.  
> 
> [Art Forest](https://hvrd.art/art-forest)  
> A simple "game" that is part classic text adventure, point-and-click adventure, and walking simulator.
>   
> [Spectrum Explorer](https://hvrd.art/spectrum-explorer)  
> See color spectrum that is part of the branding of the Harvard Art Museums.  
>  
> [Museum Explorer](https://hvrd.art/museum-explorer)  
> See the entire museum through tree and pack graphs and floor plans.  
>  
> [AI Explorer](https://ai.harvardartmuseums.org)  
> Search and browse the collection via machine generated tags and descriptions.  
>  
> [ARTphone](https://github.com/harvardartmuseums/ARTphone)  
> Call or text the word "random" to 1-617-500-1866 to listen to the collection.  
>  
> [Magnetic Poetry, Magic Message, Face Match, etc](https://hvrd.art/iiif)  
> Playful projects that show the possibilities with computer vision and IIIF.  

### Example code snippets

You can talk with the API using almost any language or tool that speaks HTTP. Here are a few snippets to get you started. Just make sure to substitute your own API key in the `apikey` parameter before running them.

#### cURL

Find all of the objects in the collection.

```shell
curl -XGET https://api.harvardartmuseums.org/object?apikey=[YOUR APIKEY HERE]
```

#### Javascript + jQuery

```javascript
// Find all of the objects that are paintings and have the word "rabbit" in the title
var apiEndpointBaseURL = "https://api.harvardartmuseums.org/object";
var queryString = $.param({
    apikey: "YOUR APIKEY HERE",
    title: "rabbit",
    classification: "Paintings"
});

$.getJSON(apiEndpointBaseURL + "?" + queryString, function(data) {
   console.log(data); 
});
```

#### Node.js

```javascript
var rest = require("restler");

// Find all of the objects with the word "dog" in the title and return only a few fields per record
rest.get("https://api.harvardartmuseums.org/object", {
    query: {
        apikey: "YOUR APIKEY HERE",
        title: "dog",
        fields: "objectnumber,title,dated",
    }
}).on("complete", function(data, response) {
    console.log(data);
});
```

#### PHP 

```php
use GuzzleHttp\Client;

$client = new Client();
// Find all of the objects with the word "squirrel" in the title and return only a few fields per record
$response = $client->get("https://api.harvardartmuseums.org/object", 
    [
        "query" => [
            "apikey" => "YOUR APIKEY HERE",
            "title" => "squirrel",
            "fields" => "objectnumber,title,dated"
        ]
    ]
);
$records = json_decode($response->getBody());
print_r($records);
```

#### Python 3

```python
import urllib3

http = urllib3.PoolManager()

# Find all of the objects with the word "cat" in the title and return only a few fields per record
r = http.request('GET', 'https://api.harvardartmuseums.org/object',
    fields = {
        'apikey': 'YOUR APIKEY HERE',
        'title': 'cat',
        'fields': 'objectnumber,title,dated'
    })

print(r.status, r.data)
```

## Feedback

Have you tried the API? [Let us know what you think.](https://docs.google.com/forms/d/118WjSPgKEYBjLU3B3iUkELwHbgeWryVb_5hw3o6_3K8/viewform)  

If you have a specific feature request or find a bug, [please open a GitHub issue](https://github.com/harvardartmuseums/api-docs/issues/new).

## About the API

#### Background information

There are many reasons why the API is important to us and why it exists. They can be summed up as this: Data is at the heart of the work we do and we need an efficient and stable system for tapping in to it. 

A more expansive list of reasons why we have an API goes like this:

- **We want our lives to be easier.** Historically it has been difficult to extract raw data from proprietary collections management systems because of the complexity of database structures and the tools required to extract it. Our API is designed with simplicity in mind. It is designed so that we can use the language of the web (HTML and Javascript) to communicate and interact with the museums' data. We strive to make every bit of data addressable through concise, persistent URLs that are not dependent on a particular language or tool.

- **We want to rapidly prototype and share ideas.** Since the API is designed for the web first, we can bring concepts to life quickly and make them accessible to anyone with a web browser almost instantly.

- **An API allows us to be more fluid.** The design takes in to consideration that we'll need to add data fields, remove data fields, or change the source of data.

- **The API makes the collections accessible to other disciplines.** Some people respond best to visual information as presented through our website. Other people, like computer scientists, might respond best to raw data as presented through the API. 

- **Having more eyes on our data is good.** API users will use our data in ways we never dreamed. They'll be looking at the data from different perspectives. They will see ways in which we can improve the shape of our data and possibly aid us in the creation of new data, and ultimately new knowledge.

- **The API elevates our records to first class citizens on the internet.** The API gives every object, person, exhibition, museum room, publication, etc a permanent, reliable address on the web. It means we can start to pivot away from an object centric view of the museum.

- **The API encourages experimentation.** Imaginative uses of the API will yield alternative approaches to teaching with the museums' collections and the creation of alternative forms of interpretation.

Several articles have been published on our magazine about how access to data (through APIs) changes the way we think about and use collections. See [Technology in the Museums](https://harvardartmuseums.org/article/technology-in-the-museums) and [The Beauty—and Complexity—of Data](https://harvardartmuseums.org/article/the-beauty-of-data) to dive a bit deeper.

#### Technical specs

The two core pieces of software behind the API are [Node.js](https://nodejs.org/en/) and [Elasticsearch](http://www.elastic.co). The API is a Node.js application running on [Heroku](https://www.heroku.com/). It talks to an Elasticsearch instance running on [Elasitc Cloud](https://www.elastic.co/cloud/).

#### The data

The bulk of the data derives from our internal collections management systems. Our primary system is The Museum System (TMS) by [Gallery Systems](http://www.gallerysystems.com/). We enhance the data in TMS by using third party services to aggregate statistics and run machine processing. These services include Google Analytics, Google Vision, Amazon Rekognition, Microsoft Cognitive Services, Clarifai, and Imagga.  

We refresh the dataset every day around 6am.  

Keep in mind that the data is not perfect. There are many gaps and a lot of ambiguity. The data is a direct manifestation of the knowledge produced by staff and affiliates of the museums. The majority of the data is produced by humans, thus subject to errors, opinion, and fuzziness. Consider it a living document and work in progress. Check back often.   

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
  
<br/>
<br/>

----

<br/>

## Coda

Congratulations! You made it to the end. Over the years the museums' design team made stickers for us to give away as a means to spread joy and promote the API. Please enjoy this sampler. 

![A collage of nine hexagons each containing a part of an image from the museum's collection](https://user-images.githubusercontent.com/3187493/80253872-1a959780-8648-11ea-826c-fc2a8b6cc082.png)
