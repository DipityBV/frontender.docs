---
currentMenu: controls
---

## Controls

For frontender there are some extentions for the controls.

## Repeatable controls
Controls can be extended with an option to make them repeatable.
This will add a menu next to the item that allows repetition.

To allow for this functionality add the following line to your control object.
```json
"repeatable": true,
"minimal": 3 // This is optional, but ensures that you can only delete repetitions when it exceeds this number.
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
    "minimal": 2
}
```

## Compound control
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

## Current controls
Here is a list of controls that can be used:

| Control | Result
| - | - |
| core/boolean | Select list with "Yes" and "No", default selected is "No" |
| core/hidden | Hidden input field (not rendered in frontender) |
| core/markdown | Markdown textarea |
| core/number | Number input field |
| core/url | URL field |
| core/route | Route field |
| core/list | Select list with custom options |
| core/textarea | Normal textarea |
| core/json | JSON textarea |
| core/abstract | @TODO |
| core/text | Text input field |
| core/robots | Robots text field |
