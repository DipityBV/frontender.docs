---
currentMenu: blueprints
---

# Blueprints

Blueprints are small snippets of template instructions in JSON format. Blueprints can be nested by adding them to the container array.

### Syntax
Example of a very basic bilingual blueprint. The `frontender` value will be automatically filled by Frontender when the page is saved.
```JSON
{
    "frontender": null,
    "template": "containers/[content_type]/[container_name]/[container_name].html.twig",
    "name": {
        "en-GB": "Name for Frontender in English",
        "fr-FR": "Name for Frontender in French"
    },
    "description": {
        "en-GB": "Description for Frontender in English",
        "fr-FR": "Description for Frontender in French"
    },
    "template_config": {
        "config": {
            "label": {
                "en-GB": "Tab label for Frontender in English",
                "fr-FR": "Tab label for Frontender in French"
            },
            "controls": {
                "your_variable_name": {
                    "label": {
                        "en-GB": "Field label for Frontender in English",
                        "fr-FR": "Field label for Frontender in French"
                    },
                    "control": "core/text",
                    "value": ""
                }
            }
        }
    },
    "containers": []
}
```

### Assigning content from an API to a blueprint
This is an example of a content tab to retrieve an image from the Unsplash API:
```JSON
{
    "model": {
        "label": {
            "en-GB": "Content"
        },
        "controls": {
            "data": {
    			"value": {
    				"adapter": "Unsplash",
    				"model": "Image\\Search",
    				"id": {
    					"en-GB": "yXmjBxvkoG4"
    				}
    			},
    			"label": {
    				"en-GB": "Image"
    			},
    			"control": "core/abstract",
    			"type": "lookup",
    			"adapters": [
    				{
    					"value": "Unsplash",
    					"label": "Unsplash",
    					"models": [
    						{
    							"value": "Image\\Search",
    							"label": "Image"
    						}
    					]
    				}
    			]
    		}
        }
    }
}
```


## Blueprint snippets

### Default properties
Frontender, name and template are required properties. Page will not work when omitted.
```JSON
{
    "frontender": null,
    "name": {
        "en-GB": ""
    },
    "description": {
        "en-GB": ""
    },
    "template": "",
    "template_config": {}
}
```

### Default tabs
Depending on your environment, content is interchangeable with labels.

**_either_**
```JSON
{
    "model": {
        "label": {
            "en-GB": "Content"
        },
        "controls": {}
    },
    "labels": {
        "label": {
            "en-GB": "Labels"
        },
        "controls": {}
    },
    "config": {
        "label": {
            "en-GB": "Settings"
        },
        "controls": {}
    }
}
```
**_or_**
```JSON
{
    "model": {
        "label": {
            "en-GB": "Content"
        },
        "controls": {}
    },
    "content": {
        "label": {
            "en-GB": "Content"
        },
        "controls": {}
    },
    "config": {
        "label": {
            "en-GB": "Settings"
        },
        "controls": {}
    }
}
```

### Default config controls
<!-- @TODO add default config controls -->
```JSON
???
```

### Model controls
Model configuration for <a href="https://unsplash.com" target="&#95;blank" rel="nofollow">Unsplash</a> used as an example.
```JSON
{
    "model": {
		"label": {
			"en-GB": "Content"
		},
		"controls": {
			"data": {
				"value": {
					"adapter": "Unsplash",
					"model": "Image\\Search",
					"id": {
						"en-GB": "E2btrNkRMMI"
					}
				},
				"label": {
					"en-GB": "Banner image"
				},
				"control": "core/abstract",
				"type": "lookup",
				"adapters": [
					{
						"value": "Unsplash",
						"label": "Unsplash",
						"models": [
							{
								"value": "Image\\Search",
								"label": "Image"
							}
						]
					}
				]
			}
		}
	}
}
```

### Page controls
Basic page configuration contains SEO settings. The user can set SERP values and
control robots data.
```JSON
{
    "page_config": {
		"seo": {
			"label": {
				"en-GB": "SEO"
			},
			"controls": {
				"title": {
					"value": {
						"en-GB": "Page title goes here."
					},
					"label": {
						"en-GB": "Page title"
					},
					"control": "core/text"
				},
				"meta_description": {
					"value": {
						"en-GB": "Meta description information goes here."
					},
					"label": {
						"en-GB": "SERP Description"
					},
					"control": "core/textarea"
				},
				"meta_keywords": {
					"value": {
						"en-GB": "Meta, keywords, are, added, in, here"
					},
					"label": {
						"en-GB": "SERP keywords"
					},
					"control": "core/textarea"
				},
				"meta_robots": {
					"value": "index, follow",
					"label": {
						"en-GB": "Indexing"
					},
					"control": "core/robots"
				}
			}
		}
	}
}
```

### Nested blueprints example
Basic blueprint with a single child container.

```JSON
{
    "frontender": null,
    "template": "containers/[content_type]/[container_name]/[container_name].html.twig",
    "name": {
        "en-GB": "Name for Frontender in English",
        "fr-FR": "Name for Frontender in French"
    },
    "description": {
        "en-GB": "Description for Frontender in English",
        "fr-FR": "Description for Frontender in French"
    },
    "template_config": {
        "config": {
            "label": {
                "en-GB": "Tab label for Frontender in English",
                "fr-FR": "Tab label for Frontender in French"
            },
            "controls": {
                "your_variable_name": {
                    "label": {
                        "en-GB": "Field label for Frontender in English",
                        "fr-FR": "Field label for Frontender in French"
                    },
                    "control": "core/text",
                    "value": {
                        "en-GB": "",
                        "fr-FR": ""
                    }
                }
            }
        }
    },
    "containers": [
        {
            "frontender": null,
            "template": "containers/[content_type]/[blueprint_name]/[container_name]/[container_name].html.twig",
            "name": {
                "en-GB": "Subcontainer",
                "fr-FR": "Subcontainer"
            },
            "description": {
                "en-GB": "Nested blueprints example",
                "fr-FR": "Nested blueprints example"
            },
            "template_config": {
                "config": {
                    "label": {
                        "en-GB": "Subcontainer configuration",
                        "fr-FR": "Subcontainer configuration"
                    },
                    "controls": {
                        "control_name": {
                            "label": {
                                "en-GB": "Description",
                                "fr-FR": "Description"
                            },
                            "control": "core/textarea",
                            "value": {
                                "en-GB": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce consectetur enim ut velit lobortis, eget maximus libero feugiat. Aliquam erat volutpat. Nunc euismod mollis nunc, nec cursus ante. Vivamus laoreet rhoncus justo, et sagittis urna placerat a.",
                                "fr-FR": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce consectetur enim ut velit lobortis, eget maximus libero feugiat. Aliquam erat volutpat. Nunc euismod mollis nunc, nec cursus ante. Vivamus laoreet rhoncus justo, et sagittis urna placerat a."
                            }
                        }
                    }
                }
            },
            "containers": []
        }
    ]
}
```

### Control config example
<!-- @TODO add control config example -->
```JSON
???
```

### Show/Hide list options
True or false selector. User cannot enter a custom value.
```JSON
{
    "options": [
        {
            "value": "1",
            "label": {
                "en-GB": "Show"
            }
        },
        {
            "value": "0",
            "label": {
                "en-GB": "Hide"
            }
        }
    ]
}
```

### List options
A set of answers, user cannot enter a custom value.
```JSON
{
    "colour_theme": {
        "label": {
            "en-GB": "Theme colour"
        },
        "control": "core/list",
        "value": "green",
        "options": [
            {
                "value": "green",
                "label": {
                    "en-GB": "Green"
                }
            },
            {
                "value": "blue",
                "label": {
                    "en-GB": "Blue"
                }
            },
            {
                "value": "lime",
                "label": {
                    "en-GB": "Lime"
                }
            }
        ]
    }
}
```

## Blueprints tips & tricks
1. Try to minimise container nesting
2. Only one model call is allowed per container - so, if you need an image from the media API and an article from the articles API you will need to code two containers (one for each model).
