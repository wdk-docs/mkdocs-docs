
## Code execution, variables & templating

### [pheasant](https://pypi.org/project/pheasant/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/pheasant">

Auto Python code execution and insertion to the original Markdown source. Any Python codes in a fenced code block of original Markdown source are executed. This process is performed by a Jupyter client. In addition to this code execution, Pheasant can automatically number headers, figures, tables, etc. See the Pheasant official site at [Pheasant Home](https://pheasant.daizutabi.net/)

- author: [daizutabi](https://github.com/daizutabi)
- links: [Pypi](https://pypi.org/project/pheasant/) \| [Github](https://github.com/daizutabi/pheasant/) \| [Docs](https://pheasant.daizutabi.net/)
- installation: `pip install pheasant`

### [macros](https://github.com/fralau/mkdocs_macros_plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-macros-plugin">

A **mini-framework** ("Swiss Army knife" of plugins): brings the power of [jinja2](http://jinja.pocoo.org/docs/2.10/) to the markdown pages of a MkDocs website. 

- author: Laurent Franceschetti [fralau](https://github.com/fralau)
- links: [Pypi](https://pypi.org/project/mkdocs-macros-plugin/) \| [Github](https://github.com/fralau/mkdocs_macros_plugin) \| [Docs](https://mkdocs-macros-plugin.readthedocs.io/)
- installation: `pip install mkdocs-macros-plugin`

### [markdownextradata](https://github.com/rosscdh/mkdocs-markdownextradata-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-markdownextradata-plugin">

Injects `mkdocs.yml->extra: *` variables into your markdown documents. Very powerful for things like `{{ client.name }}` or `<a href="{{ client.website }}"><img alt="{{ client.logo.alt }}" src="{{ client.logo.src }}" /></a>` in your markdown and not in the theme template.html files.

- author: Ross Crawford-d’Heureuse [rosscdh](https://github.com/rosscdh)
- links: [Pypi](https://pypi.org/project/mkdocs-markdownextradata-plugin/) \| [Github](https://github.com/rosscdh/mkdocs-markdownextradata-plugin) \| [Docs](https://github.com/rosscdh/mkdocs-markdownextradata-plugin/blob/master/README.md)
- installation: `pip install mkdocs-markdownextradata-plugin`

### [jinja2sandbox](https://github.com/rkoe/mkdocs-jinja2sandbox)

Enables the Jinja2-sandbox in the MkDocs-templates.

- author: Roland Koebler [rkoe](https://github.com/rkoe)
- links [Github](https://github.com/rkoe/mkdocs-jinja2sandbox) \| [Docs](https://github.com/rkoe/mkdocs-jinja2sandbox/blob/master/README.md)
- installation: `pip install git+https://github.com/rkoe/mkdocs-jinja2sandbox`

### [jinja2](https://github.com/andyoakley/mkdocs-jinja2)

Allows the use of Jinja2 templates inside Markdown content. It can be useful, for example, to enumerate pages or use the configuration or site navigation data structures from within content. Templates should render to HTML.

Example:

```jinja2
{% for year in ['2018', '2017'] %}
  <h3>{{ year }}</h3>
  {% for page in pages|sort(attribute='url', reverse=True) %}
    {{ page.title }}
    <br />
  {% endfor %}
{% endfor %}
```

- author: Andy Oakley [andyoakley](https://github.com/andyoakley)
- links: [Github](https://github.com/andyoakley/mkdocs-jinja2) \| [Docs](https://github.com/andyoakley/mkdocs-jinja2/blob/master/README.md)
- installation: `pip install git+https://github.com/andyoakley/mkdocs-jinja2`

### [gen-files](https://github.com/oprypin/mkdocs-gen-files)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-gen-files">

Generate documentation pages virtually during the build, using a Python scripting API. No more hacky Bash scripts that you forget to re-run!
 
- author: Oleh Prypin [oprypin](https://github.com/oprypin)
- links: [PyPI](https://pypi.org/project/mkdocs-gen-files/) | [GitHub](https://github.com/oprypin/mkdocs-gen-files) | [Docs](https://oprypin.github.io/mkdocs-gen-files/)
- installation: `pip install mkdocs-gen-files`

### [mkdocs-markmap](https://github.com/markmap/mkdocs-markmap)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-markmap">

Introduce mindmaps to your documents by either inline markdown conversion or separate file inclusion.

- author: [neatc0der](https://github.com/neatc0der)
- links: [PyPI](https://pypi.org/project/mkdocs-markmap/) | [GitHub](https://github.com/markmao/mkdocs-markmap)
- installation: `pip install mkdocs-markmap`

### [nbconvert](https://pypi.org/project/mkdocs-nbconvert/) (tanbro)

Source parser for `*.ipynb` [Jupyter](https://jupyter.org/) Notebook files

- author: liu xue yan [tanbro](https://github.com/tanbro)
- links: [Pypi](https://pypi.org/project/mkdocs-nbconvert/) | [Github](https://github.com/tanbro/mkdocs-nbconvert) \| [Docs](https://tanbro.github.io/mkdocs-nbconvert/)
- installation: `pip install https://pypi.org/project/mkdocs-nbconvert/`

### [nbconvert](https://github.com/andyoakley/mkdocs-nbconvert) (andyoakley)

This mkdocs plugin uses `nbconvert` to convert Jupyter notebooks into Markdown as they are loaded.

- author: Andy Oakley [andyoakley](https://github.com/andyoakley)
- links: [Github](https://github.com/andyoakley/mkdocs-nbconvert) \| [Docs](https://github.com/andyoakley/mkdocs-nbconvert/blob/master/README.md)
- installation: `pip install git+https://github.com/andyoakley/mkdocs-nbconvert/`

### [mknotebooks](https://pypi.org/project/mknotebooks/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mknotebooks">

Includes Jupyter notebooks in your project documentation.

- author: Jonathan Gray [greenape](https://github.com/greenape)
- links: [Pypi](https://pypi.org/project/mknotebooks/) \| [Github](https://github.com/greenape/mknotebooks) \| [Docs](https://github.com/greenape/mknotebooks/blob/master/README.md)
- installation: `pip install mknotebooks`

### [mkdocs-jupyter](https://pypi.org/project/mkdocs-jupyter/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-jupyter">

Add Jupyter Notebooks directly to the mkdocs navigation.

- author: Daniel Rodriguez [danielfrg](https://github.com/danielfrg)
- links: [Pypi](https://pypi.org/project/mkdocs-jupyter/) \| [Github](https://github.com/danielfrg/mkdocs-jupyter) \| [Docs](https://github.com/danielfrg/mkdocs-jupyter)
- installation: `pip install mkdocs-jupyter`

### [codeyaml](https://github.com/textileio/mkdocs-codeyaml-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-codeyaml-plugin">

Injects the mkdocs.yml extra variables PLUS extra YML files into the markdown template.

- author: textile.io [textileio](https://github.com/textileio)
- links: [Github](https://github.com/textileio/mkdocs-codeyaml-plugin) \| [Docs](https://github.com/textileio/mkdocs-codeyaml-plugin/blob/master/README.md)
- installation: `pip install git+https://github.com/textileio/mkdocs-codeyaml-plugin`

### [markdown-filter](https://github.com/byrnereese/mkdocs-markdown-filter)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-markdown-filter">

Adds a markdown filter to the Jinja templating engine in mkdocs.

- author: Byrne Reese [byrnereese](https://github.com/byrnereese)
- links: [Pypi](https://pypi.org/project/mkdocs-markdown-filter/) \| [Github](https://github.com/byrnereese/mkdocs-markdown-filter) \| [Docs](https://github.com/byrnereese/mkdocs-markdown-filter/blob/master/README.md)
- installation: `pip install mkdocs-markdown-filter`

### [theme-jinja2-filters](https://github.com/burnedikt/mkdocs-jinja2-filters-plugin)

Lets you use Jinja2 filters.

- author: Benedikt Reiser [burnedikt](https://github.com/burnedikt)
- links: [Github](https://github.com/burnedikt/mkdocs-jinja2-filters-plugin) \| [Docs](https://github.com/burnedikt/mkdocs-jinja2-filters-plugin/blob/master/README.md)
- installation: `pip install git+https://github.com/burnedikt/mkdocs-jinja2-filters-plugin`

### [mathy](https://github.com/justindujardin/mathy/tree/master/libraries/mathy_mkdocs)

Renders [mathy](https://mathy.ai/)-specific elements in a mkdocs page by template substitution. Mathy is a A modern computer algebra system and reinforcement learning environments platform for interpretable symbolic mathematics.

- author Justin DuJardin [justindujardin](https://github.com/justindujardin)
- links: [Plugin on Github](https://github.com/justindujardin/mathy/tree/master/libraries/mathy_mkdocs) | [Mathy on Github](https://github.com/justindujardin/mathy) | [Site](https://mathy.ai/)

### [user-defined-values](https://pypi.org/project/mkdocs-user-defined-values/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-user-defined-values">

Allows pages to have user-defined input values.

- author: Rahul Trikha [rahult](https://github.com/rahult)
- links: [Pypi](https://pypi.org/project/mkdocs-user-defined-values/) | [Github](https://github.com/rahult/mkdocs-user-defined-values) | [Docs](https://github.com/rahult/mkdocs-user-defined-values/blob/master/README.md)
- installation: `pip install mkdocs-user-defined-values`

### [mkdocs_protobuf](https://github.com/rymurr/mkdocs-protobuf)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs_protobuf">

Insert protobuf messages directly into documetnation

- author: Ryan Murray [rymurr](https://github.com/rymurr)
- links: [PyPI](https://pypi.org/project/mkdocs_protobuf/) | [Github](https://github.com/rymurr/mkdocs-protobuf) | [Docs](https://github.com/rymurr/mkdocs-protobuf/README.md)
- installation: `pip install mkdocs_protobuf`

### [mkjsfiddle](https://github.com/stadiamaps/mkjsfiddle)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkjsfiddle">

Enhance code fences with an "Edit in JSFiddle" button.

- author: Stadia Maps [stadiamaps](https://github.com/stadiamaps)
- links: [PyPI](https://pypi.org/project/mkjsfiddle/) | [Github](https://github.com/stadiamaps/mkjsfiddle)
- installation: `pip install mkjsfiddle`
