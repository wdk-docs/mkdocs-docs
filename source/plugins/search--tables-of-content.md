
## Search & tables of content

### [search](https://www.mkdocs.org/user-guide/configuration/#plugins)

Built-in MkDocs search plugin.

### [fastsearch](https://github.com/andyoakley/mkdocs-fastsearch)

Fork of the built-in search plugin that excludes code blocks and tables, which becomes necessary when hosting notebooks and other large content.

- author: Andy Oakley [andyoakley](https://github.com/andyoakley)
- links: [GitHub](https://github.com/andyoakley/mkdocs-fastsearch) \| [Docs](https://github.com/andyoakley/mkdocs-fastsearch/blob/master/README.md)
- installation: `pip install git+https://github.com/andyoakley/mkdocs-fastsearch`

### [localsearch](https://github.com/wilhelmer/mkdocs-localsearch)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-localsearch">

A MkDocs plugin to replace the native “search” plugin with a search plugin that also works locally (file:// protocol). This plugin currently only works with the Material for MkDocs theme.

- author: [wilhelmer](https://github.com/wilhelmer)
- links: [PyPI](https://pypi.org/project/mkdocs-localsearch/) \| [GitHub](https://github.com/wilhelmer/mkdocs-localsearch) \| [Docs](https://github.com/wilhelmer/mkdocs-localsearch/blob/master/README.md)
- installation `pip install mkdocs-localsearch`


### [exclude-search](https://github.com/chrieke/mkdocs-exclude-search)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-exclude-search">

Lets you exclude selected files or sections from the search index, results will not show up in the search.

- author: [chrieke](https://github.com/chrieke)
- links: [GitHub](https://github.com/chrieke/mkdocs-exclude-search) \| [PyPI](https://pypi.org/project/mkdocs-exclude-search/)
- installation: `pip install mkdocs-exclude-search`

### [tags](https://github.com/jldiaz/mkdocs-plugin-tags)

Support for tags in the yaml-metadata in the header of markdown files. Extracts this metadata and creates a “Tags” page which lists all tags and all pages for each tag. The metadata has to be enclosed in `---` lines, and must include a `title:` property (otherwise the page will appear as “untitled” in the tags page).

```markdown
---
title: Welcome
tags:
  - testing
  - unimportant
---

# Welcome to MkDocs
```

- author: [jldiaz](https://github.com/jldiaz)
- links: [Github](https://github.com/jldiaz/mkdocs-plugin-tags) \| [Docs](https://github.com/jldiaz/mkdocs-plugin-tags/blob/master/README.md)
- installation: `pip install git+https://github.com/jldiaz/mkdocs-plugin-tags`

### [mdoctag](https://github.com/srymh/MkdocsTagPlugin)

This plugin just make a json file that contains meta data “tags”. To display aggregation of tag, you need to make pages referencing the json file.

- author: [srymh](https://github.com/srymh)
- links: [Github](https://github.com/srymh/MkdocsTagPlugin) \| [Docs](https://github.com/srymh/MkdocsTagPlugin/blob/master/README.md) \| [Demo](https://srymh.github.io/mdoctag-demo/)
- installation: `pip install git+https://github.com/srymh/MkdocsTagPlugin`

### [autotag](https://github.com/six-two/mkdocs-auto-tag-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-auto-tag-plugin">

Automatically add tags to certain pages based on their path or filename.
You will still need to use another tag plugin (such as `mkdocs-material`) for actually managing/displaying the tags.

- author: [six-two](https://github.com/six-two)
- links: [PyPI](https://pypi.org/project/mkdocs-auto-tag-plugin/) | [Github](https://github.com/six-two/mkdocs-auto-tag-plugin) | [Docs](https://mkdocs-auto-tag-plugin.six-two.dev/)
- installation: `pip install mkdocs-auto-tag-plugin`

### [Search](https://squidfunk.github.io/mkdocs-material/setup/setting-up-site-search/) (for [mkdocs-material](https://squidfunk.github.io/mkdocs-material/))

Material for MkDocs provides its own search plugin, which provides [rich search previews](https://squidfunk.github.io/mkdocs-material/setup/setting-up-site-search/#rich-search-previews) (rendering text and code blocks in search), advanced [separator support with lookahead](https://squidfunk.github.io/mkdocs-material/setup/setting-up-site-search/#tokenizer-lookahead) and allows for the [exclusion of whole pages, sections, and blocks](https://squidfunk.github.io/mkdocs-material/setup/setting-up-site-search/#search-exclusion).

- author: [squidfunk](https://github.com/squidfunk)
- links: [GitHub](https://github.com/squidfunk/mkdocs-material)
- installation: see [documentation](https://squidfunk.github.io/mkdocs-material/setup/setting-up-site-search/)

### [Tags](https://squidfunk.github.io/mkdocs-material/setup/setting-up-tags/) (for [mkdocs-material](https://squidfunk.github.io/mkdocs-material))

Material for MkDocs adds first-class support for categorizing pages with tags, which adds the possibility to group related pages and make them discoverable via search and a dedicated tags index. If your documentation is large, tags can help to discover relevant information faster.

- author: [squidfunk](https://github.com/squidfunk)
- links: [GitHub](https://github.com/squidfunk/mkdocs-material)
- installation: see [documentation](https://squidfunk.github.io/mkdocs-material/setup/setting-up-tags/)
