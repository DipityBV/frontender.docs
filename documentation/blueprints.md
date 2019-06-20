---
currentMenu: blueprints
---

## Blueprints

Blueprints are small snippets of template instructions in JSON format. Blueprints can be nested by adding them to the container array.

### Syntax

```JSON
{
    "frontender": null,
    "template": "containers/[contenttype]/[containername]/[containername].html.twig",
    "name": {
        "en-GB": "Name for Frontender in English",
        "fr-FR": "Name for Frontender in French"
    },
    "description": {
        "en-GB": "Description for Frontender in English",
        "fr-FR": "Description for Frontender in French"
    },
    "template_config": {
        "config": {
            "label": {
                "en-GB": "Tab label for Frontender in English",
                "fr-FR": "Tab label for Frontender in French"
            },
            "controls": {
                "your_variable_name": {
                    "label": {
                        "en-GB": "Field label for Frontender in English",
                        "fr-FR": "Field label for Frontender in French"
                    },
                    "control": "core/text",
                    "value": ""
                }
            }
        }
    },
    "containers": []
}
```

### Assigning content from an API to a blueprint

This is an example of a content tab to retrieve an image from the Unsplash API:
```JSON
"model": {
    "label": {
        "en-GB": "Content",
        "fr-FR": "Content"
    },
    "controls": {
        "data": {
			"value": {
				"adapter": "Unsplash",
				"model": "Image\\Search",
				"id": {
					"en-GB": "yXmjBxvkoG4"
				}
			},
			"label": {
				"en-GB": "Image"
			},
			"control": "core/abstract",
			"type": "lookup",
			"adapters": [
				{
					"value": "Unsplash",
					"label": "Unsplash",
					"models": [
						{
							"value": "Image\\Search",
							"label": "Image"
						}
					]
				}
			]
		}
    }
}
```


## Blueprint snippets

### Default properties
```JSON
"frontender": null,
"name": {
    "en-GB": "",
    "fr-FR": ""
},
"description": {
    "en-GB": "",
    "fr-FR": ""
},
"template": "",
"template_config": {}
```

### Default tabs
```JSON
"model": {
    "label": {
        "en-GB": "Content",
        "fr-FR": "Content"
    },
    "controls": {}
},
"labels": {
    "label": {
        "en-GB": "Labels",
        "fr-FR": "Labels"
    },
    "controls": {}
},
"config": {
    "label": {
        "en-GB": "Settings",
        "fr-FR": "Settings"
    },
    "controls": {}
}
```

### Default config controls
```
@todo
```

### Model controls
```
@todo
```

### Page controls
```
@todo
```

### Control config example
```
@todo
```

### Show/Hide list options
```JSON
"options": [
    {
        "value": "1",
        "label": {
            "en-GB": "Show",
            "fr-FR": "Show"
        }
    },
    {
        "value": "0",
        "label": {
            "en-GB": "Hide",
            "fr-FR": "Hide"
        }
    }
]
```

### List options
```JSON
"colour_theme": {
    "label": {
        "en-GB": "Theme colour"
    },
    "control": "core/list",
    "value": "green",
    "options": [
        {
            "value": "green",
            "label": {
                "en-GB": "Green"
            }
        },
        {
            "value": "blue",
            "label": {
                "en-GB": "Blue"
            }
        },
        {
            "value": "lime",
            "label": {
                "en-GB": "Lime"
            }
        }
    ]
}
```

## Blueprints tips & tricks
1. Try to minimise container nesting
2. You need one (nested) container for each model call – so, if you need an image from the media API and an article from the articles API you will need to code two containers (one for each model).
