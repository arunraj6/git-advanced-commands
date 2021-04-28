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

## Squash & Merge <span id="sqash-merge"></span>

squash command will take multiple commits and it will be combained to one commit.

    git checkout main
    git merge --squash bugfix

Consider if we have a series of commit in bugfix branch
the above commands will squash all those commits into a single commit and will be merge into branch main

This way we can keep the history in a concise way.

## Reset <span id="reset"></span>

reset command will be used to unstage the changes from the staging area.
or we can use it for to go back to a particular commit and able to rework on that specific commit.

There are 2 type for reset aviliable

### 1. soft

this will unstage all the files from staged area or from a some specific commit

    git reset head
    git reset index.html
    git reset 09c02f0
### 2. hard

this will completelly wipe out the changes from the staging area

    git reset head --hard
    git reset 09c02f0 --hard

## Revert <span id="revert"></span>

## Rebase <span id="rebase"></span>

## Cherry-pick <span id="cherry-pick"></span>

## Tagging <span id="tag"></span>

### Light-weight

### Annotated
