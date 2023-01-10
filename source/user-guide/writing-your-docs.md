# 撰写文档

如何布局和编写 Markdown 源文件。

---

## 文件布局

你的文档源应该被写成常规 Markdown 文件(参见下面的[用 Markdown 写作](#writing-with-markdown))，并放在[文档目录](configuration.md#docs_dir)中。
默认情况下，这个目录将被命名为`docs`，并将与`mkdocs.yml`配置文件一起存在于项目的顶层。

你可以创建的最简单的项目是这样的:

```text
mkdocs.yml
docs/
    index.md
```

按照惯例，您的项目主页应该命名为`index.md`(参见下面的[索引页](#index-pages)了解详细信息)。
以下任何文件扩展名都可以用于 Markdown 源文件:`markdown`, `mdown`, `mkdn`, `mkd`, `md`。
文档目录中包含的所有 Markdown 文件将在构建的站点中呈现，无论任何设置。

NOTE:
名称以点开头的文件和目录(例如:`.foo.md` 或 `.bar/baz.md`)会被 MkDocs 忽略，这与大多数 web 服务器的行为相匹配。
没有覆盖此行为的选项。

你也可以创建多页文档，通过创建几个 Markdown 文件:

```text
mkdocs.yml
docs/
    index.md
    about.md
    license.md
```

您使用的文件布局决定了所生成页面所使用的 URLs。
根据上面的布局，将为以下 URLs 生成页面:

```text
/
/about/
/license/
```

如果更适合你的文档布局，你也可以将 Markdown 文件包含在嵌套目录中。

```text
docs/
    index.md
    user-guide/getting-started.md
    user-guide/configuration-options.md
    license.md
```

嵌套目录中的源文件将导致生成带有嵌套 URLs 的页面，如下所示:

```text
/
/user-guide/getting-started/
/user-guide/configuration-options/
/license/
```

在[文档目录](configuration.md#docs_dir)中，任何没有被标识为 Markdown 文件(通过其文件扩展名)的文件都会被 MkDocs 复制到构建的站点中。
详情见下面[如何链接到图片和媒体](#linking-to-images-and-media)。

### 索引页

当一个目录被请求时，默认情况下，大多数 web 服务器将返回一个包含在该目录中的索引文件(通常命名为`index.html`)，如果目录存在的话。
因此，上面所有示例中的主页都被命名为`index.md`， MkDocs 在构建网站时将其呈现为`index.html`。

许多存储库托管站点通过在浏览目录内容时显示 README 文件的内容，为 README 文件提供了特殊处理。
因此，MkDocs 将允许您将索引页命名为`README.md`而不是`index.md`。
这样，当用户浏览您的源代码时，存储库主机可以显示该目录的索引页，因为它是一个 README 文件。
然而，当 MkDocs 呈现你的网站时，文件将被重命名为`index.html`，以便服务器将其作为一个适当的索引文件。

如果在同一个目录中发现`index.md`文件和`README.md`文件，则使用`index.md`文件，而`README.md`文件被忽略。

### 配置页面和导航

The [nav](configuration.md#nav) configuration setting in your `mkdocs.yml` file
defines which pages are included in the global site navigation menu as well as
the structure of that menu. If not provided, the navigation will be
automatically created by discovering all the Markdown files in the
[documentation directory](configuration.md#docs_dir). An automatically created
navigation configuration will always be sorted alphanumerically by file name
(except that index files will always be listed first within a sub-section). You
will need to manually define your navigation configuration if you would like
your navigation menu sorted differently.

A minimal navigation configuration could look like this:

```yaml
nav:
    - "index.md"
    - "about.md"
```

All paths in the navigation configuration must be relative to the `docs_dir`
configuration option. If that option is set to the default value, `docs`, the
source files for the above configuration would be located at `docs/index.md` and
`docs/about.md`.

The above example will result in two navigation items being created at the top
level and with their titles inferred from the contents of the Markdown file or,
if no title is defined within the file, of the file name. To override the title
in the `nav` setting add a title right before the filename.

```yaml
nav:
    - Home: "index.md"
    - About: "about.md"
```

Note that if a title is defined for a page in the navigation, that title will be
used throughout the site for that page and will override any title defined
within the page itself.

Navigation sub-sections can be created by listing related pages together under a
section title. For example:

```yaml
nav:
    - Home: "index.md"
    - "User Guide":
          - "Writing your docs": "writing-your-docs.md"
          - "Styling your docs": "styling-your-docs.md"
    - About:
          - "License": "license.md"
          - "Release Notes": "release-notes.md"
```

With the above configuration we have three top level items: "Home", "User Guide"
and "About." "Home" is a link to the homepage for the site. Under the "User
Guide" section two pages are listed: "Writing your docs" and "Styling your
docs." Under the "About" section two more pages are listed: "License" and
"Release Notes."

Note that a section cannot have a page assigned to it. Sections are only
containers for child pages and sub-sections. You may nest sections as deeply as
you like. However, be careful that you don't make it too difficult for your
users to navigate through the site navigation by over-complicating the nesting.
While sections may mirror your directory structure, they do not have to.

Any pages not listed in your navigation configuration will still be rendered and
included with the built site, however, they will not be linked from the global
navigation and will not be included in the `previous` and `next` links. Such
pages will be "hidden" unless linked to directly.

## 用 Markdown 写作

MkDocs 页面必须使用[Markdown][md]编写，这是一种轻量级标记语言，可生成易于阅读、易于编写的纯文本文档，可以以可预测的方式将其转换为有效的 HTML 文档。

MkDocs 使用[Python-Markdown]库将 Markdown 文档呈现为 HTML。
Python-Markdown 几乎完全符合[参考实现][md]，尽管有一些非常小的[差异]。

除了在所有 Markdown 实现中通用的基本 Markdown[语法]之外，MkDocs 还支持使用 Python-Markdown[扩展]扩展 Markdown 语法。
关于如何启用扩展，请参阅 MkDocs 的[markdown_extensions]配置设置。

MkDocs 默认包含一些扩展，如下所示。

[python-markdown]: https://python-markdown.github.io/
[md]: https://daringfireball.net/projects/markdown/
[差异]: https://python-markdown.github.io/#differences
[语法]: https://daringfireball.net/projects/markdown/syntax
[扩展]: https://python-markdown.github.io/extensions/
[markdown_extensions]: configuration.md#markdown_extensions

### 内部链接

MkDocs allows you to interlink your documentation by using regular Markdown
[links]. However, there are a few additional benefits to formatting those links
specifically for MkDocs as outlined below.

[links]: https://daringfireball.net/projects/markdown/syntax#link

#### 链接到页面

When linking between pages in the documentation you can simply use the regular
Markdown [linking][links] syntax, including the _relative path_ to the Markdown
document you wish to link to.

```markdown
Please see the [project license](license.md) for further details.
```

When the MkDocs build runs, these Markdown links will automatically be
transformed into an HTML hyperlink to the appropriate HTML page.

WARNING:
官方不支持使用带有链接的绝对路径。相对路径由 MkDocs 调整，以确保它们始终相对于页面。
绝对路径根本不需要修改。
这意味着使用绝对路径的链接可能在本地环境中正常工作，但一旦将它们部署到生产服务器上，它们可能会中断。

如果目标文档文件在另一个目录中，则需要确保在链接中包含任何相对目录路径。

```markdown
Please see the [project license](../about/license.md) for further details.
```

MkDocs 使用[toc]扩展为 Markdown 文档中的每个标题生成 ID。
您可以使用该 ID 通过使用锚链接链接到目标文档中的某个部分。
生成的 HTML 将正确地转换链接的路径部分，而保持锚的部分不变。

```markdown
Please see the [project license](about.md#license) for further details.
```

Note that IDs are created from the text of a header.
All text is converted to lowercase and any disallowed characters, including white-space, are converted to dashes. Consecutive dashes are then reduced to a single dash.

There are a few configuration settings provided by the toc extension which you can set in your `mkdocs.yml` configuration file to alter the default behavior:

-   **`permalink`**

    Generate permanent links at the end of each header. Default: `False`.

    When set to True the paragraph symbol (&para; or `&para;`) is used as the
    link text. When set to a string, the provided string is used as the link
    text. For example, to use the hash symbol (`#`) instead, do:

    ```yaml
    markdown_extensions:
        - toc:
              permalink: "#"
    ```

-   **`baselevel`**

    Base level for headers. Default: `1`.

    This setting allows the header levels to be automatically adjusted to fit
    within the hierarchy of your HTML templates. For example, if the Markdown
    text for a page should not contain any headers higher than level 2 (`<h2>`),
    do:

    ```yaml
    markdown_extensions:
        - toc:
              baselevel: 2
    ```

    Then any headers in your document would be increased by 1. For example, the
    header `# Header` would be rendered as a level 2 header (`<h2>`) in the HTML
    output.

-   **`separator`**

    Word separator. Default: `-`.

    Character which replaces white-space in generated IDs. If you prefer
    underscores, then do:

    ```yaml
    markdown_extensions:
        - toc:
              separator: "_"
    ```

Note that if you would like to define multiple of the above settings, you must do so under a single `toc` entry in the `markdown_extensions` configuration option.

```yml
markdown_extensions:
    - toc:
          permalink: "#"
          baselevel: 2
          separator: "_"
```

[toc]: https://python-markdown.github.io/extensions/toc/

#### 链接到图像和媒体

As well as the Markdown source files, you can also include other file types in your documentation, which will be copied across when generating your documentation site. These might include images and other media.

For example, if your project documentation needed to include a [GitHub pages CNAME file] and a PNG formatted screenshot image then your file layout might look as follows:

```text
mkdocs.yml
docs/
    CNAME
    index.md
    about.md
    license.md
    img/
        screenshot.png
```

To include images in your documentation source files, simply use any of the
regular Markdown image syntaxes:

```Markdown
Cupcake indexer is a snazzy new project for indexing small cakes.

![Screenshot](img/screenshot.png)

*Above: Cupcake indexer in progress*
```

Your image will now be embedded when you build the documentation, and should
also be previewed if you're working on the documentation with a Markdown editor.

[github页面cname文件]: https://help.github.com/articles/using-a-custom-domain-with-github-pages/

#### 从 RAW HTML 链接

Markdown 允许文档作者在 Markdown 语法不能满足作者需求时使用原始 HTML。
MkDocs 并没有在这方面限制 Markdown。
然而，由于 Markdown 解析器忽略了所有原始 HTML, MkDocs 无法验证或转换原始 HTML 中包含的链接。
在原始 HTML 中包含内部链接时，需要为呈现的文档手动设置适当的链接格式。

<a id="Meta-Data"></a>

### 元数据

MkDocs 同时支持 YAML 和 MultiMarkdown 风格的元数据(通常称为 front-matter)。
元数据由 Markdown 文档开头定义的一系列关键字和值组成，这些关键字和值从 Markdown 文档中剥离
文档在被 Python-Markdown 处理之前。
键/值对由 MkDocs 传递给页面模板。
因此，如果主题包含支持，则任何键的值都可以显示在页面上或用于控制页面呈现。
如果有的话，请参阅您的主题文档以获得有关可能支持哪些键的信息。

除了在模板中显示信息外，MkDocs 还支持一些预定义的元数据键，这些元数据键可以改变 MkDocs 对于特定页面的行为。
支持以下按键:

-   **`template`**

    与当前页面一起使用的模板。

    默认情况下，MkDocs 使用主题的`main.html`模板来渲染 Markdown 页面。
    您可以使用`template`元数据键为特定页面定义不同的模板文件。
    模板文件必须在主题环境中定义的路径上可用。

-   **`title`**

    用于文档的"title"。

    MkDocs 将尝试按以下顺序确定文档的标题:

    1. 在文档的[nav]配置设置中定义的标题。
    2. 定义在文档的`title`元数据键中的标题。
    3. 文档正文第一行上的一级 Markdown 标头。请注意，不支持[Setext-style]报头。
    4. 文件的文件名。

    在找到一个页面的标题后，MkDoc 不会继续检查上面列表中的任何其他来源。

[setext-style]: https://daringfireball.net/projects/markdown/syntax#header

#### YAML Style Meta-Data

YAML 风格的元数据由[YAML]键/值对组成，它们被包装在 YAML 风格的分隔符中，用来标记元数据的开始和/或结束。
文档的第一行必须是`---`。
元数据在包含结束分隔符(`---` 或 `...`)的第一行结束。
分隔符之间的内容被解析为[YAML]。

```text
---
title: My Document
summary: A brief description of my document.
authors:
    - Waylan Limberg
    - Tom Christie
date: 2018-07-10
some_url: https://example.com
---
This is the first paragraph of the document.
```

YAML 能够检测数据类型。
因此，在上面的例子中，`title`, `summary` 和 `some_url`的值是字符串，`authors`的值是字符串列表，`date`的值是一个`datetime.date`对象。
注意，YAML 键是区分大小写的，MkDocs 希望键都是小写的。
YAML 的顶层必须是键/值对的集合，这将导致返回 Python `dict`。
如果返回任何其他类型，或者 YAML 解析器遇到错误，那么 MkDocs 不会将该节识别为元数据，页面的`meta`属性将为空，并且该节不会从文档中删除。

#### MultiMarkdown Style Meta-Data

MultiMarkdown 风格的元数据使用[MultiMarkdown]项目首次引入的格式。
数据由 Markdown 文档开头定义的一系列关键字和值组成，如下所示:

```text
Title:   My Document
Summary: A brief description of my document.
Authors: Waylan Limberg
         Tom Christie
Date:    January 23, 2018
blank-value:
some_url: https://example.com

This is the first paragraph of the document.
```

关键字不区分大小写，可以由字母、数字、`_`和`-`组成，且必须以冒号结尾。
这些值由行中冒号后面的任何内容组成，甚至可以为空。

如果一行缩进了 4 个或更多空格，则假定该行是前一个关键字值的附加行。
关键字可以有任意多的行。所有的行都连接成一个字符串。

第一个空行结束文档的所有元数据。
因此，文档的第一行不能为空。

NOTE:
对于 MultiMarkdown 风格的元数据，MkDocs 不支持 YAML 风格的分隔符(`---` 或 `...`)。
事实上，MkDocs 依赖于分隔符的存在或不存在来确定是否使用 YAML 风格的元数据或 MultiMarkdown 风格的元数据。
如果检测到分隔符，但分隔符之间的内容不是有效的 YAML 元数据，MkDocs 不会尝试将内容解析为 MultiMarkdown 风格的元数据。

[yaml]: http://yaml.org
[multimarkdown]: http://fletcherpenney.net/MultiMarkdown_Syntax_Guide#metadata
[nav]: configuration.md#nav

### Tables

The [tables] extension adds a basic table syntax to Markdown which is popular
across multiple implementations. The syntax is rather simple and is generally
only useful for simple tabular data.

A simple table looks like this:

```markdown
| First Header | Second Header | Third Header |
| ------------ | ------------- | ------------ |
| Content Cell | Content Cell  | Content Cell |
| Content Cell | Content Cell  | Content Cell |
```

If you wish, you can add a leading and tailing pipe to each line of the table:

```markdown
| First Header | Second Header | Third Header |
| ------------ | ------------- | ------------ |
| Content Cell | Content Cell  | Content Cell |
| Content Cell | Content Cell  | Content Cell |
```

Specify alignment for each column by adding colons to separator lines:

```markdown
| First Header | Second Header | Third Header |
| :----------- | :-----------: | -----------: |
| Left         |    Center     |        Right |
| Left         |    Center     |        Right |
```

Note that table cells cannot contain any block level elements and cannot contain
multiple lines of text. They can, however, include inline Markdown as defined in
Markdown's [syntax] rules.

Additionally, a table must be surrounded by blank lines. There must be a blank
line before and after the table.

[tables]: https://python-markdown.github.io/extensions/tables/

### Fenced code blocks

The [fenced code blocks] extension adds an alternate method of defining code
blocks without indentation.

The first line should contain 3 or more backtick (`` ` ``) characters, and the
last line should contain the same number of backtick characters (`` ` ``):

````markdown
```
Fenced code blocks are like Standard
Markdown’s regular code blocks, except that
they’re not indented and instead rely on
start and end fence lines to delimit the
code block.
```
````

With this approach, the language can optionally be specified on the first line
after the backticks which informs any syntax highlighters of the language used:

````markdown
```python
def fn():
    pass
```
````

Note that fenced code blocks can not be indented. Therefore, they cannot be
nested inside list items, blockquotes, etc.

[fenced code blocks]: https://python-markdown.github.io/extensions/fenced_code_blocks/
