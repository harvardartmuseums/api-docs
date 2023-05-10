# Object

Contains detailed information on the items in the Harvard Art Museums collections.

## Get objects

`GET /object` will get all objects.

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
| hasimage | 0 or 1 |
| century | CENTURY ID or pipe separated list of CENTURY IDs or CENTURY NAME or pipe separated list of CENTURY NAMES or "any"  |
| classification | CLASSIFICATION ID or pipe separated list of CLASSIFICATION IDs or CLASSIFICATION NAME or pipe separated list of CLASSIFICATION NAMES or "any" |
| color | URL encoded COLOR or pipe separated list of URL encoded colors or "any" |
| culture | CULTURE ID or pipe separated list of CULTURE IDs or CULTURE NAME or pipe separated list of CULTURE NAMES or "any" |
| exhibition | EXHIBITION ID or "any" or "none" |
| gallery | GALLERY NUMBER or pipe separated list of gallery numbers or "any" or "none" |
| group | GROUP ID or pipe separated list of GROUP IDs or GROUP NAME or "any" |
| keyword | a keyword search string; this parameter searches object titles, artists, description, classification, culture, worktype, medium terms, provenance, and creditline |
| medium | MEDIUM ID or pipe separated list of MEDIUM IDs or MEDIUM NAME or pipe separated list of MEDIUM NAMES or "any" |
| objectnumber | 1 or more terms |
| period | PERIOD or pipe separated list of periods or "any" |
| person | PERSON ID or pipe separated list of PERSON IDs or PERSON NAME or "any" |
| place | PLACE ID or pipe separated list of PLACE IDs or PLACE NAME or "any" |
| publication | PUBLICATION ID or "any" or "none" |
| relatedto | OBJECT ID |
| support | SUPPORT ID or pipe separated list of SUPPORT IDs or SUPPORT NAME or pipe separated list of SUPPORT NAMES or "any" |
| technique | TECHNIQUE ID or pipe separated list of TECHNIQUE IDs or TECHNIQUE NAME or pipe separated list of TECHNIQUE NAMES or "any" |
| title | 1 or more terms |
| exact_title | EXACT URL ENCODED TITLE |
| worktype | WORKTYPE ID or pipe separated list of WORKTYPE IDs or WORKTYPE NAME or pipe separated list of WORKTYPE NAMES or "any" |
| yearmade | four digit year |


#### Examples

> https://api.harvardartmuseums.org/object?q=totalpageviews:0&size=10  
> Returns ten objects that have never been viewed on the Art Museums main public website.  
>  
> https://api.harvardartmuseums.org/object?person=33430  
> Finds all of the objects that involve a specific person.  
>   
> https://api.harvardartmuseums.org/object?classification=Prints&q=totalpageviews:1  
> Finds all of the objects classified as prints that have been viewed only once on the Art Museums main public website.

#### Response

To keep responses reasonably sized, the output from a get objects request contains a subset of fields. To get all of the data fields for a given record, use a get object request.

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 261018,
        "pages": 26102,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/object?size=10&page=2",
        "responsetime": "6 ms"
    },
    "records": [
        {
            "accessionyear": "1969",
            "technique": null,
            "mediacount": 0,
            "edition": null,
            "totalpageviews": 98,
            "groupcount": 0,
            "people": [
                {
                    "birthplace": null,
                    "name": "Unknown Artist",
                    "prefix": null,
                    "personid": 23184,
                    "role": "Artist",
                    "displayorder": 1,
                    "culture": null,
                    "displaydate": null,
                    "deathplace": null,
                    "displayname": "Unknown Artist"
                }
            ],
            "objectnumber": "1969.172",
            "colorcount": 10,
            "lastupdate": "2015-01-07T04:21:10-0500",
            "rank": 86736,
            "imagecount": 2,
            "description": null,
            "dateoflastpageview": "2014-11-14",
            "dateoffirstpageview": "2009-05-12",
            "primaryimageurl": "http://nrs.harvard.edu/urn-3:HUAM:72721_dynmc"
        },
        {
            "accessionyear": null,
            "technique": "Engraving",
            "mediacount": 0,
            "edition": null,
            "totalpageviews": 98,
            "groupcount": 0,
            "people": [
                {
                    "birthplace": null,
                    "name": "Ignatius Cornelis Marinus",
                    "prefix": null,
                    "personid": 32489,
                    "role": "Artist",
                    "displayorder": 1,
                    "culture": "Flemish",
                    "displaydate": "1599 - 1639",
                    "deathplace": null,
                    "displayname": "Ignatius Cornelis Marinus"
                },
                {
                    "birthplace": "Siegen, Westphalia",
                    "name": "Peter Paul Rubens",
                    "prefix": "After",
                    "personid": 28402,
                    "role": "Artist after",
                    "displayorder": 2,
                    "culture": "Flemish",
                    "displaydate": "1577 - 1640",
                    "deathplace": "Antwerp, Belgium",
                    "displayname": "After Peter Paul Rubens"
                }
            ],
            "objectnumber": "R5196",
            "colorcount": 0,
            "lastupdate": "2015-01-07T04:21:30-0500",
            "rank": 235396,
            "imagecount": 1,
            "description": null,
            "dateoflastpageview": "2014-12-05",
            "dateoffirstpageview": "2009-06-19",
            "primaryimageurl": "http://nrs.harvard.edu/urn-3:HUAM:INV202403_dynmc",
            "dated": "17th century",
            "contextualtextcount": 0,
            "copyright": null,
            "period": null,
            "url": "http://harvardartmuseums.org/collections/object/240724",
            "provenance": "John Witt Randall, bequest to his sister. Belinda Lull Randall, gift to Harvard University, 1892. sister of John Witt Randall ",
            "publicationcount": 0
        }
    ]
}
```

## Get object

`GET /object/OBJECT_ID` will get the full record of the specified object.

In many cases the fields are pretty self-explanatory but in other cases they are a bit fuzzy. Sometimes you need to know the history of the institution and some of its inner workings in order to understand some of the data. This is because our data is often based on our particular cataloguing preferences and not necessarily universally accepted cataloguing standards for cultural objects. Here is a partial list of those fields with explanations.  

**accessionmethod** describes how the work came to be part of the collection  
The list of methods includes Gift, Purchase, Transfer, Bequest, and Commission. This information, along with additional details, is also found in an object's provenance and credit line.  

**accessionyear** describes the year the object was acquired  
In some cases it represents the year the object officially became part of the museums collection. In other cases it reflects the year Harvard acquired it. Many objects have accession years that predate the existence of the Fogg Museum (1895), the first museum of the three museums that are part of Harvard Art Museums, and thus can be thought of as being acquired by Harvard itself.  

**accesslevel** describes the accessibility of a record  
0 – Restricted. Object record is restricted to certain API keys  
1 – Public. Object record is available to all API keys  

**colors** describes the colors programmatically extracted from the primary image of the object  
An object may have zero or more colors. The color of each pixel is read and then sorted in to buckets. Brightness and gradient variants are reduced so similar colors group together, and to keep the number of buckets under 20. Then those colors are mapped to the [museums' color palette](https://github.com/harvardartmuseums/api-docs/blob/master/sections/spectrum.md), the CSS3 color listing, and hue names.  

`percent` - is the amount, between the range of 0 to 1, of the color found in the image  
`color` - is the color found in the image  
`spectrum` - is the closest match of the color value to the museums' design color [spectrum](https://github.com/harvardartmuseums/api-docs/blob/master/sections/spectrum.md)  
`css3` - is the closest match to the colors listed in the [CSS3 color module specification](https://www.w3.org/TR/css3-color/)  
`hue` - is the color value mapped to the name of a hue (Red, Orange, Yellow, Green, Blue, Violet, Brown, Grey, Black, White)  

**copyright** describes the copyright of the object  

**dated** describes the time frame in which the object was created  
This field contains a free text expression of the object’s date of creation. It is most often used for display purposes. We use BC and BCE ([Common Era notation](https://en.wikipedia.org/wiki/Common_Era)) to qualify dates.  

**datebegin** describes the year in which the creation of the object began  
This field is used to record the earliest year expressed in the dated field. Most often it is used for searching. The value is always a four digit integer. 

**dateend** describes the year in which the creation of the object ended  
This field is used to record the latest year expressed in the dated field. Most often it is used for searching. The value is always a four digit integer. 

**imagepermissionlevel** describes the level of image copyright permissions for a record  
0 – ok to display images at any size  
1 – images have restrictions; display at a maximum pixel dimension of 256px  
2 – do not display any images

**images** describes the images of the object  
An object may have zero or more images. As of March 2016, 91% of our objects have at least one image.  

`alttext` - is a short description of the most relevant, prominent features or general characteristics of the image  
`baseimageurl` - is the primary internet address for the image and is delivered through our [default image delivery service](https://github.com/harvardartmuseums/api-docs#default-service)  
`copyright` - is the copyright for the image  
`description` - is a long description of the contents of the image    
`displayorder` - is the preferred sequence number for the image within a group of images in the context of the object record; sequencing is especially important for manuscripts and books; an image with displayorder = 1 can be thought of as the current canonical image for the object  
`format` - is the [media type/MIME type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the image (typically image/jpeg)  
`height` - is the height of the image in pixels  
`idsid` - is the unique numeric identifier for the image in the Harvard Digital Repository    
`iiifbaseuri` - is the root of the address for accessing the image through our [IIIF image delivery service](https://github.com/harvardartmuseums/api-docs#iiif)  
`imageid` - is the numeric unique identifier for the image which can be used to construct a URI to dereference it 
`publiccaption` - is a descriptive note about the content of the media often listing information about the view (recto, verso, profile, 3/4 view)  
`renditionnumber` - is the unique name for the image; this often takes the form of a prefix + serial number; the prefix can provide hints as to when, why, and how we made the image  
`date` - is either the date of creation of the image record in our collections management system OR the date of creation of the image itself (this is very fuzzy data)  
`technique` - is the photography equipment and software used during the production of the image  
`width` - is the width of the image in pixels  

**lendingpermissionlevel** describes the level of lending restrictions for a record  
0 – ok to lend  
1 – partial restrictions on lending  
2 – unable to lend  

Objects have lending restrictions for many different reasons. Sometimes restrictions are part of the terms of a bequests and gifts. Other times lending is restricted because an object is too fragile to move. These are just a few examples.  

**objectid** describes the numeric unique identifier for a record  

**objectnumber** describes the unique identifier for a record  
This field is also known as accession number. For information on the structure and meaning of these numbers see the article [A Numbers Game](https://harvardartmuseums.org/article/2015/06/23/numbers-game).

**provenance** describes the history of ownership of the work  
This field is a record of the history of all the people/institutions who have owned the work from its creation until the present. Whenever possible it documents the legal title to a work at any particular time. This field often contains names of people along with the dates and location of ownership. See the museum's [Provenance Guidelines](https://harvardartmuseums.org/collections/collecting-policy#provenance) for more info on how to read provenance descriptions.  

**rank** is a number that is a measurement of how inactive the object is  
The number is computed every time the data in the API is refreshed. A number of factors go in to generating the number including membership in the “Collection Highlight” group, total number of page views (since 2009), and date of last page view. A lower number means the object is less active. We use the rank field to sort objects on our [Browse Our Collections](https://www.harvardartmuseums.org/collections) page. We do this to get the least active objects to rise to the top of search results so more of the collection is seen and used online.  

**seeAlso** is an array of links to alternate machine readable versions of the object  
An object many have zero or more of these links. The field structure of seeAlso is modelled on the seeAlso block in the [IIIF specification](https://iiif.io/api/presentation/2.1/#seealso)  

`id` - is the URI of the machine readable resource   
`type` - is the type of resource such as IIIF Manifest  
`format` - is the [media type/MIME type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the resource (typically application/json)   
`profile` - is the link to the service description for the resource  

**verificationlevel** describes the completeness and vetting status of information in a record  
0 - Unchecked. Object information has not been verified for completeness and has not been vetted  
1 - Poor. Object information is likely incomplete and has not been vetted  
2 - Adequate. Object is adequately described but information may not be vetted  
3 - Good. Object is well described and information is vetted  
4 - Best. Object is extensively researched, well described and information is vetted


#### Examples

> https://api.harvardartmuseums.org/object/304069  
> Returns the full record for Greek vessel titled "Hydria (water jar) with Siren Attachment".

#### Response

```json
{
    "objectid": 304069,
    "objectnumber": "1949.89",
    "accessionyear": 1949,
    "dated": "late 5th century BCE",
    "datebegin": -430,
    "dateend": -400,
    "classification": "Vessels",
    "classificationid": 57,
    "medium": "Bronze, traces of silvering and possible gilding",
    "technique": "Cast, lost-wax process",
    "techniqueid": 1311,
    "period": "Classical period, High",
    "periodid": 416,
    "century": "5th century BCE",
    "culture": "Greek",
    "style": null,
    "signed": null,
    "state": null,
    "edition": null,
    "standardreferencenumber": null,
    "dimensions": "h. 41.9 cm x diam. 28.5 cm (37 cm in diam. with handles) (16 1/2 x 11 1/4 in.; 14 9/16 in diam. with handles)",
    "copyright": null,
    "creditline": "Harvard Art Museums/Arthur M. Sackler Museum, Grace Nichols Strong Memorial Fund",
    "department": "Department of Ancient and Byzantine Art & Numismatics",
    "division": "Asian and Mediterranean Art",
    "contact": "am_asianmediterranean@harvard.edu",
    "description": "",
    "provenance": "John Edward Taylor Collection, London, (by 1912). [Christie’s, July 1, 1912, lot 367]. H. Oppenheimer collection, London, sold; [through Christie’s, London, July 22-23, 1936, lot 126]; sold; [to the International Studio Art Corp. (William Randolph Hearst), Oct. 24, 1940], sold; [through J. Brummer Gallery, New York, 1940-1949, inv. no. N4736], sold; to Fogg Art Museum, 1949.",
    "commentary": "",
    "labeltext": null,
    "imagecount": 5,
    "mediacount": 0,
    "colorcount": 9,
    "markscount": 0,
    "peoplecount": 0,
    "titlescount": 1,
    "publicationcount": 12,
    "exhibitioncount": 4,
    "contextualtextcount": 1,
    "groupcount": 3,
    "relatedcount": 0,
    "totalpageviews": 595,
    "totaluniquepageviews": 486,
    "dateoffirstpageview": "2009-06-03",
    "dateoflastpageview": "2018-08-22",
    "verificationlevel": 4,
    "verificationleveldescription": "Best. Object is extensively researched, well described and information is vetted",
    "imagepermissionlevel": 0,
    "accesslevel": 1,
    "accessionmethod": "Purchase",
    "rank": 164,
    "url": "https://www.harvardartmuseums.org/collections/object/304069",
    "id": 304069,
    "lastupdate": "2018-08-30T04:40:43-0400",
    "colors": [
        {
            "percent": 0.43642857142857,
            "spectrum": "#8c5fa8",
            "color": "#c8c8c8",
            "css3": "#c0c0c0",
            "hue": "Grey"
        },
        {
            "percent": 0.1864880952381,
            "spectrum": "#8c5fa8",
            "color": "#afafaf",
            "css3": "#a9a9a9",
            "hue": "Grey"
        },
        {
            "percent": 0.12803571428571,
            "spectrum": "#2eb45d",
            "color": "#323232",
            "css3": "#2f4f4f",
            "hue": "Grey"
        },
        {
            "percent": 0.092142857142857,
            "spectrum": "#3db657",
            "color": "#4b4b4b",
            "css3": "#2f4f4f",
            "hue": "Grey"
        },
        {
            "percent": 0.06297619047619,
            "spectrum": "#7866ad",
            "color": "#646464",
            "css3": "#696969",
            "hue": "Grey"
        },
        {
            "percent": 0.051964285714286,
            "spectrum": "#955ba5",
            "color": "#e1e1e1",
            "css3": "#dcdcdc",
            "hue": "Grey"
        },
        {
            "percent": 0.0175,
            "spectrum": "#8362aa",
            "color": "#7d7d7d",
            "css3": "#808080",
            "hue": "Grey"
        },
        {
            "percent": 0.014345238095238,
            "spectrum": "#8761aa",
            "color": "#969696",
            "css3": "#a9a9a9",
            "hue": "Grey"
        },
        {
            "percent": 0.010119047619048,
            "spectrum": "#1eb264",
            "color": "#191919",
            "css3": "#000000",
            "hue": "Grey"
        }
    ],
    "contextualtext": [
        {
            "text": "This three-handled water jar, or hydria, is of the kalpis type, which has a continuous curving profile and originated c. 500 BCE, perhaps in Athens. The body was hammered out of a single sheet of bronze to which the cast portions—three handles, the foot, and the rim—were joined with solder. The surface of the vessel is largely a greenish gold, which is reminiscent of its original color, although there are extensive areas of a darker greenish gray. \r\n \r\nThe rim (15.7 cm in diameter) features an overhanging band of egg-and-dart molding. Each egg is surrounded by a single raised ridge. Tiny beads encircle the outside of the flattened rim. The foot (15.5 cm in diameter) displays a concave band of tongues, in between each of which is a narrower convex tongue. \r\n \r\nThe side handles, decorated with four concave flutes with rounded ends, rise from circular plates decorated with concave tongues. The vertical handle, circular in section, bears five flutes separated by narrow ridges divided by fine grooves. The top rises from a base plate situated beneath the rim, identical with the plates of the side handles. \r\n \r\nThe base plate is a siren, whose sickle-shaped wings rise up out of her torso and curve inward symmetrically on either side of her head. Each individual feather, rendered in relief, has a fine incised median line, on either side of which are tiny incisions. The siren’s body is also covered with finely incised scales, which have a median line flanked by tiny incisions. The siren’s feet, each bearing three claws, hang vertically from raised edges below the scales and grasp an oval object, from which a seven-petalled palmette, with concave leaves, projects downward. \r\n \r\nAbove the palmette are two antithetical, concave S-shaped volutes, the smaller ends of which curl under the siren’s wings. The spaces between the volutes, the wings, and the tendrils are left open. The volutes’ centers are filled with small hemispherical oculi, which may be silver (1). Two curls descend in relief, curving symmetrically over the shoulders of the siren. \r\n \r\nThis hydria belongs to a class of vessels with sirens adorning the base plate of the vertical handles (2). They begin c. 480 BCE and continue throughout the rest of the fifth century, perhaps even into the first quarter of the fourth century. The shape of the Harvard hydria suggests that it dates between 430 and 400 BCE. The only intact Greek bronze vessel in the Harvard Art Museums' collection, this vase was used to carry and pour water, as the name hydria implies. Its funerary significance may be inferred from the presence of the siren at the base of this handle. Such expensive metal vases were given as prizes in athletic contests and often later contained the cremated ashes of their owners. Such use probably explains the unusually fine state of preservation of this hydria. Harvard's hydria represents the highest quality of late Classical Greek metalwork.\r\n \r\nNOTES:\r\n \r\n1. For other examples of vessels with silver in the volutes, see E. D. Reeder, Scythian Gold: Treasures from Ancient Ukraine, exh. cat., The Walters Art Gallery (Baltimore, 1999) 193-94, no. 82; and J. M. Padgett, The Centaur’s Smile, exh. cat., Princeton University Art Museum (New Haven, 2003) no. 80.\r\n \r\n2. For comparison, see D. von Bothmer, “Bronze Hydriai,” Bulletin of the Metropolitan Museum of Art 13.6 (1955): 193-200, esp. 197; I. Kouleiman­ē-Vokotopoulou, Chalkai Korinthiourgeis prochoi: Symvolē eis tēn meletēn tēs archaias Hellēnikēs chalkourgias (Athens, 1975) [in Greek]; ead., “Ē hydria tēs Aineias,” in Amētos: Timētikos tomos gia ton kathēgētē Manolē Andronikos 2, eds. M. A. Tiverios, S. Drougou, and Ch. Saatsoglou-Paliadelē (Thessaloniki, 1987) 157-69, esp. pls. 24-26 [in Greek]; L. I. Marangou, Ancient Greek Art: The N. P. Goulandris Collection (Athens, 1985), 162-63; and M. True and K. Hamma, eds., A Passion for Antiquities: Ancient Art from the Collection of Barbara and Lawrence Fleischman, exh. cat., J. Paul Getty Museum, Malibu; Cleveland Museum of Art (Malibu, 1994) 68-70, no. 24.\r\n \r\n \r\nDavid G. Mitten",
            "textiletext": null,
            "context": "Ancient Mediterranean and Near Eastern Bronzes at the Harvard Art Museums",
            "date": null,
            "type": "Published Catalogue Text"
        }
    ],
    "exhibitions": [
        {
            "citation": "<em>Dialogue with Antiquity: The Curatorial Achievement of George M.A. Hanfmann</em>, Fogg Art Museum, 05/07/1982 - 06/26/1982",
            "title": "Dialogue with Antiquity: The Curatorial Achievement of George M.A. Hanfmann",
            "exhibitionid": 4145,
            "enddate": null,
            "begindate": null
        },
        {
            "citation": "<em>Master Bronzes from the Classical World</em>, Fogg Art Museum, Cambridge, 12/04/1967 - 01/23/1968; City Art Museum of St. Louis, St. Louis, 03/01/1968 - 04/13/1968; Los Angeles County Museum of Art, Los Angeles, 05/08/1968 - 06/30/1968",
            "title": "Master Bronzes from the Classical World",
            "exhibitionid": 558,
            "enddate": "1968-06-30",
            "begindate": "1967-12-04"
        },
        {
            "citation": "<em>Greek and Roman Metalware: A Loan Exhibition</em>, Walters Art Gallery, 02/14/1976 - 04/14/1976",
            "title": "Greek and Roman Metalware: A Loan Exhibition",
            "exhibitionid": 4902,
            "enddate": "1976-04-14",
            "begindate": "1976-02-14"
        },
        {
            "citation": "<em>32Q: 3400 Greek</em>, Harvard Art Museums, Cambridge, 11/01/2014",
            "title": "32Q: 3400 Greek",
            "exhibitionid": 4470,
            "enddate": null,
            "begindate": "2014"
        }
    ],
    "gallery": {
        "gallerynumber": "3400",
        "floor": 3,
        "theme": "Ancient Greece in Black and Orange",
        "name": "Ancient Mediterranean and Near Eastern Art",
        "galleryid": 3400,
        "begindate": "2014-11-16"
    },
    "groupings": [
        {
            "name": "Collection Highlights",
            "groupid": 2039923
        },
        {
            "name": "Ancient Bronzes",
            "groupid": 2040129
        },
        {
            "name": "Google Art Project",
            "groupid": 2040174
        }
    ],
    "primaryimageurl": "https://nrs.harvard.edu/urn-3:HUAM:DDC251092_dynmc",
    "images": [
        {
            "date": "2013-05-28",
            "copyright": "President and Fellows of Harvard College",
            "imageid": 427747,
            "idsid": 46585832,
            "format": "image/jpeg",
            "description": null,
            "technique": null,
            "renditionnumber": "DDC251092",
            "displayorder": 1,
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:DDC251092_dynmc",
            "alttext": null,
            "width": 1909,
            "publiccaption": null,
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/46585832",
            "height": 2550
        },
        {
            "date": "2014-06-05",
            "copyright": "President and Fellows of Harvard College",
            "imageid": 440789,
            "idsid": 400097623,
            "format": "image/jpeg",
            "description": null,
            "technique": null,
            "renditionnumber": "LEG252741",
            "displayorder": 2,
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:LEG252741",
            "alttext": null,
            "width": 2351,
            "publiccaption": null,
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/400097623",
            "height": 2450
        },
        {
            "date": "2013-05-28",
            "copyright": "President and Fellows of Harvard College",
            "imageid": 427746,
            "idsid": 47334808,
            "format": "image/jpeg",
            "description": null,
            "technique": null,
            "renditionnumber": "DDC251030",
            "displayorder": 3,
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:DDC251030_dynmc",
            "alttext": null,
            "width": 685,
            "publiccaption": null,
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/47334808",
            "height": 1024
        },
        {
            "date": "2008-02-19",
            "copyright": "President and Fellows of Harvard College",
            "imageid": 291689,
            "idsid": 8385158,
            "format": "image/jpeg",
            "description": null,
            "technique": null,
            "renditionnumber": "DDC105025",
            "displayorder": 4,
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:DDC105025_dynmc",
            "alttext": null,
            "width": 827,
            "publiccaption": null,
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/8385158",
            "height": 1024
        },
        {
            "date": null,
            "copyright": "President and Fellows of Harvard College",
            "imageid": 14371,
            "idsid": 43182772,
            "format": "image/jpeg",
            "description": null,
            "technique": "Super XX",
            "renditionnumber": "46082",
            "displayorder": 5,
            "baseimageurl": "https://nrs.harvard.edu/urn-3:HUAM:46082_dynmc",
            "alttext": null,
            "width": 842,
            "publiccaption": null,
            "iiifbaseuri": "https://ids.lib.harvard.edu/ids/iiif/43182772",
            "height": 1024
        }
    ],
    "places": [
        {
            "placeid": 2037477,
            "type": "Creation Place",
            "displayname": "Ancient & Byzantine World, Europe, Chalke"
        }
    ],
    "publications": [
        {
            "citation": "Christie, Manson and Woods, Ltd., <em>John Edward Taylor Collection of Works of Art</em>, exh. cat., Christie, Manson and Woods, Ltd. (London, 1912)",
            "title": "John Edward Taylor Collection of Works of Art",
            "citationremarks": null,
            "publicationplace": "London",
            "publicationyear": 1912,
            "volumenumber": null,
            "format": "Exhibition Catalogue",
            "publicationid": 20129,
            "publicationdate": "1912",
            "volumetitle": null,
            "pagenumbers": "p. 92, no. 367."
        },
        {
            "citation": "Christie's, London, <em>Catalog of the collection of Egyptian and Roman antiquities, cameos and intaglios formed by the late Henry Oppenheimer</em>, exh. cat., William Clowes and Sons, Ltd. (London, 1936)",
            "title": "Catalog of the collection of Egyptian and Roman antiquities, cameos and intaglios formed by the late Henry Oppenheimer",
            "citationremarks": null,
            "publicationplace": "London",
            "publicationyear": 1936,
            "volumenumber": null,
            "format": "Exhibition Catalogue",
            "publicationid": 20128,
            "publicationdate": "1936",
            "volumetitle": null,
            "pagenumbers": "p. 41, no. 126."
        },
        {
            "citation": "<em>The Notable Art Collection Belonging to the estate of the late Joseph Brummer</em>, auct. cat., Parke-Bernet Galleries, Inc. (New York, NY, April 20 1940-April 23 1949)",
            "title": "The Notable Art Collection Belonging to the estate of the late Joseph Brummer",
            "citationremarks": null,
            "publicationplace": "New York, NY",
            "publicationyear": 1940,
            "volumenumber": null,
            "format": "Auction/Dealer Catalogue",
            "publicationid": 2387,
            "publicationdate": "April 20 1940-April 23 1949",
            "volumetitle": null,
            "pagenumbers": "p. 45, no. 185."
        },
        {
            "citation": "George M. A. Hanfmann, <em>Greek Art and Life, An Exhibition Catalogue</em>, exh. cat., Fogg Art Museum (Cambridge, MA, 1950)",
            "title": "Greek Art and Life, An Exhibition Catalogue",
            "citationremarks": null,
            "publicationplace": "Cambridge, MA",
            "publicationyear": 1950,
            "volumenumber": null,
            "format": "Exhibition Catalogue",
            "publicationid": 2769,
            "publicationdate": "1950",
            "volumetitle": null,
            "pagenumbers": "no. 15."
        },
        {
            "citation": "Erika Zwierlein-Diehl, <em>Die Hydria: Formgeschichte und Verwendung im Kult des Altertums</em>, Verlag Philipp von Zabern (Mainz, 1964)",
            "title": "Die Hydria: Formgeschichte und Verwendung im Kult des Altertums",
            "citationremarks": null,
            "publicationplace": "Mainz",
            "publicationyear": 1964,
            "volumenumber": null,
            "format": "Book",
            "publicationid": 20049,
            "publicationdate": "1964",
            "volumetitle": null,
            "pagenumbers": "p. 35ff, 219, no. B147."
        },
        {
            "citation": "David Gordon Mitten and Suzannah F. Doeringer, <em>Master Bronzes from the Classical World</em>, exh. cat., Verlag Philipp von Zabern (Mainz am Rhein, Germany, 1967)",
            "title": "Master Bronzes from the Classical World",
            "citationremarks": null,
            "publicationplace": "Mainz am Rhein, Germany",
            "publicationyear": 1967,
            "volumenumber": null,
            "format": "Exhibition Catalogue",
            "publicationid": 7820,
            "publicationdate": "1967",
            "volumetitle": null,
            "pagenumbers": "p. 108, no. 108."
        },
        {
            "citation": "Walters Art Gallery, <em>Greek and Roman Metalware: A Loan Exhibition, February 14 - April 14, 1976</em>, exh. cat., Walters Art Gallery (Baltimore, MD, 1976)",
            "title": "Greek and Roman Metalware: A Loan Exhibition, February 14 - April 14, 1976",
            "citationremarks": null,
            "publicationplace": "Baltimore, MD",
            "publicationyear": 1976,
            "volumenumber": null,
            "format": "Exhibition Catalogue",
            "publicationid": 20127,
            "publicationdate": "1976",
            "volumetitle": null,
            "pagenumbers": "no. 18."
        },
        {
            "citation": "David Gordon Mitten and Amy Brauer, <em>Dialogue with Antiquity, The Curatorial Achievement of George M. A. Hanfmann</em>, exh. cat., Fogg Art Museum (Cambridge, MA, 1982)",
            "title": "Dialogue with Antiquity, The Curatorial Achievement of George M. A. Hanfmann",
            "citationremarks": null,
            "publicationplace": "Cambridge, MA",
            "publicationyear": 1982,
            "volumenumber": null,
            "format": "Exhibition Catalogue",
            "publicationid": 2422,
            "publicationdate": "1982",
            "volumetitle": null,
            "pagenumbers": "p. 14, no. 39."
        },
        {
            "citation": "Kristin A. Mortimer and William G. Klingelhofer, <em>Harvard University Art Museums: A Guide to the Collections</em>, Harvard University Art Museums and Abbeville Press (Cambridge and New York, 1986)",
            "title": "Harvard University Art Museums: A Guide to the Collections",
            "citationremarks": null,
            "publicationplace": "Cambridge and New York",
            "publicationyear": 1986,
            "volumenumber": null,
            "format": "Book",
            "publicationid": 9088,
            "publicationdate": "1986",
            "volumetitle": null,
            "pagenumbers": "p. 112, no. 125, ill."
        },
        {
            "citation": "Amy Sowder, \"Greek Bronze Hydriai\" (2009), Emory University",
            "title": "Greek Bronze Hydriai",
            "citationremarks": null,
            "publicationplace": null,
            "publicationyear": 2009,
            "volumenumber": null,
            "format": "Dissertation/Thesis",
            "publicationid": 20098,
            "publicationdate": "2009",
            "volumetitle": null,
            "pagenumbers": "(Ph.D. diss.), p. 189, 543, no. 16.21."
        },
        {
            "citation": "Susanne Ebbinghaus, \"Men of Bronze--Cups of Bronze: Bronze in the Iron Age\", <em>Ancient Bronzes through a Modern Lens: Introductory Essays on the Study of Ancient Mediterranean and Near Eastern Bronzes</em>, ed. Susanne Ebbinghaus, Harvard Art Museums (Cambridge, MA, 2014), 146-69",
            "title": "\"Men of Bronze--Cups of Bronze: Bronze in the Iron Age\"",
            "citationremarks": null,
            "publicationplace": "Cambridge, MA",
            "publicationyear": 2014,
            "volumenumber": "146-69",
            "format": "Article/Essay",
            "publicationid": 20753,
            "publicationdate": "2014",
            "volumetitle": "Ancient Bronzes through a Modern Lens: Introductory Essays on the Study of Ancient Mediterranean and Near Eastern Bronzes",
            "pagenumbers": "pp. 164-65, fig. 7.10."
        },
        {
            "citation": "Susanne Ebbinghaus, ed., <em>Ancient Bronzes through a Modern Lens: Introductory Essays on the Study of Ancient Mediterranean and Near Eastern Bronzes</em>, Harvard Art Museum/Yale University Press (Cambridge, MA, 2014)",
            "title": "Ancient Bronzes through a Modern Lens: Introductory Essays on the Study of Ancient Mediterranean and Near Eastern Bronzes",
            "citationremarks": null,
            "publicationplace": "Cambridge, MA",
            "publicationyear": 2014,
            "volumenumber": null,
            "format": "Book",
            "publicationid": 22172,
            "publicationdate": "2014",
            "volumetitle": null,
            "pagenumbers": "pp. 54, 60, 66, 76, 164-165, fig. 7.10"
        }
    ],
    "details": {
        "technical": [
            {
                "text": "XRF data from Artax 1\r\nAlloy: Bronze\r\nAlloying Elements: copper, tin\r\nOther Elements: lead, iron, arsenic\r\nComments: Silvering and possible gilding were detected on the decorative elements.\r\n \r\nK. Eremin, January 2014",
                "type": "Chemical Composition",
                "formattedtext": "<P class=MsoNormal style=\"MARGIN: 0in 0in 0pt; LINE-HEIGHT: normal\"><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-fareast-font-family: 'Times New Roman'\">XRF data from <SPAN style=\"mso-no-proof: yes\">Artax 1</SPAN><?xml:namespace prefix = \"o\" ns = \"urn:schemas-microsoft-com:office:office\" /><o:p></o:p></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 0pt; LINE-HEIGHT: normal\"><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-fareast-font-family: 'Times New Roman'\">Alloy: <SPAN style=\"mso-no-proof: yes\">Bronze</SPAN><o:p></o:p></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 0pt; LINE-HEIGHT: normal\"><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-fareast-font-family: 'Times New Roman'\">Alloying Elements: <SPAN style=\"mso-no-proof: yes\">copper, tin</SPAN><o:p></o:p></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 0pt; LINE-HEIGHT: normal\"><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-fareast-font-family: 'Times New Roman'\">Other Elements: lead, <SPAN style=\"mso-no-proof: yes\">iron, arsenic<o:p></o:p></SPAN></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 0pt; LINE-HEIGHT: normal\"><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes; mso-ascii-theme-font: major-bidi; mso-hansi-theme-font: major-bidi; mso-bidi-theme-font: major-bidi\">Comments: Silvering and possible gilding were detected on the decorative elements.<o:p></o:p></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 0pt; LINE-HEIGHT: normal\"><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-fareast-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-theme-font: major-bidi; mso-bidi-theme-font: major-bidi\"><o:p>&nbsp;</o:p></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 0pt; LINE-HEIGHT: normal\"><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-fareast-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-theme-font: major-bidi; mso-bidi-theme-font: major-bidi\"><o:p></o:p></SPAN><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes\">K. Eremin, January 2014</SPAN></P>"
            },
            {
                "text": "The raised portion of the vessel is mostly covered with green and underlying red corrosion products, some in the form of deep-seated warts. However, about one-fourth of the surface is extremely well preserved, with bright metal showing through a thin brown oxide layer, especially at the rim and mouth. The handle and foot castings are more deeply corroded, and small losses show that the mineralization passes completely through the casting in these areas. Brown burial accretions are present on both the vessel and the attached castings. \r\n \r\nThe surface is well preserved in many areas but deeply corroded in others, with two holes (c. 2 x 3 cm) in the middle of the sides of the vessel. These are filled with a modern resin, visible as a large red blob at the interior. The interior otherwise shows a uniform layer of green corrosion products without the warts visible on the exterior. Portions of the thinner periphery of the cast handles are lost and one loss (1 x 3 cm) in the volutes at the edge of the center handle is restored with a resin. The two side handles have been reattached with a threaded rod secured by nuts at the interior.\r\n \r\nHammer marks are visible at the interior, especially at the mouth, and a deep centering punch mark (2 mm in diameter) at the bottom indicates the vessel was formed using a raising process. The handles and foot are cast, with finer details added by cold working using punches and a tracer tool. The castings each correspond perfectly to faint incised lines pre-dating the surface corrosion, which strongly suggests that they do in fact belong to this vessel. In a few areas, there is a vague correspondence in the corrosion products on the casting and the vessel, which further reinforces the match. Some lead residue at two spots point to the use of lead as the original means of attaching the castings. A gap between the cast foot and the vessel at its bottom, now filled with a modern resin, is the only area imperfectly matched. This is understandable as part of the original fabrication in this less visible location. The volute (3 mm in diameter) centers on either side of the center handle decoration, and the entire chest of the siren shows a thin wash of a white metal. This was analyzed by XRF and determined to be silver. Mercury was detected, but at such a low level that a mercury-silver amalgam process is not clearly indicated.\r\n \r\n \r\nHenry Lie (submitted 2008)",
                "type": "Technical Observations",
                "formattedtext": "<P class=MsoNormal style=\"MARGIN: 0in 0in 3pt\"><SPAN style=\"mso-ascii-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-font-family: 'Times New Roman'; mso-hansi-theme-font: major-bidi; mso-bidi-font-family: 'Times New Roman'; mso-bidi-theme-font: major-bidi\"><FONT size=3><FONT face=\"Times New Roman\">The raised portion of the vessel is mostly covered with green and underlying red corrosion products, some in the form of deep-seated warts. However, about one-fourth of the surface is extremely well preserved, with bright metal showing through a thin brown oxide layer, especially at the rim and mouth. The handle and foot castings are more deeply corroded, and small losses show that the mineralization passes completely through the casting in these areas. Brown burial accretions are present on both the vessel and the attached castings. <?xml:namespace prefix = \"o\" ns = \"urn:schemas-microsoft-com:office:office\" /><o:p></o:p></FONT></FONT></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 3pt\"><SPAN style=\"mso-ascii-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-font-family: 'Times New Roman'; mso-hansi-theme-font: major-bidi; mso-bidi-font-family: 'Times New Roman'; mso-bidi-theme-font: major-bidi\"><o:p><FONT size=3 face=\"Times New Roman\">&nbsp;</FONT></o:p></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 3pt\"><SPAN style=\"mso-ascii-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-font-family: 'Times New Roman'; mso-hansi-theme-font: major-bidi; mso-bidi-font-family: 'Times New Roman'; mso-bidi-theme-font: major-bidi\"><FONT size=3><FONT face=\"Times New Roman\">The surface is well preserved in many areas but deeply corroded in others, with two holes (c. 2 x 3 cm) in the middle of the sides of the vessel. These are filled with a modern resin, visible as a large red blob at the interior. The interior otherwise shows a uniform layer of green corrosion products without the warts visible on the exterior. Portions of the thinner periphery of the cast handles are lost and one loss (1 x 3 cm) in the volutes at the edge of the center handle is restored with a resin. The two side handles have been reattached with a threaded rod secured by nuts at the interior.<o:p></o:p></FONT></FONT></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 3pt\"><SPAN style=\"mso-ascii-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-font-family: 'Times New Roman'; mso-hansi-theme-font: major-bidi; mso-bidi-font-family: 'Times New Roman'; mso-bidi-theme-font: major-bidi\"><o:p><FONT size=3 face=\"Times New Roman\">&nbsp;</FONT></o:p></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 3pt\"><SPAN style=\"mso-ascii-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-font-family: 'Times New Roman'; mso-hansi-theme-font: major-bidi; mso-bidi-font-family: 'Times New Roman'; mso-bidi-theme-font: major-bidi\"><FONT size=3><FONT face=\"Times New Roman\">Hammer marks are visible at the interior, especially at the mouth, and a deep centering punch mark (2 mm in diameter) at the bottom indicates the vessel was formed using a raising process. The handles and foot are cast, with finer details added by cold working using punches and a tracer tool. The castings each correspond perfectly to faint incised lines pre-dating the surface corrosion, which strongly suggests that they do in fact belong to this vessel. In a few areas, there is a vague correspondence in the corrosion products on the casting and the vessel, which further reinforces the match. Some lead residue at two spots point to the use of lead as the original means of attaching the castings. A gap between the cast foot and the vessel at its bottom, now filled with a modern resin, is the only area imperfectly matched. This is understandable as part of the original fabrication in this less visible location. The volute (3 mm in diameter) centers on either side of the center handle decoration, and the entire chest of the siren shows a thin wash of a white metal. This was analyzed by XRF and determined to be silver. Mercury was detected, but at such a low level that a mercury-silver amalgam process is not clearly indicated.<o:p></o:p></FONT></FONT></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 3pt\"><SPAN style=\"mso-ascii-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-font-family: 'Times New Roman'; mso-hansi-theme-font: major-bidi; mso-bidi-font-family: 'Times New Roman'; mso-bidi-theme-font: major-bidi\"><o:p><FONT size=3 face=\"Times New Roman\">&nbsp;</FONT></o:p></SPAN></P>\r\n<P class=MsoNormal style=\"MARGIN: 0in 0in 3pt\"><SPAN style=\"mso-ascii-font-family: 'Times New Roman'; mso-ascii-theme-font: major-bidi; mso-hansi-font-family: 'Times New Roman'; mso-hansi-theme-font: major-bidi; mso-bidi-font-family: 'Times New Roman'; mso-bidi-theme-font: major-bidi\"><o:p><FONT size=3 face=\"Times New Roman\">&nbsp;</FONT></o:p></SPAN></P><SPAN style=\"FONT-SIZE: 12pt; FONT-FAMILY: 'Times New Roman','serif'; mso-ascii-theme-font: major-bidi; mso-hansi-theme-font: major-bidi; mso-bidi-theme-font: major-bidi; mso-fareast-font-family: Calibri; mso-fareast-theme-font: minor-latin; mso-bidi-language: AR-SA; mso-ansi-language: EN-US; mso-fareast-language: EN-US\">Henry Lie (submitted 2008)</SPAN>"
            }
        ]
    },
    "terms": {
        "medium": [
            {
                "id": 2028222,
                "name": "Metal"
            },
            {
                "id": 2028223,
                "name": "bronze"
            },
            {
                "id": 2028401,
                "name": "silver"
            },
            {
                "id": 2028692,
                "name": "gold"
            },
            {
                "id": 2040148,
                "name": "copper alloy"
            }
        ],
        "place": [
            {
                "id": 2028220,
                "name": "Ancient & Byzantine World"
            },
            {
                "id": 2028226,
                "name": "Europe"
            },
            {
                "id": 2037477,
                "name": "Chalke"
            }
        ],
        "century": [
            {
                "id": 37525581,
                "name": "5th century BCE"
            }
        ],
        "culture": [
            {
                "id": 37527534,
                "name": "Greek"
            }
        ],
        "topic": [
            {
                "id": 2040173,
                "name": "Artstor Digital Library"
            },
            {
                "id": 2040174,
                "name": "Google Art Project"
            }
        ]
    },
    "title": "Hydria (water jar) with Siren Attachment",
    "titles": [
        {
            "title": "Hydria (water jar) with Siren Attachment",
            "titletype": "Title",
            "displayorder": 1,
            "titleid": 753004
        }
    ],
    "worktypes": [
        {
            "worktypeid": "387",
            "worktype": "vessel"
        }
    ],
    "seeAlso": [
        {
            "id": "https://iiif.harvardartmuseums.org/manifests/object/304069",
            "type": "IIIF Manifest",
            "format": "application/json",
            "profile": "http://iiif.io/api/presentation/2/context.json"
        }
    ]
}
```

## Get object subsection

`GET /object/OBJECT_ID/SECTION` will get a section of detailed info about the specified object.

| Sections | Description |
| :--------- | :----- |
| colors | an array of the colors programmatically extracted from the primary image of the object |
| exhibitions | an array of the exhibitions featuring this object |
| experimental | all of the data generated by machine processing the object |
| images | an array of the images of the object |
| people | an array of the people associated with the creation of the object |
| publications | an array of the publications featuring this object |
| videos | an array of videos about or featuring this object |


#### Examples 

> https://api.harvardartmuseums.org/object/6772/publications  
> Returns an array containing all the publications related to Marianne Brandt’s "Untitled [with Anna May Wong]".

#### Response

```json
[
    {
        "citation": "Wulf Herzogenrath, <em>Bauhaus Utopien: Arbeiten auf Papier</em>, Cantz'sche Druckerei (Stuttgart, 1988)",
        "title": "Bauhaus Utopien: Arbeiten auf Papier",
        "citationremarks": null,
        "publicationplace": "Stuttgart",
        "publicationyear": 1988,
        "volumenumber": null,
        "format": "Book",
        "publicationid": 16007,
        "publicationdate": "1988",
        "volumetitle": null,
        "pagenumbers": "p. 66"
    },
    {
        "citation": "Elizabeth Otto, \"Figuring Gender: Photomontage and Cultural Critique in Germany's Weimar Republic: Dissertation\" (2003), University of Michigan",
        "title": "Figuring Gender: Photomontage and Cultural Critique in Germany's Weimar Republic: Dissertation",
        "citationremarks": null,
        "publicationplace": "Ann Arbor",
        "publicationyear": 2003,
        "volumenumber": null,
        "format": "Dissertation/Thesis",
        "publicationid": 16008,
        "publicationdate": "2003",
        "volumetitle": null,
        "pagenumbers": "pp. 143-145, 319"
    },
    {
        "citation": "Elizabeth Otto, <em>Tempo, Tempo!  The Bauhaus Photomontages of Marianne Brandt</em>, exh. cat., Bauhaus-Archiv and jovis Verlag (Berlin, 2005)",
        "title": "Tempo, Tempo!  The Bauhaus Photomontages of Marianne Brandt",
        "citationremarks": null,
        "publicationplace": "Berlin",
        "publicationyear": 2005,
        "volumenumber": null,
        "format": "Exhibition Catalogue",
        "publicationid": 16006,
        "publicationdate": "2005",
        "volumetitle": null,
        "pagenumbers": "pp. 104-105, 173"
    },
    {
        "citation": "Peter Nisbet and Joseph Koerner, <em>The Busch-Reisinger Museum, Harvard University Art Museums</em>, ed. Peter Nisbet, Harvard University Art Museums and Scala Publishers Ltd. (Cambridge, MA and London, England, 2007)",
        "title": "The Busch-Reisinger Museum, Harvard University Art Museums",
        "citationremarks": null,
        "publicationplace": "Cambridge, MA and London, England",
        "publicationyear": 2007,
        "volumenumber": null,
        "format": "Book",
        "publicationid": 19954,
        "publicationdate": "2007",
        "volumetitle": null,
        "pagenumbers": "p. 117"
    },
    {
        "citation": "Gu Zheng, \"Documentary and Representative: Harvard Art Museums' Photography Collections (Part Two)\", <em>Chinese Photography</em> (Beijing, China, 2018), 468, pp. 128-135",
        "title": "\"Documentary and Representative: Harvard Art Museums' Photography Collections (Part Two)\"",
        "citationremarks": null,
        "publicationplace": "Beijing, China",
        "publicationyear": 2018,
        "volumenumber": "468, pp. 128-135",
        "format": "Article/Essay",
        "publicationid": 23600,
        "publicationdate": "2018",
        "volumetitle": "Chinese Photography",
        "pagenumbers": "p. 134, ill. (color)"
    }
]
```
