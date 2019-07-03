---
currentMenu: adapters
---

## Adapters

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
