# Annotation

Contains information on the annotations in the Harvard Art Museums collections.

Each annotation indicates an area of interest in an image in our dataset. An area can be a small portion of an image or it can be the entire image. Small regions typically contain a persons face or words. Annotations on the full image are typically tags (e.g. cat, watermelon, rock) and descriptions (e.g. a cow standing in a field).

Annotations come from a number of different sources. Some of the annotations are created by humans. Most of the data is a result of machine processing our images with external services. We use the following services.

- [Amazon Nova](https://aws.amazon.com/ai/generative-ai/nova/)
- [Amazon Rekognition](https://aws.amazon.com/rekognition/)
- [Anthropic Claude on AWS Bedrock](https://aws.amazon.com/bedrock/claude/)
- [Azure OpenAI Service](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
- [Clarifai](https://clarifai.com/)
- [Google Gemini](https://cloud.google.com/ai/gemini/)
- [Google Vision](https://cloud.google.com/vision/)
- [Imagga](https://imagga.com/)
- [Meta Llama on AWS Bedrock](https://aws.amazon.com/bedrock/llama/)
- [Microsoft Cognitive Services](https://www.microsoft.com/cognitive-services)

We use the services to perform face detection, text detection, tagging, categorization, and captioning. We do not use custom training sets with these services. We feed in our images and data as-is. We then process, store, and serve whatever comes out.  

Note: We are paying customers of these services. We do not have partnerships with these services, nor do we endorse any one particular service. All of the services are black boxes so we use them and provide the data, in part, to call attention to the differences and biases inherent in AI services.  

## Get Annotations

`GET /annotation` will get all annotations.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY ***required*** |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/query-dsl-query-string-query.html) for more options) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/7.17/search-aggregations.html#_structuring_aggregations) |
| id | pipe separated list of record IDs |
| image | [IMAGE ID](image.md)  |

#### Examples

> https://api.harvardartmuseums.org/annotation  
> Returns all of the annotations.

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 2,
        "totalrecords": 6274466,
        "pages": 3137233,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/annotation?size=2&page=2",
        "responsetime": "10 ms"
    },
    "records": [
        {
            "raw": {
                "id": "ai_4Qjv5PTH",
                "name": "modern",
                "value": 0.88892984,
                "app_id": "main"
            },
            "body": "modern",
            "createdate": "2018-03-22T21:30:54-04:00",
            "fileid": 359384,
            "confidence": 0.88893,
            "type": "tag",
            "imageid": 371197,
            "id": 1798459,
            "lastupdate": "2018-10-30T14:33:18-0400",
            "annotationid": 1798459,
            "source": "Clarifai",
            "selectors": [
                {
                    "value": "xywh=0,0,1024,916",
                    "type": "FragmentSelector"
                }
            ],
            "target": "https://ids.lib.harvard.edu/ids/iiif/15865142/full/full/0/native.jpg",
            "feature": "full",
            "idsid": 15865142
        },
        {
            "raw": {
                "annotationFragment": "xywh=171,458,33,29",
                "description": "A",
                "boundingPoly": {
                    "vertices": [
                        {
                            "y": 458,
                            "x": 171
                        },
                        {
                            "y": 458,
                            "x": 199
                        },
                        {
                            "y": 482,
                            "x": 199
                        },
                        {
                            "y": 482,
                            "x": 171
                        }
                    ]
                },
                "iiifTextImageURL": "https://ids.lib.harvard.edu/ids/iiif/5021442/171,458,33,29/full/0/native.jpg"
            },
            "body": "A",
            "createdate": "2018-06-27T22:53:39-04:00",
            "fileid": 155102,
            "confidence": -1,
            "type": "text",
            "imageid": 188184,
            "id": 333467,
            "lastupdate": "2018-10-30T13:24:40-0400",
            "annotationid": 333467,
            "source": "Google Vision",
            "selectors": [
                {
                    "value": "xywh=171,458,33,29",
                    "type": "FragmentSelector"
                }
            ],
            "target": "https://ids.lib.harvard.edu/ids/iiif/5021442/full/full/0/native.jpg",
            "feature": "region",
            "idsid": 5021442
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

**source** describes how the annotation was generated. These are the possible values.   
- Amazon - means the annotation was generated using machine processing  
- Anthropic - means the annotation was generated using machine processing  
- AWS Rekognition - means the annotation was generated using machine processing
- Azure OpenAI Service - means the annotation was generated using machine processing  
- Clarifai - means the annotation was generated using machine processing   
- Google Gemini - means the annotation was generated using machine processing  
- Google Vision - means the annotation was generated using machine processing  
- Imagga - means the annotation was generated using machine processing  
- Manual - means the annotation was generated by a human
- Meta - means the annotation was generated using machine processing  
- Microsoft Cognitive Services - means the annotation was generated using machine processing   

**model** describes the model used for machine generated annotations  

**feature** describes the size of the annotation in relation to the image it is on. These are the possible values.  
- region - the annotation describes a portion of the image    
- full - the annotation describes the entire image  

**type** describes generally what the annotation contains. These are the possible values.   
- face - a face is found within the annotation  
- text - some text is found within the annotation  
- category - a broad categorization of the contents of the image  
- description - a full sentence caption of the contents of the image   
- tag - a term or set of terms   

**confidence** describes the services degree of confidence in its thinking. Values range from 0 (no confidence) to 1 (very confident). A value of -1 means confidence is unknown or was not provided by the service for the annotation.  

**raw** describes the unparsed version of the annotation directly from the source  

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
    "source": "Google Vision",
    "feature": "region",
    "confidence": -1,
    "type": "text",
    "raw": {
        "description": "Düsseldorf",
        "boundingPoly": {
            "vertices": [
                {
                    "y": 641,
                    "x": 341
                },
                {
                    "y": 640,
                    "x": 425
                },
                {
                    "y": 662,
                    "x": 425
                },
                {
                    "y": 663,
                    "x": 341
                }
            ]
        }
    },
    "createdate": "2018-02-09T17:10:56-05:00",
    "id": 9329,
    "selectors": [
        {
            "type": "FragmentSelector",
            "value": "xywh=1068,2005,268,77"
        }
    ],
    "lastupdate": "2018-10-30T13:09:18-0400"
}
```
