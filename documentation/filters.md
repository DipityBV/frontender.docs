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

### Translate
```twig
{{ {'en-GB': 'Red', 'fr-FR': "Rouge"}|i18n }}
```
```twig
{{ {'en-GB': 'Red', 'fr-FR': "Rouge"}|t }}
```
```twig
{{ {'en-GB': 'Red', 'fr-FR': "Rouge"}|translate }}
```
All result in the following output:
```
output: Red
```
