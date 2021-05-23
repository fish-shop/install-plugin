# fish-shop/install-plugin

[![License](https://img.shields.io/badge/license-MIT-blue)](http://opensource.org/licenses/mit-license.php) [![fish](https://img.shields.io/badge/fish-3.2.2-blue)](https://fishshell.com) [![Issues](https://img.shields.io/github/issues/fish-shop/install-plugin)](https://github.com/fish-shop/install-plugin/issues)

A GitHub action for installing [fish shell](https://fishshell.com) plugins.

## Prerequisites

This action requires the [fish shell](https://fishshell.com). You can install it within jobs in your workflow using the [install-fish](https://github.com/fish-actions/install-fish) action.

## Usage

Add a suitable `uses` step to your GitHub [workflow](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions) and specify the plugin manager and plugin(s) to be installed by providing values for the `plugin-manager` and `plugins` inputs respectively:

```yaml
jobs:
  install-plugin:
    runs-on: ubuntu-latest
    steps:
      - name: Install Pond plugin with Fisher
        uses: fish-shop/install-plugin@1.0.0
        with:
          plugin-manager: fisher
          plugins: marcransome/pond
```

:warning: The value provided for the `plugins` input is passed unchanged as an argument to the `install` command of the specified plugin manager. In most cases this means multiple plugins may be installed at the same time, however this is dependent upon the plugin manager being used. Refer to the official documentation for the chosen plugin manager for details (see [Supported plugin managers](#supported-plugin-managers) for a list of supported tools).

The plugin manager will be installed only if not already present. If your workflow job contains multiple `install-plugin` actions that use the same plugin manager then only the first action will install the plugin manager.

If you wish to install a plugin manager without also installing any plugin(s) at the same time—for more complex workflows—consider using the [fish-shop/install-plugin-manager](https://github.com/fish-shop/install-plugin-manager) action instead.

## Supported plugin managers

The following table lists the supported plugin managers and the corresponding `plugin-manager` input value to use in your workflow:

| Plugin manager                                         | `plugin-manager` value |
|--------------------------------------------------------|------------------------|
| [Fisher](https://github.com/jorgebucaran/fisher)       | `fisher`               |
| [Oh My Fish](https://github.com/oh-my-fish/oh-my-fish) | `oh-my-fish`           |
| [plug.fish](https://github.com/kidonng/plug.fish)      | `plug.fish`            |

## License
`fish-shop/install-plugin` is provided under the terms of the [MIT License](http://opensource.org/licenses/mit-license.php).

## Contact
Email me at [marc.ransome@fidgetbox.co.uk](mailto:marc.ransome@fidgetbox.co.uk) or tweet [@marcransome](http://www.twitter.com/marcransome).
