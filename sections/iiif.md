# IIIF

Most of the museums' data is also accessible through [IIIF](http://iiif.io) image and presentation services.   

## Services

These are the services implemented thus far.

#### Image

The base URL for all images begins with:

```shell
https://ids.lib.harvard.edu/ids/iiif
```

#### Presentation

The museums sevices conforms to the Presentation API version 2.1 Read the specification at http://iiif.io/api/presentation/2.1/. 

###### Collections

The top level collection is at:

```
https://iiif.harvardartmuseums.org/collections/top
```

###### Manifests

The base URL for all presentation manifests begins with:

```
https://iiif.harvardartmuseums.org/manifests
```

Append object, exhibition, gallery

#### Viewers

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

#### Search

Coming soon