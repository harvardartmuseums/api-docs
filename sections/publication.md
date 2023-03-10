# Publication

Contains information on publications that have been written about or contain images of artworks in the Harvard Art Museums collection.

## Get publications

`GET /publication` will get all publications affiliated with the museums collections.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/query-dsl-query-string-query.html) for more options) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/7.17/search-aggregations.html#_structuring_aggregations) |
| hasimage | 0 or 1 |

#### Examples

> https://api.harvardartmuseums.org/publication?q=publicationyear:2013
> Returns all records for publications that were published in 2013. 

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 118,
        "pages": 12,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/publication?q=publicationyear%3A2013&size=10&page=2",
        "responsetime": "6 ms"
    },
    "records": [
        {
            "citation": "American Gropius: The Cambridge Years, <em>Architecture Boston</em> (Boston, MA, 2013), Vol. 16, No. 2",
            "primaryimageurl": null,
            "publicationplace": "Boston, MA",
            "format": "Article/Essay",
            "publicationdate": "2013",
            "shortdescription": null,
            "id": 20222,
            "objectcount": 4,
            "lastupdate": "2015-01-09T04:11:57-0500",
            "title": "American Gropius: The Cambridge Years",
            "description": null,
            "publicationyear": 2013,
            "volumenumber": "Vol. 16, No. 2",
            "publicationid": 20222,
            "volumetitle": "Architecture Boston"
        },
        {
            "citation": "Melissa Renn, \"Deep Seers: John Ruskin, Charles Herbert Moore and the Teaching of Art at Harvard\", <em>Persistent Ruskin: Studies in Influence, Assimilation and Effect</em>, ed. Keith Hanley and Brian Maidment, Ashgate Publishing, Ltd. (Surrey, England, 2013), pp. 137-155",
            "primaryimageurl": null,
            "publicationplace": "Surrey, England",
            "format": "Article/Essay",
            "publicationdate": "2013",
            "shortdescription": null,
            "people": [
                {
                    "personid": 9290,
                    "name": "Melissa Renn",
                    "role": "Author",
                    "displayorder": 1
                },
                {
                    "personid": 59165,
                    "name": "Keith Hanley",
                    "role": "Editor",
                    "displayorder": 2
                },
                {
                    "personid": 59166,
                    "name": "Brian Maidment",
                    "role": "Editor",
                    "displayorder": 3
                },
                {
                    "personid": 43162,
                    "name": "Ashgate Publishing, Ltd.",
                    "role": "Publisher",
                    "displayorder": 4
                }
            ],
            "id": 19908,
            "objectcount": 6,
            "lastupdate": "2015-01-09T04:11:53-0500",
            "title": "\"Deep Seers: John Ruskin, Charles Herbert Moore and the Teaching of Art at Harvard\"",
            "description": null,
            "publicationyear": 2013,
            "volumenumber": "pp. 137-155",
            "publicationid": 19908,
            "volumetitle": "Persistent Ruskin: Studies in Influence, Assimilation and Effect"
        }
    ]
}
```

## Get publication

`GET /publication/PUBLICATION_ID` will get detailed info about a specific publication.

The identifiers array contains numeric ID values that have special meaning and can help connect our records to other data sets. Not all records have these fields because we couldn't always find a match. 

**Hollis Number** is the identifier for the matching entry in the [HOLLIS](http://hollis.harvard.edu/) catalogue

**ISBN** is a commercial unique book identifier the can be used to match entries in sites like [Amazon](http://amazon.com) and [LibraryThing](https://www.librarything.com)

**Shopify Product ID** is the identifier for the matching entry in the [Harvard Art Museums' Shop](http://shop.harvardartmuseums.org/)

#### Examples

> https://api.harvardartmuseums.org/publication/19947  
> Returns the full record for the exhibition catalogue “Jasper Johns / In Press: The Crosshatch Works and the Logic of Print”.

#### Response

```json
{
    "publicationid": 19947,
    "format": "Exhibition Catalogue",
    "title": "Jasper Johns / In Press: The Crosshatch Works and the Logic of Print",
    "volumetitle": null,
    "volumenumber": null,
    "publicationplace": "Cambridge, MA",
    "publicationdate": "2012",
    "publicationyear": 2012,
    "citation": "Jennifer L. Roberts and Jennifer Quick, <em>Jasper Johns / In Press: The Crosshatch Works and the Logic of Print</em>, exh. cat., Harvard Art Museums (Cambridge, MA, 2012)",
    "description": "<P>Jennifer L. Roberts, with catalogue entries by Jennifer Quick<BR>ISBN 978-1-891771-60-6<BR>Available May 2012<BR>96 pages; 10 x 13 in.<BR>35 color illustrations<BR>Hardcover, $45.00<BR>Published by the Harvard Art Museums and Hatje Cantz Verlag</P>\r\n<P><STRONG>Winner, American Institute of Graphic Arts (AIGA) Best of New England (BoNE) 2013 Award</STRONG></P>\r\n<P>Centering on Jasper Johns’s signature “crosshatch” works in the Harvard Art Museums collections, this catalogue explores the impact of print on the artist’s oeuvre. It examines “print” and “the press” with reference not only to Johns’s experiments in printmaking, but also to print as a medium of information transfer, tracing his frequent use of newsprint, with its temporal, political, and formal implications. Complementing the selection of Johns’s production with works by Albrecht Dürer, Sol LeWitt, Pablo Picasso, and others, the volume examines the history and character of print as it informs Johns’s work in all media.</P>\r\n<P>This catalogue and the exhibition it accompanies grew out of a collaboration between the Art Museums and Harvard University’s Department of History of Art and Architecture. Four undergraduates enrolled in a class with professor Roberts devoted to the study of Johns’s diptych painting The Dutch Wives (1975), on long-term loan to the Art Museums from the artist’s collection. The students helped select other objects for the related exhibition at the Arthur M. Sackler Museum, and wrote interpretive essays for a companion digital publication.</P>\r\n<P>Jennifer L. Roberts is Professor of History of Art and Architecture, Harvard University. Jennifer Quick is a PhD candidate, Department of History of Art and Architecture, Harvard University, and Agnes Mongan Curatorial Intern, Harvard Art Museums.</P>",
    "shortdescription": "Jennifer L. Roberts, with catalogue entries by Jennifer Quick<BR>ISBN 978-1-891771-60-6<BR>Hardcover, $45.00",
    "primaryimageurl": null,
    "objectcount": 23,
    "id": 19947,
    "lastupdate": "2015-01-09T04:11:57-0500",
    "identifiers": [
        {
            "id": "013220264",
            "identifier": "Hollis Number"
        },
        {
            "id": "9781891771606",
            "identifier": "ISBN"
        },
        {
            "id": "1891771604",
            "identifier": "ISBN"
        },
        {
            "id": "9783775732918",
            "identifier": "ISBN"
        },
        {
            "id": "3775732918",
            "identifier": "ISBN"
        },
        {
            "id": "327413779",
            "identifier": "Shopify Product ID"
        }
    ],
    "people": [
        {
            "name": "Jennifer L. Roberts",
            "personid": 54877,
            "role": "Author",
            "displayorder": 1
        },
        {
            "name": "Jennifer Quick",
            "personid": 56528,
            "role": "Author",
            "displayorder": 2
        },
        {
            "name": "Harvard Art Museums",
            "personid": 55780,
            "role": "Publisher",
            "displayorder": 3
        }
    ]
}
```