# gitprofile

A command-line utility that helps you easily switch between different Git configurations. Useful for managing multiple Git identities (e.g., work, personal, open source) without manually changing Git configurations each time.

## Features

- Switch between predefined Git profiles
- Maintain separate email addresses and usernames for different contexts
- Keep your Git commits properly attributed across different projects

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/gitprofile.git
    ```
2. Navigate to the project directory:
    ```sh
    cd gitprofile
    ```
3. Make the script executable:
    ```sh
    chmod +x gitprofile
    ```
4. Move the script to a directory in your PATH, for example:
    ```sh
    sudo mv gitprofile /usr/local/bin/
    ```

## Usage

```sh
gitprofile <profile_name> [-c|--config <config_file>] [-g|--global]
```

### Options

- `-c, --config <config_file>`: Override the default config file path.
- `-g, --global`: Set git config globally.
- `-h, --help`: Display help information.
- `-v, --version`: Display the version of gitprofile.

### Examples

Switch to the "work" profile:
```sh
gitprofile work
```

Switch to the "personal" profile using a custom config file:
```sh
gitprofile personal -c /path/to/custom/gitprofile.toml
```

Set the "opensource" profile globally:
```sh
gitprofile opensource -g
```

## Configuration

The configuration file is a TOML file that defines different profiles. Here is an example configuration:

```toml
# Common Git configurations applied to all profiles
[common]
core.editor = "vim"
core.autocrlf = "input"
init.defaultBranch = "main"
pull.rebase = true
fetch.prune = true
merge.ff = "only"
pull.ff = "only"

# Useful git aliases
alias.lg = "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
alias.st = "status -sb"
alias.co = "checkout"
alias.br = "branch"

# Work profile
[work]
user.name = "John Doe"
user.email = "john.doe@company.com"
user.signingkey = "YOUR_SIGNING_KEY"
commit.gpgsign = true

# Personal profile
[personal]
user.name = "John Doe"
user.email = "john.personal@gmail.com"
user.signingkey = "YOUR_PERSONAL_SIGNING_KEY"

# Open source profile
[opensource]
user.name = "John Doe"
user.email = "john.opensource@gmail.com"
commit.gpgsign = true
```

## License

This project is licensed under the MIT License.
