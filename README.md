# Git Require

Git plugin script for incorporating a git repository in a project

This will allow using certain file(s) from one git project in another. This is helpful when coding plugins, and you want to track the main project and plugins independently but need to test them together.
The plugin will reside in its own git file system, and can be incorporated in the main project by symbolic links or by cloning (set in configuration).


## Getting Started

Copy git-require file to your bin folder and make sure it is executable.

Open the terminal in the directory containing the git repository,
and run the command `git require init`.
This will create the .git-require directory. If you do not want this to be included in your git repository, add .git-require to your .gitignore file

Takes the following optional parameters:
* `-l <license>` Use defined license
* `-r <path-to-remote>` Add a remote origin
* `-f` Force overwrite license
* `-h` Show usage options
* `-v` Display version

### Prerequisites

Intended for use on a linux system with bash. Not tested on windows.

### Installing

Copy git-create file to your bin folder and make sure it is executable.

## Authors

* **Joe Rothrock** - *Initial work* - [akmjoe](https://github.com/akmjoe)


## License

This project is licensed under the GPL License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Thanks to (adamcod.es)[https://adamcod.es/2013/07/12/how-to-create-git-plugin.html] for the tutorial on creating a git plugin.

