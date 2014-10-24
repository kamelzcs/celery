celery
=================

Ansible role which manage [celery](http://www.celeryproject.org/)
Ansible role apt which help you with:

* Install and manage [celery](http://www.celeryproject.org/)
* Provide handlers for reload and restart celery

#### Variables

The role variables and default values.

```yaml

# Names of nodes to start (space-separated)
celeryd_nodes: "default"

# Where to chdir at start. This could be the root of a virtualenv.
celeryd_chdir: "/home/site/src/apps"

# Absolute or relative path to the celery program
celery_bin: "/usr/local/bin/celery"

# App instance to use (value for --app argument).
celery_app: "proj.celery:app"

# How to call celeryd-multi
#CELERYD_MULTI:"$CELERYD_CHDIR/bin/celeryd-multi"

# Extra arguments
#CELERYD_OPTS:"--time-limit=300 --concurrency=8 --loglevel=DEBUG"

# Create log/pid dirs, if they don't already exist
celery_create_dirs: 1

# - %n will be replaced with the first part of the nodename.
# - %I will be replaced with the current child process index
#   and is important when using the prefork pool to avoid race conditions.
celeryd_log_dir: "/var/log/celery"
celeryd_pid_file: "/var/run/celery/%n.pid"

# Workers run as an unprivileged user
celeryd_user: "celery"
celeryd_group: "celery"

```

#### Usage

Add `kamelzcs.celery` to your roles and set vars in your playbook file.

Example:

```yaml

- hosts: all

  roles:
    - kamelzcs.celery

  vars:
    celeryd_user: "celery"
    celeryd_group: "celery"
```

#### License

Licensed under the MIT License. See the LICENSE file for details.

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/kamelzcs/celery/issues)!
