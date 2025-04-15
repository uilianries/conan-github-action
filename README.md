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
      config_url: 'https://github.com/<org>/conan-config.git'

  - name: Install Conan dependencies
    run: conan install . --build=missing
```

## Options

It's possible to customize the action using the following options:

| Option         | Description                                                                                 |
|----------------|---------------------------------------------------------------------------------------------|
| `version`      | Conan client version to be installed. By default, it's the latest version available.        |
| `audit_token`  | The Conan audit token to authenticate to the Audit server.                                  |
| `config_url`   | The URL of the Git repository containing the custom Conan configurations to be installed.   |
| `config_source_folder`  | Install files only from a source subfolder from the specified origin.              |
| `config_target_folder`  | Install to that path in the conan cache.                                           |


## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE.md) file for details.
