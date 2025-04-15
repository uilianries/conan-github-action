# Install Conan Action

[![Validate Conan Action](https://github.com/uilianries/conan-github-action/actions/workflows/ci.yml/badge.svg?branch=master)](https://github.com/uilianries/conan-github-action/actions/workflows/ci.yml)

A GitHub Action to install and configure the Conan package manager in your workflow. This action provides a simple and flexible way to set up Conan with custom configurations and audit settings.

## Features

- 🚀 Install any version of Conan
- ⚙️ Apply custom Conan configurations
- 🔐 Configure audit tokens
- 💪 Cross-platform support
- 🔄 Composite action for better reliability

## Usage

### Basic Usage

Install Conan, authenticate to Audit server and install custom configurations:

```yaml
steps:
  - name: Checkout code
    uses: actions/checkout@v4

  - name: Install Conan
    uses: uilianries/conan-github-action@v1
    with:
      audit_token: ${{ secrets.CONAN_AUDIT_TOKEN }}
      config_urls: 'https://github.com/<org>/conan-config.git,https://myrepo.com/conan-config.git'

  - name: Install Conan dependencies
    run: conan install . --build=missing
```

## Options

This Github Action offers options inputs to execute extra steps just after installing Conan.
This is useful for installing custom configurations or applying any other setup you need.
It's possible to customize the action using the following options:

| Option         | Description                                                                                                    |
|----------------|----------------------------------------------------------------------------------------------------------------|
| `version`      | Conan client version to be installed. By default, it's the latest version available.                           |
| `home`         | A custom path to be used as Conan cache directory.                                                             |
| `audit_token`  | The Conan audit token to authenticate to the Audit server with Conan.                                          |
| `config_urls`  | URLs of the Git repositories containing the custom Conan configurations to be installed. It's comma separated  |


## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE.md) file for details.
