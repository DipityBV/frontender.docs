---
currentMenu: controls
---

## Controls
Frontender comes with a couple of core controls out of the box, these may be used alongside custom project controls.
The following controls are build into Frontender:

| Control | Information
| - | - |
| core/boolean | [Boolean](#boolean) |
| core/hidden | Hidden input field (not rendered in frontender) |
| core/markdown | Markdown textarea |
| core/number | Number input field |
| core/url | URL field |
| core/route | Route field |
| core/list | [List](#list) |
| core/textarea | Normal textarea |
| core/json | JSON textarea |
| core/abstract | ??? |
| core/text | Text input field |
| core/robots | Robots text field |

Additional core controls will be added in the near future.

### Boolean
Select list with "Yes" and "No", default value is "No"(0).

Example config:
```json
"boolean": {
    "label": {
        "en-GB": "Show example"
    },
    "value": 1,
    "control": "core/boolean"
}
```

### List
This control allows the user to pick a value from a list of options.

Example config:
```json
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

### Repeatable
Controls can be extended with an option to make them repeatable.
This will add a menu next to the item that allows repetition.

To allow for this functionality add the following line to your control object.
```json
"repeatable": true,
"at_least": 3 // This is optional, but ensures that you can only delete repetitions when it exceeds this number.
"at_most": 7  // Also optional, it's used to enforce the maximum amount of repetitions.
```

Example config:
```json
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

```json
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
