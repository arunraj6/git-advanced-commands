# Advanced GIT commands

Work with some advanced GIT commands

- [General](#config)
    - [Editor](#config-editor)
    - [Logs](#config-log)
- [Amend](#amend)
- [Sqash & Merge](#sqash-merge)
- [Reset](#reset)
    - [Soft](#reset-soft)
    - [Hard](#reset-hard)
- [Revert](#revert)
- [Rebase](#rebase)
- [Cherry pickking](#cherry-pick)
- [Tagging](#tag)
    - [Lightweight](#tag-lightweight)
    - [Annotated](#tag-annotated)

## General<span id="config"></span>

### default editor<span id="config-editor"></span>

Set the <b>VS Code</b> as default editor:

    git config --global core.editor code

View the config file in the editor:

    git config --global -e

See the content inside the global config file without opening the file:

    git config --global --list

### logs<span id="config-log"></span>

See the logs with complete details:

    git log

See the logs in a much cleaner way:

    git log --oneline

See the logs with the graph:

    git log --graph

Apply different filters on logs:

    $ git log --oneline @{1.day.ago}
    $ git log --oneline -3
    $ git log --author="John"

## Amend<span id="amend"></span>

GIT `amend` commands can rewrite the history by updating the previous commits details like the message, adding or removing a file, changing a part of the code.

    git commit —amend -m "updated message here"

The above command will change the commit message of the most recent commit. Also, it will take the present changes from the stage area if any, and add them to this amend commit.

All the amend original commits are called <b>unreachable</b> and will not be a part of any branch history.

## Reflog

GIT `reflog` commands can be used to see the unreachable commits.
The normal GIT `log` will not display the unreachable commits.

    git reflog

It is possible to point the head to a specific unreachable commit then we can create a new branch out of it to start reworking.

`reflog` can also be used to clean unreachable commits.

    git reflog expire --expire-unreachable=now --all

The above command creates a variable for the Garbage Collector for the pruning operation.

To run the GC:

    git gc —prune=now

## Squash & Merge <span id="sqash-merge"></span>

GIT `squash` command will take multiple commits and combined them into a single commit.

    git checkout main
    git merge --squash bugfix

Consider, if we have a series of commits in bugfix branch
the above commands will squash all those commits into a single commit and will be merged into branch main with a single new commit.

This way we can concisely keep the history.

## Reset <span id="reset"></span>

GIT `reset` command will be used to unstage the changes from the staging area
or allow to go back to a particular commit and able to rework that specific commit.

There are 2 types of `reset` available:

### soft<span id="reset-soft"></span>

Unstage all the files from the staged area:

    git reset head

Unstage all the files from a specific commit:

    git reset 09c02f0

### hard<span id="reset-hard"></span>

Completely wipe out the changes from the staging area:

    git reset head --hard

Completely wipe out the changes from a specific commit:

    git reset 09c02f0 --hard

## Revert <span id="revert"></span>

GIT `revert` command will help to undo a specific commit we made.

    git revert 09c02f0

## Rebase <span id="rebase"></span>

GIT `rebase` will result in a linear commit history, it looks like we never branch with master/ main.

## Cherry-pick <span id="cherry-pick"></span>

    git cherry-pick 09c02f0

## Tagging <span id="tag"></span>

GIT `tag` is a nice way to put a bookmark on the commits that are easy to find and also used to publish the information about the tag.

It’s common practice to prefix the version names with the letter v. Some good tag names might be v1.0 or v2.3.4.

List all the available tags:

    git tag

There are 2 types of tag available:

### Lightweight<span id="tag-lightweight"></span>

    git tag v1.0.0

### Annotated<span id="tag-annotated"></span>

This tag will have a few more additional information than the Lightweight tag.

    git tag -a v1.0.1

### Some additional commands related to tags

Display all the tags that are part of version 1:

    git tag -l "v1*"

`tag` a specific commit in the past:

    git tag v0.0.0 09c02f0

Delete a tag:

    git tag -d v0.0.0

`push` the tags to the remote repo:

    git push --tags

Command that automatically push/pull the tags, don’t need to do separately:

     git config --global push.followTags true
