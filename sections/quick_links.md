Quick Links
===========

Quick links allow you to quickly share a single file with someone else. They also can be embedded in HTML allowing you to
server your Image Relay files from your own sites directly from Image Relay. Downloads via quick links are counted against
your company's bandwidth account limits.

Get Quick Links
---------------

* `GET /quick_links.json` will return the API user's list of quick links

We will return 100 files per page. If the result set has 100 files, it's your responsibility to check the next page to see if there are any more files -- you do this by adding &page=2 to the query, then &page=3 and so on.

```json
[
    {
        "id": 365,
        "uid": "283f889bb3424fce814577d0d87979zd",
        "purpose": null,
        "created_at": "2013-08-12T14:58:34Z",
        "processing": false,
        "asset_id": 241635,
        "user_id": 405,
        "url": "https://your_url.imagerelay.com/ql/283f889bb3424fce814577d0d87979zd/00007-a_52x78_72_RGB.jpg"
    },
    {
        "id": 366,
        "uid": "88460f259af94d819f2032c09206a4zz",
        "purpose": null,
        "created_at": "2013-08-12T14:58:58Z",
        "processing": false,
        "asset_id": 241636,
        "user_id": 405,
        "url": "https://your_url.imagerelay.com/ql/88460f259af94d819f2032c09206a4zz/00007-a_55x82_72_RGB.jpg"
    },
    {
        "id": 7,
        "uid": "ddc5f4615d3d4dc4b46c095e913011z7",
        "purpose": "API",
        "created_at": "2012-05-04T14:04:17Z",
        "processing": false,
        "asset_id": 239370,
        "user_id": 405,
        "url": "https://your_url.imagerelay.com/ql/ddc5f4615d3d4dc4b46c095e913011z7/IMG_1178.JPG"
    }
]
```

Get Quick Link
--------------

* `GET /quick_links/97.json` will return the specified quick link.

```json
{
    "id": 97,
    "uid": "630f1eaf95474d8288a9b62ff3c3549bt",
    "purpose": "API",
    "created_at": "2012-11-30T09:21:54Z",
    "processing": false,
    "asset_id": 240095,
    "user_id": 405,
    "url": "https://your_url.imagerelay.com/ql/630f1eaf95474d8288a9b62ff3c3549bt/276499331_1.tif"
}
```

Create Quick Link
-----------------

* `POST /quick_links.json` will create a new quick link.

```json
{
  "purpose": "Embed in marketing web site",
  "asset_id": 123456,
  "expires": "2013-08-12",
  "max_width": "200",
  "max_height": "300",
  "format": "jpg",
  "dpi": 72,
  "disposition": "inline",
  "color_format": "rgb"
}
```

This will return `201 Created`, if successful, as well as a representation of the quick link.

```json
{
    "id": 97,
    "uid": "630f1eaf95474d8288a9b62ff3c3549bt",
    "purpose": "API",
    "created_at": "2012-11-30T09:21:54Z",
    "processing": true,
    "asset_id": 240095,
    "user_id": 405,
    "url": "https://your_url.imagerelay.com/ql/630f1eaf95474d8288a9b62ff3c3549bt/276499331_1.tif"
}
```

Required parameters are purpose and asset_id. All other parameters are optional. If the quick link "processing" flag is
true, then then the image hasn't finished resizing yet. It will not be ready to download until "processing" is false. You can
poll every few seconds (we recommend every 5 seconds), to see if the quick link is ready for viewing yet.


Delete Quick Link
-----------------

* `DELETE /quick_links/97.json` will delete a quick link.

This will return `204 No Content`, if successful.
