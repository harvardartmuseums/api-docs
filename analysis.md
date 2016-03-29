# Analysis

The aggregation parameter provides a method for analyzing the museums data on our end so you have to do less work to use it on yours. You can ask for aggregations on every resource. The aggregration parameter accepts the structure and syntax of [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/1.4/search-aggregations.html#_structuring_aggregations). A typical example looks like this.

```json
aggregation={"by_division":{"terms":{"field":"division"}}}
```

Output from aggregations will appear as an additional block of data in the response. 

```json
"aggregations": {
    "by_division": {
        "buckets": [
            {
                "key": "Modern and Contemporary Art",
                "doc_count": 117564
            },
            {
                "key": "European and American Art",
                "doc_count": 73077
            },
            {
                "key": "Asian and Mediterranean Art",
                "doc_count": 61077
            }
        ]
    }
}
```

To see aggregations in action, take a look at the object activity graphs in the [Art Explorer](http://apps.harvardartmuseums.org/art-explorer/) demo application. The application fetches aggregation data from the [activity](https://github.com/harvardartmuseums/api-docs/blob/master/activity.md) endpoint. The data is fed in to [D3](https://d3js.org/) to produce the graphs.  

#### Tips and tricks

* Include the parameter `size=0` if you don't want records in your results set. The records block will return as an empty array.
* It's not always obvious which field to use when running an aggregation. For example the classification field on the object endpoint is indexed both as `classification` and `classification.exact`. We are adding field definitions for each endpoint but it will take some time for us to cover everything. In the meantime, don't hesitate to [ask us](https://docs.google.com/forms/d/118WjSPgKEYBjLU3B3iUkELwHbgeWryVb_5hw3o6_3K8/viewform) for clarification on fields.
* It is possible to ask for multiple aggregations in a single request.
* It is possible to subdivide an aggregation.

#### Examples

Here are a few basic examples.  

> http://api.harvardartmuseums.org/object?aggregation={"by_division":{"terms":{"field":"division"}}}  
> Tell me how many objects are in each curatorial division.  

> http://api.harvardartmuseums.org/object?&aggregation={"by_classification":{"terms":{"field":"classification.exact","size":0},"aggs":{"by_century":{"terms":{"field":"century"}}}}}  
> Tell me how many objects are in each classification and then subdivide each classification by century.

Here is a more advanced example. This request fetches data from the activity endpoint for a specific object. The data is first grouped by activity type. Then for each activity type the data is tallied for each month/year. The aggregation parameter is expanded to make it more readable.

```json
http://api.harvardartmuseums.org/activity?object=299843&aggregation={
    "by_activitytype": {
        "terms": {
            "field": "activitytype"
        },
        "aggs": {
            "by_yearmonth": {
                "date_histogram": {
                    "field": "date",
                    "interval": "month",
                    "format": "yyy-MM"
                },
                "aggs": {
                    "totals": {
                        "sum": {
                            "field": "activitycount"
                        }
                    }
                }
            }
        }
    }
}
```