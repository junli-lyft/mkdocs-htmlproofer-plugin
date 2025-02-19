# mkdocs-htmlproofer-plugin [![PyPI - Version](https://img.shields.io/pypi/v/mkdocs-htmlproofer-plugin.svg)](https://pypi.org/project/mkdocs-htmlproofer-plugin)

*A [MkDocs](https://www.mkdocs.org/) plugin that validates URL in rendered html files*

## Table of Contents

* [Installation](#installation)
* [Acknowledgement](#acknowledge)

## Installation

0. Prerequisites

* Python >= 3.6
* MkDocs >= 0.17

1. Install the package with pip:

```bash
pip install mkdocs-htmlproofer-plugin
```

2. Enable the plugin in your `mkdocs.yml`:

```yaml
plugins:
    - search
    - htmlproofer
```

Optionally, you may raise error and fail the build on bad url status.

```yaml
plugins:
    - search
    - htmlproofer:
        raise_error: True
```

That can be switched off for combinations of urls (`'*'` means all urls) and status codes with `raise_error_excludes`.

```yaml
plugins:
    - search
    - htmlproofer:
        raise_error: True
        raise_error_excludes: 
          504: ['https://www.mkdocs.org/']
          404: ['https://github.com/manuzhang/mkdocs-htmlproofer-plugin']
          400: ['*']
```

> **Note:** If you have no `plugins` entry in your config file yet, you'll likely also want to add the `search` plugin. MkDocs enables it by default if there is no `plugins` entry set, but now you have to enable it explicitly.

More information about plugins in the [MkDocs documentation](https://www.mkdocs.org/user-guide/plugin)

## `localhost` URLs

`localhost` URLs are safely ignored by `mkdocs-htmlproofer-plugin` and will not raise warnings:

- <http://localhost>

- <http://127.0.0.1>

- <https://localhost>

- <https://127.0.0.1>

## Acknowledgement

This work is based on the [mkdocs-markdownextradata-plugin](https://github.com/rosscdh/mkdocs-markdownextradata-plugin) project and the [Finding and Fixing Website Link Rot with Python, BeautifulSoup and Requests](https://www.twilio.com/blog/2018/07/find-fix-website-link-rot-python-beautifulsoup-requests.html) article. 
