# Spectrum

Contains a list of the colors used in the color spectrum that is part of the branding of the Harvard Art Museums. Read more about the spectrum at http://magazine.harvardartmuseums.org/article/2013/10/01/index-color-spectrum.  

## Get spectrum

`GET /spectrum` will get the museums’ color spectrum.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |

#### Examples

> https://api.harvardartmuseums.org/spectrum?q=month:1&sort=daynumber  
> Returns the colors assigned to the month of January.

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 31,
        "pages": 4,
        "page": 1
    },
    "records": [
        {
            "id": 1,
            "color": "#009bdf",
            "month": 1,
            "day": 1,
            "daynumber": 1
        },
        {
            "id": 2,
            "color": "#009ade",
            "month": 1,
            "day": 2,
            "daynumber": 2
        }
    ]
}
```

## Get spectrum color by day

`GET /spectrum/DAY_NUMBER` will get the color associated with a particular day.

#### Examples

> https://api.harvardartmuseums.org/spectrum/50  
> Returns the hex value of the color associated with day 50.

#### Response

```json
{
    "month": 2,
    "day": 19,
    "color": "#0089ae",
    "id": 50,
    "daynumber": 50
}
```