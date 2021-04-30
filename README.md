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

## General<span id="config"></span>

### default editor

Setting the VS code as default editor:

    git config --global core.editor code

Command to view the config file in the editor:

    git config --global -e

See the content inside the global config file without opening the file:

    git config --global --list

### logs

To see the logs with complete details:

    git log

To see the logs in a much cleaner way:

    git log --oneline

To see the logs with the graph:

    git log --graph

Apply different filters on logs:

    git log --oneline @{1.day.ago}
    git log --oneline -3
    git log --author="John"

## Amend<span id="amend"></span>

Git amend commands can rewrite the history by updating the previous commits details like the message, adding or removing a file, changing a part of the code, etc...

To change the previous commit message:

    git commit —amend -m "updated message here"

All the amend original commits are called <b> unreachable </b>and will not be a part of any branch history.

## Reflog

reflog comments can be used to see the unreachable commits.
The normal log will not display the reachable commits.

    git reflog

It is possible to point the head to the unreachable commit and create a new branch with that and start reworking with it to make this commit a valid reachable one.

reflog can also be used to clean unreachable commits.

    git reflog expire --expire-unreachable=now --all

The above command, the git creates a variable for the garbage collector for the pruning operation

To run the GC:

    git gc —prune=now

## Squash & Merge <span id="sqash-merge"></span>

squash command will take multiple commits and combined them into a single commit.

    git checkout main
    git merge --squash bugfix

Consider, if we have a series of commits in bugfix branch
the above commands will squash all those commits into a single commit and will be merged into branch main with a single new commit.

This way we can concisely keep the history.

## Reset <span id="reset"></span>

reset command will be used to unstage the changes from the staging area
or we can use it to go back to a particular commit and able to rework that specific commit.

There are 2 types of reset available:

### soft

This will unstage all the files from the staged area or some specific commit.

    git reset head

    git reset index.html

    git reset 09c02f0

### hard

This will completely wipe out the changes from the staging area.

    git reset head --hard

    git reset 09c02f0 --hard

## Revert <span id="revert"></span>

revert command will help to undo a specific commit we made.

    git revert 09c02f0

## Rebase <span id="rebase"></span>

rebase a branch will result in a linear commit history, it looks like we never branch with master/ main.

## Cherry-pick <span id="cherry-pick"></span>

    git cherry-pick 09c02f0

## Tagging <span id="tag"></span>

A nice way to put a bookmark on the commits that are easy to find and also used to publish the information about the tag.

It’s common practice to prefix the version names with the letter v. Some good tag names might be v1.0 or v2.3.4.

To list all the available tags:

    git tag

There are 2 types of tag available:

### Lightweight

    git tag v1.0.0

### Annotated

This tag will have a few more additional information than the Lightweight tag.

    git tag -a v1.0.1

### Some additional commands related to tags

This will display all the tags that are part of version 1:

    git tag -l "v1*"

Can tag a specific commit in the past:

    git tag v0.0.0 09c02f0

Delate a tag:

    git tag -d v0.0.0

push the tags to the repo:

    git push --tags

The command that automatically push/pull the tags, don’t need to do separately:

     git config --global push.followTags true
