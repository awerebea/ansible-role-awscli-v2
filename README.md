# Ansible Role: AWS Command Line Interface (CLI) version 2

An Ansible Role that installs [AWS CLI version 2](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html) on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    # If no version is specified, the latest version will be installed.
    awscli_version: v2.x.x

    # If no installation directory is specified, /usr/local/aws-cli is used.
    awscli_install_dir: $HOME/.local/aws-cli

    # The path containing a symbolic link to the main aws program in the installation directory.
    # If not specified, /usr/local/bin is used.
    awscli_bin_dir: $HOME/.local/bin

    # List of user environment files to add conditional export to the system PATH of a directory with symbolic links.
    # Only existing files with write access for the current ansible_user will be processed.
    # If not specified, empty list is used.
    awscli_env_files_to_modify:
      - $HOME/.profile
      - $HOME/.bashrc
      - $HOME/.zshenv

## Dependencies

`unzip` - UNZIP(1) Linux command line utility for the ansible built-in `unarchive` module to work.

## Example Playbook

```yaml
- hosts: all
  roles:
    - ansible-role-awscli-v2
```

## License

MIT
