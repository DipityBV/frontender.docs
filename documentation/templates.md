---
currentMenu: templates
---

## Templates

### Hiding functionality in Frontender

In some cases it is required to disable certain functionality in the site, that isn't required in Frontender. (eg: cookie policy notice)

Inside of every twig file a query is available, this allows you to check what is in the query.
When a page is called by Frontender, it will send a query variable called ```fromFrontender```, when this variable is set you can hide functionality that you don't want to show in Frontender.

Below is an example, in which we hide Google Analytics from Frontender.
```twig
{% if not query.fromFrontender %}
    window.addEventListener("load", function(){

        (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
        (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
        m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
        })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

        ga('create', 'UA-XXXXXXXX-1', 'auto');
        ga('send', 'pageview');
    });
{% endif %}
```

### Localisation
Localisation is done through translation files written in YAML. These files are located in the ```project/translations``` folder.


### Internationalisation (i18n) and localisation (l10n)
We need to keep in mind the different versions of a language, and the support for them in either routes or domains. These are all legitimate examples:
```
domain.ext/en/english_content
en.domain.ext/english_content
domain.uk/english_content
domain.au/australian_english_content
domain.ext/en/gb/british_english_content
domain.ext/en/us/american_english_content
domain.ext/en/au/australian_english_content
en.domain.ext/us/american_english_content
au.en.domain.ext/australian_english_content
us.domain.ext/american_english_content
```

A solid and flexible  implementation is yet to be found. Currently, we use ```"en"``` to indicate English locale, however this will not hold up when multiple variations of language (e.g. ```"en-GB"```, ```"en-AU"``` and ```"en-US"```) are used in a single site.

A possible solution is to use the full locale ISO (```"en-GB"```) and then have rules on how to parse these to a route. We could also assume that each part of the ISO is a path component, so ```"en"``` would parse as ```en/``` and ```"en-GB"``` would parse as ```en/gb/```.

This is a suggestion on how to define a language/domain combination (totally arbitrary examples):
```JSON
{
    "nl-NL": "brickson.nl",
    "nl-BE": "brickson.be",
    "en-EN": "en.brickson.nl",
    "en-US": "brickson.nl/en/us",
    "en-AU": "en.brickson.nl/au"
}
```
