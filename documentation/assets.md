---
currentMenu: assets
---

# Assets
A catch-all term referring to all materials needed to successfully complete a project. In terms of web design and development, `assets` typically refer to the text content, graphics, photographs, videos, audio files, scripts and styles.

<!-- @TODO Verify -->
Site assets have a fallback to the space’s assets. A template may have its own assets, so the file structure is somewhat loose. The fallback scenario will assume an identical file structure and will look for its files in the space’s file structure in such cases where it does not have its files itself.

### Asset loading snippet
There are two alias method for loading code or other library files.
* [Script loading](#script-loading)
* [Style loading](#style-loading)

##### Script loading
First we will explain the script loading function.
This can handle normal `.js` and `.js.twig` files.

So basically it is possible loading a `.js` file with twig variables.
Below a few examples.
```twig
{{'path_to_js_file'|addScript('position')}}
{{'path_to_js_twig_file'|addScript('position', {
    various: 'config',
    required: 'in',
    twig: 'go',
    in: 'here',
    enabled: true
}) }}
```

The following code should be placed in the template file to load the scripts from above.
It's recommended to use multiple positions, i.e. in the head and before the end of the body.
```twig
{{ renderAssets('position')|raw }}
```

##### Style loading
Just as described with the scripts above, it is also possible to load stylesheets.

Below an example
```twig
{{'path_to_css_file'|addStyle('position')}}
{{'path_to_css_twig_file'|addStyle('position', {
    various: 'config',
    required: 'in',
    twig: 'go',
    in: 'here',
    enabled: true
}) }}
```

### Advanced loading
**Note!** This is advanced stuff, and a lot might/ could go wrong, use with care!  
**Note!** All of the mentioned information is also available in the `addStyle` and `addScript`.

It is also possible to load other kind of files, complete with tag data and attributes.

This function is very verbose. However if the need arises it is very powerful.

```twig
{{'path_to_misc_file'|addAsset('position', {
    attributes: {
    {
        all: 'items',
        in: 'here',
        become: 'tag',
        arguments: true
    },
    config: {
        tag: 'link'
    },
    other: 'config',
    variables: 'here'
}) }}
```

The above example will result in the following:
```html
<link all="items" in="here" become="tag" arguments="1"></link>
```
