Permissions
==========

Allow you to retrieve information about different permissions groups.

Get Permissions
--------------

* `GET /permissions.json` will return `200 OK` and we will respond with all the permission groups for the account.  

We will return 100 permissions per page. If the result set has 100 permissions, it's your responsibility to check the next page to see if there are any more permissions -- you do this by adding &page=2 to the query, then &page=3 and so on.

```json
[
  {
    "id":1,
    "name":"IR ADMIN",
    "description":"admin",
    "created_on":null,
    "updated_on":"2015-05-20T19:47:30Z"
  },
  {
    "id":145,
    "name":"maxpermissions",
    "description":"testing asset permissions",
    "created_on":"2009-05-05T08:53:37Z",
    "updated_on":"2011-04-20T10:59:20Z"
  }
]
```

Get Permission
-------------

* `GET /permissions/555.json` will return `200 OK`.  The 555 in the example refers to the permissions unique ID.  We will respond with a representation of the permission requested.

```json
{
  "id":555,
  "name":"IR ADMIN",
  "description":"admin",
  "created_on":null,
  "updated_on":"2015-05-20T19:47:30Z"
}
```
