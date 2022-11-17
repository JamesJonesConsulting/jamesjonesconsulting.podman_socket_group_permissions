permissions_setup
=========

Sets up a user group that has permissions to the socket and integrates pretty seemlessly into tools like docker-compose, Azure DevOps, GitLab and Github Actions.

Requirements
------------

Requires `ansible-core` until this is published to Ansible Galaxy.

Role Variables
--------------

The `podman_user_group` variable 'defaults' to the 'docker' group and can be exluded _unless_ you want to use a different group. Members of this group
can access the socket. If you are installing agents like Azure DevOps's VSTS agent, Gitlab Runners or Github Action Agents, you'll need to include
those users in the `podman_users` variable list as they will be added to that group (it will be created if it doesn't exist).
A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

This role and it's parent collection require `ansible-core`.

Example Playbook
----------------

The role is called like this in an ansible playbook.


```
    - hosts: servers
      tasks:
        include_role:
          name: jamesjonesconsulting.permissions_setup
        vars:
          podman_user_group: docker
          podman_users:
            - moe
            - larry
            - curly
            - shimp
            - curly_joe
```

License
-------

LGPL-2.0-or-later

