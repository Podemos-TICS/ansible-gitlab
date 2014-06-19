Gitlab
======

Installs [gitlab](https://github.com/gitlabhq/gitlabhq/) from git.
Generally follows the installation document on their site.

Based on gdamjan.gitlab

Only tested in Ubuntu 14.04 server

Requirements
------------

The role is created for Debian-like OS's. Installs nginx as a frontend.


Role Variables
--------------

The role uses the following variables, that you can also override:

* `gitlab_hostname` - override to set the name of the virtual host, also used for email (defaults to `ansible_hostname`)
* `gitlab_branch` - gitlab branch to checkout
* `gitlab_shell_version` - gitlab shell version to checkout
* `gitlab_db_type` - database type to use (mysql by default)
* `gitlab_db_name` - database name (gitlab)
* `gitlab_db_user` - database user (gitlab)
* `gitlab_db_passwd` - database password (probably should change this, it's some random string now)
* `gitlab_user` - system user that's needed for ssh access
* `gitlab_uwsgi_port` - port used for nginx - uwsgi communucation
* `gitlab_ssh_port` - override if using different port for ssh (22 by default)


Usage
-----

    ansible-galaxy install raulkite.gitlab

    Create a gitlab.yml with this content:
    ```
    ---
    - hosts: all
      user: root

      pre_tasks:
      - name: apt get update
        apt: update_cache=yes

      vars:
        gitlab_hostname: "gitlab.test.com"                                                             
 
      roles:
      - raulkite.gitlab

    ```

Also check the [Ansible Galaxy](https://galaxy.ansibleworks.com/intro) about page.


License
-------

BSD

Author and other Information
----------------------------

Raul Sanchez <raul@um.es>

[GitHub project page](https://github.com/raulkite/ansible-gitlab)
