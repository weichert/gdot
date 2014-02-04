# gdot #

/ˈɡɪdoʊ/ GID-oh/ waiting for the dead-simple dotfile manager

Gdot is an extremely small deployment tool that uses Git as its back-end.
It only has a few commands and relies on Git commands for most of the actual work.

The workflow with this tool will require you to track a file, thus adding it to a git repository and creating a symbolic link in its place, and then commit any changes to that file as you normally would with Git.

## commands ##

__`init`__ will create an empty Gdot repository or reinitialize an existing one. This is how you bootstrap your Gdot setup.

__`status`__ will show you the status of the symlink setup. It will however not show any changes to the content. This command will traverse the whole deploy tree and as such will take some time.

__`track`__ will add a file to the repository and put a symlink in its place.

__`untrack`__ will remove the file from the repository and the symlink to this file and restore it to its place. This command will automatically clean.

__`deploy`__ will create symlinks to files in the repository if necessary. You probably want to call this every time you check out or merge for example. This command will automatically clean.

__`clean`__ will clean the deploy tree from broken or renamed symlinks that point to the repository. This command will traverse the whole deploy tree and as such will take some time.

__`git`__ You will need git for anything else as the actual repository is still just a regular git repository. This command is a convenient wrapper that executes any command given to it in the Gdot repository.

## files ##

__`.gdotignore`__ should contain any files and directories you do not want to traverse. Please note that this is not a safety feature and does not stop `deploy` from putting files there. But it does stop `status` and any `clean` from traversing the whole deploy tree and as such is meant to save you time.
