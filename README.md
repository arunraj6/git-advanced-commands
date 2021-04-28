# Advanced GIT commands

Work with some advanced GIT commands

- [General](#config)
- [Amend](#amend)
- [Sqash & Merge](#sqash-merge)
- [Reset](#reset)
- [Revert](#revert)
- [Rebase](#rebase)
- [Cherry pickking](#cherry-pick)
- [Tagging](#tag)

## Config file<span id="config"></span>

### default editor

Setting the VS code as default editor.

    git config --global core.editor code

Command to view the config file in the default editor.

    git config --global -e

See the content inside the global config file without opening the file.

    git config --global --list

### default diff and merge tool

### log

## Amend<span id="amend"></span>


Git amend commands can rewrites the history by updating the previous commits details like message, adding or removing a file, changing a part of the code, etc..

Change the previous commit message

    git commit —amend -m "updated message here"

All the amend original commits are called unreachable and will not be a part of any branch history.

## reflog

reflog comments can be used to see the unreachanble commits.
Normal log will not display the reachable commits.

    git reflog

it is possible to point the head to the unreachable commit and create a new branch with that and start reworking with it to make this commit a valid reachable one.

reflog can also be used to clean unreachable commits.

    git reflog expire --expire-unreachable=now --all

This command, the git creates a variable for the garbage collector for the burning pruning operation

To clear the unreachable 

    git gc —prune=now

The git log and reflog does the same except the case of unreachable

### clear unreachables

## Sqash & Merge <span id="sqash-merge"></span>

### Sqash

## Reset <span id="reset"></span>

### soft

### hard

## Revert <span id="revert"></span>

## Rebase <span id="rebase"></span>

## Cherry-pick <span id="cherry-pick"></span>

## Tagging <span id="tag"></span>

### Light-weight

### Annotated
