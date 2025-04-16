# Install Conan Action

[![Validate Conan Action](https://github.com/uilianries/conan-github-action/actions/workflows/ci.yml/badge.svg?branch=master)](https://github.com/uilianries/conan-github-action/actions/workflows/ci.yml)
[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-Conan%20Package%20Manager-blue.svg?colorA=24292e&colorB=0366d6&style=flat&longCache=true&logo=github)](https://github.com/marketplace/actions/conan-io-github-action)


A GitHub Action to install and configure the Conan package manager in your workflow.
This action provides a simple and flexible way to set up Conan with custom configurations and audit settings.

## Features

- 🚀 Install any version of Conan
- ⚙️ Apply custom Conan configurations
- 🔐 Configure audit tokens
- 🗂️ Cache Conan packages using GitHub cache
- 🔍 Support for custom Conan cache directory
- 🔗 Support for multiple configuration URL
- 🧩 Support for multiple remote URL
- 💪 Cross-platform support
- 🔄 Composite action for better reliability

## Usage

### Basic Usage

Install Conan, authenticate to Audit server, install custom configurations and configure remotes:

```yaml
steps:
  - name: Checkout code
    uses: actions/checkout@v4

  - name: Install Conan
    uses: uilianries/conan-github-action@v1
    with:
      audit_token: ${{ secrets.CONAN_AUDIT_TOKEN }}
      config_urls: 'https://github.com/<org>/conan-config.git,https://myrepo.com/conan-config.git'
      remotes: 'https://mycompany/artifactory/api/conan/conan-local,https://worldwide.org/artifactory/api/conan/conan-remote'

  - name: Install Conan dependencies
    run: conan install . --build=missing
```

## Options

This Github Action offers options inputs to execute extra steps just after installing Conan.
This is useful for installing custom configurations or applying any other setup you need.
It's possible to customize the action using the following options:

| Option           | Type    | Description                                                                                                    |
|------------------|---------|----------------------------------------------------------------------------------------------------------------|
| `version`        | string  | Conan client version to be installed. By default, it's the latest version available.                           |
| `home`           | string  | A custom path to be used as Conan cache directory.                                                             |
| `audit_token`    | string  | The Conan audit token to authenticate to the Audit server with Conan.                                          |
| `config_urls`    | list    | URLs of the Git repositories containing the custom Conan configurations to be installed. It's comma separated  |
| `cache_packages` | boolean | Cache all stored Conan packages, under Conan cache, using Github cache support. false by default               |
| `remotes`        | list    | A list of remote URLs to be added to the Conan configuration. It's comma separated.                            |


## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE.md) file for details.
