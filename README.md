# Git Require

Git plugin script for incorporating a git repository in a project

This will allow using certain file(s) from one git project in another. This is helpful when coding plugins, and you want to track the main project and plugins independently but need to test them together.
The plugin will reside in its own git file system, and can be incorporated in the main project by symbolic links or by cloning (set in configuration).


## Getting Started

### Prerequisites

Intended for use on a linux system with bash. Not tested on windows.

### Installing

Copy git-require file to your bin folder and make sure it is executable.

### Initializing

Open the terminal in the directory containing the git repository,
and run the command `git require init`.
This will create the .git-require directory. If you do not want this to be included in your git repository, add .git-require to your .gitignore file

Now run the command `git require add <name> <source> [<destination>]`

Takes the following optional parameters:
* `-c` Copy the files instead of using symbolic links

This will stage the files. To copy them, run `git require update [<source>]`. If no source is provided, all will be updated.

To remove a require, run `git require remove <source>`. This will stage it for removal when update is called.

There is a global exclude file located in the .git-require directory. These paths use basic wildcard matching - they are sent to the `find` command.
Each require source is saved in a directory within .git-require under the `name` parameter. Within this directory are the configuration files for this source.
Each named require can have multiple source-destination combinations.

If the source is a file instead of a directory, the file will be copied to the destination exactly, so make sure the destination path includes the desired filename.

* `update [-f] [<name>]` Copies/links the files, removing any removed from the source. The `-f` option will force overwrite existing files.
* `info` This file contains the tab-separated configuration parameters source path, destination path, and copy mode (true for copy, false for symbolic links)
* `list` This file contains a list of files that were copied/linked from the source. This is used to check for conflicts and to know what to remove.
* `exclude` (Optional) This file can be used to provide source-specific excludes.
* `status [-o]` Shows if uncommited changes in require sources (if they are git directories). The `-o` option opens directories with changes in a new terminal.
* `disable [<name>]` Disables a require. Disabled requires will be removed on update, but no information is lost. Se also `remove`. 
* `enable [<name>]` Re-enables a require.
* `remove <name>` Permanently removes a require.
* `all "<command>"` Run a git command on all source git directories

To see all options, run `git require --help`

## Authors

* **Joe Rothrock** - *Initial work* - [akmjoe](https://github.com/akmjoe)


## License

This project is licensed under the GPL License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Thanks to (adamcod.es)[https://adamcod.es/2013/07/12/how-to-create-git-plugin.html] for the tutorial on creating a git plugin.

