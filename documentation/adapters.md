---
currentMenu: adapters
---

# Adapters
An adapter is a connection to an API. An adapter is an extension package of:
* PHP Models - which extend/implement Frontender Platform core adapter models;
* Control blueprints, which are used inside container blueprints and are used to set the model states.

#### Unsplash adapter
Data lookup with images from https://unsplash.com/
```JSON
{
	"data": {
		"value": {
			"adapter": "Unsplash",
			"model": "Image\\Search",
			"id": {
				"en-GB": "yXmjBxvkoG4"
			}
		},
		"label": {
			"en-GB": "Banner image"
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
```
