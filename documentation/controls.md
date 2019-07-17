---
currentMenu: controls
---

# Controls
A special kind of blueprint, only for controls. A control can reference another control.
Frontender comes with a couple of core controls out of the box, these may be used alongside custom project controls.
The following controls are part of the into Frontender core:

| Control | Information
| :---: | :---: |
| core/boolean | [Boolean](#boolean) |
| core/hidden | [Hidden](#hidden) |
| core/markdown | [Markdown](#markdown) |
| core/number | [Number](#number) |
| core/url | [URL](#url) |
| core/route | [Route](#route) |
| core/list | [List](#list) |
| core/locale | [Locale](#locale)
| core/textarea | [Textarea](#textarea) |
| core/json | [JSON](#json) |
| core/abstract | [Abstract](#abstract) |
| core/text | [Text](#text) |
| core/page | [Page](#page)
| core/robots | [Robots](#robots) |

Additional core controls will be added in the near future.

### Boolean
Options list with two values: "True"(1) and "False"(0).   
The default value is "False".

Example config:
```JSON
{
    "boolean": {
        "label": {
            "en-GB": "Boolean example"
        },
        "value": 0,
        "control": "core/boolean"
    }
}
```

### Hidden
Hidden input field (not rendered in Frontender).
```JSON
{
    "hidden": {
        "label": {
            "en-GB": "Hidden example"
        },
        "value": {
            "en-GB": "I'm not visible in Frontender!"
        },
        "control": "core/hidden"
    }    
}
```

### Markdown
Allows user to use <a href="https://daringfireball.net/projects/markdown/" target="&#95;blank" rel="nofollow">Markdown</a> inside of a text area.
```JSON
{
    "body": {
    	"value": {
    		"en-GB": "## Topping cotton candy jelly beans biscuit cake. \nToffee sweet cupcake sweet lemon drops pie. Tart jujubes sweet biscuit dragée fruitcake dessert liquorice cotton candy. Chocolate cake carrot cake gingerbread soufflé tootsie roll cake marshmallow. Cake jelly cake jelly-o croissant. Jelly brownie tootsie roll toffee danish lollipop topping. Caramels chocolate fruitcake cotton candy jelly-o topping macaroon. Cotton candy sweet roll gummies. Dessert candy brownie tootsie roll. Oat cake cheesecake gummi bears. Bear claw liquorice fruitcake cake icing sugar plum cotton candy macaroon. Dessert cheesecake lollipop bear claw croissant. Marshmallow cookie cotton candy gingerbread icing jelly beans bonbon chocolate cake.\n\nCake chupa chups apple pie candy canes. Jujubes sugar plum cookie. Caramels gingerbread lemon drops brownie soufflé tart. Brownie chocolate cake topping cake. Gummies muffin gingerbread icing dragée. Tart gummies cake. Bear claw dragée halvah. Chupa chups tootsie roll gummi bears tootsie roll cotton candy chocolate bar wafer. Donut jelly pie jelly-o halvah. Sesame snaps candy croissant danish. Brownie pudding oat cake gummi bears candy. Soufflé chocolate bar fruitcake soufflé. Croissant marzipan sweet. Sesame snaps icing oat cake sweet icing cookie cookie soufflé chocolate cake."
    	},
    	"label": {
    		"en-GB": "Post body"
    	},
    	"control": "core/markdown"
    }
}
```

### Number
Number input field, only numbers are allowed inside this control.
```JSON
{
    "number": {
        "label": {
            "en-GB": "Only numbers are allowed in this input"
        },
        "value": 4,
        "control": "core/number"
    }
}
```

### URL
URL field
```JSON
{
    "url": {
        "label": {
            "en-GB": "URL"
        },
        "value": {
            "en-GB": "https://getfrontender.com"
        },
        "control": "core/url"
    }
}
```

### Route
Route field. Up to 3 values can be added.
* Link label (Optional) - The text that is shown instead of the URI.
* Link destination - The target destination of the link.
* Model ID (Optional) - When the target is a page that requires a model ID.

```JSON
{
    "route": {
		"value": {
			"label": {
				"en-GB": "Link description"
			},
			"page": "destination_route.html",
			"id": ""
		},
		"label": {
			"en-GB": "Route field"
		},
		"control": "core/route"
	}
}
```

### List
This control allows the user to pick a value from a pre-configured list of options.

Example config:
```JSON
{
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
}
```

### Locale
<!-- @TODO ??? -->
???
```JSON
{
    "???"
}
```

### Textarea
Normal textarea
```JSON
{
    "textarea": {
        "label": {
            "en-GB": "Textarea"
        },
        "value": {
            "en-GB": "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
        },
        "control": "core/textarea"
    }
}
```

### JSON
<!-- @TODO ??? -->
JSON textarea
```JSON
???
```

### Abstract
<!-- @TODO ??? -->
```JSON
???
```

### Text
Text input field
```JSON
{
    "text": {
        "label": {
            "en-GB": "Text"
        },
        "value": {
            "en-GB": "Value goes here..."
        },
        "control": "core/text"
    }
}
```

### Page
Page control
<!-- @TODO ??? -->
```JSON
{
    "???"
}
```

### Robots
Robots text field
```JSON
{
    "meta_robots": {
		"value": "index, follow",
		"label": {
			"en-GB": "Indexing"
		},
		"control": "core/robots",
		"type": "text"
	}
}
```
---

## Control settings

### Repeatable
Controls can be extended with an option to make them repeatable.
This will add a menu next to the item that allows repetition.

To allow for this functionality add the following line to your control object.
```JSON
"repeatable": true,
"at_least": 3 // This is optional, but ensures that you can only delete repetitions until the set amount remains.
"at_most": 7  // Also optional, it's used to enforce the maximum amount of repetitions.
```

Example config:
```JSON
{
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
}
```

### Compound
This control allows you to include multiple controls and form them to one.  
A compound may also be [repeatable](#repeatable).

Here is an example for the compound control. A compound control may only contain non-compounded fields.


```JSON
{
    "value": {
        "title": {
            "en-GB": ""
        },
        "link": {
            "en-GB": ""
        }
    },
    "label": {
        "en-GB": "My Compound",
        "fr-FR": "My Compound"
    },
    "type": "compound",
    "controls": {
        "title": {
            "value": "",
            "label": {
                "en-GB": "Title"
            },
            "control": "core/text"
        },
        "link": {
            "value": "",
            "label": {
                "en-GB": "Link"
            },
            "control": "core/text"
        }
    }
}
```

In this example we have added two text controls, each with their own label.
This will also become the keys to the values.

**Protip**: Compound controls are also repeatable.
