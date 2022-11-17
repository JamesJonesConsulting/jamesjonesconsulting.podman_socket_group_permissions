# Ansible Collection 
## `jamesjonesconsulting.podman_socket_group_permissions`

This collection is for setting up Podman to _act_ more like Docker particularly for automation that specifically
supports Docker and needs to make use of the docker socket (like docker-compose, Azure DevOps, GitLab and Github Actions).

Currently, this collection contains 'one' role that `jamesjonesconsulting.permissions_setup` that sets up a user group that
has permissions to the socket and integrates pretty seemlessly into the tools I aformentioned. 

## Usage

The role is called like this in an ansible playbook (note: you will need to be running `ansible-core`)

```
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

The `podman_user_group` variable 'defaults' to the 'docker' group and can be exluded _unless_ you want to use a different group. Members of this group
can access the socket. If you are installing agents like Azure DevOps's VSTS agent, Gitlab Runners or Github Action Agents, you'll need to include
those users in the `podman_users` variable list as they will be added to that group (it will be created if it doesn't exist).

## Setup

Usually you have a `requirements.yml` file you can specify the collection like this:

```
collections:
  - name: https://github.com/JamesJonesConsulting/jamesjonesconsulting.podman_socket_group_permissions.git
    type: git
    version: main
```

Or, you can just install it via command line as well like this:

```
ansible-galaxy collection install git+https://github.com/JamesJonesConsulting/jamesjonesconsulting.podman_socket_group_permissions.git,main
```
