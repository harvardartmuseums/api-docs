# IIIF

Most of the museums' data is accessible through [IIIF](http://iiif.io) image and presentation services. The IIIF image and presentation services are separate from our main data API. They do not require an access key.  

## Services

These are the services implemented thus far.

### Image

The service we provide adheres to version 2.1 of the API. Read more about the capabilities of the IIIF Image API at http://iiif.io/api/image/2.1/.   

The base URL for all images begins with:

```shell
https://ids.lib.harvard.edu/ids/iiif
```

Please note that URLs for images of objects that have rights restrictions are excluded for most API users. This means images for many 20th and 21st century works of art will not be available to you at the present time. We are working on a solution to this. 

### Presentation

The museums sevices conforms to the Presentation API version 2.1 Read the specification at http://iiif.io/api/presentation/2.1/. 

#### Collections

The top level collection is at:

```
https://iiif.harvardartmuseums.org/collections/top
```

#### Manifests

The base URL for all presentation manifests begins with:

```
https://iiif.harvardartmuseums.org/manifests
```

You can request a manifest for any object or gallery by appending /ENDPOINT/ITEM_ID to the base URL. 

For example the primary manifest for the object [Self-Portrait Dedicated to Paul Gauguin](https://www.harvardartmuseums.org/collections/object/299843) is at:

```
https://iiif.harvardartmuseums.org/manifests/object/299843
```

The primary manifest for gallery 1600, [Arts of Ancient China from the Bronze Age to the Golden Age](https://www.harvardartmuseums.org/visit/floor-plan/1/1600), is at:  

```
https://iiif.harvardartmuseums.org/manifests/gallery/1600
```

### Viewers

Our IIIF service includes two versions of the [Mirador](https://projectmirador.org/) viewer.

Mirador 2 is at:

```
https://iiif.harvardartmuseums.org/viewers/mirador/v2
```

Include one or more of the following optional parameters to control the display.

| Parameter | Value |
| :--------- | :----- |
| manifest | a valid IIIF manifest |
| collection | a valid IIIF collection |
| showmainmenu | 0 (false) or 1 (true) default |

Mirador 3 is at:

```
https://iiif.harvardartmuseums.org/viewers/mirador/v3
```

Include one or more of the following optional parameters to control the display.

| Parameter | Value |
| :--------- | :----- |
| manifest | a valid IIIF manifest |
| collection | a valid IIIF collection |
| showmainmenu | 0 (false) or 1 (true) default |

## Use Cases

We use IIIF in a variety of ways. Here are a few examples of how we currently use the services. 

**Image access**  
Most of the images on our public website are delivered via the libraries image delivery services. We use OpenSeadragon (OSD) as the image viewer on the object pages in the [collections section](https://www.harvardartmuseums.org/collections) of our site to enable deep zoom.

* [Floating Fans (Ōgi nagashi)](https://www.harvardartmuseums.org/collections/object/199913?rendition=LEG255051) is an example of a very large image (91342x3385 pixels) in OSD

**Sharing and reuse of objects**  
Every object page on our website has a link that opens its manifest in the Mirador viewer. 

**Rendering complex objects**  
Sometimes we have to create custom manifests for use in Mirador within publications (see [special collections](https://www.harvardartmuseums.org/publications/special-collections)) on our website. We do this mostly for book viewing and archives viewing.

* [Jacques-Louis David sketchbook]( https://www.harvardartmuseums.org/tour/drawing-the-invention-of-a-modern-medium/slide/8568) as part of a publication tied to the exhibition _Drawing: The Invention of a Modern Medium_

* [Christopher Wilmarth Studio Archive](https://www.harvardartmuseums.org/tour/christopher-wilmarth/slide/9826)

**R&D**  
We create ephemeral demos, research, and art projects. Most are bespoke viewers of IIIF compatible content. Most of them are designed around the IIIF Image API and the ability to clip and remix image regions on the fly. There a variety of demo videos in our [R&D playlist on YouTube](https://www.youtube.com/playlist?list=PLjiqsPexHHILT8FZc4I1p0idzdLNWLPff). Here are two projects that make extensive use of IIIF.

* [IIIF Explorer](https://iiif-explorer.herokuapp.com/)
* [AI research website](https://ai.harvardartmuseums.org/)

**Sharing collections**  
We have an option for “exporting” user created collections as IIIF collections. Links are exposed alongside each collection on the user’s profile page. The link opens the collection in Mirador by default. [View a demo](https://youtu.be/HOwH57om1dU).
