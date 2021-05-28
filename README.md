# fish-shop/install-plugin

[![Tests Status](https://github.com/fish-shop/install-plugin/actions/workflows/test.yml/badge.svg)](https://github.com/fish-shop/install-plugin/actions?query=workflow%3Atests) [![License](https://img.shields.io/badge/license-MIT-blue)](http://opensource.org/licenses/mit-license.php) [![fish](https://img.shields.io/badge/fish-3.2.2-blue)](https://fishshell.com) [![Issues](https://img.shields.io/github/issues/fish-shop/install-plugin)](https://github.com/fish-shop/install-plugin/issues)

A GitHub action for installing [fish shell](https://fishshell.com) plugins.

## Prerequisites

This action requires the [fish shell](https://fishshell.com). You can install using the [fish-actions/install-fish](https://github.com/fish-actions/install-fish) action.

## Usage

Add a suitable `uses` step to your GitHub [workflow](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions) and specify the plugin manager and plugin(s) to be installed by providing values for the `plugin-manager` and `plugins` inputs respectively:

```yaml
jobs:
  install-plugin:
    runs-on: ubuntu-latest
    steps:
      - name: Install Pond plugin with Fisher
        uses: fish-shop/install-plugin@v1
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
| [plug.fish](https://github.com/kidonng/plug.fish)      | `plug.fish`            |

## Action versions

Use one of the following patterns when specifying the version reference for this action in your workflow (i.e. the `{ref}` value in `uses: fish-shop/install-plugin@{ref}`):

* The major version tag (e.g. `v1`) - will always point at the latest `v1.*` release and will include non-breaking changes and bug fixes
* The minor version tag (e.g. `v1.1`) - will always point at the latest `v1.1.*` release and will include bug fixes
* The patch version tag (e.g. `v1.1.0`) - will always point at the `v1.1.0` release
* The branch reference `main` - will include the latest changes from the `main` branch
* A specific commit SHA (e.g. `c3aad46b6014e86ab163e323bdfc79c987de0eba`)

The recommended form is `vX` (e.g. `v1`). This will ensure that the version of the action used in your workflow includes the latest non-breaking changes and bug fixes, and guarantees compatibility with previous versions of that major release number.


## License
`fish-shop/install-plugin` is provided under the terms of the [MIT License](http://opensource.org/licenses/mit-license.php).

## Contact
Email me at [marc.ransome@fidgetbox.co.uk](mailto:marc.ransome@fidgetbox.co.uk) or tweet [@marcransome](http://www.twitter.com/marcransome).
