File Types
==========

Each file in Image Relay is assigned a file type. Different file types have different sets of metadata associated with them.

_Note that on the web, this is known as a Metadata Template. Not all plans have the ability to create new templates and alter the terms associated with your default template. Please contact support@imagerelay.com if you have questions about your plan features._

Get File Types
--------------

* `GET /file_types.json` will return all the file types for the account.

```json
[
  {
    "name":"Action A1",
    "description":"NaN",
    "created_on":"2008-05-18T20:16:52Z",
    "updated_on":"2013-01-07T17:06:14Z",
    "id":"<file_type_id>",
    "terms":
      [
        {
          "name":"Keywords",
          "position":1,
          "meta_name":"",
          "display_in_download":null,
          "field_type": "text_field",
          "metaterm_options": [],
          "created_on":"2012-06-08T12:44:38Z",
          "updated_on":"2012-06-08T12:44:38Z",
          "id":"<term_id>"
         },
         {
           "name":"Copyright",
           "position":2,
           "meta_name":"",
           "display_in_download":null,
           "field_type": "text_field",
           "metaterm_options": [],
           "created_on":"2012-06-08T12:44:38Z",
           "updated_on":"2012-06-08T12:44:38Z",
           "id":"<term_id>"
         },
      ]
  },
  {
    "name":"Meta Data",
    "description":"Testing Excel",
    "created_on":"2009-05-06T10:48:00Z",
    "updated_on":"2009-05-06T12:43:30Z",
    "id":"<file_type_id>",
    "terms":
      [
        {
          "name":"Title",
          "position":1,
          "meta_name":"Title",
          "display_in_download":null,
          "field_type": "text_field",
          "metaterm_options": [],
          "created_on":"2009-05-06T10:48:00Z",
          "updated_on":"2009-05-06T10:48:00Z",
          "id":"<term_id>"
        }
      ]
  }
]
```

Get File Type
-------------

* `GET /file_types/<file_type_id>.json` will return the specified file type.

```json
{
  "name":"Action A1",
  "description":"NaN",
  "created_on":"2008-05-18T20:16:52Z",
  "updated_on":"2013-01-07T17:06:14Z",
  "id":"<file_type_id>",
  "terms":
    [
      {
        "name":"Keywords",
        "position":1,
        "meta_name":"",
        "display_in_download":null,
        "field_type": "text_field",
        "metaterm_options": [],
        "created_on":"2012-06-08T12:44:38Z",
        "updated_on":"2012-06-08T12:44:38Z",
        "id":"<term_id>"
       },
       {
         "name":"Copyright",
         "position":2,
         "meta_name":"",
         "display_in_download":null,
         "field_type": "text_field",
         "metaterm_options": [],
         "created_on":"2012-06-08T12:44:38Z",
         "updated_on":"2012-06-08T12:44:38Z",
         "id":"<term_id>"
       },
    ]
}
```

Field Types and Metaterm Options
-------------

The `field_type` attribute can take values `text_field` or `single_select_field`. When it is set to `single_select_field`, populate the `metaterm_options` with choices you want available for that `term`. When it is set to `text_field` any input is acceptable and the `metaterm_options` array will be empty.

```json
{
  "name": "Rock Stars",
  "description": null,
  "created_on": "2019-06-25T18:56:14.000Z",
  "updated_on": "2019-06-26T21:40:26.000Z",
  "id": "<file_type_id>",
  "terms": [
     {
          "name": "Favorite Rolling Stones Member",
          "position": 1,
          "meta_name": "",
          "display_in_download": null,
          "field_type": "single_select_field",
          "metaterm_options": [
              {
                  "id": 6,
                  "metaterm_id": 48,
                  "value": "Keith Richards",
                  "position": 1,
                  "created_at": "2019-06-25T18:57:44.000Z",
                  "updated_at": "2019-06-25T18:57:44.000Z",
                  "deleted_at": 0
              },
              {
                  "id": 7,
                  "metaterm_id": 49,
                  "value": "Mick Jagger",
                  "position": 2,
                  "created_at": "2019-06-25T18:58:44.000Z",
                  "updated_at": "2019-06-25T18:58:44.000Z",
                  "deleted_at": 0
              }
          ],
          "created_on": "2019-06-25T18:57:44.000Z",
          "updated_on": "2019-06-25T19:33:45.000Z",
          "id": "<term_id>"
      }
    ]
}
```
