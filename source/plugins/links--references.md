
## Links & references

### [Autolink References](https://github.com/theskumar/autolink-references-mkdocs-plugin/)

Looks for the presence of a reference to tickets from issues trackers like Jira, Linear, etc and automatically 
convert them to links that point to respective platforms.

- author: Saurabh Kumar [theskumar](https://github.com/theskumar)
- links: [Github](https://github.com/theskumar/autolink-references-mkdocs-plugin/) | [PyPI](https://pypi.org/project/autolink-references-mkdocs-plugin/)
- installation: `pip install autolink-references-mkdocs-plugin`

```yaml
plugins:
   - autolink_references:
        autolinks:
            - reference_prefix: AF-
              target_url: https://linear.com/AF-<num>
            - reference_prefix: PROJ-
              target_url: https://jiracloud.com/PROJ-<num>
```

### [autorefs](https://github.com/mkdocstrings/autorefs)

Automatically link across pages in MkDocs.

Why another "automatic cross linking" plugin?
Because none of the other implementations were meeting our requirements for *mkdocstrings*.
*mkdocs-autorefs* is actually performant (no HTML re-parsing), compatible with other plugins, and provides an easy-to-use syntax.

- authors: @oprypin and @pawamoy
- links: [PyPI](https://pypi.org/project/mkdocs-autorefs) | [GitHub](https://github.com/mkdocstrings/autorefs) | [Docs](https://mkdocstrings.github.io/usage/#cross-references-to-any-markdown-heading)
- installation: `pip install mkdocs-autorefs`

### [ezlinks](https://github.com/orbikm/mkdocs-ezlinks-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-ezlinks-plugin"></img>

Plugin for mkdocs which enables easier linking between pages.

This plugin was written in order to provide an up-to-date and
feature complete plugin for easily referencing documents
with a variety of features:

```
- File name linking (e.g. `[Text](file)`)
- Absolute paths (e.g. `[Text](/link/to/file.md)`)
- WikiLinks support (e.g. `[[Link]]`)
```

- author: Mick Orbik [orbikm](https://github.com/orbikm)
- links: [Github](https://github.com/orbikm/mkdocs-ezlinks-plugin)
- installation: `pip install mkdocs-ezlinks-plugin`

### [unused-files](https://github.com/wilhelmer/mkdocs-unused-files)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-unused-files">

Find unused (orphaned) files in your project.

This is useful, e.g., if your project contains a lot of image files and you lost track which images are still in use.

A file is considered "used" when it is referenced in at least one Markdown file of your project, either as an image or as a hyperlink reference.

- author: [wilhelmer](https://github.com/wilhelmer)
- links: [PyPI](https://pypi.org/project/mkdocs-unused-files/) \| [GitHub](https://github.com/wilhelmer/mkdocs-unused-files) \| [Docs](https://github.com/wilhelmer/mkdocs-unused-files/blob/master/README.md)
- installation: `pip install mkdocs-unused-files`

### [gitlab](https://gitlab.inria.fr/vidjil/mkdocs-gitlab-plugin/) 

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-gitlab-plugin">

Transform handles such as `#1234`, `%56`, `!789`, `&12` or `$34` into links to a gitlab repository,
given by the `gitlab_url` configuration option.

- author: [Mathieu Giraud](http://cnrs.magiraud.org/)
- links: [PyPI](https://pypi.org/project/mkdocs-gitlab-plugin) | [Gitlab](https://gitlab.inria.fr/vidjil/mkdocs-gitlab-plugin) 
- installation: `pip install mkdocs-gitlab-plugin`


### [autoreflinks](https://github.com/pauloue/mkdocs-autoreflinks-plugin)

Automatically links heading references in the form `[My heading]`, similar to Pandoc’s `implicit_header_references` [extension](https://pandoc.org/MANUAL.html#extension-implicit_header_references).

- author: Paul Ouellette [pauloue](https://github.com/pauloue)
- links: [Github](https://github.com/pauloue/mkdocs-autoreflinks-plugin)
- installation: `pip install git+https://github.com/pauloue/mkdocs-autoreflinks-plugin`

### [autolinks](https://github.com/midnightprioriem/mkdocs-autolinks-plugin/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-autolinks-plugin">

Simplifies relative linking between documents. Allows you to link to pages and images within your MkDocs site without providing the entire relative path to the file in your document structure.

- author: Zach Hannum [midnightprioriem](https://github.com/midnightprioriem)
- links: [Github](https://github.com/midnightprioriem/mkdocs-autolinks-plugin) | [Docs](https://github.com/midnightprioriem/mkdocs-autolinks-plugin/blob/master/README.md)
- installation: `pip install mkdocs-autolinks-plugin`

### [roamlinks](https://github.com/Jackiexiao/mkdocs-roamlinks-plugin) 

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-roamlinks-plugin">

Inherit from autolinks, support `[[mdfile]]` -> `[mdfile](path-to-file)`, also implicit heading `[[#A Title]]` -> `[#A Title](#a-title)`

- author: jackiexiao [jackiexiao](https://github.com/Jackiexiao/)
- links: [PyPI](https://pypi.org/project/mkdocs-roamlinks-plugin/) | [Github](https://github.com/Jackiexiao/mkdocs-roamlinks-plugin) | [Docs](https://github.com/Jackiexiao/mkdocs-roamlinks-plugin)
- installation: `pip install mkdocs-roamlinks-plugin`

### [abs-to-rel](https://github.com/sander76/mkdocs-abs-rel-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-abs-rel-plugin">

Mkdocs absolute to relative link converter. Mkdocs officially only supports relative links. While this makes sense there are situation where it is useful to make use of absolute links. For example when creating a document with absolute links to an image folder. If that file is to be moved later on, links are kept intact.

- author: Sander [sander76](https://github.com/sander76)
- links: [Github](https://github.com/sander76/mkdocs-abs-rel-plugin) \| [Docs](https://github.com/sander76/mkdocs-abs-rel-plugin/blob/master/readme.md)
- installation: `pip install mkdocs-abs-rel-plugin`

### [webcontext](https://github.com/Darrelk/mkdocs-webcontext-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-webcontext-plugin">

Converting absolute image/link paths to webcontext aware paths. Use when you are not going to upload your MkDocs to the site root but rather a sub folder on an existing site. You will then be able to use the same absolute path (staring with "/") for development and after deploy.
Examples of site urls before and after using the webcontext plugin:
| Site Url               | Context | Image before     | Image after          |
| ---------------------- | ------- | ---------------- | -------------------- |
| http://example.com/foo | /foo    | /images/img1.jpg | /foo/images/img1.jpg |

- author: Darrel Kleynhans [Darrelk](https://github.com/Darrelk)
- links: [PyPI](https://pypi.org/project/mkdocs-webcontext-plugin/) | [Github](https://github.com/Darrelk/mkdocs-webcontext-plugin) | [Docs](https://github.com/Darrelk/mkdocs-webcontext-plugin)
- installation: `pip install mkdocs_webcontext_plugin`

### [emailprotect](https://github.com/rkoe/mkdocs-emailprotect)

Obscures email addresses from address-harvesting spam bots.

- author: Roland Freikamp [rkoe](https://github.com/rkoe)
- links [Github](https://github.com/rkoe/mkdocs-emailprotect) \| [Docs](https://github.com/rkoe/mkdocs-emailprotect/blob/master/README.md)
- installation: `pip install git+https://github.com/rkoe/mkdocs-emailprotect`

### [linkpatcher-plugin](https://github.com/sekikawattt/mkdocs-linkpatcher-plugin)

Extends the Markdown syntax by providing an alternative `:` header prefix, and provides special autolinking functionality for such headers.

- author: [sekikawattt](https://github.com/sekikawattt)
- links: [Github](https://github.com/sekikawattt/mkdocs-linkpatcher-plugin) \| [Docs](https://github.com/sekikawattt/mkdocs-linkpatcher-plugin/blob/master/README.md)
- installation: `pip install git+https://github.com/sekikawattt/mkdocs-linkpatcher-plugin`

### [redirects](https://pypi.org/project/mkdocs-redirects/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-redirects">

Makes it easy to create dynamic page redirects, so you can move docs around and prevent broken links. Instead of using the meta “redirect:” support (which requires you to have extraneous Markdown files cluttering up your docs folder), this plugin dynamically generates the meta redirect HTML pages in the site_dir based on configuration in mkdocs.yml mapping old paths to new page locations.

- author: [datarobot](https://github.com/datarobot)
- links: [Pypi](https://pypi.org/project/mkdocs-redirects/) \| [Github](https://github.com/datarobot/mkdocs-redirects) \| [Docs](https://github.com/datarobot/mkdocs-redirects/blob/master/README.md)
- installation: `pip install mkdocs-redirects`

### [htmlproofer](https://github.com/manuzhang/mkdocs-htmlproofer-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-htmlproofer-plugin">

Validates URLs in rendered HTML files.

- author: Manu Zhang [manuzhang](https://github.com/manuzhang)
- links: [Pypi](https://pypi.org/project/mkdocs-htmlproofer-plugin/) \| [Github](https://github.com/manuzhang/mkdocs-htmlproofer-plugin) \| [Docs](https://github.com/manuzhang/mkdocs-htmlproofer-plugin/blob/master/README.md)
- installation: `pip install mkdocs-htmlproofer-plugin`

### [tooltipster-links](https://pypi.org/project/mkdocs-tooltipster-links-plugin/)

**Not functional with current release of Mkdocs**

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-tooltipster-links-plugin">

Adds tooltips to preview the content of page links using tooltipster.

- author: Zach Hannum [midnightprioriem](https://github.com/midnightprioriem)
- links: [Pypi](https://pypi.org/project/mkdocs-tooltipster-links-plugin/) | [Github](https://github.com/midnightprioriem/mkdocs-tooltipster-links-plugin) | [Docs](https://github.com/midnightprioriem/mkdocs-tooltipster-links-plugin/blob/master/README.md)
- installation: `pip install mkdocs-tooltipster-links-plugin`

### [alternate-link](https://github.com/cmitu/mkdocs-altlink-plugin)

Simplifies internal links. Very simple mkdocs plugin using [John Gruber's relative path link](https://daringfireball.net/projects/markdown/syntax#link) as an alternate syntax for internal links, removing the need to add the .md suffix for the target page.

- author: Cristi Mitrana [cmitu](https://github.com/cmitu)
- links: [Github](https://github.com/cmitu/mkdocs-altlink-plugin) | [Docs](https://github.com/cmitu/mkdocs-altlink-plugin/blob/master/README.md)
- installation: `pip install git+https://github.com/cmitu/mkdocs-altlink-plugin/`

### [mkdocs-alias-plugin](https://github.com/eddyluten/mkdocs-alias-plugin)

Allows linking to your pages using a custom alias, such as `[[my-alias]]`. The syntax of the alias is reminiscent of MediaWiki links, while aliases themselves are defined in the meta section of the Markdown document. This allows for a decoupling of the wiki page from the file system in case you make frequent changes to filenames or your directory structure without having to fix broken links.

- author: Eddy Luten [EddyLuten](https://github.com/EddyLuten)
- links: [PyPI](https://pypi.org/project/mkdocs-alias-plugin/) | [Github](https://github.com/eddyluten/mkdocs-alias-plugin)
- installation: `pip install mkdocs-alias-plugin`
