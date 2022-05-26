# stateful CLI

```
$ stateful help
```

## Installation

> You can replace "latest" with a specific [released version](https://github.com/stateful/cli/releases).

### macOS

The most convenient way is to use [Homebrew](https://brew.sh/):

```
$ brew install stateful/tap/stateful
$ stateful --help

# Upgrade is also trivial
$ brew upgrade stateful
```

### Linux

#### Ubuntu

You can download a `deb` package:

```
# Linux (arch: arm64, x86_64, i386)
$ curl -LO "https://download.stateful.com/stateful-cli/latest/stateful_linux_<arch>.deb"
$ dpkg -i stateful_linux_<arch>.deb
```

#### Alpine

You can download an `apk` package:

```
# Linux (arch: arm64, x86_64, i386)
$ curl -LO "https://download.stateful.com/stateful-cli/latest/stateful_linux_<arch>.apk"
$ apk add --allow-untrusted stateful_linux_<arch>.apk
```

#### RedHat/CentOS

You can download a `rpm` package:

```
# Linux (arch: arm64, x86_64, i386)
$ curl -LO "https://download.stateful.com/stateful-cli/latest/stateful_linux_<arch>.rpm"
$ rpm -i stateful_linux_<arch>.rpm

# Or using yum
$ yum localinstall stateful_linux_<arch>.rpm
```

### Windows

The most convenient way is to use [Scoop](https://scoop.sh/):

```
$ scoop bucket add stateful https://github.com/stateful/scoop-bucket.git
$ scoop install stateful/stateful
$ stateful version
```

### Binary installation

Download a binary directly:

```
# Linux (arch: arm64, x86_64, i386)
$ curl -LO "https://download.stateful.com/stateful-cli/latest/stateful_linux_<arch>.tar.gz"
$ tar -xvf stateful_linux_<arch>.tar.gz

# macOS (arch: arm64, x86_64)
$ curl -LO "https://download.stateful.com/stateful-cli/latest/stateful_darwin_<arch>.tar.gz"
$ tar -xvf stateful_linux_<arch>.tar.gz

# Windows (with PowerShell) (arch: arm64, x86_64, i386)
$ curl.exe -LO "https://download.stateful.com/stateful-cli/latest/stateful_windows_<arch>.zip"
$ Expand-Archive -Path stateful_windows_<arch>.zip
```

## Configuration

Configuration of the CLI is possible through the following ways:
* CLI flags which can be viewed using `stateful help` command
* A config file which by default is located in `$HOME/.config/stateful/config.yaml`. It can be changed using `--config` flag (note: only `yaml` format is supported)
* Using environment variables, for example to override `--api-url` use `export STATEFUL_API_URL=<value>`

## Authorization

The current authorization flow uses [GitHub OAuth web application flow](https://docs.github.com/en/developers/apps/building-oauth-apps/authorizing-oauth-apps#web-application-flow).

It saves the GitHub token locally in `$HOME/.config/stateful`.

The next step is to exchange it for a JWT token using `/auth/vscode` endpoint. It is refresh transparently whenever needed.

## Logging

You can enable logs with `--debug`. Additionally, you can also enable logging of HTTP traffic with `--trace` and `--trace-all` flags. The latter might print sensitive information during authorization flow so be careful.

Logs are printed to `stderr` while regular output to `stdout`. In order to redirect logs to a file, use your shell's features:
```
$ stateful standup --debug --trace 2>stateful.log
```
