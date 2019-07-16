---
currentMenu: templates
---

# Templates
Templates are HTML instructions and may include other assets like CSS, JavaScript and Images. Templates are currently Twig files. Templates are stored in the space, but overrides on a site level may be supported in a future version.

### Template structure
All _templates_ (Twig files), _blueprints_ (JSON files) and pages are located in folders in `/source/projects/main/templates`.

Templates and blueprints are stored in subfolders that indicate their content types or their intended use.  
For example, Twig files intended to be used with Event content are stored inside a `/templates/containers/events` folder.  
Each template needs to have an data-frontender attribute declared on it:
```twig
{{ helper.container_id_attribute(container, 'frontender')|raw }}
```
Frontender will use this if to identify a container and its configuration.

### Hiding functionality in Frontender

In some cases it is required to disable certain functionality in the site, that isn't required in Frontender. (eg: cookie policy notice)

Inside of every twig file a query is available, this allows you to check what is in the request.
When a page is called by Frontender, it will send a query variable called ```fromFrontender```, using this variable you can hide functionality that you don't want to show in Frontender.

In the following example we make sure the Google analytics code is not used inside of the Frontender application.
The code will run if the page is previewed in the browser.
```twig
{% if not query.fromFrontender %}
    /*
     * Google Analytics is of no use inside of the Frontender application.
     * Prevent the script from loading.
     */
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
Localisation is done through translation files written in YAML. These files are generally located in the ```project/translations``` folder.


### Internationalisation(i18n) and localisation(l10n)
We need to keep in mind the different versions of a language and the support for them in either routes or domains. These are all potential possibilities:

| Domain | Language |
| - | :-: |
| domain.com/en/ | English content |
| domain.co.uk | English content |
| domain.au | Australian English content |
| domain.com/en/gb/ | British English content |
| domain.com/en/us/ | American English content |
| domain.com/en/au/ | Australian English content |
| en.domain.com | English content |
| en.domain.com/us/ | American English content |
| au.en.domain.com | Australian English content |
| us.domain.com | American English content |

A solution is to use the full locale ISO (`"en-GB"`) and then have rules on how to parse these to a route. We could also assume that each part of the ISO is a path component, so `"en"` would parse as `en/` and `"en-GB"` would parse as `en/gb/`.

This is a suggestion on how to define a language/domain combination (totally arbitrary examples):
```JSON
{
    "nl-NL": "getfrontender.com",
    "nl-BE": "getfrontender.be",
    "en-EN": "en.getfrontender.com",
    "en-US": "getfrontender.com/en/us",
    "en-AU": "en.getfrontender.com/au"
}
```
