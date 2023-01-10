
## Site management

### [mkdocs-multirepo-plugin](https://github.com/jdoiro3/mkdocs-multirepo-plugin) 
[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=jdoiro3&repo=mkdocs-multirepo-plugin)](https://github.com/jdoiro3/mkdocs-multirepo-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-multirepo-plugin?style=plastic">

- author: Joseph Doiron [jdoiro3](https://github.com/jdoiro3)
- links: [PyPI](https://pypi.org/project/mkdocs-monorepo-plugin/) | [Github](https://github.com/jdoiro3/mkdocs-multirepo-plugin)
- installation: `pip install mkdocs-multirepo-plugin`

### [monorepo](https://github.com/spotify/mkdocs-monorepo-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-monorepo-plugin">

Build multiple documentation in a single Mkdocs. Designed for large codebases.

This plugin enables you to build multiple sets of documentation in a single Mkdocs. It is designed to address writing documentation in Spotify’s largest and most business-critical codebases (typically monoliths or monorepos).

- **Support for multiple `docs/` folders in Mkdocs.** Having a single `docs/` folder in a large codebase is hard to maintain. Who owns which documentation? What code is it associated with? Bringing docs closer to the associated code enables you to update them better, as well as leverage folder-based features such as [GitHub Codeowners].

- **Support for multiple navigations.** In Spotify, large repositories typically are split up by multiple owners. These are split by folders. By introducing multiple `mkdocs.yml` files along with multiple `docs/` folder, each team can take ownership of their own navigation. This plugin then intelligently merges of the documentation together into a single repository.

- **Support across multiple repositories.** Using [Git Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) it is possible to merge documentation across multiple repositories into a single codebase dynamically.

- **The same great Mkdocs developer experience.** It is possible to run `mkdocs serve` in the root to merge all of your documentation together, or in a subfolder to build specific documentation. Autoreload still works as usual. No more using [symlinks](https://devdojo.com/tutorials/what-is-a-symlink**)!

> **Note: This plugin is in beta.** Whilst it is not expected to significantly change in functionality, it may not yet be fully compatible with other Mkdocs configuration and thus may break with some advanced configurations. Once these have been resolved and all bugs have been ironed out, we will move this to a stable release.

- author: Spotify [spotify](https://github.com/spotify)
- links: [PyPI](https://pypi.org/project/mkdocs-monorepo-plugin/) \| [Github](https://github.com/spotify/mkdocs-monorepo-plugin) \| [Docs](https://spotify.github.io/mkdocs-monorepo-plugin/) \| [Demo](https://spotify.github.io/mkdocs-monorepo-plugin/monorepo-example/) \| [Blog Post](https://labs.spotify.com/2019/10/01/solving-documentation-for-monoliths-and-monorepos/)
- installation: `pip install mkdocs-monorepo-plugin`

### [multirepo](https://github.com/wilhelmer/mkdocs-multirepo)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-multirepo">

A bit like [monorepo](https://github.com/mkdocs/mkdocs/wiki/MkDocs-Plugins#monorepo), but keeps MkDocs projects separate.

This CLI tool allows you to build multiple MkDocs documentation projects and generate a landing page for them.

Unlike monorepo, multirepo doesn't merge projects into one.

Instead, multirepo adds the MkDocs projects as Git submodules, builds them individually, and generates an HTML landing page based on a template file.

- author: [wilhelmer](https://github.com/wilhelmer)
- links: [PyPI](https://pypi.org/project/mkdocs-multirepo/) \| [GitHub](https://github.com/wilhelmer/mkdocs-multirepo) \| [Docs](https://github.com/wilhelmer/mkdocs-multirepo/blob/master/README.md) \| [Demo](https://github.com/wilhelmer/mkdocs-multirepo/tree/master/mkdocs_multirepo/demo)
- installation: `pip install mkdocs-multirepo`

### [mkdocs-yamp](https://github.com/boozallen/mkdocs-yamp-plugin) 

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-yamp?style=plastic">

Yet Another Multirepo Plugin is another take on how to aggregate content from multiple source code repositories.

Through `mkdocs-yamp`, users can define a list of repositories that are cloned into a local directory within the docs directory, allowing them to reference markdown files in arbitrary locations within the navigational page tree.

- author: Steven Terrana [steven-terrana](https://github.com/steven-terrana)
- links: [PyPI](https://pypi.org/project/mkdocs-yamp/) | [Github](https://github.com/boozallen/mkdocs-yamp-plugin)
- installation: `pip install mkdocs-yamp`

### [subsite](https://github.com/inuits/mkdocs-subsite)

Lets you integrate standalone MkDocs git submodules into a main repo.

- author: Jakub Zárybnický [inuits](https://github.com/inuits)
- links: [GitHub](https://github.com/inuits/mkdocs-subsite) \| [Docs](https://github.com/inuits/mkdocs-subsite/blob/master/README.md)
- installation: `pip install git+https://github.com/inuits/mkdocs-subsite`

### [multiple](https://github.com/experimaestro/mkdocs-multiple)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-multiple">

Allows to merge mkdocs documentations dynamically

- author: [experimaestro](https://github.com/experimaestro)
- links: [GitHub](https://github.com/experimaestro/mkdocs-multiple) \| [Docs](https://github.com/experimaestro/mkdocs-multiple/blob/master/README.md)
- installation: `pip install mkdocs-multiple`



### [simple](https://github.com/athackst/mkdocs-simple-plugin) (mkdocs-simple-plugin)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-simple-plugin">

Lets you build a doc site from markdown files and comments interspersed within your code.  With this plugin, documentation files no longer need to be relegated to a dedicated `docs` folder.  They can live alongside -- or within -- your source code.

**Support for navigation** You can specify the navigation paths and titles for the documentation within your code, the same way you normally would with mkdocs.  Simply consider the location of the mkdocs.yml file as the root of your site.

**Autoreload** Auto-reload works on any file that was previously generated by this plugin.

**Auto-generate configuration** Includes helper program `mkdocs_simple_gen` to automatically generate configuration file.

**Docker integration** Create a local mkdocs site in any directory.  

- author: Allison Thackston [athackst](https://github.com/athackst)
- links: [PyPI](https://pypi.org/project/mkdocs-simple-plugin/) | [Github](https://github.com/athackst/mkdocs-simple-plugin) | [Docs](https://athackst.github.io/mkdocs-simple-plugin) | [Docker](https://hub.docker.com/repository/docker/athackst/mkdocs-simple-plugin)
- installation: `pip install mkdocs-simple-plugin`

### [semiliterate](https://code.studioinfinity.org/glen/mkdocs-semiliterate) (mkdocs-semiliterate)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-semiliterate">

Extends Allison Thackston's [simple](https://athackst.github.io/mkdocs-simple-plugin) with easy content inclusion from one file into another. With this addition and a couple of other tweaks, aims to provide a comfortable and reasonably complete environment for a "semiliterate" programming and documentation style. 

- author: [Glen Whitney](http://studioinfinity.org)
- links: [PyPI](https://pypi.org/project/mkdocs-semiliterate/) | [Source](https://code.studioinfinity.org/glen/mkdocs-semiliterate) | [Docs](http://studioinfinity.org/semiliterate)
- installation: `pip install mkdocs-semiliterate`

### [mkdocs-versioning](https://github.com/zayd62/mkdocs-versioning)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-versioning">

Lets you build different versions of documentation. For example, a newer versions of some software may work differently from an older version and it is important that users of an older version of the software reads the appropriate version of the documentation in order to ensure that the user has the correct information and uses the software appropriately.

- author: Zayd Patel [zayd62](https://github.com/zayd62)
- links: [PyPI](https://pypi.org/project/mkdocs-versioning/) \| [Github](https://github.com/zayd62/mkdocs-versioning) \| [Docs](https://zayd62.github.io/mkdocs-versioning/)
- installation: `pip install mkdocs-versioning`

### [mike](https://github.com/jimporter/mike)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mike">

Although not _technically_ a mkdocs plugin, it should be listed here. `mike` is a Python utility to easily deploy multiple versions of your MkDocs-powered docs to a Git branch, suitable for deploying to Github via `gh-pages`. Supported by `mkdocs-material` (see [versioning](https://squidfunk.github.io/mkdocs-material/setup/setting-up-versioning/#versioning)).

- author: Jim Porter [jimporter](https://github.com/jimporter)
- links: [PyPI](https://pypi.org/project/mike/) \| [Github](https://github.com/jimporter/mike)
- installation: `pip install mike`

### [mkdocs-new-features-notifier](https://pypi.org/project/mkdocs-new-features-notifier/)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-new-features-notifier">

Lets you notify users of new features in your product. It does this by identifying new documentation files, and having these listed under a blinking navigation entry.

- author: Kevin Obuya [Obuya](https://github.com/obuya)
- links: [PyPI](https://pypi.org/project/mkdocs-new-features-notifier/) | [Github](https://github.com/obuya/mkdocs-new-features-notifier) | [Docs](https://github.com/obuya/mkdocs-new-features-notifier/blob/master/README.md)
- installation: `pip install mkdocs-new-features-notifier`

### [progress](https://github.com/rdilweb/mkdocs-plugin-progress)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/mkdocs-plugin-progress">

Outputs real-time updates from the build to the console.

- author: [Reece Dunham](https://rdil.rocks/)
- links: [GitHub](https://github.com/rdilweb/mkdocs-plugin-progress) \| [Docs](https://docs.rdil.rocks/libraries/mkdocs-plugin-progress/)
- installation: `pip install mkdocs-plugin-progress`
