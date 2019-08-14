---
currentMenu: collection
---

# Collections

Page, blueprint and control definitions are stored in MongoDB collections.

MongoDB stores data records as <a href="https://docs.mongodb.com/manual/core/document/#bson-document-format" target="&#95;blank" rel="nofollow">BSON documents</a>. BSON is a binary representation of JSON documents, though it contains more data types than JSON.

Collections are always named in <a href="https://stackoverflow.com/questions/9868323/is-there-a-convention-to-name-collection-in-mongodb/ 28619919" target="&#95;blank" rel="nofollow">plural form</a>.

Both Frontender Desktop and Frontender Platform have access to the following collections:

-   blueprints
-   controls
-   lots
-   pages
-   pages.public
-   pages.trash
-   routes
-   settings
-   teams

### Blueprints

Blueprints have a revision object. The definition object contains the actual blueprint. The UUID is referenced in containers that implement that blueprint (inside page definitions). A blueprint has instructions on how to render a control, or includes a reference to a control.

A blueprint has a type attribute in the revision object. Possible types are:

-   container
-   page
-   control

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

### Lots

Permissions are saved in the lots collection. All pages are linked to teams in this collection, you won't be able to edit a page if you're not linked to it by team.

### Pages

Pages are similar to a blueprint, but contain containers (that may reference blueprints). They also contain a `template_config.route.path` object that is used by the front-end router. When the path object is empty, the lot id will be used as a default.

The `template_config.route.path` object is required for each page object, without it the router cannot access it. Frontender Desktop will be implement a UI that enforces that the path object is not empty. When the path object is empty, the lot id will be used as a default.

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

### Pages.trash

Pages that have been removed. The published page is permanently deleted, all its revisions are moved to the `trash` collection.

### Controls

A special kind of blueprint, only for controls. A control can reference another control.
Frontender comes with a couple of core controls out of the box, these may be used alongside custom project controls. See the [controls page](/controls.html) for more information.

```JSON
{
    "value": "",
    "label": {
        "en-GB": "Allow overlap"
    },
    "control": "core/list",
    "options": [
        {
            "value": "",
            "label": {
                "en-GB": "none"
            }
        },
        {
            "value": "overlap-top",
            "label": {
                "en-GB": "Top overlap"
            }
        },
        {
            "value": "overlap-bottom",
            "label": {
                "en-GB": "Bottom overlap"
            }
        }
    ]
}
```

### Routes

All redirects are stored in the routes collection. Both permanent and temporary redirects.  
Each redirect is saved with a status of `301` or `302`.

A page is identified by its route. When a route changes, it will trigger the storage of a new version. This implies that the previous route is part of the previous revision but since the route defines the page the revisions can no longer be related to the same route.

### Settings

Site settings are saved in this collection. This includes a randomly generated `site_id` used to identify the website.  
Scopes, locales, root page and preview settings.

### Teams

An array list of user ids.  
Teams are used to set the permissions of user groups.
