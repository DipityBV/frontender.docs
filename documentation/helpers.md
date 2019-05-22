---
currentMenu: helpers
---

## Helpers


### Template helper

```twig
{# Process any class variables from the config and return a single class string #}
{% macro class_string(config) %}
    {{ [
        config.crown|t ? config.crown|t,
        config.body_class|t ? config.body_class|t,
        config.container_class|t ? config.container_class|t,
        config.divider|t ? config.divider|t,
        config.wings|t ? config.wings|t,
        config.leader|t ? config.leader|t,
        config.leader_inside|t ? config.leader_inside|t,
        config.trailer|t ? config.trailer|t,
        config.trailer_inside|t ? config.trailer_inside|t,
        config.colour_theme|t ? config.colour_theme|t,
        config.colour_background|t ? config.colour_background|t
    ]|join(' ')|trim }}
{% endmacro %}

{# Process any class variables from the config and return class attribute #}
{% macro class_attribute(config, class) %}
    {% import _self as helper %}
    {% set class = [helper.class_string(config)|trim, class|trim]|join(' ')|trim %}
    {% if class %} class="{{ class }}"{% endif %}
{% endmacro %}

{# Alias for class_string, for backward compatibility #}
{% macro class(config) %}
    {% import _self as helper %}
    {{ helper.class_string(config) }}
{% endmacro %}

{# Build container id attribute #}
{% macro container_id_attribute(value, namespace) %}
    {% if value %} data-{{namespace}}="{{ value|raw }}"{% endif %}
{% endmacro %}
```
