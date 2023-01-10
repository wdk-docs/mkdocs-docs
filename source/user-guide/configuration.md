# 配置

指南所有可用的配置设置。

---

## 介绍

项目设置默认使用项目目录下名为`mkdocs.yml`的 YAML 配置文件进行配置。
你可以通过使用`-f`/`--config-file`选项为它指定另一个路径(参见`mkdocs build --help`)。

至少，这个配置文件必须包含 **`site_name`**。
所有其他设置都是 _可选_ 的。

## 项目信息

### site_name

This is a **required setting**, and should be a string that is used as the main
title for the project documentation. For example:

```yaml
site_name: Marshmallow Generator
```

When rendering the theme this setting will be passed as the `site_name` context
variable.

### site_url

Set the canonical URL of the site. This will add a `link` tag with the
`canonical` URL to the `head` section of each HTML page. If the 'root' of the
MkDocs site will be within a subdirectory of a domain, be sure to include that
subdirectory in the setting (`https://example.com/foo/`).

This setting is also used for `mkdocs serve`: the server will be mounted onto a
path taken from the path component of the URL, e.g. `some/page.md` will be
served from `http://127.0.0.1:8000/foo/some/page/` to mimic the expected remote
layout.

**default**: `null`

### repo_url

When set, provides a link to your repository (GitHub, Bitbucket, GitLab, ...)
on each page.

```yaml
repo_url: https://github.com/example/repository/
```

**default**: `null`

### repo_name

When set, provides the name for the link to your repository on each page.

**default**: `'GitHub'`, `'Bitbucket'` or `'GitLab'` if the `repo_url` matches
those domains, otherwise the hostname from the `repo_url`.

### edit_uri

The path from the base `repo_url` to the docs directory when directly viewing a
page, accounting for specifics of the repository host (e.g. GitHub, Bitbucket,
etc), the branch, and the docs directory itself. MkDocs concatenates `repo_url`
and `edit_uri`, and appends the input path of the page.

When set, and if your theme supports it, provides a link directly to the page in
your source repository. This makes it easier to find and edit the source for the
page. If `repo_url` is not set, this option is ignored. On some themes, setting
this option may cause an edit link to be used in place of a repository link.
Other themes may show both links.

The `edit_uri` supports query ('?') and fragment ('#') characters. For
repository hosts that use a query or a fragment to access the files, the
`edit_uri` might be set as follows. (Note the `?` and `#` in the URI...)

```yaml
# Query string example
edit_uri: "?query=root/path/docs/"
```

```yaml
# Hash fragment example
edit_uri: "#root/path/docs/"
```

For other repository hosts, simply specify the relative path to the docs
directory.

```yaml
# Query string example
edit_uri: root/path/docs/
```

For example, having this config:

```yaml
repo_url: https://example.com/project/repo
edit_uri: blob/main/docs/
```

means that a page named 'foo/bar.md' will have its edit link lead to:  
<https://example.com/project/repo/blob/main/docs/foo/bar.md>

`edit_uri` can actually be just an absolute URL, not necessarily relative to `repo_url`, so this can achieve the same result:

```yaml
repo_url: https://example.com/project/repo/blob/main/docs/
```

For more flexibility, see [edit_uri_template](#edit_uri_template) below.

> NOTE:
> On a few known hosts (specifically GitHub, Bitbucket and GitLab), the
> `edit_uri` is derived from the 'repo_url' and does not need to be set
> manually. Simply defining a `repo_url` will automatically populate the
> `edit_uri` configs setting.
>
> For example, for a GitHub- or GitLab-hosted repository, the `edit_uri`
> would be automatically set as `edit/master/docs/` (Note the `edit` path
> and `master` branch).
>
> For a Bitbucket-hosted repository, the equivalent `edit_uri` would be
> automatically set as `src/default/docs/` (note the `src` path and `default`
> branch).
>
> To use a different URI than the default (for example a different branch),
> simply set the `edit_uri` to your desired string. If you do not want any
> "edit URL link" displayed on your pages, then set `edit_uri` to an empty
> string to disable the automatic setting.

WARNING:
On GitHub and GitLab, the default "edit" path (`edit/master/docs/`) opens
the page in the online editor. This functionality requires that the user
have and be logged in to a GitHub/GitLab account. Otherwise, the user will
be redirected to a login/signup page. Alternatively, use the "blob" path
(`blob/master/docs/`) to open a read-only view, which supports anonymous
access.

**default**: `edit/master/docs/` for GitHub and GitLab repos or
`src/default/docs/` for a Bitbucket repo, if `repo_url` matches those domains,
otherwise `null`

### edit_uri_template

The more flexible variant of [edit_uri](#edit_uri). These two are equivalent:

```yaml
edit_uri: "blob/main/docs/"
edit_uri_template: "blob/main/docs/{path}"
```

(they are also mutually exclusive -- don't specify both).

Starting from here, you can change the positioning or formatting of the path, in case the default behavior of appending the path isn't enough.

The contents of `edit_uri_template` are normal [Python format strings](https://docs.python.org/3/library/string.html#formatstrings), with only these fields available:

-   `{path}`, e.g. `foo/bar.md`
-   `{path_noext}`, e.g. `foo/bar`

And the conversion flag `!q` is available, to percent-encode the field:

-   `{path!q}`, e.g. `foo%2Fbar.md`

> ? NOTE: **Suggested useful configurations:**
>
> -   GitHub Wiki:  
>     (e.g. `https://github.com/project/repo/wiki/foo/bar/_edit`)
>
>     ```yaml
>     repo_url: "https://github.com/project/repo/wiki"
>     edit_uri_template: "{path_noext}/_edit"
>     ```
>
> -   BitBucket editor:  
>     (e.g. `https://bitbucket.org/project/repo/src/master/docs/foo/bar.md?mode=edit`)
>
>     ```yaml
>     repo_url: "https://bitbucket.org/project/repo/"
>     edit_uri_template: "src/master/docs/{path}?mode=edit"
>     ```
>
> -   GitLab Static Site Editor:  
>     (e.g. `https://gitlab.com/project/repo/-/sse/master/docs%2Ffoo%2bar.md`)
>
>     ```yaml
>     repo_url: "https://gitlab.com/project/repo"
>     edit_uri_template: "-/sse/master/docs%2F{path!q}"
>     ```
>
> -   GitLab Web IDE:  
>     (e.g. `https://gitlab.com/-/ide/project/repo/edit/master/-/docs/foo/bar.md`)
>
>     ```yaml
>     edit_uri_template: "https://gitlab.com/-/ide/project/repo/edit/master/-/docs/{path}"
>     ```

**default**: `null`

### site_description

Set the site description. This will add a meta tag to the generated HTML header.

**default**: `null`

### site_author

Set the name of the author. This will add a meta tag to the generated HTML
header.

**default**: `null`

### copyright

Set the copyright information to be included in the documentation by the theme.

**default**: `null`

### remote_branch

Set the remote branch to commit to when using `gh-deploy` to deploy to GitHub
Pages. This option can be overridden by a command line option in `gh-deploy`.

**default**: `gh-pages`

### remote_name

Set the remote name to push to when using `gh-deploy` to deploy to GitHub Pages.
This option can be overridden by a command line option in `gh-deploy`.

**default**: `origin`

## 文档导航

### nav

此设置用于确定站点全局导航的格式和布局。
一个最小的导航配置应该是这样的:

```yaml
nav:
    - "index.md"
    - "about.md"
```

导航配置中的所有路径必须相对于[`docs_dir`](#docs_dir) 配置选项。
请参阅[配置页面和导航][configuring pages and navigation]一节，了解更详细的细分，包括如何创建子节。

导航项也可以包括到外部站点的链接。
虽然标题对于内部链接是可选的，但是对于外部链接是必需的。
外部链接可以是完整 URL，也可以是相对 URL。
在文件中没有找到的任何路径都被认为是外部链接。
关于 MkDocs 如何确定文档的页面标题，请参阅[Meta-Data]部分。

```yaml
nav:
    - Introduction: "index.md"
    - "about.md"
    - "Issue Tracker": "https://example.com/"
```

在上面的示例中，前两项指向本地文件，而第三项指向外部站点。

然而，有时 MkDocs 站点托管在项目站点的子目录中，您可能希望链接到同一站点的其他部分而不包括完整的域。
在这种情况下，您可以使用适当的相对 URL。

```yaml
site_url: https://example.com/foo/

nav:
    - Home: "../"
    - "User Guide": "user-guide.md"
    - "Bug Tracker": "/bugs/"
```

在上面的例子中，使用了两种不同风格的外部链接。
首先，请注意`site_url`表示 MkDocs 站点托管在域的`/foo/`子目录中。

因此，`Home`导航项是一个相对链接，它上一级到服务器根目录，有效地指向`https://example.com/`。

`Bug Tracker`项使用了来自服务器根目录的绝对路径，有效地指向`https://example.com/bugs/`。

当然，`User Guide`指向一个本地 MkDocs 页面。

**default**: 默认情况下，`nav` 将包含在`docs_dir`及其子目录中找到的所有 Markdown 文件的字母数字排序嵌套列表。
索引文件总是在子节中列在前面。

## 建立目录

### theme

设置文档站点的主题和特定于主题的配置。
可以是字符串，也可以是一组键/值对。

如果是字符串，则必须是已知已安装主题的字符串名称。
如需可用主题列表，请访问[选择您的主题][choosing your theme]。

一个键/值对的例子可能是这样的:

```yaml
theme:
    name: mkdocs
    locale: en
    custom_dir: my_theme_customizations/
    static_templates:
        - sitemap.html
    include_sidebar: false
```

If a set of key/value pairs, the following nested keys can be defined:

> BLOCK:
>
> #### name
>
> The string name of a known installed theme. For a list of available themes
> visit [Choosing Your Theme].
>
> #### locale
>
> A code representing the language of your site. See [Localizing your theme]
> for details.
>
> #### custom_dir
>
> A directory containing a custom theme. This can either be a relative
> directory, in which case it is resolved relative to the directory containing
> your configuration file or it can be an absolute directory path from the
> root of your local file system.
>
> See [Customizing Your Theme][theme_dir] for details if you would like to tweak an
> existing theme.
>
> See the [Theme Developer Guide] if you would like to build your own theme
> from the ground up.
>
> #### static_templates
>
> A list of templates to render as static pages. The templates must be located
> in either the theme's template directory or in the `custom_dir` defined in
> the theme configuration.
>
> #### (theme specific keywords)
>
> Any additional keywords supported by the theme can also be defined. See the
> documentation for the theme you are using for details.

**default**: `'mkdocs'`

### docs_dir

The directory containing the documentation source markdown files. This can
either be a relative directory, in which case it is resolved relative to the
directory containing your configuration file, or it can be an absolute directory
path from the root of your local file system.

**default**: `'docs'`

### site_dir

The directory where the output HTML and other files are created. This can either
be a relative directory, in which case it is resolved relative to the directory
containing your configuration file, or it can be an absolute directory path from
the root of your local file system.

**default**: `'site'`

> NOTE:
> If you are using source code control you will normally want to ensure that
> your _build output_ files are not committed into the repository, and only
> keep the _source_ files under version control. For example, if using `git`
> you might add the following line to your `.gitignore` file:
>
> ```text
> site/
> ```
>
> If you're using another source code control tool, you'll want to check its
> documentation on how to ignore specific directories.

### extra_css

Set a list of CSS files in your `docs_dir` to be included by the theme. For
example, the following example will include the extra.css file within the
css subdirectory in your [docs_dir](#docs_dir).

```yaml
extra_css:
    - css/extra.css
    - css/second_extra.css
```

**default**: `[]` (an empty list).

### extra_javascript

Set a list of JavaScript files in your `docs_dir` to be included by the theme.
See the example in [extra_css] for usage.

**default**: `[]` (an empty list).

### extra_templates

Set a list of templates in your `docs_dir` to be built by MkDocs. To see more
about writing templates for MkDocs read the documentation about [custom themes]
and specifically the section about the [available variables] to
templates. See the example in [extra_css] for usage.

**default**: `[]` (an empty list).

### extra

A set of key-value pairs, where the values can be any valid YAML construct, that
will be passed to the template. This allows for great flexibility when creating
custom themes.

For example, if you are using a theme that supports displaying the project
version, you can pass it to the theme like this:

```yaml
extra:
    version: 1.0
```

**default**: By default `extra` will be an empty key-value mapping.

## 预览控件

## 现场重装

### watch

Determines additional directories to watch when running `mkdocs serve`.
Configuration is a YAML list.

```yaml
watch:
    - directory_a
    - directory_b
```

Allows a custom default to be set without the need to pass it through the `-w`/`--watch`
option every time the `mkdocs serve` command is called.

> NOTE:
> The paths provided via the configuration file are relative to the configuration file.
>
> The paths provided via the `-w`/`--watch` CLI parameters are not.

### use_directory_urls

This setting controls the style used for linking to pages within the
documentation.

The following table demonstrates how the URLs used on the site differ when
setting `use_directory_urls` to `true` or `false`.

| Source file      | use_directory_urls: true | use_directory_urls: false |
| ---------------- | ------------------------ | ------------------------- |
| index.md         | /                        | /index.html               |
| api-guide.md     | /api-guide/              | /api-guide.html           |
| about/license.md | /about/license/          | /about/license.html       |

The default style of `use_directory_urls: true` creates more user friendly URLs,
and is usually what you'll want to use.

The alternate style can be useful if you want your documentation to remain
properly linked when opening pages directly from the file system, because it
creates links that point directly to the target _file_ rather than the target
_directory_.

**default**: `true`

### strict

Determines how warnings are handled. Set to `true` to halt processing when a
warning is raised. Set to `false` to print a warning and continue processing.

This is also available as a command line flag: `--strict`.

**default**: `false`

### dev_addr

Determines the address used when running `mkdocs serve`. Must be of the format
`IP:PORT`.

Allows a custom default to be set without the need to pass it through the
`--dev-addr` option every time the `mkdocs serve` command is called.

**default**: `'127.0.0.1:8000'`

See also: [site_url](#site_url).

## 格式选项

### markdown_extensions

MkDocs uses the [Python Markdown][pymkd] library to translate Markdown files
into HTML. Python Markdown supports a variety of [extensions][pymdk-extensions]
that customize how pages are formatted. This setting lets you enable a list of
extensions beyond the ones that MkDocs uses by default (`meta`, `toc`, `tables`,
and `fenced_code`).

For example, to enable the [SmartyPants typography extension][smarty], use:

```yaml
markdown_extensions:
    - smarty
```

Some extensions provide configuration options of their own. If you would like to
set any configuration options, then you can nest a key/value mapping
(`option_name: option value`) of any options that a given extension supports.
See the documentation for the extension you are using to determine what options
they support.

For example, to enable permalinks in the (included) `toc` extension, use:

```yaml
markdown_extensions:
    - toc:
          permalink: True
```

Note that a colon (`:`) must follow the extension name (`toc`) and then on a new
line the option name and value must be indented and separated by a colon. If you
would like to define multiple options for a single extension, each option must be
defined on a separate line:

```yaml
markdown_extensions:
    - toc:
          permalink: True
          separator: "_"
```

Add an additional item to the list for each extension. If you have no
configuration options to set for a specific extension, then simply omit options
for that extension:

```yaml
markdown_extensions:
    - smarty
    - toc:
          permalink: True
    - sane_lists
```

In the above examples, each extension is a list item (starts with a `-`). As an
alternative, key/value pairs can be used instead. However, in that case an empty
value must be provided for extensions for which no options are defined.
Therefore, the last example above could also be defined as follows:

```yaml
markdown_extensions:
    smarty: {}
    toc:
        permalink: True
    sane_lists: {}
```

This alternative syntax is required if you intend to override some options via
[inheritance].

> NOTE: **See Also:**
>
> The Python-Markdown documentation provides a [list of extensions][exts]
> which are available out-of-the-box. For a list of configuration options
> available for a given extension, see the documentation for that extension.
>
> You may also install and use various [third party extensions][3rd]. Consult
> the documentation provided by those extensions for installation instructions
> and available configuration options.

**default**: `[]` (an empty list).

### hooks

NEW: **New in version 1.4.**

A list of paths to Python scripts (relative to `mkdocs.yml`) that are loaded and used as [plugin](#plugins) instances.

For example:

```yaml
hooks:
    - my_hooks.py
```

Then the file _my_hooks.py_ can contain any [plugin event handlers](../dev-guide/plugins.md#events) (without `self`), e.g.:

```python
def on_page_markdown(markdown, **kwargs):
    return markdown.replace('a', 'z')
```

> ? EXAMPLE: **Advanced example:**
>
> This produces warnings based on the Markdown content (and warnings are fatal in [strict](#strict) mode):
>
> ```python
> import logging, re
> import mkdocs.plugins
>
> log = logging.getLogger('mkdocs')
>
> @mkdocs.plugins.event_priority(-50)
> def on_page_markdown(markdown, page, **kwargs):
>     path = page.file.src_uri
>     for m in re.finditer(r'\bhttp://[^) ]+', markdown):
>         log.warning(f"Documentation file '{path}' contains a non-HTTPS link: {m[0]}")
> ```

This does not enable any new abilities compared to [plugins][], it only simplifies one-off usages, as these don't need to be _installed_ like plugins do.

Note that for `mkdocs serve` the hook module will _not_ be reloaded on each build.

You might have seen this feature in the [mkdocs-simple-hooks plugin](https://github.com/aklajnert/mkdocs-simple-hooks). If using standard method names, it can be directly replaced, e.g.:

```diff
-plugins:
-  - mkdocs-simple-hooks:
-      hooks:
-        on_page_markdown: 'my_hooks:on_page_markdown'
+hooks:
+  - my_hooks.py
```

### plugins

A list of plugins (with optional configuration settings) to use when building
the site. See the [Plugins] documentation for full details.

If the `plugins` config setting is defined in the `mkdocs.yml` config file, then
any defaults (such as `search`) are ignored and you need to explicitly re-enable
the defaults if you would like to continue using them:

```yaml
plugins:
    - search
    - your_other_plugin
```

To define options for a given plugin, use a nested set of key/value pairs:

```yaml
plugins:
    - search
    - your_other_plugin:
          option1: value
          option2: other value
```

In the above examples, each plugin is a list item (starts with a `-`). As an
alternative, key/value pairs can be used instead. However, in that case an empty
value must be provided for plugins for which no options are defined. Therefore,
the last example above could also be defined as follows:

```yaml
plugins:
    search: {}
    your_other_plugin:
        option1: value
        option2: other value
```

This alternative syntax is required if you intend to override some options via
[inheritance].

To completely disable all plugins, including any defaults, set the `plugins`
setting to an empty list:

```yaml
plugins: []
```

**default**: `['search']` (the "search" plugin included with MkDocs).

#### Search

A search plugin is provided by default with MkDocs which uses [lunr.js] as a
search engine. The following config options are available to alter the behavior
of the search plugin:

##### **separator**

A regular expression which matches the characters used as word separators when
building the index. By default whitespace and the hyphen (`-`) are used. To add
the dot (`.`) as a word separator you might do this:

```yaml
plugins:
    - search:
          separator: '[\s\-\.]+'
```

**default**: `'[\s\-]+'`

##### **min_search_length**

An integer value that defines the minimum length for a search query. By default
searches shorter than 3 chars in length are ignored as search result quality with
short search terms are poor. However, for some use cases (such as documentation
about Message Queues which might generate searches for 'MQ') it may be preferable
to set a shorter limit.

```yaml
plugins:
    - search:
          min_search_length: 2
```

**default**: 3

##### **lang**

A list of languages to use when building the search index as identified by their
[ISO 639-1] language codes. With [Lunr Languages], the following languages are
supported:

-   `ar`: Arabic
-   `da`: Danish
-   `nl`: Dutch
-   `en`: English
-   `fi`: Finnish
-   `fr`: French
-   `de`: German
-   `hu`: Hungarian
-   `it`: Italian
-   `ja`: Japanese
-   `no`: Norwegian
-   `pt`: Portuguese
-   `ro`: Romanian
-   `ru`: Russian
-   `es`: Spanish
-   `sv`: Swedish
-   `th`: Thai
-   `tr`: Turkish
-   `vi`: Vietnamese

You may [contribute additional languages].

WARNING:
While search does support using multiple languages together, it is best not
to add additional languages unless you really need them. Each additional
language adds significant bandwidth requirements and uses more browser
resources. Generally, it is best to keep each instance of MkDocs to a single
language.

NOTE:
Lunr Languages does not currently include support for Chinese or other Asian
languages. However, some users have reported decent results using Japanese.

**default**: The value of `theme.locale` if set, otherwise `[en]`.

##### **prebuild_index**

Optionally generates a pre-built index of all pages, which provides some
performance improvements for larger sites. Before enabling, confirm that the
theme you are using explicitly supports using a prebuilt index (the builtin
themes do). Set to `true` to enable.

WARNING:
This option requires that [Node.js] be installed and the command `node` be
on the system path. If the call to `node` fails for any reason, a warning
is issued and the build continues uninterrupted. You may use the `--strict`
flag when building to cause such a failure to raise an error instead.

NOTE:
On smaller sites, using a pre-built index is not recommended as it creates a
significant increase is bandwidth requirements with little to no noticeable
improvement to your users. However, for larger sites (hundreds of pages),
the bandwidth increase is relatively small and your users will notice a
significant improvement in search performance.

**default**: `False`

##### **indexing**

Configures what strategy the search indexer will use when building the index
for your pages. This property is particularly useful if your project is large
in scale, and the index takes up an enormous amount of disk space.

```yaml
plugins:
    - search:
          indexing: "full"
```

###### Options

| Option     | Description                                                      |
| ---------- | ---------------------------------------------------------------- |
| `full`     | Indexes the title, section headings, and full text of each page. |
| `sections` | Indexes the title and section headings of each page.             |
| `titles`   | Indexes only the title of each page.                             |

**default**: `full`
＃＃ 环境变量

In most cases, the value of a configuration option is set directly in the
configuration file. However, as an option, the value of a configuration option
may be set to the value of an environment variable using the `!ENV` tag. For
example, to set the value of the `site_name` option to the value of the
variable `SITE_NAME` the YAML file may contain the following:

```yaml
site_name: !ENV SITE_NAME
```

If the environment variable is not defined, then the configuration setting
would be assigned a `null` (or `None` in Python) value. A default value can be
defined as the last value in a list. Like this:

```yaml
site_name: !ENV [SITE_NAME, "My default site name"]
```

Multiple fallback variables can be used as well. Note that the last value is
not an environment variable, but must be a value to use as a default if none
of the specified environment variables are defined.

```yaml
site_name: !ENV [SITE_NAME, OTHER_NAME, "My default site name"]
```

Simple types defined within an environment variable such as string, bool,
integer, float, datestamp and null are parsed as if they were defined directly
in the YAML file, which means that the value will be converted to the
appropriate type. However, complex types such as lists and key/value pairs
cannot be defined within a single environment variable.

For more details, see the [pyyaml_env_tag](https://github.com/waylan/pyyaml-env-tag)
project.

## 配置继承

通常，单个文件将保存站点的整个配置。
然而，一些组织可能维护多个站点，这些站点之间共享一个公共配置。
公共配置选项可以在父配置文件中定义，每个站点的主配置文件将继承该配置文件，而不是为每个站点维护单独的配置。

要为配置文件定义父文件，请将`INHERIT`(全大写)键设置为父文件的路径。
路径必须相对于主文件的位置。

对于要与父配置合并的配置选项，必须将这些选项定义为键/值对。
具体来说，[markdown_extensions]和[plugins](#plugins)选项必须使用不使用列表项(以`-`开头的行)的替代语法。

例如，假设公共(父)配置定义在`base.yml`中:

```yaml
theme:
    name: mkdocs
    locale: en
    highlightjs: true

markdown_extensions:
    toc:
        permalink: true
    admonition: {}
```

然后，对于“foo”站点，主配置文件将定义在`foo/mkdocs.yml`:

```yml
INHERIT: ../base.yml
site_name: Foo Project
site_url: https://example.com/foo
```

当运行`mkdocs build`时，`foo/mkdocs.yml`处的文件将作为配置文件传入。
然后 MkDocs 将解析该文件，检索并解析父文件`base.yml` ，并将两者深度合并。
这将导致 MkDocs 收到以下合并配置:

```yaml
site_name: Foo Project
site_url: https://example.com/foo

theme:
    name: mkdocs
    locale: en
    highlightjs: true

markdown_extensions:
    toc:
        permalink: true
    admonition: {}
```

深度合并允许您在主配置文件中添加和/或覆盖各种值。
例如，假设对于一个站点，您希望添加对定义列表的支持，为永久链接使用不同的符号，并定义不同的分隔符。
在该站点的主配置文件中，您可以这样做:

```yaml
INHERIT: ../base.yml
site_name: Bar Project
site_url: https://example.com/bar

markdown_extensions:
    def_list: {}
    toc:
        permalink: 
        separator: "_"
```

在这种情况下，上述配置将与`base.yml`深度合并，并产生以下配置:

```yaml
site_name: Bar Project
site_url: https://example.com/bar

theme:
    name: mkdocs
    locale: en
    highlightjs: true

markdown_extensions:
    def_list: {}
    toc:
        permalink: 
        separator: "_"
    admonition: {}
```

注意，`admonition`扩展从父配置中保留，`def_list`扩展被添加，`toc.permalink`的值被替换，`toc.separator`的值被添加。

您可以替换或合并任何键的值。
但是，任何非键都将被替换。
因此，不能将项追加到列表中。
您必须重新定义整个列表。

由于[nav]配置由嵌套列表组成，这意味着您不能合并导航项。
当然，你可以将整个`nav`配置替换为一个新的。但是，通常期望整个导航将在项目的主配置文件中定义。

WARNING:
提醒一下，所有基于路径的配置选项都必须相对于主配置文件，MkDocs 在合并时不会改变路径。
因此，在由多个不同站点继承的父文件中定义路径可能无法正常工作。
通常最好只在主配置文件中定义基于路径的选项。

[theme developer guide]: ../dev-guide/themes.md
[pymdk-extensions]: https://python-markdown.github.io/extensions/
[pymkd]: https://python-markdown.github.io/
[smarty]: https://python-markdown.github.io/extensions/smarty/
[exts]: https://python-markdown.github.io/extensions/
[3rd]: https://github.com/Python-Markdown/markdown/wiki/Third-Party-Extensions
[configuring pages and navigation]: writing-your-docs.md#configure-pages-and-navigation
[theme_dir]: customizing-your-theme.md#using-the-theme_dir
[choosing your theme]: choosing-your-theme.md
[localizing your theme]: localizing-your-theme.md
[extra_css]: #extra_css
[plugins]: ../dev-guide/plugins.md
[lunr.js]: https://lunrjs.com/
[iso 639-1]: https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes
[lunr languages]: https://github.com/MihaiValentin/lunr-languages#lunr-languages-----
[contribute additional languages]: https://github.com/MihaiValentin/lunr-languages/blob/master/CONTRIBUTING.md
[node.js]: https://nodejs.org/
[markdown_extensions]: #markdown_extensions
[nav]: #nav
[inheritance]: #configuration-inheritance
