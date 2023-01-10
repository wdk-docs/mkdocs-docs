
## Contributing to this page

If you add info about a new plugin, you may use the following template. The plugins are categorized in some broad categories. Place the info about the plugin into the most appropriate category. If you’re unsure, place it into the “Other” category, or — if it makes sense — add a new category (then also add it in the top list of categories, with a link).

```markdown
### [name-of-plugin](source-to-obtain-plugin) (optional-variant)

<img alt="PyPI - Downloads" src="https://img.shields.io/pypi/dm/<NAME OF YOUR PACKAGE>">

Does this or that. Concise description of what the plugin does,
one paragraph or a few. No need to write “An MkDocs plugin that...”,
just start the sentence with the verb, such as “Adds more headings”
or “Lets you merge” etc.

- author: name-of-author [handle-of-author](url-to-author)
- links: [PyPI](https://pypi.org/project/link-to-plugin-on-pypi/) | [Github](https://github.com/plugin-url) | [Docs](link-to-docs-page-or-readme)
- installation: `pip install plugin-location`
```

As `name-of-plugin` on this page, please use the `mkdocs.plugins` entry point name in `setup.py` (see below), linked to the “best” location where more info about the plugin can be found. If multiple plugins with the same name exist, add an `optional-variant` in parantheses after the linked `name-of-plugin`, for example `(handle-of-author)`.

```python
entry_points={
        'mkdocs.plugins': [
            'name-of-plugin = name_of_module...',
        ]
    },
```

If the plugin is on Pypi, add a `[Pypi](https://pypi.org/project/link-to-plugin-on-pypi/)` link in the `links` line. Follow with additional links, separating them with `|`. Use a short link descriptor such as `Github`, `Gitlab`, `Site`, `Docs`, `Demo` etc.

If the plugin is on PyPI, the `plugin-location` in the `installation` line should be the Pypi package name. If it’s only available as a publicly hosted git repo, the `plugin-location` should be `git+https://url-to-the-public-repo`.
