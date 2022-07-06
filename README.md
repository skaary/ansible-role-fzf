# Ansible Role: fzf

[![CI](https://github.com/skaary/ansible-role-fzf/actions/workflows/ci.yml/badge.svg?branch=main&event=push)](https://github.com/skaary/ansible-role-fzf/actions?query=workflow%3Ci)

An Ansible Role that installs [fzf](https://github.com/junegunn/fzf) on Linux.

## Installation

Download the role directly from git by typing into your terminal:

```bash
$ ansible-galaxy install git+https://github.com/skaary/ansible-role-fzf.git
```
or

```bash
$ ansible-galaxy install git+https://github.com/skaary/ansible-role-fzf.git,,fzf
```

to change the installed role name from _ansible-role-fzf_ to just _fzf_.

Alternatively, install the role via a _requirements.yml_ file, e.g. when installing multiple roles at once. See [ansible galaxy documentation](https://galaxy.ansible.com/docs/using/installing.html#installing-multiple-roles-from-a-file) for more information.

## Role Variables

| Variable name       | Default value                         | Description                                                                                            |
| ------------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| `user`              | `{{ ansible_user_id }}`               | Set user.                                                                                              |
| `user_home`         | `{{ ansible_user_dir }}`              | Set user_home directory (e.g. "home/user")                                                             |
| `fzf_path`          | `{{ user_home }}/.config/fzf`         | Directory to place the fzf configuration in.                                                           |
| `fzf_path_git`      | `{{ fzf_path }}/fzf-git`              | Directory where the git repository will be downloaded to.                                              |
| `fzf_repo`          | `https://github.com/junegunn/fzf.git` | fzf github repository                                                                                  |
| `fzf_update_rc`     | `false`                               | Add sourcing ~/.fzf.bash to your normal shell config?                                                  |
| `fzf_completion`    | `false`                               | Enable/Disable fuzzy completion (bash & zsh)?                                                          |
| `fzf_key_bindings`  | `false`                               | Enable/disable key bindings (CTRL-T, CTRL-R, ALT-C)?                                                   |
| `fzf_template`      | `true`                                | Set to true to use custom paths for bash and zsh. If set to false, the default fzf script will be run. |
| `fzf_bash`          | `true`                                | Set to true to use `bashrc_location` and `fzf_bash_location`.                                          |
| `bashrc_location`   | `{{ user_home }}/.bashrc`             | Enter the path to your .bashrc.                                                                        |
| `fzf_bash_location` | `{{ fzf_path }}/.fzf.bash`            | The path .fzf.bash will be put in.                                                                     |
| `fzf_zsh`           | `false`                               | Set to true to use `zshrc_location` and `fzf_zsh_location`.                                            |
| `zshrc_location`    | `{{ user_home }}/.config/zsh/.zshrc`  | Enter the path to your .zshrc                                                                          |
| `fzf_zsh_location`  | `{{ fzf_path }}/.fzf.zsh`             | The path .fzf.zsh will be put in.                                                                      |

## Example playbook

```yaml
- hosts: all
  roles:
    - ansible-role-fzf
```

## Testing the role

### Vagrant

Vagrant can be used to test the role in order to graphically see it working in a virtual machine. Make sure Vagrant and VirtualBox are installed:

```bash
$ sudo apt install vagrant virtualbox
```

Use the following commands to run vagrant and boot up the virtual machine:

```bash
$ cd tests
$ vagrant up
```

Use `vagrant destroy` after you are done testing to delete the virtual machine. For more information about Vagrant and its commands, see the [Vagrant documentation](https://www.vagrantup.com/docs/cli).

### Molecule with Docker

Molecule can be used to test the role with a docker container. Make sure Molecule is installed:

```bash
$ python3 -m pip install --user "molecule[docker]"
```

Use the following commands to run Molecule in order to create the docker container and access the created container:
```bash
$ molecule converge && molecule login
```

For more information on how to use Molecule please consult the [Molecule documentation](https://molecule.readthedocs.io/en/latest/getting-started.html).

> Note: Python and Docker are required for the use of molecule. For more information, see [Molecule installation](https://molecule.readthedocs.io/en/latest/installation.html).

## License

MIT / BSD
