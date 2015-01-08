# Harvard Art Museums API Documentation

The Harvard Art Museums API is a REST-style service designed for developers who wish to explore and integrate the museums’ collections in their projects. The API provides direct access to [JSON](http://json.org) formatted data that powers the [museums' website](http://www.harvardartmuseums.org) and many other aspects of the museums. 

## Access to the API

All requests to the API begin with: 

```shell
http://api.harvardartmuseums.org
```

The API uses keys to authenticate requests. Every request must be accompanied by the `apikey` parameter and an API key. [Send a request](https://docs.google.com/forms/d/1Fe1H4nOhFkrLpaeBpLAnSrIMYvcAxnYWm0IU9a6IkFA/viewform) to obtain your key.

## Resources that are available

Several primary museum resources are accessible in this API. They include the following:

* [Object](https://github.com/harvardartmuseums/api-docs/blob/master/object.md)
* Person
* Exhibition
* Publication
* Gallery

## Feedback

Have you tried the API? [Let us know what you think.](https://docs.google.com/forms/d/118WjSPgKEYBjLU3B3iUkELwHbgeWryVb_5hw3o6_3K8/viewform)

## Terms of use
If you make a request to this service you are deemed to have accepted the terms and conditions listed here.

You may not use the Harvard Art Museums logo on your website without the specific written permission of Harvard Art Museums.

You may not use the Harvard Art Museums name or any derivative phrases (such as "ham", "harvard", "harvardmuseum" or "harvardartmuseums") in the hostname of your website or application.

Harvard Art Museums is constantly updating the data provided by the API. You will not cache or store any content returned by the Harvard Art Museums API for more than two weeks unless specific written permission has been given by the museums.

If you display images in your website or application you must use the image URL returned by our API rather than create a copy on your local web server.

We reserve the right to turn off or modify the API service at any time.

We reserve the right to block or cancel your access to the API service without prior notice.

We require at all times free access to and a description of any applications that include Harvard Art Museums content via the API.

The API is for non-commercial use only.

All Harvard Art Museums API content that is located on your website must include a link back to the location of the content on the Harvard Art Museums website.

You must identify all Harvard Art Museums content on your website as originating from the Harvard Art Museums.

You must not use the API or Harvard Art Museums content in any context that is obscene, indecent, pornographic, illegal or defamatory of any nature, or otherwise inappropriate.

The Harvard Art Museums reserves the right to extend or alter these terms and conditions at any time.

Respect other users of the API by limiting the number of API calls to 2500 per day.

Respect the works of art.
