---
currentMenu: introduction
---

## Frontender introduction

### Container definition
A container (definition) is a JSON object. Containers may be nested to create compound containers. A page in Frontender is a compound container.
```JSON
{
    "name": "Name for Frontender",
    "description": "A description of the container for Frontender",
    "template":  "path/to/container/template.html.twig",
    "template_config": {},
    "containers": [],
    "blueprint": "a3248875-d0bf-4b0b-a496-0e1f0dec1f57"
}
```
| Term  | Definition |
| --- | --- |
| Name | the name of the container definition, only visible to Frontender. |
| Description | the description of the container definition, only visible to Frontender. |
| Template | the file path of the template, this template will be used to render the container in the frontend. |
| Config | the configuration object used by the template to render the container. This object may contain model instructions as well as configuration instructions. |
| Containers | additional containers that may be included in the template. |

---

### Blueprint definition
A blueprint (definition) is like a container. Blueprints have controls that allow Frontender Desktop to render the configuration UI used to edit the container instructions (config). Blueprints are used as a template to create containers. They are preformatted to container useful default settings that can be overridden once they have been included onto a page.


### Page definitions
A page (definition) is a (compound) container. A page commonly consists of a header, body and footer container and may look like:
```JSON
{
    "route": "blog",
    "name": {
        "en-GB": "Name for Frontender"
    },
    "description": {
        "en-GB": "A description of the container for Frontender"
    },
    "template": "path/to/page/template.html.twig",
    "template_config": {},
    "containers": [
        {
            "frontender": "1558357549",
            "name": {
                "en-GB": "Header container"
            },
            "description": {
                "en-GB": "A description for Frontender"
            },
            "template": "path/to/header/template.html.twig",
            "template_config": {},
            "blueprint": "ea6b893c-de10-47d6-9370-1ecddf011e58",
            "containers": []
        },
        {
            "frontender": "1558357550",
            "name": {
                "en-GB": "Body container"
            },
            "description": {
                "en-GB": "A description for Frontender"
            },
            "template": "path/to/body/template.html.twig",
            "template_config": {},
            "blueprint": "ea6b893c-de10-47d6-9370-1ecddf011e58",
            "Containers": []
        },
        {
            "frontender": "1558357551",
            "name": {
                "en-GB": "Footer container"
            },
            "description": {
                "en-GB": "A description for Frontender"
            },
            "template": "path/to/footer/template.html.twig",
            "template_config": {},
            "containers": [],
            "blueprint": "ea6b893c-de10-47d6-9370-1ecddf011e58"
        }
    ],
    "blueprint": "a3248875-d0bf-4b0b-a496-0e1f0dec1f57",
    "frontender": "1558357552"
}
```


### Page states
A page has different states that define its access:

#### Public
The revision of the page that is accessible to the frontend. It is stored in the Pages.public Collection (see: Collections).

#### Revision
A version of a page. It is stored in the Pages Collection (see: Collections). A revision is a complete page definition that can be loaded and previewed in Frontender Desktop and Frontender Platform(using its uuid). A revision is not publicly accessible to the frontend. A revision is defined by a date and time.

Revisions are managed in Frontender.

A revision of a page definition contains a MD5 hash of the page definition’s config attribute (which contains the actual container object).

#### Draft
A non-persisted version of a page. The draft is the working copy of a page. A draft is persisted in some kind of memory storage and is destroyed when:

- The user navigates away without saving
- The application is quit without saving
- …

Drafts are not accessible outside one user’s installation of Frontender. A draft is not accessible by the frontend and can not be previewed in a browser.

When a user wishes to preview a draft in Frontender, it must be saved first to create a revision of it.

Opening a (public) revision with Frontender Desktop will generate a draft.

#### Trash
A revision lot (all revisions of a page) that have been moved to the pages.trash collection. Pages in the trash will be retrievable (in some future version of Frontender).


### Container and blueprint attributes
Pages, containers and blueprints are JSON objects that contain configuration on which template to render, how, and with what data.

- A **blueprint contains controls** (and optionally default values)
- A **container contains values** (and optionally a reference to a blueprint)

If a blueprint attribute is not included in the container, the container will still function but its values can only be edited in Code view.

Likewise, when a container contains a property that cannot be matched to a control in a referenced blueprint, its value will only be editable in the Code view.

A value can be expressed as a simple value (string, number or boolean), an object with {locale}/{simple value} pairs or an array of values (see: Blueprints::Controls).

When a value is a simple value, it is considered non-translatable and will be used for all locales.

#### Template path (required)
The template.path attribute is exposed to the frontend. It can consist of values for each of one supported locales in the frontend. It defines what template (markup) to use.

>In Frontender, when a container does not contain a value for template, it is invalid and a notification should be displayed upon saving the file (or while editing its JSON).
>On the frontend, when a container does not contain a value for template, it can not be rendered and will simply be ignored by the JSON parser and discarded in the rendering process.

```JSON
{
    "template": {
        "en-GB": "File path for en_GB, String",
        "en-US": "File path for en_US, String"
    }
}
```

#### Name
The name attribute is only exposed to Frontender. It can consist of values for each of one supported locale in Frontender.

When name is omitted (or its value empty) the revision id is used as a fallback value.

>This is no longer accurate when we store files in db. We need another value for this.

```JSON
{
    "name": {
        "en-GB": "Name in en_GB, String",
        "en-US": "Name in en_US, String"
    }
}
```

#### Description
The description attribute is only exposed to Frontender. It can consist of values for each of one supported locale in Frontender.

When description is omitted (or its value empty) the attribute is disregarded.

```JSON
{
    "description": {
        "en-GB": "Description in en_GB, String",
        "en-US": "Description in en_US, String"
    }
}
```

#### Template config
The template.config attribute holds configuration properties for rendering of the template.

Settings are grouped into different sections (one level). Each group will be rendered as a tab in the Frontender Desktop UI (see Image 1: Container configuration UI).

>Examples below are for a frontend in Dutch and English

```JSON
{
    "template_config": {
        "layout": {
            "theme": "",
            "class": ""
        },
        "model": {
            "name": "contentful/article",
            "id": "A68B45686AGB0"
        },
        "labels": {
            "headline": {
                "nl-NL": "Jouw volgende digitale stap",
                "en-GB": "Your next step in digital"
            },
            "standfirst": {
                "nl-NL": "",
                "en-GB": ""
            }
        }
    }
}
```

#### Blueprint
Blueprint is the reference to a blueprint that is to be used to render a container’s UI in Frontender Desktop (see Image 1: Container configuration UI).

A blueprint holds the controls for the value(s) in a container. (see: Blueprints::Controls).
```JSON
{
    "blueprint": "project/containers/container"
}
```

#### Route
The route attribute defines the page’s URL, e.g. its address to the browser:
```JSON
{
    "route": {
        "en-GB": "home",
        "en-US": "home"
    }
}
```

#### Containers
Containers is an array and consists of one or more nested containers. A container containing other containers is referred to as a compound containers. A container in a container array is referred to as a nested container.
```JSON
{
    "containers": []
}
```

#### Revision
Revision contains a date (when the revision was created), a hash (of all container attributes but omitting the revision attribute) and a user object (who saved the revision). At the moment of writing this document, a revision attribute is only used on page level (root page definition container).

```JSON
{
    "revision" : {
        "lot": "07156454-f83b-4f8e-ba8f-46417564f409",
        "date": "2018-04-20 00:00:00",
        "hash": "71e089512689b9f29ba26a3d8db5aac9",
        "user": {}
    }
}
```
