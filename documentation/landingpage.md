---
currentMenu: landingpage
---

## Landing page
The root page is the default landing page of the entire site. It is accessed by the root URL, e.g. https://your-domain.ext/ The route page is stored in the site configuration settings.
> A root page is also a route page, and may also only be removed or unpublished under certain conditions.


A landing page is a dynamic page with a fixed resource id. It’s function is to be able to expose, for instance, a popular article on its own URL.

A landing page is defined in Frontender Desktop by saving a page with a model configuration including resource id in the top-level container (page definition):
```JSON
{
    "definition": {
        "template": "path/to/template.html.twig",
        "template_config": {
            "model": {
                "controls": {
                    "name": "article",
                    "id": "811cfa64-e6a3-4c79-b115-50e3dc7016c4"
                }
            }
        },
        "containers": []
    }
}
```
Landing page routes are stored in in a routes.json
