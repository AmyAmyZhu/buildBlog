title: Use MkDocs to Build-up Documentation Wiki
date: 2018-09-19 15:34:59
categories:
- Markdown
tags:
- Markdown
- Wiki
- Documentation
---

MkDocs is a great documentation tool that can generate a beautiful Wiki website for your project. Here is the step to install and use it.

Ensure Python and pip are installed on your system and check the versions of them are updated:

<!-- more -->

```
pip install --upgrade python
pip install --upgrade pip
```
If you need to install pip for the first time, download get-pip.py. Then run the following command to install it:

```
python get-pip.py
```

## Installing MkDocs

Install the mkdocs package using pip:

```
pip install mkdocs
```

Create new project if needed:

```
mkdocs new my-project
```

There's a single configuration file named `mkdocs.yml`, and a folder named `docs` that will contain your documentation source files. Right now the `docs` folder just contains a single documentation page, named `index.md`.

MkDocs comes with a built-in dev-server that lets you preview your documentation as you work on it. Make sure you're in the same directory as the `mkdocs.yml` configuration file, and then start the server by running the `mkdocs serve` command:

```
$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
[I 160402 15:50:43 server:271] Serving on http://127.0.0.1:8000
[I 160402 15:50:43 handlers:58] Start watching changes
[I 160402 15:50:43 handlers:60] Start detecting changes
```
## Theme

Theme I choose is Material: https://squidfunk.github.io/mkdocs-material/getting-started/, you can search from MkDocs website or github to find a theme you like.

installing Material is simple:

```
pip install mkdocs-material
```


{% alert danger no-icon %}
Don't use git clone recommanded on the website. It is not working.
{% endalert %}



Add the following lines in `mkdocs.yml`:

```
theme:
name: 'material'
```

### Customization

In order to remove the footer of MkDocs, customize Material theme under the path: `\Library\Python`. Find the python version you use and go to `site-packages`, this is the place pip put Material theme after downloaded.

Under path `material\partials\footer.html`, delete the footer.

You can do other customization of theme Material in this folder as well.

## Extensions

Extensions currently I use are:

1. __Admonition__: is an extension included in the standard Markdown library that makes it possible to add block-styled side content to your documentation, for example summaries, notes, hints or warnings.
2. __CodeHilite__: is an extension that adds syntax highlighting to code blocks and is included in the standard Markdown library. The highlighting process is executed during compilation of the Markdown file.
3. __PyMdown__: Extensions is a collection of Markdown extensions that add some great features to the standard Markdown library. For this reason, the installation of this package is highly recommended as it's well-integrated with the Material theme.

