# Expanded Search plugin for Craft CMS 3.x

Ported https://github.com/composedcreative/craft-expandedsearch from Craft 2 to Craft 3.
Is is an expansion of Crafts search, which gives you a context for search hits.

![Screenshot](resources/img/plugin-logo.png)

## Requirements

This plugin requires Craft CMS 3.0.0-beta.23 or later.

## Installation

To install the plugin, follow these instructions.

1. Open your terminal and go to your Craft project:

        cd /path/to/project

2. Then tell Composer to load the plugin:

        composer require mustasj/expanded-search

3. In the Control Panel, go to Settings → Plugins and click the “Install” button for Expanded Search.


## Using Expanded Search

The first parameter is the search term. Which will be salted automatically: `*{term}*`
The second is settings.

| Setting | Type | Default |
| ------ | ------ | ------ |
| length | int | 300 |
| Github | array | null (all sections) |

In your search results template


```
{% set expandedResults = craft.expandedSearch.search(query) %}
{% set expandedResults = craft.expandedSearch.search(query, { sections: ['news'], length: 150 }) %}
{% for result in expandedResults %}
    <strong data-field="{{result.matchedField}}">{{result.entry.title}}</strong><br>
    <p>{{result.matchedValue}}</p>
    <a href="{{result.entry.url}}">{{result.entry.url}}</a>
{% else %}
    <p>Sorry, no results for {{query}}.</p>
{% endfor %}
```

## Expanded Search Roadmap

Some things to do, and ideas for potential features:

- [x] ~~Release it~~
- [ ] Add handling for more fields
- [ ] Add proper pagination within the plugin
