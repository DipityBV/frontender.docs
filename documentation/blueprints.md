---
currentMenu: blueprints
---

## Blueprints

Blueprints are small snippets of template instructions in JSON format. Blueprints can be nested by adding them to the container array.

### Syntax

```JSON
{
    "fe-id": null,
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

### Assigning content from the SCR to a blueprint

This is an example of a content tab to retrieve an list of impact stories from the SCR (note that the content type is currently a text field – it may become a select list instead, but for the sake of the example we keep it a text field):
```JSON
"model": {
    "label": {
        "en-GB": "Content",
        "fr-FR": "Content"
    },
    "controls": {
        "name": {
            "label": {
                "en-GB": "API Resource",
                "fr-FR": "API Resource"
            },
            "control": "core/hidden",
            "value": "Channel\\Articles"
        },
        "channelId": {
            "label": {
                "en-GB": "Channel id",
                "fr-FR": "Channel id"
            },
            "control": "core/text",
            "value": "d226b59695f00554161d3014a5008b40"
        },
        "limit": {
            "label": {
                "en-GB": "Limit",
                "fr-FR": "Limit"
            },
            "control": "core/text",
            "value": "4"
        },
        "limit": {
            "label": {
                "en-GB": "Limit",
                "fr-FR": "Limit"
            },
            "control": "core/text",
            "value": "4"
        },
        "articleType": {
            "label": {
                "en-GB": "Article type",
                "fr-FR": "Article type"
            },
            "control": "core/text",
            "value": "impact"
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

### Article content types option list options
```JSON
"options": [
    {
        "value": "blog",
        "label": {
            "en-GB": "Blog post"
        }
    },
    {
        "value": "corporate_news",
        "label": {
            "en-GB": "Corporate news article"
        }
    },
    {
        "value": "impact",
        "label": {
            "en-GB": "Impact article"
        }
    },
    {
        "value": "background",
        "label": {
            "en-GB": "Background story"
        }
    },
    {
        "value": "opinion",
        "label": {
            "en-GB": "Opinion article"
        }
    },
    {
        "value": "interview",
        "label": {
            "en-GB": "Interview"
        }
    },
    {
        "value": "syndicated",
        "label": {
            "en-GB": "Syndicated articles"
        }
    },
    {
        "value": "review",
        "label": {
            "en-GB": "Publication review"
        }
    },
    {
        "value": "technical_scientific",
        "label": {
            "en-GB": "Technical articles"
        }
    },
    {
        "value": "data_report",
        "label": {
            "en-GB": "Data report"
        }
    },
    {
        "value": "communique",
        "label": {
            "en-GB": "Communiqué"
        }
    },
    {
        "value": "vacancy",
        "label": {
            "en-GB": "Vacancy announcement"
        }
    },
    {
        "value": "internship",
        "label": {
            "en-GB": "Internship vacancy announcement"
        }
    },
    {
        "value": "call_for_external_expert",
        "label": {
            "en-GB": "Call for external expert"
        }
    },
    {
        "value": "call_for_tender",
        "label": {
            "en-GB": "Call for tender"
        }
    },
    {
        "value": "call_for_proposal",
        "label": {
            "en-GB": "Call for proposal"
        }
    },
    {
        "value": "partnership",
        "label": {
            "en-GB": "Call for partnership"
        }
    },
    {
        "value": "tender_award_notice",
        "label": {
            "en-GB": "Tender award notice"
        }
    },
    {
        "value": "tender_highlight",
        "label": {
            "en-GB": "Tender highlight"
        }
    },
    {
        "value": "speech",
        "label": {
            "en-GB": "Speech transcript"
        }
    }
]
```

### Colour list options
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
        },
        {
            "value": "yellow",
            "label": {
                "en-GB": "Yellow"
            }
        },
        {
            "value": "gold",
            "label": {
                "en-GB": "Gold"
            }
        },
        {
            "value": "orange",
            "label": {
                "en-GB": "Orange"
            }
        },
        {
            "value": "salmon",
            "label": {
                "en-GB": "Salmon"
            }
        },
        {
            "value": "red",
            "label": {
                "en-GB": "Red"
            }
        },
        {
            "value": "burgundy",
            "label": {
                "en-GB": "Burgundy"
            }
        },
        {
            "value": "purple",
            "label": {
                "en-GB": "Purple"
            }
        }
    ]
}
```

## Blueprints tips & tricks
1. Try to minimize container nesting
2. You need one (nested) container for each model call – so, if you need an image from the media API and an article from the articles API you will need to code two containers (one for each model).
