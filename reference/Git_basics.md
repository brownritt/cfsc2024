# Basic git usage

## Initializing 

To initialize a new git repo in a terminal type the command
```shell
git init
```
This will create a `.git` subdirectory in the *current working directory* (check `pwd`to make sure you are in the right place first!) and initialize it with information git needs to track changes.

*However*, since we often want our local repo linked to a remote provider like GitHub or GitLab, it is likely you would not invoke `git init` directly, but instead use `clone` or another application to [initialize a GitHub enabled project](GitHub_enabled_projects.md).

## Checking the state of things

The terminal command 
```
git status
```
displays information on changes git has detected, what is staged for the next commit, and things like branching and comparison to any remote repositories. When in doubt, check `git status`.

By itself, `git status` will not request updated information from remotes; one must use
```
git fetch
```
This will download the current git information from the remote, but will not make any changes to local files (unlike `pull`). It is a good idea to `fetch` whenever you have been away from a repo for a while, or whenever there is a chance someone else may have made changes to the remote repo. Otherwise, `status` may be using out of date information, and when you go to `push` you may be surprised by conflicting code changes.


## The local loop

Once a repo is set up, most git usage is just a "change-add-commit" loop:
```
<MAKE CHANGES TO LOCAL FILES>
git add <FILENAMES>
git commit -m "<COMMIT MESSAGE>"
```
Following the camera metaphor in the course, you can think of `add` as telling git to point the camera at specific files, and `commit` as telling git to take a picture. Any files that change "out of frame" (not staged for commit by `add`) will not be stored in the latest commit.

One has to choose when to commit changes. It's generally unhelpful to treat commits like file saving, or commit only at the end of a day. One rule of thumb is to commit each distinct "idea": a new function, an added feature, a new analysis. 

## Other git functions 

Git is a very powerful version control system, and with that power comes some complexity. One can move back and forth between new and old versions of code, edit several independent versions in parallel, get precise summaries of changes, and combine changes from multiple collaborators with a minimum of friction. Learning how to use these other parts of git takes some time; the change-add-commit loop is the core practice that enables all the other functions.

## Commit messages

All commits should have a message that summarizes what changed. Most commit messages are brief one liners, but they can span several pages if desired. There are many conventions and style guides for commit messages, but the main goal is just to make it easy to skim or search the log of commits for particular changes. A common convention is to use a small set of prefixes such as `fix:` (for bug fixes), `feat:` (for adding a new feature), or `doc:` (for updating documentation), followed by a simple description of the details.

If you type `git commit` without the `-m` flag, git will launch a text editor, usually [vim](https://en.wikipedia.org/wiki/Vim_(text_editor)) (tip: to quit vim right away and cancel the commit, type `:q!` and hit enter/return; you can then retry with the `-m` flag). 

## The remote loop

When there is a remote repo, there is an additional "pull-push" loop to keep the local and remote git history in sync:
```
git pull
<MAKE CHANGES TO LOCAL FILES>
git add <FILENAMES>
git commit -m "<COMMIT MESSAGE>"
git push
```
If you know you are the only one working on a repo, it is not necessary to `pull` (since the remote should not have any changes not on your local machine), and one can rack up a sequence of local commits before deciding to `push` them to the remote server.

`pull` will change local (tracked) files to match the most recent commit on the remote. In general, any local changes that have not been committed are at risk, but committed changes can be recovered, even when there is a conflict between local and remote versions. As much as possible, git tries to provides options and hints for resolving conflicts.

One can use `git fetch` to find out if things have changed on the remote (with `git status`), but without making any local changes.  
