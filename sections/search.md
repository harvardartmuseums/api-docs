# Search

There are four ways to search the collections data.

| Parameter | What it does | Available on |
| :--------- | :----- | :----- |
| q | A field-scoped query in [Elasticsearch query string syntax](https://www.elastic.co/docs/reference/query-languages/query-dsl/query-dsl-query-string-query) | every resource |
| keyword | A plain-language search run across many fields at once | object, image, exhibition, publication |
| match | Controls how many `keyword` terms must match | object, image |
| semantic | A natural language search that finds records by meaning | object, image, exhibition, publication, gallery, video, audio |

## Keyword search

The `keyword` parameter is the simplest way to search. Hand it a word or a phrase and it searches a broad set of fields, scoring records so the strongest matches come back first.

> https://api.harvardartmuseums.org/object?keyword=van+gogh  
> Finds objects connected to van Gogh, with the closest matches first.  

On the object resource, `keyword` searches titles, artist names, description, classification, culture, period, century, worktype, medium terms, support terms, technique, provenance, creditline, medium, commentary, label text, object number, contextual text, exhibition titles, marks, places, and gallery names.

On the image resource it searches description and caption. On the exhibition and publication resources it searches titles, description, and the names of people connected to the exhibition or publication.

Keyword search tolerates small misspellings, so `keyword=Monett` still finds Monet and `keyword=Winthorp` still finds Winthrop.

#### Requiring some or all of the terms

By default every term you supply must match. Set `match=any` to find records matching at least one term instead. Records matching more of your terms rank higher.

> https://api.harvardartmuseums.org/object?keyword=paintings+flowers+Japanese  
> Finds objects matching all three terms.  
>   
> https://api.harvardartmuseums.org/object?keyword=paintings+flowers+Japanese&match=any  
> Finds objects matching any one of the three terms. Returns a much larger result set.  

`match` is available on the object and image resources only. It accepts `all` (the default) or `any`.

#### Advanced keyword syntax

If your search string contains any of the operators below, `keyword` switches to a precise query mode and the whole string is interpreted as a query rather than as a bag of words.

| Operator | Meaning | Example |
| :--------- | :----- | :----- |
| `*` | Match zero or more characters | `straus.918.*` |
| `?` | Match a single character | `pa?nting` |
| `"` | Match an exact phrase | `"oil on canvas"` |
| `~` | Fuzzy or proximity match | `"oil canvas"~3` |
| `AND` `OR` `NOT` | Boolean operators, written in capitals | `Monet OR Renoir` |
| `-` | Exclude a term | `porcelain -Chinese` |
| `FIELD:VALUE` | Restrict a term to one field | `exhibitions.title:"van gogh"` |

> https://api.harvardartmuseums.org/object?keyword=porcelain+NOT+Chinese  
> Finds objects matching porcelain but excludes those matching Chinese.  
>   
> https://api.harvardartmuseums.org/object?keyword=Monet+OR+Renoir  
> Finds objects matching either artist.  

Two things to know about this mode:

* **`match` has no effect here.** Terms are combined with AND unless you say otherwise with an explicit operator.
* **Leading wildcards are rejected.** `*.newman` will not run. Wildcards must appear somewhere other than the first character.

## Semantic search

The `semantic` parameter searches by meaning rather than by matching words, so you can describe what you are looking for in ordinary language and find records that never use your words.

> https://api.harvardartmuseums.org/object?semantic=a+quiet+domestic+scene+with+afternoon+light  
> Finds objects whose descriptive text conveys that idea.  

Semantic search reads the prose attached to a record. What that means differs by resource.

| Resource | Text searched |
| :--------- | :----- |
| object | visual summaries, commentary, label text, contextual text, technical details, image descriptions, and discovery hooks |
| image | image descriptions |
| exhibition | description, short description, and image descriptions |
| publication | description, short description, and image descriptions |
| gallery | label text |
| video | description |
| audio | description |

On any other resource the `semantic` parameter is ignored and the request runs as though you had not supplied it.

## Hybrid search

Supplying `semantic` together with `keyword` or `q` runs both searches and fuses the two result sets, so you get records that match your words and records that match your meaning, interleaved by rank. This is the one case where two search parameters genuinely work together.

> https://api.harvardartmuseums.org/object?keyword=landscape&semantic=a+storm+gathering+over+open+water  
> Blends a keyword search for landscape with a semantic search for the scene described.  

All of the usual filters still apply in hybrid mode, so you can narrow a hybrid search by century, classification, culture, and anything else.

#### Current limitations

* `sort` does not work in hybrid mode. Omit it and use the fused relevance order.
* `sort=random` is ignored whenever `semantic` is in play.
* Paging is approximate. See the note on `next` in the [paging section](https://github.com/harvardartmuseums/api-docs#paging-through-data) of the main documentation.

## Highlighting matches

Add `highlight=1` to any request to find out *why* a record matched. Each record gains a `_highlight` block naming the fields that matched and showing the matched text wrapped in `<em>` tags.

> https://api.harvardartmuseums.org/object?keyword=shipwreck&highlight=1  
> Returns matching objects along with the text that matched.  

```json
"_highlight": {
    "titles.title": [
        "The <em>Shipwreck</em>"
    ],
    "description": [
        "a study for the larger <em>shipwreck</em> composition"
    ]
}
```

#### Tips and tricks

* `keyword` and `q` are alternatives to each other. If you supply both, `keyword` is used and `q` is ignored.
* Use `q` when you know the field you want and `keyword` when you do not.
* Searching and filtering are independent. Any search parameter can be combined with any filter parameter.
* URL encode your search strings. Spaces become `+` or `%20`, and `&` becomes `%26`.
* Quote a phrase to keep its words together. `keyword="still life"` is far narrower than `keyword=still+life`.
