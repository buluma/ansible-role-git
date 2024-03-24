# Ansible role [git](https://galaxy.ansible.com/ui/standalone/roles/buluma/git/documentation)

Install and configure git on your system.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-git/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-git/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-git.svg)](https://github.com/buluma/ansible-role-git/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-git.svg)](https://github.com/buluma/ansible-role-git/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-git.svg)](https://github.com/buluma/ansible-role-git/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/git)](https://galaxy.ansible.com/ui/standalone/roles/buluma/git/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-git/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  vars:
    git_username: root
    git_groupname: root
    git_repository_destination: /root
    git_repositories:
      - repo: https://github.com/buluma/buluma.bootstrap
        dest: bootstrap
      - repo: https://github.com/buluma/buluma.bootstrap
        dest: bootstrap-force
        force: yes
      - repo: https://github.com/buluma/buluma.bootstrap
        dest: bootstrap-version
        version: "v2.0.0"

  roles:
    - role: buluma.git
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-git/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes
  serial: 30%

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-git/blob/master/defaults/main.yml):

```yaml
---
# defaults file for git

# The system username in /home where to place the gitconfig file.
# git_username: johndoe

# The group to own directories.
# git_groupname: "{{ git_username }}"

# Settings for git configuration.
# git_user_email: johndoe@example.com
# git_user_name: John Doe

# Where to place the copies of the repositories.
git_repository_destination: /home/{{ git_username | default('unset') }}/Documents/github.com/{{ git_username | default('unset') }}

# Should git force (overwrite locally changed) clone? (Can also be controlled
# per repository, see below.
git_force: no

# The repositories to check out, bootstrap is pinned to a version, java will get HEAD/latest.
# git_repositories:
#   - repo: https://github.com/robertdebock/ansible-role-bootstrap.git
#     dest: bootstrap
#     version: "2.2.4"
#   - repo: ssh://git@github.com/robertdebock/ansible-role-java.git
#     dest: java
#   - repo: ssh://git@github.com/robertdebock/ansible-role-tomcat.git
#     dest: tomcat
#     force: yes
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-git/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-git/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Alpine](https://hub.docker.com/r/buluma/alpine)|all|
|[Amazon](https://hub.docker.com/r/buluma/amazonlinux)|Candidate|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|8|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[opensuse](https://hub.docker.com/r/buluma/opensuse)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-git/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-git/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-git/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

