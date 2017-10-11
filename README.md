# docker

Master: [![Build Status](https://travis-ci.org/sansible/docker.svg?branch=master)](https://travis-ci.org/sansible/docker)  
Develop: [![Build Status](https://travis-ci.org/sansible/docker.svg?branch=develop)](https://travis-ci.org/sansible/docker)

* [ansible.cfg](#ansible-cfg)
* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Examples](#examples)

This role installs Docker and optional sets up a user for sudo-less usage.




## ansible.cfg

This role is designed to work with merge "hash_behaviour". Make sure your
ansible.cfg contains these settings

```INI
[defaults]
hash_behaviour = merge
```




## Installation and Dependencies

To install run `ansible-galaxy install sansible.docker` or add this to your
`roles.yml`.

```YAML
- name: sansible.docker
  version: v1.0
```

and run `ansible-galaxy install -p ./roles -r roles.yml`




## Tags

This role uses tags: **build** and **configure**

* `build` - Installs ...
* `configure` - Configures ...




## Examples

Simply include role in your playbook

```YAML
- name: Install and configure docker
  hosts: "somehost"

  roles:
    - role: sansible.docker
```

Setup user for sudo-less access:

```YAML
- name: Install and configure docker
  hosts: "somehost"

  roles:
    - role: sansible.docker
      docker:
        workspace_user: some_user
```

Note that if you want to make use of Docker via this user within the same
Ansible run then you will need to be aware of this issue: [https://github.com/ansible/ansible-modules-core/issues/921]().
