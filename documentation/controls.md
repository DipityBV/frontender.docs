---
currentMenu: controls
---

## Controls
A special kind of blueprint, only for controls. A control can reference another control.
Frontender comes with a couple of core controls out of the box, these may be used alongside custom project controls.
The following controls are build into Frontender:

| Control | Information
| - | - |
| core/boolean | [Boolean](#boolean) |
| core/hidden | [Hidden](#hidden) |
| core/markdown | [Markdown](#markdown) |
| core/number | [Number](#number) |
| core/url | [URL](#url) |
| core/route | [Route](#route) |
| core/list | [List](#list) |
| core/textarea | [Textarea](#textarea) |
| core/json | [JSON](#json) |
| core/abstract | [Abstract](#abstract) |
| core/text | [Text](#text) |
| core/robots | [Robots](#robots) |

Additional core controls will be added in the near future.

### Boolean
Select list with "Yes" and "No", default value is "No"(0).

Example config:
```JSON
"boolean": {
    "label": {
        "en-GB": "Boolean example"
    },
    "value": 1,
    "control": "core/boolean"
}
```

### Hidden
Hidden input field (not rendered in Frontender).
```JSON
"hidden": {
    "label": {
        "en-GB": "Hidden example"
    },
    "value": {
        "en-GB": "I'm not visible in Frontender!"
    },
    "control": "core/hidden"
}
```

### Markdown
Allows user to use markdown inside of a text area.
```JSON
"markdown": {
    "label": {
        "en-GB": "Markdown example"
    },
    "value": {
        "en-GB": "###Markdown heading level 3"
    },
    "control": "core/markdown"
}
```

### Number
Number input field
```JSON
"number": {
    "label": {
        "en-GB": "Only numbers are allowed in this input"
    },
    "value": 4,
    "control": "core/number"
}
```

### URL
URL field
```JSON
"url": {
    "label": {
        "en-GB": "URL"
    },
    "value": {
        "en-GB": "https://getfrontender.com"
    },
    "control": "core/url"
}
```

### Route
Route field
```JSON
"route": {
    "label": {
        "en-GB": "Route"
    },
    "value": {
        "en-GB": "example/route/index.php"
    },
    "control": "core/route"
}
```

### List
This control allows the user to pick a value from a list of options.

Example config:
```JSON
"list": {
	"value": "",
	"label": {
		"en-GB": "List example"
	},
	"control": "core/list",
	"options": [
		{
			"value": "One",
			"label": {
				"en-GB": "One",
                "fr-FR": "Un"
			}
		},
		{
			"value": "Two",
			"label": {
				"en-GB": "Two",
                "fr-FR": "Deux"
			}
		},
        {
			"value": "Three",
			"label": {
				"en-GB": "Three",
                "fr-FR": "Trois"
			}
		}
	]
}
```

### Textarea
Normal textarea
```JSON
"textarea": {
    "label": {
        "en-GB": "Textarea"
    },
    "value": {
        "en-GB": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
    },
    "control": "core/textarea"
}
```

### JSON
JSON textarea
```JSON
???
```

### Abstract
```JSON
???
```

### Text
Text input field
```JSON
"text": {
    "label": {
        "en-GB": "Text"
    },
    "value": {
        "en-GB": "Value goes here..."
    },
    "control": "core/text"
}
```
---
### Robots
Robots text field
```JSON
"meta_robots": {
	"value": "index, follow",
	"label": {
		"en-GB": "Indexing"
	},
	"control": "core/robots",
	"type": "text"
}
```
---
### Repeatable
Controls can be extended with an option to make them repeatable.
This will add a menu next to the item that allows repetition.

To allow for this functionality add the following line to your control object.
```JSON
"repeatable": true,
"at_least": 3 // This is optional, but ensures that you can only delete repetitions when it exceeds this number.
"at_most": 7  // Also optional, it's used to enforce the maximum amount of repetitions.
```

Example config:
```JSON
"item": {
    "value": [
        {
            "en-GB": "One",
            "fr-FR": "Un"
        },
        {
            "en-GB": "Two",
            "fr-FR": "Deux"
        },
        {
            "en-GB": "Three",
            "fr-FR": "Trois"
        }
    ],
    "label": {
        "en-GB": "List item"
    },
    "control": "core/text",
    "repeatable": true,
    "at_least": 2
}
```

### Compound
This control allows you to include multiple controls and form them to one.

Here is an example for the compound control. A compound control may only contain non-compounded fields.

```JSON
{
    "value": {
        "title": {},
        "link": {}
    },
    "label": {
        "en-GB": "My Compound",
        "fr-FR": "My Compound"
    },
    "type": "compound",
    "controls": {
        "title": {
            "control": "core/text"
        },
        "link": {
            "control": "core/text"
        }
    }
}
```

In this example we have added two text controls, each with their own label.
This will also become the keys to the values.

**Protip**: Compound controls are also repeatable.
