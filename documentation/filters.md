---
currentMenu: filters
---

# Filters

A list of basic Twig filters can be found <a href="https://twig.symfony.com/doc/2.x/filters/index.html" target="&#95;blank" rel="nofollow">in the Twig documentation</a>.

The following filters are custom made for Frontender:

### Pluralise
A simple extension that allows you to pluralise a given string.

```twig
'string'|pluralize
```
```
output: strings
```

### Singularise
A simple extension that allows you to singularise a given string.

```twig
'strings'|singularize
```
```
output: string
```

### Translate
Additional information about localisation can be found on the [Templates page](/templates.html#localisation).
Translate a string into a different locale with ```|i18n```, ```|t``` or ```|translate```.
```twig
{{ {'en-GB': 'Red', 'fr-FR': "Rouge"}|i18n }}
```
```twig
{{ {'en-GB': 'Red', 'fr-FR': "Rouge"}|t }}
```
```twig
{{ {'en-GB': 'Red', 'fr-FR': "Rouge"}|translate }}
```
All result in the following output, assuming the English scope is active:
```
output: Red
```
