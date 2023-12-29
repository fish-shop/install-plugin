<img alt="fish" src="images/fish-market.png" width="160" align="right">

# fish-shop/install-plugin

[![Tests](https://img.shields.io/github/actions/workflow/status/fish-shop/install-plugin/test.yml?branch=main&color=brightgreen&label=tests)](https://github.com/fish-shop/install-plugin/actions) [![Issues](https://img.shields.io/github/issues/fish-shop/install-plugin)](https://github.com/fish-shop/install-plugin/issues) [![Dependabot](https://img.shields.io/badge/dependabot-active-brightgreen.svg)](https://github.com/fish-shop/install-plugin/network/dependencies) [![License](https://img.shields.io/badge/license-MIT-blue)](https://opensource.org/licenses/mit-license.php) [![fish](https://img.shields.io/badge/fish-3.2.2-blue)](https://fishshell.com)

A GitHub action for installing [fish shell](https://fishshell.com) plugins.

<hr>

## Prerequisites

This action requires the [fish shell](https://fishshell.com). You can install it using the [fish-actions/install-fish](https://github.com/fish-actions/install-fish) action.

## Usage

Add a suitable `uses` step to your GitHub [workflow](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions) and specify the plugin manager and plugin(s) to be installed by providing values for the `plugin-manager` and `plugins` inputs respectively:

```yaml
jobs:
  install-plugin:
    runs-on: ubuntu-latest
    steps:
      - name: Install Pond plugin with Fisher
        uses: fish-shop/install-plugin@v2
        with:
          plugin-manager: fisher
          plugins: marcransome/pond
```

The value provided for the `plugins` input is passed _unchanged_ as an argument to the `install` command of the specified plugin manager. In most cases this means multiple plugins may be installed at the same time, however this is dependent upon the plugin manager being used. Refer to the official documentation for the chosen plugin manager for details (see [Supported plugin managers](#supported-plugin-managers) for a list of supported tools and links to their respective project repositories).

The plugin manager will be installed only if not already present. If your workflow job contains multiple `install-plugin` actions that use the same plugin manager then only the first action will install the plugin manager.

If you wish to install a plugin manager in isolation, without installing any plugins at the same time, consider using the [fish-shop/install-plugin-manager](https://github.com/fish-shop/install-plugin-manager) action instead.

## Supported plugin managers

The following table lists the supported plugin managers and the corresponding `plugin-manager` input value to use in your workflow:

| Plugin manager                                         | `plugin-manager` value |
|--------------------------------------------------------|------------------------|
| [Fisher](https://github.com/jorgebucaran/fisher)       | `fisher`               |
| [Oh My Fish](https://github.com/oh-my-fish/oh-my-fish) | `oh-my-fish`           |
| ~~[plug.fish](https://github.com/kidonng/plug.fish)~~  | ~~`plug.fish`~~[^1]    |

[^1]: `plug.fish` support was removed in `v2.0.0` due to functional changes made in recent versions of this plugin manager.

## Action versions

Use one of the following patterns when specifying the version reference for this action in your workflow (i.e. the `{ref}` value in `uses: fish-shop/install-plugin@{ref}`):

| Pattern  | Example   | Description                                                            |
|----------|-----------|------------------------------------------------------------------------|
| `vX`     | `v2`      | the latest `v2.*` release including non-breaking changes and bug fixes |
| `vX.Y`   | `v2.1`    | the latest `v2.1.*` release including bug fixes                        |
| `vX.Y.Z` | `v2.1.0`  | the `v2.1.0` release only                                              |

> [!TIP]
> The recommended pattern is `vX` (e.g. `v2`). This will ensure that the version of the action used in your workflow includes the latest non-breaking changes and bug fixes, and guarantees compatibility with previous versions of that major release number.

Using a `main` branch reference in your workflow is _not_ recommended as this branch may include breaking changes intended for the next major release.

## Other GitHub actions

A number of related composite actions are also available from the [fish-shop](https://github.com/fish-shop) 🐟. Check them out:

* [fish-shop/syntax-check](https://github.com/fish-shop/syntax-check) - A GitHub action for syntax checking fish shell files
* [fish-shop/install-plugin-manager](https://github.com/fish-shop/install-plugin-manager) - A GitHub action for installing a fish shell plugin manager
* [fish-shop/run-fishtape-tests](https://github.com/fish-shop/run-fishtape-tests) - A GitHub action for running Fishtape tests

## Acknowledgements

* Fish market icon made by [Freepik](https://www.flaticon.com/authors/freepik) from [www.flaticon.com](https://www.flaticon.com/)

## License
`fish-shop/install-plugin` is provided under the terms of the [MIT License](https://opensource.org/licenses/mit-license.php).

## Contact
Email me at [marc.ransome@fidgetbox.co.uk](mailto:marc.ransome@fidgetbox.co.uk) or [create an issue](https://github.com/fish-shop/install-plugin/issues).
