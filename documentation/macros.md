---
currentMenu: macros
---

## Macros


### Container class
Process any class variables from the config and return class attribute
```twig
{% macro class_attribute(config, class) %}
    {% import _self as helper %}
    {% set class = [helper.class_string(config)|trim, class|trim]|join(' ')|trim %}
    {% if class %} class="{{ class }}"{% endif %}
{% endmacro %}
```
