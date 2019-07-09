---
currentMenu: collection
---

# Collections
Page, blueprint and control definitions are stored in MongoDB collections.

MongoDB stores data records as BSON documents. BSON is a binary representation of JSON documents, though it contains more data types than JSON.

Both Frontender Desktop and Frontender Platform have access to these collections:
* lots
* blueprints
* containers
* pages
* pages.public
* pages.trash
* controls
* settings
* teams

### Blueprints
Blueprints have a revision object. The definition object contains the actual blueprint. The UUID is referenced in containers that implement that blueprint (inside page definitions). A blueprint has instructions on how to render a control, or includes a reference to a control.

A blueprint has a type attribute in the revision object. Possible types are:
* container
* page

```JSON
{
    "_id": "ea6b893c-de10-47d6-9370-1ecddf011e58",
    "revision": {
        "hash": "71e089512689b9f29ba26a3d8db5aac9",
        "type": "container",
        "date": "2018-04-20 00:00:00",
        "lot": "07156454-f83b-4f8e-ba8f-46417564f409",
        "thumbnail": {}
    },
    "definition": {
        "frontender": "1234567890",
        "template": "path/to/template.html.twig",
        "name": {},
        "description": {},
        "template_config": {},
        "containers": []
    },
    "identifier": "container/blueprint_name"
}
```

### Pages
Pages are similar to a blueprint, but contain containers (that may reference blueprints). They also contain a `template_config.route.path` object that is used by the frontend router. When the path object is empty, the lot id will be used as a default.

```JSON
{
    "_id": "ea6b839c-de10-47d6-9730-1ecddf101e58",
    "revision": {
        "lot": "07465154-f83b-4f8e-ba8f-46417564f409",
        "date": "2018-04-20 00:00:00",
        "hash": "71e052198689b9f29ba26a3d8db5aac9",
        "thumbnail": {},
        "user": {}
    },
    "definition": {
        "route": {},
        "frontender": "1234567890",
        "template": "path/to/template.html.twig",
        "name": {},
        "description": {},
        "page_config": {},
        "template_config": {},
        "containers": []
    }
}
```

### Pages.public
Identical to `pages` collection. Each page is an identical copy of a revision. When a page is published, the page definition is copied from the `pages` collection to the `pages.public` collection. When requesting a revision list in Frontender, page definitions from the `pages` collections are sanitised to exclude pages with identical hashes, only the version with the earliest revision date is included. When the a revision has an identical lot and hash as a page in the `pages.public` collection, it is marked in the UI as the currently published revision.

### Pages.thrash
Pages that have been removed. The published page is permanently deleted, all its revisions are moved to the `trash` collection.

### Controls
A special kind of blueprint, only for controls. A control can reference another control.

```JSON
{
    "_id": "ea6b893c-de10-47d6-9370-1ecddf011e58",
    "revision" : {
       "lot": "07156454-f83b-4f8e-ba8f-46417564f409",
       "date": "2018-04-20 00:00:00",
       "hash": "71e089512689b9f29ba26a3d8db5aac9",
       "user": {}
    },
    "definition": {
        "control": "ea6b893c-de10-47d6-9370-1ecddf011e58",
        "label": {},
        "type": "compound",
        "controls": {
            "label": {
                "label": {},
                "control": "ea6b893c-de10-47d6-9370-1ecddf011e58"
            },
            "url": {
                "label": {},
                "control": "ea6b893c-de10-47d6-9370-1ecddf011e58"
            }
        },
        "value": {
            "label": {},
            "url": {}
        }
    }
}
```
