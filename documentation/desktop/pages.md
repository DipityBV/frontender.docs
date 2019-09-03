---
currentMenu: desktop_pages
---

# Pages
![Pages overview](https://getfrontender.com/assets/images/product-shots/F-PagesList.png)

There are a couple types of pages:
* [Draft](#draft)
* [Unpublished](#unpublished)
* [Published](#published)
* [Revision](#revision)

#### Draft
A non-persisted version of a page. The draft is the working copy of a page. A draft is persisted in some kind of memory storage and is destroyed when:
- The user navigates away without saving
- The application is closed without saving
- The drafted page is removed

Drafts are not accessible outside the user’s installation of Frontender. A draft is not accessible by the front-end and can not be previewed in a browser.

If you want to preview a draft in the browser, it has to be saved first in order to create a revision of it.

Opening a (public) revision with Frontender Desktop will generate a draft.

#### Unpublished
Page is only visible in the Frontender application, it has not yet been published to the public. The page may be previewed in the browser, the link can be shared between users.  
The temporary page will not be indexed and will not be visible to front-end users, unless they have access to the uuid of the page.

#### Published
The page is visible on the front-end. Users may visit this page using their web browser.  
The page will be, if correctly configured, indexed.

#### Revision
A revision is not visible in the pages overview. Select a single page and use the `Revisions` button at the top of your application.  
A version of a page, defined by a date and time. It is stored in the Pages Collection (see: Collections). A revision is a complete page definition that can be loaded and previewed in Frontender Desktop and Frontender Platform (using its uuid). A revision is not publicly accessible to the front-end and will not be indexed.

### Page config
The page configuration menu contains several settings.
* Name *
* Description
* Team *
* Route **

_Settings marked with `*` are required._  
_Settings marked with `**` are required when publishing._
