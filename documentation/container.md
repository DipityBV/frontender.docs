---
currentMenu: container
---

## Container
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
JSON code:
```JSON
{
    "frontender": "1558425992",
    "template": "containers/[content-type]/[container-name].html.twig",
    "name": {
        "en-GB": "Name for Frontender in English"
    },
    "description": {
        "en-GB": "Description for Frontender in English"
    },
    "template_config": {
        "content": {
            "label": {
                "en-GB": "Tab label for Frontender in English"
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
A Frontender ID is required

### Multilingual
##### Project locale
##### Environment locale
