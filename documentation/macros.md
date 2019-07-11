---
currentMenu: macros
---

# Macros
Macro is a rule or pattern that specifies how a certain input sequence (often a sequence of characters) should be mapped to a replacement output sequence (also often a sequence of characters) according to a defined procedure. The mapping process that instantiates (transforms) a macro use into a specific sequence is known as macro expansion.

Macros are used to make a sequence of computing instructions available to the programmer as a single program statement, making the programming task less tedious and less error-prone. (Thus, they are called "macros" because a "big" block of code can be expanded from a "small" sequence of characters.) Macros often allow positional or keyword parameters that dictate what the conditional assembler program generates and have been used to create entire programs or program suites according to such variables as operating system, platform or other factors. The term derives from "macro instruction", and such expansions were originally used in generating assembly language code.

We would recommended the usage of the following macros, as they are easy to use and they link up with Frontender controls.

### Container class
Process any class variables from the config and return class attribute.
```twig
{% macro class_attribute(config, class) %}
    {% import _self as helper %}
    {% set class = [helper.class_string(config)|trim, class|trim]|join(' ')|trim %}
    {% if class %} class="{{ class }}"{% endif %}
{% endmacro %}
```

### Template macro
The template macro can be found on the [helpers page](/helpers.html).


### Pagination
##### pagination.pages
This will show the first, previous, next, last and all the pages between.
```twig
{{ pagination.pages(articles, articles_total, model) }}
```

##### pagination.browse
This macro will only show a previous and next, also just as mentioned above a layout and target is required.
```twig
{{ pagination.browse(articles, articles_total, model) }}
```

##### pagination.extend
This will only show a "load more" button. This macro however needs a little more configuration, namely a layout( twig file ) it needs to load and a target ( preferably an ID ).

Also it is possible to supply an optional config object for the options that the loaded template will need.

**Note**: This is the only method currently that is able to append to content.  
**Note**: Currently the model_name is a reserved namespace, this functionality will change in the future.
```twig
{{ pagination.extend(articles, articles_total, model, {
    model_name: 'Channel\Articles',
    layout: 'path/to/file.twig',
    target: 'jquery_selector',
    config: {
        labels: {
            next: 'Volgende'
        }
    }
}) }}
```
