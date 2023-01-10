# 部署您的文档

将文档部署到各种托管提供商的基本指南

---

## GitHub Pages

如果你在[GitHub]上托管项目的源代码，你可以很容易地使用[GitHub Pages]来托管项目的文档。
有两种基本类型的GitHub页面网站:[项目页面][Project Pages]网站，和[用户和组织页面][User and Organization Pages] 网站。
它们几乎相同，但有一些重要的差异，在部署时需要不同的工作流程。

### Project Pages

Project Pages站点更简单，因为站点文件被部署到项目存储库中的分支(默认为`gh-pages`)。
在你`checkout`维护项目源文档的git存储库的主要工作分支(通常是`master`)后，运行以下命令:

```sh
mkdocs gh-deploy
```

That's it! Behind the scenes, MkDocs will build your docs and use the
[ghp-import] tool to commit them to the `gh-pages` branch and push the
`gh-pages` branch to GitHub.

Use `mkdocs gh-deploy --help` to get a full list of options available for the
`gh-deploy` command.

Be aware that you will not be able to review the built site before it is pushed
to GitHub. Therefore, you may want to verify any changes you make to the docs
beforehand by using the `build` or `serve` commands and reviewing the built
files locally.

WARNING:
You should never edit files in your pages repository by hand if you're using
the `gh-deploy` command because you will lose your work the next time you
run the command.

WARNING:
If there are untracked files or uncommitted work in the local repository where
`mkdocs gh-deploy` is run, these will be included in the pages that are deployed.

### Organization and User Pages

User and Organization Pages sites are not tied to a specific project, and the
site files are deployed to the `master` branch in a dedicated repository named
with the GitHub account name. Therefore, you need working copies of two
repositories on our local system. For example, consider the following file
structure:

```text
my-project/
    mkdocs.yml
    docs/
orgname.github.io/
```

After making and verifying updates to your project you need to change
directories to the `orgname.github.io` repository and call the
`mkdocs gh-deploy` command from there:

```sh
cd ../orgname.github.io/
mkdocs gh-deploy --config-file ../my-project/mkdocs.yml --remote-branch master
```

Note that you need to explicitly point to the `mkdocs.yml` configuration file as
it is no longer in the current working directory. You also need to inform the
deploy script to commit to the `master` branch. You may override the default
with the [remote_branch] configuration setting, but if you forget to change
directories before running the deploy script, it will commit to the `master`
branch of your project, which you probably don't want.

### 自定义的域

GitHub Pages includes support for using a [Custom Domain] for your site. In
addition to the steps documented by GitHub, you need to take one additional step
so that MkDocs will work with your custom domain. You need to add a `CNAME` file
to the root of your [docs_dir]. The file must contain a single bare domain or
subdomain on a single line (see MkDocs' own [CNAME file] as an example). You may
create the file manually, or use GitHub's web interface to set up the custom
domain (under Settings / Custom Domain). If you use the web interface, GitHub
will create the `CNAME` file for you and save it to the root of your "pages"
branch. So that the file does not get removed the next time you deploy, you need
to copy the file to your `docs_dir`. With the file properly included in your
`docs_dir`, MkDocs will include the file in your built site and push it to your
"pages" branch each time you run the `gh-deploy` command.

If you are having problems getting a custom domain to work, see GitHub's
documentation on [Troubleshooting custom domains].

[github]: https://github.com/
[github pages]: https://pages.github.com/
[project pages]: https://help.github.com/articles/user-organization-and-project-pages/#project-pages-sites
[user and organization pages]: https://help.github.com/articles/user-organization-and-project-pages/#user-and-organization-pages-sites
[ghp-import]: https://github.com/davisp/ghp-import
[remote_branch]: ./configuration.md#remote_branch
[custom domain]: https://help.github.com/articles/adding-or-removing-a-custom-domain-for-your-github-pages-site
[docs_dir]: ./configuration.md#docs_dir
[cname file]: https://github.com/mkdocs/mkdocs/blob/master/docs/CNAME
[troubleshooting custom domains]: https://help.github.com/articles/troubleshooting-custom-domains/

## 阅读文档

[Read the Docs][rtd] offers free documentation hosting. You can import your docs
using any major version control system, including Mercurial, Git, Subversion,
and Bazaar. Read the Docs supports MkDocs out-of-the-box. Follow the
[instructions] on their site to arrange the files in your repository properly,
create an account and point it at your publicly hosted repository. If properly
configured, your documentation will update each time you push commits to your
public repository.

NOTE:
To benefit from all of the [features] offered by Read the Docs, you will need
to use the [Read the Docs theme][theme] which ships with MkDocs. The various
themes which may be referenced in Read the Docs' documentation are Sphinx
specific themes and will not work with MkDocs.

[rtd]: https://readthedocs.org/
[instructions]: https://docs.readthedocs.io/en/stable/intro/getting-started-with-mkdocs.html
[features]: https://docs.readthedocs.io/en/latest/features.html
[theme]: ./choosing-your-theme.md#readthedocs

## 其他供应商

任何可以提供静态文件的托管提供商都可以用来提供MkDocs生成的文档。
虽然不可能记录如何将文档上传到每个托管提供商，但以下指南应该能提供一些一般性的帮助。

When you build your site (using the `mkdocs build` command), all of the files
are written to the directory assigned to the [site_dir] configuration option
(defaults to `"site"`) in your `mkdocs.yaml` config file. Generally, you will
simply need to copy the contents of that directory to the root directory of your
hosting provider's server. Depending on your hosting provider's setup, you may
need to use a graphical or command line [ftp], [ssh] or [scp] client to transfer
the files.

For example, a typical set of commands from the command line might look
something like this:

```sh
mkdocs build
scp -r ./site user@host:/path/to/server/root
```

Of course, you will need to replace `user` with the username you have with your
hosting provider and `host` with the appropriate domain name. Additionally, you
will need to adjust the `/path/to/server/root` to match the configuration of
your hosts' file system.

[ftp]: https://en.wikipedia.org/wiki/File_Transfer_Protocol
[ssh]: https://en.wikipedia.org/wiki/Secure_Shell
[scp]: https://en.wikipedia.org/wiki/Secure_copy

See your host's documentation for specifics. You will likely want to search
their documentation for "ftp" or "uploading site".

## 本地文件

Rather than hosting your documentation on a server, you may instead distribute
the files directly, which can then be viewed in a browser using the `file://`
scheme.

Note that, due to the security settings of all modern browsers, some things
will not work the same and some features may not work at all. In fact, a few
settings will need to be customized in very specific ways.

-   [site_url]:

    The `site_url` must be set to an empty string, which instructs MkDocs to
    build your site so that it will work with the `file://` scheme.

    ```yaml
    site_url: ""
    ```

-   [use_directory_urls]:

    Set `use_directory_urls` to `false`. Otherwise, internal links between
    pages will not work properly.

    ```yaml
    use_directory_urls: false
    ```

-   [search]:

    You will need to either disable the search plugin, or use a third-party
    search plugin which is specifically designed to work with the `file://`
    scheme. To disable all plugins, set the `plugins` setting to an empty list.

    ```yaml
    plugins: []
    ```

    If you have other plugins enabled, simply ensure that `search` is not
    included in the list.

When writing your documentation, it is imperative that all internal links use
relative URLs as [documented][internal links]. Remember, each reader of your
documentation will be using a different device and the files will likely be in a
different location on that device.

If you expect your documentation to be viewed off-line, you may also need to be
careful about which themes you choose. Many themes make use of CDNs for various
support files, which require a live Internet connection. You will need to choose
a theme which includes all support files directly in the theme.

When you build your site (using the `mkdocs build` command), all of the files
are written to the directory assigned to the [site_dir] configuration option
(defaults to `"site"`) in your `mkdocs.yaml` config file. Generally, you will
simply need to copy the contents of that directory and distribute it to your
readers. Alternatively, you may choose to use a third party tool to convert the
HTML files to some other documentation format.

## 404 Pages

当MkDocs构建文档时，它将在[build目录][site_dir]中包含一个404.html文件。
该文件将在部署到[GitHub](#github-pages)时自动使用，但仅限于自定义域。
其他web服务器可能会配置使用它，但该功能并不总是可用的。
有关更多信息，请参阅所选服务器的文档。

[site_dir]: ./configuration.md#site_dir
[site_url]: ./configuration.md#site_url
[use_directory_urls]: ./configuration.md#use_directory_urls
[search]: ./configuration.md#search
[internal links]: ./writing-your-docs.md#internal-links
