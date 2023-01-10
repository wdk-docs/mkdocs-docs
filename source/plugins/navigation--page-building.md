
## Navigation & page building

### [exclude](https://github.com/apenwarr/mkdocs-exclude)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-exclude">

Lets you exclude arbitrary file paths and patterns from the input. Normally, mkdocs will include every file in the docs directory in the output, which is not always what you want.

- author: [apenwarr](https://github.com/apenwarr)
- links: [GitHub](https://github.com/apenwarr/mkdocs-exclude) \| [Docs](https://github.com/apenwarr/mkdocs-exclude/blob/master/README.md)
- installation: `pip install mkdocs-exclude`

### [select-files](https://github.com/supcik/mkdocs-select-files)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-select-files">

Filters out files (pages) using a parametrized regular expression.

- author: Jacques Supcik [supcik](https://github.com/supcik)
- links: [PyPI](https://pypi.org/project/mkdocs-select-files/) \| [Github](https://github.com/supcik/mkdocs-select-files) \| [Docs](https://github.com/supcik/mkdocs-select-files/blob/master/README.md)
- installation: `pip install mkdocs-select-files`

### [awesome-pages](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-awesome-pages-plugin">

Simplifies configuring page titles and their order. Allows you to customize how your pages show up the navigation of your MkDocs without having to configure the full structure in your `mkdocs.yml`. It gives you detailed control using a small configuration file directly placed in the relevant directory of your documentation.

> **Note:** This plugin works best without a `nav` or `pages` entry in your `mkdocs.yml`. Having a `nav` entry is supported, but you might not get the results you expect, especially if your `nav` structure doesn’t match the file structure.

- author: Lukas Geiter [lukasgeiter](https://github.com/lukasgeiter)
- links: [PyPI](https://pypi.org/project/mkdocs-awesome-pages-plugin/) \| [Github](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin) \| [Docs](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin/blob/master/README.md)
- installation: `pip install mkdocs-awesome-pages-plugin`

### [mkdocs-nav-enhancements](https://pypi.org/project/mkdocs-nav-enhancements/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-nav-enhancements">

Enhances the nav. Supports more types of Markdown titles, including level 1–6 atx-style headers and Setext-style headers. Collapses folders with only one file in, to help keep the nav clean.

- author: Ryan Conway [rylon](https://github.com/rylon/)
- links: [PyPI](https://pypi.org/project/mkdocs-nav-enhancements/)
- installation: `pip install mkdocs-nav-enhancements`

### [navtitles](https://github.com/andyoakley/mkdocs-navtitles)

Ensures that all entries in the site navigation are shown with their best title. By default, if titles are not specified in the configuration yaml, the file name is used in their place which may not always be aesthetically pleasing. The plugin will add some build overhead as it effectively loads all pages twice.

- author: Andy Oakley [andyoakley](https://github.com/andyoakley)
- links: [GitHub](https://github.com/andyoakley/mkdocs-navtitles) \| [Docs](https://github.com/andyoakley/mkdocs-navtitles/blob/master/README.md)
- installation: `pip install git+https://github.com/andyoakley/mkdocs-navtitles`

### [section-index](https://github.com/oprypin/mkdocs-section-index)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-section-index">

Makes nav section headings clickable, leading to a section index page.

<table><tr><th><code>nav:</code> (<i>mkdocs.yml</i>)</th><th>Nav before</th><th>Nav after</th></tr><tr><td>

```yaml
- Borgs:
  - borgs/index.md
  - Foo: borgs/foo.md
  - Bar: borgs/bar.md
```

</td><td>

* Borgs
  * [Index](#)
  * [Foo](#)
  * [Bar](#)

</td><td>

* [Borgs](#)
  * [Foo](#)
  * [Bar](#)

</td></tr></table>

- author: Oleh Prypin [oprypin](https://github.com/oprypin)
- links: [PyPI](https://pypi.org/project/mkdocs-section-index/) | [GitHub](https://github.com/oprypin/mkdocs-section-index) | [Docs](https://oprypin.github.io/mkdocs-section-index/) | [Demo](https://oprypin.github.io/crystal-book/syntax_and_semantics/literals/)
- installation: `pip install mkdocs-section-index`

### [literate-nav](https://github.com/oprypin/mkdocs-literate-nav)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-literate-nav">

Replaces the `nav:` section of the `mkdocs.yml` configuration with a simple Markdown file, or can infer (portions of) it from the documentation's directory structure.  
An alternative to [awesome-pages](#awesome-pages). Assists with migration from [GitBook](https://github.com/GitbookIO/gitbook).
 
- author: Oleh Prypin [oprypin](https://github.com/oprypin)
- links: [PyPI](https://pypi.org/project/mkdocs-literate-nav/) | [GitHub](https://github.com/oprypin/mkdocs-literate-nav) | [Docs](https://oprypin.github.io/mkdocs-literate-nav/)
- installation: `pip install mkdocs-literate-nav`

### [encryptcontent](https://github.com/CoinK0in/mkdocs-encryptcontent-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-encryptcontent-plugin">

Allows you to have password protected articles and pages in MkDocs. The content is encrypted with AES-256 in Python using PyCrypto, and decrypted in the browser with Crypto-JS. It has been tested in Python 2.7 and Python 3.5.

- author: [CoinK0in](https://github.com/CoinK0in)
- links: [GitHub](https://github.com/CoinK0in/mkdocs-encryptcontent-plugin) \| [Docs](https://github.com/CoinK0in/mkdocs-encryptcontent-plugin/blob/master/README.md)
- installation: `pip install mkdocs-encryptcontent-plugin`

### [awesome-list](https://github.com/carlosperate/mkdocs-awesome-list-plugin)

Injects social media cards for each entry in an awesome-list.

- author: Carlos Pereira Atencio [carlosperate](https://github.com/carlosperate)
- links: [Github](https://github.com/carlosperate/mkdocs-awesome-list-plugin) \| [Docs](https://github.com/carlosperate/mkdocs-awesome-list-plugin/blob/master/README.md)
- installation: `pip install git+https://github.com/carlosperate/mkdocs-awesome-list-plugin`

### [toc-sidebar](https://pypi.org/project/mkdocs-toc-sidebar-plugin/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-toc-sidebar-plugin">

Allows users to add additional content to the ToC sidebar using the Material theme.

- author: Zach Hannum [midnightprioriem](https://github.com/midnightprioriem)
- links: [PyPI](https://pypi.org/project/mkdocs-toc-sidebar-plugin/) | [GitHub](https://github.com/midnightprioriem/mkdocs-toc-sidebar-plugin) | [Docs](https://github.com/midnightprioriem/mkdocs-toc-sidebar-plugin/blob/master/README.md)
- installation: `pip install mkdocs-toc-sidebar-plugin`

### [mkdocs-simple-hooks](https://pypi.org/project/mkdocs-simple-hooks/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-simple-hooks">

Define your own hooks for mkdocs, without having to create a new package.

- author: Andrzej Klajnert [aklajnert](https://github.com/aklajnert)
- links: [PyPI](https://pypi.org/project/mkdocs-simple-hooks/) | [GitHub](https://github.com/aklajnert/mkdocs-simple-hooks)
- installation: `pip install mkdocs-simple-hooks`

### [schema-reader](https://pypi.org/project/mkdocs-schema-reader/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-schema-reader">

Converts JSON Schema files into readable documentation.

- author: Tom Robinson [magicaljellybeans](https://github.com/magicaljellybeans)
- links: [PyPI](https://pypi.org/project/mkdocs-schema-reader/) | [Github](https://github.com/magicaljellybeans/mkdocs_schema_reader)
- installation: `pip install mkdocs-schema-reader`

### [pagenav-generator](https://github.com/Andre601/mkdocs-pagenav-generator)

Plugin to quickly create a ToC like list of all pages within a directory, based on the directory's `.pages` file.  
This requires [awesome-pages](#awesome-pages) to work properly.

Just add a `{nav}` where you want the list to show up.

- author: Lukas Geiter [lukasgeiter](https://github.com/lukasgeiter) (Distributed by Andre_601 [Andre601](https://github.com/Andre601)
- links: [GitHub](https://github.com/Andre601/mkdocs-pagenav-generator)
- installation: `pip install git+https://github.com/Andre601/mkdocs-pagenav-generator`

### [mkdocs-categories-plugin](https://github.com/eddyluten/mkdocs-categories-plugin)

This plugin allows you to categorize the pages in your wiki. It allows for multiple categories per page and will generate a category index page with links to each page within the category. The title of your page will be used as the link text. It's easy to configure via the meta section of your pages:

```yaml
---
categories:
    - Novels
    - Fiction
---
```

- author: Eddy Luten [EddyLuten](https://github.com/EddyLuten)
- links: [PyPI](https://pypi.org/project/mkdocs-categories-plugin/) | [Github](https://github.com/EddyLuten/mkdocs-categories-plugin)
- installation: `pip install mkdocs-categories-plugin`
