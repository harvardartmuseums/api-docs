# Sync

Every record carries two fields that exist to answer one question: has this changed since I last looked? Use them to keep a local copy of the data in step with ours without refetching everything.

| Field | Description |
| :--------- | :----- |
| md5 | A fingerprint of the record. A different value means the underlying data changed. |
| lastupdate | When the record was last republished. Empty until the record changes for the first time. |

Both fields are included in every response by default, so you do not have to ask for them. Every endpoint carries `lastupdate`. Every endpoint except [annotation](https://github.com/harvardartmuseums/api-docs/blob/master/sections/annotation.md) and [activity](https://github.com/harvardartmuseums/api-docs/blob/master/sections/activity.md) also carries `md5`.

A record is only republished when its fingerprint changes, so the two fields always move together. `md5` tells you *whether* something changed; `lastupdate` tells you *when*.

Which one you reach for depends on what you are tracking. If you care about a particular set of records, compare their fingerprints. If you want to follow everything happening across a resource, watch `lastupdate`.

## Watching records you already have

Most applications are built around a known set of records: the objects in an exhibition microsite, the people in a research project, a gallery's worth of images. To keep those current, ask for their fingerprints and compare them with the ones you stored last time.

The `id` parameter takes a pipe separated list, so you can check an entire set in a single request.

> https://api.harvardartmuseums.org/object?id=299843|230942|55320&fields=objectid,md5&size=3  
> Returns just the identifier and fingerprint for three specific objects.  

```json
"records": [
    {
        "objectid": 230942,
        "md5": "518d90713e13f6d819b44a7801daa487"
    },
    {
        "objectid": 55320,
        "md5": "3f5802f2f79347d59439e8c510895dee"
    },
    {
        "objectid": 299843,
        "md5": "4eb5a1584d9cd69524ada49c063cf2ed"
    }
]
```

Any fingerprint that differs from your stored copy marks a record worth refetching in full. Everything else you can leave alone.

Set `size` to at least the number of identifiers you send, and keep each batch within a single page of results. Records are not returned in the order you list them, so match them up by identifier rather than by position.

This approach does not depend on `lastupdate` at all, which makes it the more dependable of the two. It keeps working across a rebuild of the data, and it tells you about a record you care about even when a great many other records changed at the same time.

## Watching a whole resource

If you are following everything rather than a fixed set, ask for what has changed since your last run. `lastupdate` is a date field, so you can give it a range through the `q` parameter.

> https://api.harvardartmuseums.org/object?q=lastupdate:[2026-11-01 TO *]&size=100  
> Finds objects republished on or after 1 November 2026.  
>   
> https://api.harvardartmuseums.org/object?q=lastupdate:[2026-11-01 TO *]&sort=lastupdate&sortorder=asc&size=100  
> The same request in the order the changes happened, which makes it easy to record where you stopped.  

Store the highest `lastupdate` you have seen and use it as the lower bound next time. Records whose `lastupdate` is empty have not changed since the data was first loaded.

Because the data is refreshed daily, polling more than once a day gains you nothing.

## Auditing a full copy

If you hold a copy of an entire resource, the same fingerprint comparison scales up. Page through the whole set asking only for identifiers and fingerprints, and refetch just the records that differ.

> https://api.harvardartmuseums.org/object?fields=objectid,md5&size=100  
> Returns a lightweight list you can diff against your own copy.  

You can also look up a single fingerprint.

> https://api.harvardartmuseums.org/object?q=md5:4eb5a1584d9cd69524ada49c063cf2ed  
> Finds the record carrying that fingerprint.  

A full sweep of the object endpoint is about 2,500 requests at 100 records per page, so treat it as an occasional audit rather than a daily job. Watch `lastupdate` day to day and sweep fingerprints when you want to be sure.

## Things to know

**The fingerprint is ours, not yours.** It is computed on our side from the source record before we prepare it for the API. You cannot recreate it from the data you receive, so use it only to compare one of our values against another of our values.

**A record can change without looking any different.** The fingerprint covers source data that may never reach the API, or that your API key is not permitted to see. You will occasionally refetch a record and find it identical to the copy you already had. That is expected.

**Fingerprints are not stable forever.** They describe the shape of the source record as well as its content, so when we add, remove, or restructure a field, every fingerprint in that dataset changes even though nothing about the artwork did. The same is true after the data is rebuilt from scratch. When that happens, a great many records will look changed at once, and `lastupdate` may be empty across the board or set to the same moment for everything.

Treat a sudden collection-wide change as a signal to re-baseline rather than as thousands of real edits. If you are unsure, [ask us](https://github.com/harvardartmuseums/api-docs/issues).

#### Tips and tricks

* Use `fields` to keep sync requests small. `fields=objectid,md5` returns a fraction of the bytes of a full record.
* Checking a known set of records by `id` is cheaper and more reliable than scanning a whole resource. Prefer it whenever you know which records you care about.
* Combine change tracking with any filter. `q=lastupdate:[2026-11-01 TO *]&classification=Paintings` watches only the part of the collection you care about.
* `size=0` with a `lastupdate` range is a quick way to count how much has changed before you fetch any of it.
* For [annotation](https://github.com/harvardartmuseums/api-docs/blob/master/sections/annotation.md) and [activity](https://github.com/harvardartmuseums/api-docs/blob/master/sections/activity.md), which have no fingerprint, use `lastupdate` together with each endpoint's own filters.
