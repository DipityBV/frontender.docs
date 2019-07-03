---
currentMenu: introduction
---

## Introduction
Content, design and technology are the cornerstones of online publishing. A successful combination of each of these results in a better user experience, which leads to happier visitors and higher conversions. And yet, the way in which we publish content to the web is compromised by one of those very cornerstones – technology.

For years now, we use content management systems to produce content. We construct web pages from that content by injecting it into templates that can be published by the CMS. While that process is simple and offers many benefits, it also introduces many disadvantages.
Developing templates is different for each of those systems, and most of them have highly opinionated ideas about structure, composition and technology making templates and content tightly integrated within those systems. Content and presentation sit tightly integrated within the CMS, impairing re-use of both content as well as presentation.

Frontender changes that. With Frontender you publish your content how, where and when you want. On any device, in any format, and in any language. From any source and to as many websites or applications as you need. Using your favourite front-end technology stack and your favourite CMS.

## The Frontender Ecosystem
Frontender is a collection of systems that in combination are referred to as Frontender. In reality Frontender Desktop (FED), Frontender Platform (FEP) and Frontender Manager (FEM) are the individual components in the ecosystem.

![](https://lh6.googleusercontent.com/tKsC09ZJSapku1TOeyrm4AnHkJZq1fO6UUsl2Ynr5wsJwqFTx1rmcurFpcNxf1V_JOFeQdHCryJntrOmNrzFHU2jgAOZqcHnRiYxpjnI2mdq9_ObXNPGxH7Kdh7cytXWxg)

## Frontender Desktop
Frontender Desktop is the Frontend Management System. It is a desktop application (OSX, Windows and Linux) with which webviews are created, edited and managed from a WYSIWYG User Interface.

Frontender Desktop ‘talks’ to Frontender Platform and Frontender Manager.

## Frontender Platform
Frontender Platform is the physical environment where your websites ‘live’. Its consists of a the core software and an instance for each website that is managed via that particular core – or also referred to as ‘Space’.

The space consists of core code and a databases. The core database holds all the Space resources like adapters, controls and blueprints. The space may also contain templates or any other shared assets, which may be overridden from each site using a ‘fallback strategy’.

The site consists of site specific code like templates, scripts and styling. It also has a database that stores page definitions.

Frontender Platform is a secluded environment and only Frontender Desktop and Frontender Manager have access to it. Frontender Platform has no access to Frontender Manager or Frontender Desktop but it does have an API that can expose information and functionality, but only Frontender Manager and Frontender Desktop are authorised to access the API.

## Frontender Manager
Frontender Manager is an web application that functions as the control center. It manages all information regarding user-space-site access. Frontender Desktop authenticates users via the Frontender Manager. When the user is successfully logged in, Frontender Manager will serve him all spaces and sites that the user is authorised to manage. Frontender Manager is responsible for access control in Frontender Desktop (not in Frontender Platform!).

Frontender Manager will store the bare minimum data that is required for Frontender Desktop to function. This includes information about the physical location of a Space (via it’s IP) and the roles and permissions for each user and per site.

It is important to note that when Frontender Manager is offline, it has no implications to Frontender Platform, all sites will continue to function. However, Frontender Desktop will only (partly?) function while it has an active session. So when a user is not logged in to Frontender Desktop, a site’s pages can not be managed until such time Frontender Manager is back online. Again: all sites will still be accessible for visitors.

Frontender Manager has access to Frontender Desktop and Frontender Platform.
