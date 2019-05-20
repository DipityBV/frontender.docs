---
currentMenu: filters
---

## Filters

### Pluralize
```twig
'string'|pluralize
```
```
output: strings
```

### Singularize
```twig
'strings'|singularize
```
```
output: string
```

### Raw
```twig
'<p>strings</p>'|raw
```
```
output: <p>strings</p>
```

### Translate
```twig
{{ {'en-GB': 'Red', 'fr-FR': "Rouge"}|t }}
```
```
output: Red
```
