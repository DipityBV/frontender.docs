---
currentMenu: faq_controls
---

# Controls

##### What are controls?

<!-- @TODO Add clear definition of 'control'. -->

A special kind of blueprint, only for controls. A control can reference another control.
Frontender comes with a couple of core controls out of the box, these may be used alongside custom project controls. Additional information about controls can be found [here](/controls.html).

##### How do I add controls?

Controls are stored in the MongoDB table `controls`. Frontender delivers a set of core controls, these can be found on the [controls page](/controls.html).  
Custom project controls can be added to this table using the importer.

##### How do I manage my controls?

Controls can be added/adjusted/removed directly from the mongoDB. It's highly recommended to keep the core controls, removing them can result in unexpected issues.

##### Why should I use controls?

Keep your pages <a href="https://en.wikipedia.org/wiki/Don%27t_repeat_yourself" target="&#95;blank" rel="nofollow">DRY</a>. Instead of repeating the same content over and over you can use a control to reduce the size of your page.
