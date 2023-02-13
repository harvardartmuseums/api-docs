# Experimental

USE AT YOUR OWN RISK

We don't guarantee the stability of this data. That being said, there is some fun stuff to play with here. This endpoint does not cover all object records. The data is a result of machine processing data and images through external services including [Google Vision](https://cloud.google.com/vision/), [Microsoft Cognitive Services](https://www.microsoft.com/cognitive-services), [Imagga](https://imagga.com/), and [Clarifai](https://clarifai.com/). We are using the services to perform face detection, text detection, color analysis, and automatic feature detection/tagging of images. We have not created training sets for these services. We are feeding in our images and data as-is to see what comes out.  

## Get experimental objects

`GET /experimental/object` will get all experimental data for objects.

#### Examples

> https://api.harvardartmuseums.org/experimental/object?q=images.googlevision.responses.faceAnnotations.joyLikelihood:VERY_LIKELY  
> Returns all records for object that were processed with Google Vision and contain a person's face expressing joy.  

#### Response

```json
[SAMPLE RESPONSE GOES HERE]
```

## Get experimental object

`GET /experimental/object/OBJECT_ID` will get the full experimental record of the specified object.

#### Examples

> https://api.harvardartmuseums.org/experimental/object/155597  
> Returns the full record for the object with ID 155597.  

#### Response

```json
[SAMPLE RESPONSE GOES HERE]
```

## Example projects

> [Machine Tag Explorer](http://apps.harvardartmuseums.org/machine-tag-explorer/)  
> A simple rendering of the data produced by machine processing photographs.    
