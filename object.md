# Object

Contains detailed information on the items in the Harvard Art Museums collections.

## Get objects

`GET /object` will get all objects.

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
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/1.4/search-aggregations.html#_structuring_aggregations) |
| hasimage | 0 or 1 |
| century | CENTURY or pipe separated list of centuries or "any" |
| classification | CLASSIFICATION ID or pipe separated list of CLASSIFICATION IDs or CLASSIFICATION NAME or pipe separated list of CLASSIFICATION NAMES or "any" |
| color | COLOR or pipe separated list of colors or "any" |
| culture | CULTURE ID or pipe separated list of CULTURE IDs or CULTURE NAME or pipe separated list of CULTURE NAMES or "any" |
| exhibition | EXHIBITION ID or "any" or "none" |
| gallery | GALLERY NUMBER or pipe separated list of gallery numbers or "any" or "none" |
| group | GROUP ID or pipe separated list of GROUP IDs or GROUP NAME or "any" |
| keyword | 1 or more terms |
| medium | MEDIUM ID or pipe separated list of MEDIUM IDs or MEDIUM NAME or pipe separated list of MEDIUM NAMES or "any" |
| objectnumber | 1 or more terms |
| period | PERIOD or pipe separated list of periods or "any" |
| person | PERSON ID or pipe separated list of PERSON IDs or PERSON NAME or "any" |
| place | PLACE ID or pipe separated list of PLACE IDs or PLACE NAME or "any" |
| publication | PUBLICATION ID or "any" or "none" |
| relatedto | OBJECT ID |
| technique | TECHNIQUE ID or pipe separated list of TECHNIQUE IDs or TECHNIQUE NAME or pipe separated list of TECHNIQUE NAMES or "any" |
| title | 1 or more terms |
| exact_title | EXACT URL ENCODED TITLE |
| worktype | WORKTYPE ID or pipe separated list of WORKTYPE IDs or WORKTYPE NAME or pipe separated list of WORKTYPE NAMES or "any" |
| yearmade | four digit year |


#### Examples

> http://api.harvardartmuseums.org/object?q=totalpageviews:0&size=10  
> Returns ten objects that have never been viewed on the Art Museums main public website.  
>  
> http://api.harvardartmuseums.org/object?person=33430  
> Finds all of the objects that involve a specific person.  
>   
> http://api.harvardartmuseums.org/object?classification=Prints&q=totalpageviews:1  
> Finds all of the objects classified as prints that have been viewed only once on the Art Museums main public website.

#### Response

To keep responses reasonably sized, the output from a get objects request contains a subset of fields. To get all of the data fields for a given record, use a get object request.

```json
{
	"info": {
		"totalrecordsperquery": 10,
		"totalrecords": 261018,
		"pages": 26102,
		"page": 1
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

**accessionyear** describes the year the object was acquired  
In some cases it represents the year the object officially became part of the museums collection. In other cases it reflects the year Harvard acquired it. Many objects have accession years that predate the existence of the Fogg Museum (1895), the first museum of the three museums that are part of Harvard Art Museums, and thus can be thought of as being acquired by Harvard itself.  

**colors** describes the colors programmatically extracted from the primary image of the object  
An object may have zero or more colors. The color of each pixel is read and then sorted in to buckets. Brightness and gradient variants are reduced so similar colors group together and to keep the number of buckets under 20. Then the those colors are mapped to the museums' color palette, the CSS3 color listing, and hue names.  

`percent` - is the amount, between the range of 0 to 1, of the color found in the image  
`color` - is the color found in the image  
`spectrum` - is the closest match of the color value to the museums' design color [spectrum](https://github.com/harvardartmuseums/api-docs/blob/master/spectrum.md)  
`css3` - is the closest match to the colors listed in the [CSS3 color module specification](https://www.w3.org/TR/css3-color/)  
`hue` - is the color value mapped to the name of a hue (Red, Orange, Yellow, Green, Blue, Violet, Brown, Grey, Black, White)  

**objectnumber** describes the unique identifier for a record  
This field is also known as accession number. For information on the structure and meaning of these numbers see the article [A Numbers Game](http://magazine.harvardartmuseums.org/article/2015/06/23/numbers-game).

Some fields contain numeric values that have special meaning.

**imagepermissionlevel** describes the level of image copyright permissions for a record  
0 – ok to display images at any size  
1 – images have restrictions; display at a maximum pixel dimension of 256px  
2 – do not display any images

**images** describes the images of the object  
An object may have zero or more images. As of March 2016, 91% of our objects have at least one image.  

`baseimageurl` - is the primary internet address for the image and is delivered through our [default image delivery service](https://github.com/harvardartmuseums/api-docs#default-service)  
`copyright` - is the copyright for the image  
`displayorder` - is the preferred sequence number for the image within a group of images in the context of the object record; sequencing is especially important for manuscripts and books; an image with displayorder = 1 can be thought of as the current canonical image for the object  
`idsid` - is the unique numeric identifier for the image in the Harvard Digital Repository    
`iiifbaseuri` - is the root of the address for accessing the image through our [IIIF image delivery service](https://github.com/harvardartmuseums/api-docs#iiif)  
`publiccaption` - is a descriptive note about the content of the media often listing information about the view (recto, verso, profile, 3/4 view)  
`renditionnumber` - is the unique name for the image; this often takes the form of a prefix + serial number; the prefix can provide hints as to when, why, and how we made the image  

**verificationlevel** describes the completeness and vetting status of information in a record  
0 - Unchecked. Object information has not been verified for completeness and has not been vetted  
1 - Poor. Object information is likely incomplete and has not been vetted  
2 - Adequate. Object is adequately described but information may not be vetted  
3 - Good. Object is well described and information is vetted  
4 - Best. Object is extensively researched, well described and information is vetted

**accesslevel** describes the accessibility of a record  
0 – Restricted. Object record is restricted to certain API keys  
1 – Public. Object record is available to all API keys

#### Examples

> http://api.harvardartmuseums.org/object/304069  
> Returns the full record for Greek vessel titled "Hydria (water jar) with Siren Attachment".

#### Response

```json
{
    "objectid": 304069,
    "objectnumber": "1949.89",
    "accessionyear": "1949",
    "dated": "late 5th century BCE",
    "datebegin": -430,
    "dateend": -400,
    "classification": "Vessels",
    "medium": "Bronze, traces of silvering and possible gilding",
    "technique": "Cast, lost-wax process",
    "period": "Classical period, High",
    "century": "5th century BCE",
    "culture": "Greek",
    "style": null,
    "signed": null,
    "state": null,
    "edition": null,
    "standardreferencenumber": null,
    "dimensions": "41.9 cm h x 28.5 cm diam (37 cm diam with handles) (16 1/2 x 11 1/4 in.; 14 9/16 in. diam with handles)",
    "copyright": null,
    "creditline": "Harvard Art Museums/Arthur M. Sackler Museum, Grace Nichols Strong Memorial Fund",
    "department": "Department of Ancient and Byzantine Art & Numismatics",
    "division": "Asian and Mediterranean Art",
    "contact": "am_asianmediterranean@harvard.edu",
    "description": "",
    "provenance": "John Edward Taylor Collection, London, (by 1912). [Christie’s, July 1, 1912, lot 367]. H. Oppenheimer collection, London, sold; [through Christie’s, London, July 22-23, 1936, lot 126]; sold; [to the International Studio Art Corp. (William Randolph Hearst), Oct. 24, 1940], sold; [through J. Brummer Gallery, New York, 1940-1949, inv. no. N4736], sold; to Fogg Art Museum, 1949.",
    "commentary": "",
    "imagecount": 5,
    "mediacount": 0,
    "colorcount": 9,
    "markscount": 0,
    "peoplecount": 0,
    "titlescount": 1,
    "publicationcount": 11,
    "exhibitioncount": 3,
    "contextualtextcount": 1,
    "groupcount": 4,
    "relatedcount": 0,
    "totalpageviews": 149,
    "totaluniquepageviews": 117,
    "dateoffirstpageview": "2009-06-03",
    "dateoflastpageview": "2015-01-24",
    "verificationlevel": 4,
    "verificationleveldescription": "Best. Object is extensively researched, well described and information is vetted",
    "imagepermissionlevel": 0,
    "accesslevel": 1,
    "rank": 118,
    "url": "http://harvardartmuseums.org/collections/object/304069",
    "id": 304069,
    "lastupdate": "2015-01-28T04:19:50-0500",
    "colors": [
        {
            "percent": 0.44202380952381,
            "spectrum": "#8c5fa8",
            "color": "#c8c8c8",
            "css3": "#c0c0c0",
            "hue": "Grey"
        },
        {
            "percent": 0.18071428571429,
            "spectrum": "#8c5fa8",
            "color": "#afafaf",
            "css3": "#a9a9a9",
            "hue": "Grey"
        },
        {
            "percent": 0.12672619047619,
            "spectrum": "#2eb45d",
            "color": "#323232",
            "css3": "#2f4f4f",
            "hue": "Grey"
        },
        {
            "percent": 0.092559523809524,
            "spectrum": "#3db657",
            "color": "#4b4b4b",
            "css3": "#2f4f4f",
            "hue": "Grey"
        },
        {
            "percent": 0.066369047619048,
            "spectrum": "#7866ad",
            "color": "#646464",
            "css3": "#696969",
            "hue": "Grey"
        },
        {
            "percent": 0.051369047619048,
            "spectrum": "#955ba5",
            "color": "#e1e1e1",
            "css3": "#dcdcdc",
            "hue": "Grey"
        },
        {
            "percent": 0.014940476190476,
            "spectrum": "#8761aa",
            "color": "#969696",
            "css3": "#a9a9a9",
            "hue": "Grey"
        },
        {
            "percent": 0.014642857142857,
            "spectrum": "#8362aa",
            "color": "#7d7d7d",
            "css3": "#808080",
            "hue": "Grey"
        },
        {
            "percent": 0.010654761904762,
            "spectrum": "#1eb264",
            "color": "#191919",
            "css3": "#000000",
            "hue": "Grey"
        }
    ],
    "contextualtext": [
        {
            "text": "This three-handled water jar, or hydria, is of the kalpis type, which has a continuous curving profile and originated c. 500 BCE, perhaps in Athens. The body was hammered out of a single sheet of bronze to which the cast portions—three handles, the foot, and the rim—were joined with solder. The surface of the vessel is largely a greenish gold, which is reminiscent of its original color, although there are extensive areas of a darker greenish gray. \r\n \r\nThe rim (15.7 cm in diameter) features an overhanging band of egg-and-dart molding. Each egg is surrounded by a single raised ridge. Tiny beads encircle the outside of the flattened rim. The foot (15.5 cm in diameter) displays a concave band of tongues, in between each of which is a narrower convex tongue. \r\n \r\nThe side handles, decorated with four concave flutes with rounded ends, rise from circular plates decorated with concave tongues. The vertical handle, circular in section, bears five flutes separated by narrow ridges divided by fine grooves. The top rises from a base plate situated beneath the rim, identical with the plates of the side handles. \r\n \r\nThe base plate is a siren, whose sickle-shaped wings rise up out of her torso and curve inward symmetrically on either side of her head. Each individual feather, rendered in relief, has a fine incised median line, on either side of which are tiny incisions. The siren’s body is also covered with finely incised scales, which have a median line flanked by tiny incisions. The siren’s feet, each bearing three claws, hang vertically from raised edges below the scales and grasp an oval object, from which a seven-petalled palmette, with concave leaves, projects downward. \r\n \r\nAbove the palmette are two antithetical, concave S-shaped volutes, the smaller ends of which curl under the siren’s wings. The spaces between the volutes, the wings, and the tendrils are left open. The volutes’ centers are filled with small hemispherical oculi, which may be silver (1). Two curls descend in relief, curving symmetrically over the shoulders of the siren. \r\n \r\nThis hydria belongs to a class of vessels with sirens adorning the base plate of the vertical handles (2). They begin c. 480 BCE and continue throughout the rest of the fifth century, perhaps even into the first quarter of the fourth century. The shape of the Harvard hydria suggests that it dates between 430 and 400 BCE. The only intact Greek bronze vessel in the Harvard Art Museums' collection, this vase was used to carry and pour water, as the name hydria implies. Its funerary significance may be inferred from the presence of the siren at the base of this handle. Such expensive metal vases were given as prizes in athletic contests and often later contained the cremated ashes of their owners. Such use probably explains the unusually fine state of preservation of this hydria. Harvard's hydria represents the highest quality of late Classical Greek metalwork.\r\n \r\nNOTES:\r\n \r\n1. For other examples of vessels with silver in the volutes, see E. D. Reeder, Scythian Gold: Treasures from Ancient Ukraine, exh. cat., The Walters Art Gallery (Baltimore, 1999) 193-94, no. 82; and J. M. Padgett, The Centaur’s Smile, exh. cat., Princeton University Art Museum (New Haven, 2003) no. 80.\r\n \r\n2. For comparison, see D. von Bothmer, “Bronze Hydriai,” Bulletin of the Metropolitan Museum of Art 13.6 (1955): 193-200, esp. 197; I. Kouleiman­ē-Vokotopoulou, Chalkai Korinthiourgeis prochoi: Symvolē eis tēn meletēn tēs archaias Hellēnikēs chalkourgias (Athens, 1975) [in Greek]; ead., “Ē hydria tēs Aineias,” in Amētos: Timētikos tomos gia ton kathēgētē Manolē Andronikos 2, eds. M. A. Tiverios, S. Drougou, and Ch. Saatsoglou-Paliadelē (Thessaloniki, 1987) 157-69, esp. pls. 24-26 [in Greek]; L. I. Marangou, Ancient Greek Art: The N. P. Goulandris Collection (Athens, 1985), 162-63; and M. True and K. Hamma, eds., A Passion for Antiquities: Ancient Art from the Collection of Barbara and Lawrence Fleischman, exh. cat., J. Paul Getty Museum, Malibu; Cleveland Museum of Art (Malibu, 1994) 68-70, no. 24.\r\n \r\n \r\nDavid G. Mitten",
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
            "citation": "<em>Master Bronzes from the Classical World</em>, City Art Museum of St. Louis, St. Louis, 03/01/1968 - 04/13/1968; Los Angeles County Museum of Art, Los Angeles, 05/08/1968 - 06/30/1968; Fogg Art Museum, Cambridge, 12/04/1967 - 01/23/1968",
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
        }
    ],
    "gallery": {
        "galleryid": 3400,
        "gallerynumber": "3400",
        "floor": 3,
        "theme": "Ancient Greece in Black and Orange",
        "name": "Ancient Mediterranean and Near Eastern Art"
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
            "name": "Artstor Digital Library",
            "groupid": 2040173
        },
        {
            "name": "Google Art Project",
            "groupid": 2040174
        }
    ],
    "primaryimageurl": "http://nrs.harvard.edu/urn-3:HUAM:DDC251092_dynmc",
    "images": [
        {
            "baseimageurl": "http://nrs.harvard.edu/urn-3:HUAM:DDC251092_dynmc",
            "publiccaption": null,
            "idsid": "46585832",
            "displayorder": 1,
            "copyright": "President and Fellows of Harvard College",
            "renditionnumber": "DDC251092"
        },
        {
            "baseimageurl": "http://nrs.harvard.edu/urn-3:HUAM:LEG252741",
            "publiccaption": null,
            "idsid": "400097623",
            "displayorder": 2,
            "copyright": "President and Fellows of Harvard College",
            "renditionnumber": "LEG252741"
        },
        {
            "baseimageurl": "http://nrs.harvard.edu/urn-3:HUAM:DDC251030_dynmc",
            "publiccaption": null,
            "idsid": "47334808",
            "displayorder": 3,
            "copyright": "President and Fellows of Harvard College",
            "renditionnumber": "DDC251030"
        },
        {
            "baseimageurl": "http://nrs.harvard.edu/urn-3:HUAM:DDC105025_dynmc",
            "publiccaption": null,
            "idsid": "8385158",
            "displayorder": 4,
            "copyright": "President and Fellows of Harvard College",
            "renditionnumber": "DDC105025"
        },
        {
            "baseimageurl": "http://nrs.harvard.edu/urn-3:HUAM:46082_dynmc",
            "publiccaption": null,
            "idsid": "43182772",
            "displayorder": 5,
            "copyright": "President and Fellows of Harvard College",
            "renditionnumber": "46082"
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
            "citation": "Kristin A. Mortimer, <em>Harvard University Art Museums: A Guide to the Collections</em>, Harvard University Art Museums/Abbeville Press (Cambridge, MA; New York, NY, 1985)",
            "title": "Harvard University Art Museums: A Guide to the Collections",
            "citationremarks": null,
            "publicationplace": "Cambridge, MA; New York, NY",
            "publicationyear": 1985,
            "volumenumber": null,
            "format": "Book",
            "publicationid": 9088,
            "publicationdate": "1985",
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
        }
    ],
    "details": {
        "technical": [
            {
                "text": "XRF data from Artax 1\r\nAlloy: Bronze\r\nAlloying Elements: copper, tin\r\nOther Elements: lead, iron, arsenic\r\nComments: Silvering and possible gilding were detected on the decorative elements.\r\nK. Eremin, January 2014",
                "type": "Chemical Composition"
            },
            {
                "text": "The raised portion of the vessel is mostly covered with green and underlying red corrosion products, some in the form of deep-seated warts. However, about one-fourth of the surface is extremely well preserved, with bright metal showing through a thin brown oxide layer, especially at the rim and mouth. The handle and foot castings are more deeply corroded, and small losses show that the mineralization passes completely through the casting in these areas. Brown burial accretions are present on both the vessel and the attached castings. \r\n \r\nThe surface is well preserved in many areas but deeply corroded in others, with two holes (c. 2 x 3 cm) in the middle of the sides of the vessel. These are filled with a modern resin, visible as a large red blob at the interior. The interior otherwise shows a uniform layer of green corrosion products without the warts visible on the exterior. Portions of the thinner periphery of the cast handles are lost and one loss (1 x 3 cm) in the volutes at the edge of the center handle is restored with a resin. The two side handles have been reattached with a threaded rod secured by nuts at the interior.\r\n \r\nHammer marks are visible at the interior, especially at the mouth, and a deep centering punch mark (2 mm in diameter) at the bottom indicates the vessel was formed using a raising process. The handles and foot are cast, with finer details added by cold working using punches and a tracer tool. The castings each correspond perfectly to faint incised lines pre-dating the surface corrosion, which strongly suggests that they do in fact belong to this vessel. In a few areas, there is a vague correspondence in the corrosion products on the casting and the vessel, which further reinforces the match. Some lead residue at two spots point to the use of lead as the original means of attaching the castings. A gap between the cast foot and the vessel at its bottom, now filled with a modern resin, is the only area imperfectly matched. This is understandable as part of the original fabrication in this less visible location. The volute (3 mm in diameter) centers on either side of the center handle decoration, and the entire chest of the siren shows a thin wash of a white metal. This was analyzed by XRF and determined to be silver. Mercury was detected, but at such a low level that a mercury-silver amalgam process is not clearly indicated.\r\n \r\n \r\nHenry Lie (submitted 2008)",
                "type": "Technical Observations"
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
            "worktype": "vessel"
        }
    ]
}
```

## Get object subsection

`GET /object/OBJECT_ID/SECTION` will get a section of detailed info about the specified object.

#### Examples 

> http://api.harvardartmuseums.org/object/299843/publications  
> Returns an array containing all the publications related to van Gogh’s "Self-Portrait Dedicated to Paul Gauguin".

#### Response

```json
[
	{
		"citation": "E. H. DuQuesne-van Gogh, <em>Persönnliche Erinnerungen an Vincent Van Gogh</em> (Munich, Germany, 1911)",
		"title": "Persönnliche Erinnerungen an Vincent Van Gogh",
		"citationremarks": null,
		"publicationplace": "Munich, Germany",
		"publicationyear": 1911,
		"volumenumber": null,
		"format": "Book",
		"publicationid": 9382,
		"publicationdate": "1911",
		"volumetitle": null,
		"pagenumbers": "repr. as frontispiece"
	},
	{
		"citation": "Vincent van Gogh, <em>Brieven aan zijn broeder</em> (Amsterdam, The Netherlands, 1914)",
		"title": "Brieven aan zijn broeder",
		"citationremarks": null,
		"publicationplace": "Amsterdam, The Netherlands",
		"publicationyear": 1914,
		"volumenumber": null,
		"format": "Book",
		"publicationid": 8666,
		"publicationdate": "1914",
		"volumetitle": null,
		"pagenumbers": "v. iii, no. 537, p. 174; no. 545, pp. 204-205"
	},
	{
		"citation": "Julius Meier-Graefe, <em>Vincent</em>, R. Piper (Munich, Germany, 1922)",
		"title": "Vincent",
		"citationremarks": "Also English translation, New York, 1933; reproduced pl. 47",
		"publicationplace": "Munich, Germany",
		"publicationyear": 1922,
		"volumenumber": null,
		"format": "Book",
		"publicationid": 8787,
		"publicationdate": "1922",
		"volumetitle": null,
		"pagenumbers": "repr. v. II, pl. 79"
	}
]
```