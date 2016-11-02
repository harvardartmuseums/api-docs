# Experimental

USE AT YOUR OWN RISK

We don't guarantee the stability of this data. That being said, there is some fun stuff to play with here. This endpoint does not cover all object records. The data is a result of machine processing data and images through external services including [Google Vision](https://cloud.google.com/vision/), [Imagga](https://imagga.com/), and [Clarifai](https://clarifai.com/). The services perform face detection, text detection, and automatic feature detection/tagging of images.

## Get experimental objects

`GET /experimental/object` will get all experimental data for objects.

#### Examples

> http://api.harvardartmuseums.org/experimental/object?q=googlevision.responses.faceAnnotations.joyLikelihood:VERY_LIKELY
> Returns all records for object that were processed with Google Vision and contain a person's face expressing joy. 

#### Response

```json
```

## Get experimental object

`GET /experimental/object/OBJECT_ID` will get the full experimental record of the specified object.

#### Examples

> http://api.harvardartmuseums.org/experimental/object/155597 
> Returns the full record for the object with ID 155597.

#### Response

```json
```