# DEPRECATED

Now included in my [JetBrains Collection](https://github.com/diademiemi/ansible_collection_diademiemi.jetbrains)

# Ansible Role PyCharm
This is an Ansible role that installs PyCharm on Linux. It uses the tarball from the official website so this role is not dependent on any package manager.  
It can take a list of plugin IDs which it will automatically install.  

Tested on Fedora 36 with PyCharm 2022.3, should work on any Linux distribution that the PyCharm tarball supports.  

## Requirements

### Base requirements
None  

### Installing plugins
Plugins are installer per-user, so you will need to give `pycharm_user`, this defaults to `{{ ansible_user_id }}`.  

## Variables
| Variable | Default | Description |
|----------|---------|-------------|
| `pycharm_edition` | `IC` | Default version of PyCharm to download. Valid options are: `[community, professional]` |
| `pycharm_version` | `2022.2.3` | Default version of PyCharm to download |
| `pycharm_url` | See [defaults/main.yml](./defaults/main.yml) | Base URL for the PyCharm tarball |
| `pycharm_user` | `{{ ansible_user_id }}` | User to install plugins for. |

## Installing plugins
To install plugins for PyCharm, define the `pycharm_plugins` variable.  
```yaml
pycharm_plugins:
  - 10233 # Discord Integration
  - 17718 # GitHub Copilot
```

You can get this ID by going to the plugin homepage from PyCharm's Plugins tab and copying the number from the URL it opens.  
