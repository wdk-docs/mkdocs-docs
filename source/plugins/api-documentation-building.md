
## API documentation building

### [automacdoc](https://github.com/AlexandreKempf/automacdoc/)

Automatically generates API docs from your Python 3 project.

- author: Alexandre Kempf [AlexandreKempf](https://github.com/AlexandreKempf)
- links: [Github](https://github.com/AlexandreKempf/automacdoc/) \| [Docs](https://github.com/AlexandreKempf/automacdoc/blob/master/README.md)
- installation: `pip install git+https://github.com/AlexandreKempf/automacdoc/`

### [mkdocstrings](https://github.com/pawamoy/mkdocstrings)

Automatic documentation from sources, for MkDocs.

- Features
  - **Language agnostic:** `mkdocstrings` is written in Python but is language-agnostic. It means you can use it for any language, as long as you implement a [`handler`](https://mkdocstrings.github.io/handlers/overview/) for it. Currently, we have a [Python handler](https://mkdocstrings.github.io/handlers/python/) and a [Crystal handler](https://mkdocstrings.github.io/crystal/).
  - **Multiple themes support:** each handler can offer multiple themes. Currently, we support the [Material theme](https://squidfunk.github.io/mkdocs-material/) and offer basic support for the `mkdocs` and `readthedocs` themes.
  - **Cross-references to other objects:** `mkdocstrings` makes it possible to reference other headings from your Markdown files with the classic Markdown syntax: `[identifier][]` or `[title][identifier]`. See [autorefs](#autorefs).
  - **Inline injection in Markdown:** instead of generating Markdown files, `mkdocstrings` allows you to inject documentation anywhere in your Markdown contents. The syntax is simple: `::: identifier` followed by a 4-spaces indented YAML configuration block.
  - **...and more!**
- author: Timothée Mazzucotelli [pawamoy](https://github.com/pawamoy)
- links: [Pypi](https://pypi.org/project/mkdocstrings/) \| [Github](https://github.com/pawamoy/mkdocstrings) \| [Docs](https://pawamoy.github.io/mkdocstrings)
- installation: `pip install mkdocstrings`

### [MkAutoDoc](https://github.com/tomchristie/mkautodoc)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkautodoc">

A Markdown extension which adds autodoc style support, for use with MkDocs.

- author: Tom Christie [tomchristie](https://github.com/tomchristie)
- links: [PyPI](https://pypi.org/project/mkautodoc/) \ [GitHub](https://github.com/tomchristie/mkautodoc)
- installation: `pip install mkautodoc`

### [doxygen](https://github.com/pieterdavid/mkdocs-doxygen-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-doxygen-plugin">

Allows to generate Doxygen documentation as part of the build process.
Doxygen is run (post-build) for each entry in the `packages` configuration entry
(a list of mappings) and the html output moved to a subdirectory of `site_dir`,
with the same name as the entry’s key.

- author: Pieter David [pieterdavid](https://github.com/pieterdavid)
- links: [Github](https://github.com/pieterdavid/mkdocs-doxygen-plugin) \| [Docs](https://github.com/pieterdavid/mkdocs-doxygen-plugin/blob/master/README.md)
- installation: `pip install git+https://github.com/pieterdavid/mkdocs-doxygen-plugin`

### [dodoc](https://github.com/plasmatech8/Python-Mkdocs-Autodoc-Plugin)

An low-effort attempt to create autodocumentation of class and function definitions/docstrings.

- author: Mark Connelly [plasmatech8](https://github.com/plasmatech8)
- links: [Github](https://github.com/plasmatech8/Python-Mkdocs-Autodoc-Plugin) \| [Docs](https://github.com/plasmatech8/Python-Mkdocs-Autodoc-Plugin/blob/master/README.md)
- installation: `pip install git+https://github.com/plasmatech8/Python-Mkdocs-Autodoc-Plugin`

### [inari](https://github.com/tkamenoko/inari)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/inari">

Write docstrings in Markdown.

- author: T.Kameyama [tkamenoko](https://github.com/tkamenoko/)
- links: [Pypi](https://pypi.org/project/inari/) \| [Github](https://github.com/tkamenoko/inari) \| [Docs](https://tkamenoko.github.io/inari/)
- installation: `pip install inari`

### [mktheapidocs](https://pypi.org/project/mktheapidocs/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mktheapidocs">

Generate markdown API documentation from Numpydoc docstrings.

- author: Jonathan Gray [greenape](https://github.com/greenape)
- links: [Pypi](https://pypi.org/project/mktheapidocs/) \| [Github](https://github.com/greenape/mktheapidocs) \| [Docs](https://github.com/greenape/mktheapidocs/blob/master/README.md)
- installation: `pip install mktheapidocs`

### [MkApi](https://github.com/daizutabi/mkapi/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkapi">

Generate API documentation from Markdown docstrings. MkApi supports two styles of docstrings: [Google](http://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings) and [NumPy](https://numpydoc.readthedocs.io/en/latest/format.html#docstring-standard). 

- Features of MkApi are:

  * **Section syntax**: Supported sections are `Args`, `Arguments`, `Attributes`, `Example[s]`, `Note[s]`, `Parameters`, `Raises`, `Returns`, `References`, `Todo`, `Warning[s]`, `Warns`, and `Yields`.
  * **Type annotation**: If you write your function such as `def func(x: int) -> str:`, you don't need write type(s) in `Args`, `Parameters`, `Returns`, or `Yields` section again. You can overwrite the type annotation in the corresponding docstring.
  * **Object type inspection**: MkApi plugin creates `CLASS`, `DATACLASS`, `FUNCTION`, `GENERATOR`, or `METHOD` prefix for each object.
  * **Attribute inspection**: If you write attributes with description as comment in `__init__()`, Attributes section is automatically created.
  * **Docstring inheritance**: Docstring of a subclass can inherit parameters and attributes description from its superclasses.
  * **Page mode**: Comprehensive API documentation for your project, in which objects are linked to each other by type annotation.

- author: Daizu [daizutabi](https://github.com/daizutabi)
- links: [PyPI](https://pypi.org/project/mkapi/) \| [Github](https://github.com/daizutabi/mkapi/) \| [Docs](https://mkapi.daizutabi.net/)
- installation: `pip install mkapi`
