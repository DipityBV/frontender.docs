---
currentMenu: helpers
---

# Helpers

### Template helper
Process any class variables from the config and return a single class string
```twig
{% macro class_string(config) %}
    {{ [
        config.body_class ? config.body_class,
        config.container_class ? config.container_class,
        config.divider ? config.divider,
        config.colour_theme ? config.colour_theme,
        config.colour_background ? config.colour_background
    ]|join(' ')|trim }}
{% endmacro %}
```

Process any class variables from the config and return class attribute
```twig
{% macro class_attribute(config, class) %}
    {% import _self as helper %}
    {% set class = [helper.class_string(config)|trim, class|trim]|join(' ')|trim %}
    {% if class %} class="{{ class }}"{% endif %}
{% endmacro %}
```

Alias for class_string, for backward compatibility
```twig
{% macro class(config) %}
    {% import _self as helper %}
    {{ helper.class_string(config) }}
{% endmacro %}
```


Build container id attribute
```twig
{% macro container_id_attribute(value, namespace) %}
    {% if value %} data-{{namespace}}="{{ value|raw }}"{% endif %}
{% endmacro %}
```
