---
currentMenu: glossary
---

## Glossary

| Term | Definition |
| --- | --- |
| Adapter | An adapter is the gateway to the content. |
| API | An API enables data access from an external client. |
| Blueprint definition | A JSON object containing the presets from which a container may be generated. |
| Container definition | A JSON object containing instructions to render a template. A container is the visual representation of a blueprint. |
| Control | A JSON object with instructions to render a field. Controls are very specialised, tiny snippets of JSON that Frontender Desktop uses to render its interface. |
| Definition | A JSON object with rendering instructions. |
| Dirty | A changed value or set of values (definition) that have not (yet) been persisted (saved). |
| Extension Package | A collection of files needed for the import of an extension (blueprint, adapter or template). |
| Frontend | The frontend application. |
| Frontender Desktop | Frontender, the Electron desktop application (FED) |
| Frontender Platform | The frontend application, a (collection of) site(s). |
| JSON | JavaScript Object Notation https://www.json.org/ |
| Locale | A language scope, includes time, date and currency in the locale’s format. |
| Lot revisions | A collection of page, collection, blueprint or control definitions that have the same lot id. |
| Modules | A modules is a nested in container. |
| Page definition | Pages are collections of containers. In fact, a page is also a container. This JSON object will also contain a path attribute. |
| Path | A routable path to a page (e.g. "/blog"). |
| Revision | A stored, older version of a container. |
| Route | The path to a resource as displayed in the browser's address bar. |
| Space | A collection of sites and resources. Usually, a Space represents a (paying) client. There is also a global Space (frontendermanager.com?) that is used for smaller clients, comparable to wordpress.com. |
| Template | Templates render the containers in the browser. Templates contain layout and styling instructions. |

## Terms

###### Adapter
An adapter interacts directly with an API. An adapter is an extension package of
- PHP Models, which extend/implement Frontender Platform core adapter models,
- Control blueprints, which are used inside container blueprints and are used to set the model states
Adapters have one or more models, any website can have multiple adapters.

###### Blueprints
Blueprints are (JSON) definitions. These definitions contain instructions for the templates and the adapters.

When blueprints are imported (uploaded into Frontender Platform) any referenced blueprints and/or assets (templates, CSS, JavaScript, media) may also be included in the extension package.

###### Container blueprints
Instructions for a single container.

###### Control blueprints
A special kind of blueprint that contains instructions on how to render a field to edit the attributes (values) of a container.

Controls are only used inside Frontender Desktop and are not included in the page.

###### Frontender Desktop
Frontender Desktop is the Frontend Management System. It is a desktop application (OSX, Windows and Linux) with which webviews are created, edited and managed from a WYSIWYG User Interface.

###### Extensions
Extensions are installable components. Components may be developed by Frontender or 3rd parties.
We distinguish between three types of extensions:
1. Adapters
2. Blueprints
3. Templates

Extensions are considered a space asset. Extensions are managed from the Space Dashboard.
Extensions are available to all sites in a space. We may introduce extension management in a future version of Frontender (Desktop and Platform).

###### Page blueprints
Instructions for a page. Technically, they are identical to a container blueprint definition as a page is in fact also a container. A page blueprint contains a collection of other containers.

###### Templates
Templates are HTML instructions and may include other assets like CSS, JavaScript and Images. Templates are currently Twig files. Templates are stored in the space, but overrides on a site level may be supported in a future version.
