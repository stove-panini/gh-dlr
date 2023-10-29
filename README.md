gh-dlr
======
_A GitHub release downloader_

Maybe a program you love isn't in your repos. Maybe [brew](https://docs.brew.sh/Homebrew-on-Linux) has it but you don't wanna set up brew. But hey, there's a release on GitHub...
```
usage: gh-dlr [-h] [-c CONFIG_FILE]

options:
  -h, --help      show this help message and exit
  -c CONFIG_FILE  Path to config file. Default: ~/.config/gh-dlr/config.yaml
```
Requirements
------------
* Some reasonably recent version of Python 3.
* [PyYAML](https://pyyaml.org), for reading the config file.

Your distro most likely has PyYAML packaged as `python3-yaml` or `python3-pyyaml`.

Config file
-----------
There are two main sections in the config file: the map of **defaults** and the list of **releases**. The settings below could go in either section, but some make more sense as defaults than others. See [example-config.yaml](example-config.yaml) for further detail.

Settings in bold are required.
| setting | description |
| ------- | ----------- |
| **name** | User-selected, unique name for this config entry |
| **repo** | GitHub repo like username/reponame |
| **tag**  | Tag of the release |
| **file** | Filename to download from the assets portion of the release |
| **dest** | Download destination of **file** |
| before_script | Shell script to run before downloading **file** |
| after_script  | Shell script to run after downloading **file** |
| creates | Filepath of the "end result" after running scripts |
| draft |  Whether to download draft releases |
| prerelease | Whether to download prereleases |

You can also use special substitution variables in the config file.

| variable | value |
| -------- | ----- |
| @d | "dest" from config |
| @f | "file" from config |
| @n | "name" from release data |
| @t | "tag_name" from release data |
| @v | If tag_name is a version string like "vX.X.X", this strips the "v" prefix |

Before & after scripts
----------------------
This will run anything you define as a script, so please be careful. There shouldn't be any reason to run this as root. Just don't do it!

Automatic updates via systemd
-----------------------------
Check the [contrib](contrib/) directory ;)
