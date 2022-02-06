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

    # If the directory for downloading and extracting the installation archive is not specified, /tmp is used.
    awscli_download_dir: $HOME/Downloads

    # List of user environment files to add conditional export to the system PATH of a directory with symbolic links.
    # Only existing files with write access for the current ansible_user will be processed.
    # If not specified, empty list is used.
    awscli_env_files_to_modify:
      - $HOME/.profile
      - $HOME/.bashrc
      - $HOME/.zshenv

**NOTE:** By default, the base tasks of a role are skipped if the application is already installed in the desired
<br />bin directory (linked there) and no version upgrade is required.
<br />&nbsp;&nbsp;&nbsp;&nbsp;If you want to add a conditional export to the system `PATH` of a directory with the app binary, after the Playbook
<br />has already been run once, you can force the launch base role tasks by defining the `update_apps` variable
<br />and adding `awscli`, `aws` to the list. For example:
``` bash
$ ansible-playbook main.yaml -e "update_apps=[awscli]"
```
This approach is also used to force an update to the latest available release.

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
