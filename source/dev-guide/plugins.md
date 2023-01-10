# MkDocs 插件

一个安装，使用和创建MkDocs插件的指南

---

## 安装插件

在使用插件之前，必须在系统上安装该插件。
如果你使用的是MkDocs自带的插件，那么它在你安装MkDocs的时候就已经安装了。
但是，要安装第三方插件，您需要确定适当的包名并使用`pip`安装它:

```bash
pip install mkdocs-foo-plugin
```

一旦插件成功安装，它就可以使用了。
它只需要在配置文件中[启用](#using-plugins)。
[MkDocs 插件] wiki页面有一个不断增长的插件列表，您可以安装和使用。

## 使用插件

[`插件`][config]配置选项应该包含在构建网站时使用的插件列表。
每个“插件”必须是分配给该插件的字符串名称(请参阅给定插件的文档以确定其“名称”)。
这里列出的插件必须已经[安装](#installing-plugins)。

```yaml
plugins:
    - search
```

一些插件可能提供自己的配置选项。
如果你想设置任何配置选项，那么你可以嵌套一个给定插件支持的任何选项的键/值映射(`option_name: option value`)。
注意，插件名后面必须跟着冒号(`:`)，然后在新行中，选项名和值必须缩进并用冒号分隔。
如果你想为一个插件定义多个选项，每个选项必须在单独的行中定义。

```yaml
plugins:
    - search:
        lang: en
        foo: bar
```

有关给定插件可用的配置选项的信息，请参阅该插件的文档。

有关默认插件的列表以及如何覆盖它们，请参阅[配置][config]文档。

## 开发插件

像MkDocs一样，插件必须用Python编写。尽管可以在同一个模块中定义多个插件，但通常期望每个插件都作为单独的Python模块发布。
MkDocs Plugin至少必须包含一个[BasePlugin]子类和一个指向它的[入口点]。

### BasePlugin

`mkdocs.plugins.BasePlugin`的子类应该定义插件的行为。
该类通常由构建过程中对特定事件执行的操作以及插件的配置方案组成。

所有`BasePlugin` 子类包含以下属性:

#### config_scheme

A tuple of configuration validation instances. Each item must consist of a
two item tuple in which the first item is the string name of the
configuration option and the second item is an instance of
`mkdocs.config.config_options.BaseConfigOption` or any of its subclasses.

For example, the following `config_scheme` defines three configuration options: `foo`, which accepts a string; `bar`, which accepts an integer; and `baz`, which accepts a boolean value.

```python
class MyPlugin(mkdocs.plugins.BasePlugin):
    config_scheme = (
        ('foo', mkdocs.config.config_options.Type(str, default='a default value')),
        ('bar', mkdocs.config.config_options.Type(int, default=0)),
        ('baz', mkdocs.config.config_options.Type(bool, default=True))
    )
```

!!! new "**New in version 1.4.**"

    **Subclassing `Config` 指定配置模式**

    为了获得类型安全的好处，如果你只针对MkDocs 1.4+，请将配置模式定义为一个类:

    ```python
    class MyPluginConfig(mkdocs.config.base.Config):
        foo = mkdocs.config.config_options.Type(str, default='a default value')
        bar = mkdocs.config.config_options.Type(int, default=0)
        baz = mkdocs.config.config_options.Type(bool, default=True)

    class MyPlugin(mkdocs.plugins.BasePlugin[MyPluginConfig]):
        ...
    ```

##### Examples of config definitions

>! EXAMPLE:
>
> ```python
> from mkdocs.config import base, config_options as c
>
> class _ValidationOptions(base.Config):
>     enable = c.Type(bool, default=True)
>     verbose = c.Type(bool, default=False)
>     skip_checks = c.ListOfItems(c.Choice(('foo', 'bar', 'baz')), default=[])
>
> class MyPluginConfig(base.Config):
>     definition_file = c.File(exists=True)  # required
>     checksum_file = c.Optional(c.File(exists=True))  # can be None but must exist if specified
>     validation = c.SubConfig(_ValidationOptions)
> ```
>
> From the user's point of view `SubConfig` is similar to `Type(dict)`, it's just that it also retains full ability for validation: you define all valid keys and what each value should adhere to.
>
> And `ListOfItems` is similar to `Type(list)`, but again, we define the constraint that each value must adhere to.
>
> This accepts a config as follows:
>
> ```yaml
> my_plugin:
>   definition_file: configs/test.ini  # relative to mkdocs.yml
>   validation:
>     enable: !ENV [CI, false]
>     verbose: true
>     skip_checks:
>       - foo
>       - baz
> ```
<!-- -->
>? EXAMPLE:
>
> ```python
> import numbers
> from mkdocs.config import base, config_options as c
>
> class _Rectangle(base.Config):
>     width = c.Type(numbers.Real)  # required
>     height = c.Type(numbers.Real)  # required
>
> class MyPluginConfig(base.Config):
>     add_rectangles = c.ListOfItems(c.SubConfig(_Rectangle))  # required
> ```
>
> In this example we define a list of complex items, and that's achieved by passing a concrete `SubConfig` to `ListOfItems`.
>
> This accepts a config as follows:
>
> ```yaml
> my_plugin:
>   add_rectangles:
>     - width: 5
>       height: 7
>     - width: 12
>       height: 2
> ```

When the user's configuration is loaded, the above scheme will be used to
validate the configuration and fill in any defaults for settings not
provided by the user. The validation classes may be any of the classes
provided in `mkdocs.config.config_options` or a third party subclass defined
in the plugin.

Any settings provided by the user which fail validation or are not defined
in the `config_scheme` will raise a `mkdocs.config.base.ValidationError`.

#### config

A dictionary of configuration options for the plugin, which is populated by
the `load_config` method after configuration validation has completed. Use
this attribute to access options provided by the user.

```python
def on_pre_build(self, config, **kwargs):
    if self.config['baz']:
        # implement "baz" functionality here...
```

> NEW: **New in version 1.4.**
>
> ##### Safe attribute-based access
>
> To get type safety benefits, if you're targeting only MkDocs 1.4+, access options as attributes instead:
>
> ```python
> def on_pre_build(self, config, **kwargs):
>     if self.config.baz:
>         print(self.config.bar ** 2)  # OK, `int ** 2` is valid.
> ```

All `BasePlugin` subclasses contain the following method(s):

#### load_config(options)

Loads configuration from a dictionary of options. Returns a tuple of
`(errors, warnings)`. This method is called by MkDocs during configuration
validation and should not need to be called by the plugin.

#### on_&lt;event_name&gt;()

Optional methods which define the behavior for specific [events]. The plugin
should define its behavior within these methods. Replace `<event_name>` with
the actual name of the event. For example, the `pre_build` event would be
defined in the `on_pre_build` method.

Most events accept one positional argument and various keyword arguments. It
is generally expected that the positional argument would be modified (or
replaced) by the plugin and returned. If nothing is returned (the method
returns `None`), then the original, unmodified object is used. The keyword
arguments are simply provided to give context and/or supply data which may
be used to determine how the positional argument should be modified. It is
good practice to accept keyword arguments as `**kwargs`. In the event that
additional keywords are provided to an event in a future version of MkDocs,
there will be no need to alter your plugin.

For example, the following event would add an additional static_template to
the theme config:

```python
class MyPlugin(BasePlugin):
    def on_config(self, config, **kwargs):
        config['theme'].static_templates.add('my_template.html')
        return config
```

> NEW: **New in version 1.4.**
>
> To get type safety benefits, if you're targeting only MkDocs 1.4+, access config options as attributes instead:
>
> ```python
> def on_config(self, config: MkDocsConfig):
>     config.theme.static_templates.add('my_template.html')
>         return config
> ```

### Events

There are three kinds of events: [Global Events], [Page Events] and
[Template Events].

<details class="card">
  <summary>
    See a diagram with relations between all the plugin events
  </summary>
  <div class="card-body">
    <ul>
      <li>The events themselves are shown in yellow, with their parameters.
      <li>Arrows show the flow of arguments and outputs of each event.
          Sometimes they're omitted.
      <li>The events are chronologically ordered from top to bottom.
      <li>Dotted lines appear at splits from global events to per-page events.
      <li>Click the events' titles to jump to their description.
    </ul>
--8<-- "docs/img/plugin-events.svg"
  </div>
</details>
<br>

#### One-time Events

One-time events run once per `mkdocs` invocation. The only case where these tangibly differ from [global events](#global-events) is for `mkdocs serve`: global events, unlike these, will run multiple times -- once per *build*.

##### on_startup

::: mkdocs.plugins.BasePlugin.on_startup
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_shutdown

::: mkdocs.plugins.BasePlugin.on_shutdown
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_serve

::: mkdocs.plugins.BasePlugin.on_serve
    options:
        show_root_heading: false
        show_root_toc_entry: false

#### Global Events

Global events are called once per build at either the beginning or end of the
build process. Any changes made in these events will have a global effect on the
entire site.

##### on_config

::: mkdocs.plugins.BasePlugin.on_config
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_pre_build

::: mkdocs.plugins.BasePlugin.on_pre_build
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_files

::: mkdocs.plugins.BasePlugin.on_files
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_nav

::: mkdocs.plugins.BasePlugin.on_nav
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_env

::: mkdocs.plugins.BasePlugin.on_env
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_post_build

::: mkdocs.plugins.BasePlugin.on_post_build
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_build_error

::: mkdocs.plugins.BasePlugin.on_build_error
    options:
        show_root_heading: false
        show_root_toc_entry: false

#### Template Events

Template events are called once for each non-page template. Each template event
will be called for each template defined in the [extra_templates] config setting
as well as any [static_templates] defined in the theme. All template events are
called after the [env] event and before any [page events].

##### on_pre_template

::: mkdocs.plugins.BasePlugin.on_pre_template
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_template_context

::: mkdocs.plugins.BasePlugin.on_template_context
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_post_template

::: mkdocs.plugins.BasePlugin.on_post_template
    options:
        show_root_heading: false
        show_root_toc_entry: false

#### Page Events

Page events are called once for each Markdown page included in the site. All
page events are called after the [post_template] event and before the
[post_build] event.

##### on_pre_page

::: mkdocs.plugins.BasePlugin.on_pre_page
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_page_read_source

::: mkdocs.plugins.BasePlugin.on_page_read_source
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_page_markdown

::: mkdocs.plugins.BasePlugin.on_page_markdown
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_page_content

::: mkdocs.plugins.BasePlugin.on_page_content
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_page_context

::: mkdocs.plugins.BasePlugin.on_page_context
    options:
        show_root_heading: false
        show_root_toc_entry: false

##### on_post_page

::: mkdocs.plugins.BasePlugin.on_post_page
    options:
        show_root_heading: false
        show_root_toc_entry: false

### Event Priorities

For each event type, corresponding methods of plugins are called in the order that the plugins appear in the `plugins` [config][].

Since MkDocs 1.4, plugins can choose to set a priority value for their events. Events with higher priority are called first. Events without a chosen priority get a default of 0. Events that have the same priority are ordered as they appear in the config.

#### ::: mkdocs.plugins.event_priority

### Handling Errors

MkDocs defines four error types:

#### ::: mkdocs.exceptions.MkDocsException

#### ::: mkdocs.exceptions.ConfigurationError

#### ::: mkdocs.exceptions.BuildError

#### ::: mkdocs.exceptions.PluginError

Unexpected and uncaught exceptions will interrupt the build process and produce
typical Python tracebacks, which are useful for debugging your code. However,
users generally find tracebacks overwhelming and often miss the helpful error
message. Therefore, MkDocs will catch any of the errors listed above, retrieve
the error message, and exit immediately with only the helpful message displayed
to the user.

Therefore, you might want to catch any exceptions within your plugin and raise a
`PluginError`, passing in your own custom-crafted message, so that the build
process is aborted with a helpful message.

The [on_build_error] event will be triggered for any exception.

For example:

```python
from mkdocs.exceptions import PluginError
from mkdocs.plugins import BasePlugin


class MyPlugin(BasePlugin):
    def on_post_page(self, output, page, config, **kwargs):
        try:
            # some code that could throw a KeyError
            ...
        except KeyError as error:
            raise PluginError(str(error))

    def on_build_error(self, error, **kwargs):
        # some code to clean things up
        ...
```

### Entry Point

Plugins need to be packaged as Python libraries (distributed on PyPI separate
from MkDocs) and each must register as a Plugin via a setuptools `entry_points`.
Add the following to your `setup.py` script:

```python
entry_points={
    'mkdocs.plugins': [
        'pluginname = path.to.some_plugin:SomePluginClass',
    ]
}
```

The `pluginname` would be the name used by users (in the config file) and
`path.to.some_plugin:SomePluginClass` would be the importable plugin itself
(`from path.to.some_plugin import SomePluginClass`) where `SomePluginClass` is a
subclass of [BasePlugin] which defines the plugin behavior. Naturally, multiple
Plugin classes could exist in the same module. Simply define each as a separate
entry point.

```python
entry_points={
    'mkdocs.plugins': [
        'featureA = path.to.my_plugins:PluginA',
        'featureB = path.to.my_plugins:PluginB'
    ]
}
```

Note that registering a plugin does not activate it. The user still needs to
tell MkDocs to use it via the config.

[BasePlugin]:#baseplugin
[config]: ../user-guide/configuration.md#plugins
[entry point]: #entry-point
[env]: #on_env
[events]: #events
[extra_templates]: ../user-guide/configuration.md#extra_templates
[Global Events]: #global-events
[Page Events]: #page-events
[post_build]: #on_post_build
[post_template]: #on_post_template
[static_templates]: ../user-guide/configuration.md#static_templates
[Template Events]: #template-events
[MkDocs Plugins]: https://github.com/mkdocs/mkdocs/wiki/MkDocs-Plugins
[on_build_error]: #on_build_error
