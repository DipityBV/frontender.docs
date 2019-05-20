---
currentMenu: templates
---

## Templates

### Hiding functionality in Frontender

In some cases it is required to disable certain functionality in the site, that isn't required in Frontender. (eg: cookie policy notice)

Inside of every twig file a query is available, this allows you to check what is in the query.
When a page is called by Frontender, it will send a query variable called ```fromFrontender```, when this variable is set you can hide functionality that you don't want to show in frontender.

Below is an example, in which we hide Google Analytics from frontender.
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

### Localization
Localization is done through translation files written in yaml. These files are located in the ```project/translations``` folder.
