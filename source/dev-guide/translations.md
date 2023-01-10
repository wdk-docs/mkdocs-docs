# 翻译

主题本地化指南。

--- 

MkDocs中包含的[内置主题][built-in themes]提供了翻译支持。
这是一个翻译指南，它记录了贡献新翻译和/或更新现有翻译的过程。
有关修改现有主题的指导，请参阅[贡献指南][update themes]。
要启用特定的翻译，请参阅[用户指南][built-in themes]中关于您正在使用的特定主题的文档。
有关第三方主题的翻译，请参阅这些主题的文档。
第三方主题要想使用MkDocs的翻译工具和方法，必须正确配置该主题才能使用这些工具。

!!! NOTE

    翻译仅适用于主题模板中包含的文本，例如 "next" 和 "previous" 链接。
    页面的Markdown内容不会被翻译。
    如果您希望创建多语言文档，则需要将主题本地化与第三方国际化/本地化插件结合起来。

[built-in themes]: ../user-guide/choosing-your-theme.md
[update themes]: ../about/contributing.md#submitting-changes-to-the-builtin-themes
[configured]: themes.md#supporting-theme-localizationtranslation

## 本地化工具先决条件

Theme localization makes use of the [babel][babel] project for generation and
compilation of localization files. You will need to be working from the
git working tree on your local machine to make use of the translation commands.

See the [Contributing Guide] for direction on how to [Install for Development]
and [Submit a Pull Request]. The instructions in this document assume that you
are working from a properly configured development environment.

Make sure translation requirements are installed in your environment:

```bash
pip install mkdocs[i18n]
```

[babel]: http://babel.pocoo.org/en/latest/cmdline.html
[Contributing Guide]: ../about/contributing.md
[Install for Development]: ../about/contributing.md#installing-for-development
[Submit a Pull Request]: ../about/contributing.md#submitting-pull-requests

## 将语言翻译添加到主题

If your favorite language locale is not yet supported on one (or both) of the
built-in themes (`mkdocs` and `readthedocs`), you can easily contribute a
translation by following the steps below.

Here is a quick summary of what you'll need to do:

1. [Initialize new localization catalogs](#initializing-the-localization-catalogs) for your language (if a translation for your locale already exists, follow the instructions for [updating theme localization files](/user-guide/custom-themes/#localizing-themes) instead).
2. [Add a translation](#translating-the-mkdocs-themes) for every text placeholder in the localized catalogs.
3. [Locally serve and test](#testing-theme-translations) the translated themes for your language.
4. [Update the documentation](#updating-theme-documentation) about supported translations for each translated theme.
5. [Contribute your translation](#contributing-translations) through a Pull Request.

NOTE:
Translation locales are usually identified using the [ISO-639-1] (2-letter)
language codes. While territory/region/county codes are also supported,
location specific translations should only be added after the general
language translation has been completed and the regional dialect requires
use of a term which differs from the general language translation.

[ISO-639-1]: https://en.wikipedia.org/wiki/ISO_639-1

### 初始化本地化目录

The templates for each theme contain text placeholders that have been extracted
into a Portable Object Template (`messages.pot`) file, which is present in each
theme's folder.

Initializing a catalog consists of running a command which will create a
directory structure for your desired language and prepare a Portable Object
(`messages.po`) file derived from the `pot` file of the theme.

Use the `init_catalog` command on each theme's directory and provide the
appropriate language code (`-l <language>`). For example, to add a translation
for the Spanish `es` language to the `mkdocs` theme, run the following command:

```bash
pybabel init --input-file mkdocs/themes/mkdocs/messages.pot --output-dir mkdocs/themes/mkdocs/locales --locale es
```

The above command will create the following file structure:

```text
mkdocs/themes/mkdocs/locales
├── es
│   └── LC_MESSAGES
│       └── messages.po
```

You can now move on to the next step and [add a
translation](#translating-the-mkdocs-themes) for every text placeholder in the
localized catalog.

## 更新主题翻译

If a theme's `messages.pot` template file has been [updated][update themes]
since the `messages.po` was last updated for your locale, follow the steps
below to update the theme's `messages.po` file:

1. [Update the theme's translation catalog](#updating-the-translation-catalogs) to refresh the translatable text placeholders of each theme.
2. [Translate](#translating-the-mkdocs-themes) the newly added translatable text placeholders on every `messages.po` catalog file language you can.
3. [Locally serve and test](#testing-theme-translations) the translated themes for your language.
4. [Contribute your translation](#contributing-translations) through a Pull Request.

### Updating the translation catalogs

This step should be completed after a theme template have been [updated][update
themes] for each language that you are comfortable contributing a translation
for.

To update the `fr` translation catalog of the `mkdocs` theme, use the following
command:

```bash
pybabel update --ignore-obsolete --update-header-comment --input-file mkdocs/themes/mkdocs/messages.pot --output-dir mkdocs/themes/mkdocs/locales --locale fr
```

You can now move on to the next step and [add a translation] for every updated
text placeholder in the localized catalog.

[add a translation]: #translating-the-mkdocs-themes

### Translating the MkDocs themes

Now that your localized `messages.po` files are ready, all you need to do is
add a translation in each `msgstr` item for each `msgid` item in the file.

```text
msgid "Next"
msgstr "Siguiente"
```

WARNING:
Do not modify the `msgid` as it is common to all translations. Just add
its translation in the `msgstr` item.

Once you have finished translating all of the terms listed in the `po` file,
you'll want to [test your localized theme](#testing-theme-translations).

### Testing theme translations

To test a theme with translations, you need to first compile the `messages.po`
files of your theme into `messages.mo` files. The following command will compile
the `es` translation for the `mkdocs` theme.

```bash
pybabel compile --statistics --directory mkdocs/themes/mkdocs/locales --locale es
```

The above command results in the following file structure:

```text
mkdocs/themes/mkdocs/locales
├── es
│   └── LC_MESSAGES
│       ├── messages.mo
│       └── messages.po
```

Note that the compiled `messages.mo` file was generated based on the
`messages.po` file that you just edited.

Then modify the `mkdocs.yml` file at the root of the project to test the new
and/or updated locale:

```yaml
theme:
    name: mkdocs
    locale: es
```

Finally, run `mkdocs serve` to check out your new localized version of the theme.

> NOTE:
> The build and release process takes care of compiling and distributing
> all locales to end users so you only have to worry about contributing the
> actual text translation `messages.po` files (the rest is ignored by git).
>
> After you have finished testing your work, be sure to undo the change to
> the `locale` setting in the `mkdocs.yml` file before submitting your
> changes.
##更新主题文档

Update the lists of supported translations for each translated theme located at
[Choosing your theme](../user-guide/choosing-your-theme.md)
(`docs/user-guide/choosing-your-theme.md`), in their __`locale`__ options.

## 贡献翻译

It is now time for you to [contribute](../about/contributing.md) your nice work
to the project. Thank you!
