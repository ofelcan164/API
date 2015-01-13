Users
===========

Allows you to retrieve information about a specific user

Get Users Quick Links
---------------

* `GET users/:id/quick_links.json` will return the user's list of quick links where :id is the id of the user whos quick links you want to retrieve.

We will return 100 files per page. If the result set has 100 files, it's your responsibility to check the next page to see if there are any more files -- you do this by adding &page=2 to the query, then &page=3 and so on.

```json
[
    {
        "id":437,
        "uid":"999710a0a4f54e248c1ae139ae2199ff",
        "purpose":"api test",
        "created_at":"2015-01-09T20:40:09Z",
        "processing":false,
        "asset_id":242286,
        "user_id":1,
        "filename":"1921996_385805548233952_1402137311_n.jpg",
        "url":"http://your_url.imagerelay.com/share/999710a0a4f54e248c1ae139ae2199ff"}
    }
]
```



