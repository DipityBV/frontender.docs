---
currentMenu: container
---

# Container
Twig container with data from it's JSON configuration.
```twig
<{{ config.container_tag|default('section') }} {{ helper.container_id_attribute(frontender, 'frontender')|raw }}>
    {% if content.title|t %}
        <h1>{{ content.title|t }}</h1>
    {% endif %}
    {% if content.body|t %}
        <p>{{ content.body|t }}</p>
    {% endif %}
</{{ config.container_tag|default('section') }}>
```

JSON configuration:
```JSON
{
    "frontender": "1558425992",
    "template": "containers/[content-type]/[container-name].html.twig",
    "name": {
        "en-GB": "Container name"
    },
    "description": {
        "en-GB": "Description for container"
    },
    "template_config": {
        "content": {
            "label": {
                "en-GB": "Contextual data"
            },
            "controls": {
                "title": {
                    "label": {
                        "en-GB": "Title"
                    },
                    "control": "core/text",
                    "value": {
                        "en-GB": "Title goes here."
                    }
                },
                "body": {
                    "label": {
                        "en-GB": "Body text"
                    },
                    "control": "core/textarea",
                    "value": {
                        "en-GB": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
                    }
                }
            }
        }
    },
    "containers": []
}
```

### Frontender ID
Frontender ID is a required field. The page/container will not work properly if it is omitted.  
It's perfectly fine to add `"frontender": null`, the Frontender application will change it to a valid ID after the page has been saved.

### Multilingual
##### Project locale
The language(s) of the website itself. Can be configured to contain multiple languages.

```JSON
{
    "content_type_example": {
        "label": {
            "en-GB": "Environment locale label."
        },
        "control": "core/text",
        "value": {
            "en-GB": "English project locale",
            "fr-FR": "French project locale",
            "es-ES": "Spanish project locale"
        }
    }
}
```

##### Environment locale
The language of the the Frontender configuration. The default value is `en-GB`.
