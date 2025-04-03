
# GIT COMMANDS
Commonly Used Git Commands


## CONFIG
Configuring user information

`git config --global user.name "[firstname lastname]"`
Set a name that is identifiable for credit when reviewing version history

`git config --global user.email "[valid-email]"`
Set an email address that will be associated with each history marker

`git config --global color.ui auto`
Set automatic command line coloring for Git for easy reviewing

## INIT
Initializing and cloning repositories

`git init`
Initialize an existing directory as a Git repository

`git clone [url]`
Retrieve an entire repository from a hosted location via URL

## STAGE & SNAPSHOT

Working with snapshots and the Git staging area

`git status`
Show modified files in the working directory, staged for your next commit

`git add [file]`
Add a file as it looks now to your next commit (stage)

`git reset [file]`
Unstage a file while retaining the changes in the working directory

`git diff`
Diff of what is changed but not staged

`git diff --staged`
Diff of what is staged but not yet committed

`git commit -m "[descriptive message]"`
Commit your staged content as a new commit snapshot

## BRANCH & MERGE

Isolating work in branches, changing context, and integrating changes

`git branch`
List your branches. A `*` will appear next to the currently active branch

`git branch [branch-name]`
Create a new branch at the current commit

`git checkout [branch-name]`
Switch to another branch and check it out into your working directory

`git merge [branch-name]`
Merge the specified branch’s history into the current one

`git log`
Show all commits in the current branch’s history

## INSPECT & COMPARE

Examining logs, diffs, and object information

`git log`
Show the commit history for the currently active branch

`git log branchB..branchA`
Show the commits on branchA that are not on branchB

`git log --follow [file]`
Show the commits that changed file, even across renames

`git diff branchB...branchA`
Show the diff of what is in branchA that is not in branchB

`git show [SHA]`
Show any object in Git in human-readable format

## TRACKING PATH CHANGES

Versioning file removes and path changes

`git rm [file]`
Delete the file from the project and stage the removal for commit

`git mv [existing-path] [new-path]`
Change an existing file path and stage the move

`git log --stat -M`
Show all commit logs with an indication of any paths that moved

## IGNORING PATTERNS

Preventing unintentional staging or committing of files

```
logs/
*.notes
pattern*/
```


Save a file with desired patterns as `.gitignore` with either direct string matches or wildcard globs.

`git config --global core.excludesfile [file]`
System-wide ignore pattern for all local repositories

## SHARE & UPDATE

Retrieving updates from another repository and updating local repos

`git remote add [alias] [url]`
Add a Git URL as an alias

`git fetch [alias]`
Fetch down all the branches from that Git remote

`git merge [alias]/[branch]`
Merge a remote branch into your current branch to bring it up to date

`git push [alias] [branch]`
Transmit local branch commits to the remote repository branch

`git pull`
Fetch and merge any commits from the tracking remote branch

## REWRITE HISTORY

Rewriting branches, updating commits, and clearing history

`git rebase [branch]`
Apply any commits of the current branch ahead of the specified one

`git reset --hard [commit]`
Clear staging area, rewrite working tree from the specified commit **(Use with caution!)**

## TEMPORARY COMMITS

Temporarily store modified, tracked files in order to change branches

`git stash`
Save modified and staged changes

`git stash list`
List stack-order of stashed file changes

`git stash pop`
Write working from the top of the stash stack

`git stash drop`
Discard the changes from the top of the stash stack

## UNDOING CHANGES

### Local Modifications

`git checkout -- [file]`
Discard changes in the specified file in your working directory, reverting to the last version in the staging area or the last commit.

`git restore [file]` (More recent alternative to `git checkout --`)
Restore the specified file to its previous state.

`git restore --staged [file]`
Remove the specified file from the staging area, but keep the changes in the working directory.

### Commits

`git revert [commit]`
Create a new commit that undoes the changes introduced by the specified commit. This is a safe way to undo changes in a shared history.

`git reset --soft [commit]`
Move the HEAD to a previous commit, but keep the changes made after that commit in the staging area. Useful if you want to modify the last commit message or add more changes before recommitting.

`git reset --mixed [commit]` (or simply `git reset [commit]`)
Move the HEAD to a previous commit and remove the changes made after that commit from the staging area. The changes are kept in your working directory.

`git reset --hard [commit]`
**DANGER!** Move the HEAD to a previous commit and delete all changes made after that commit from both the staging area and the working directory. You will lose these changes permanently. Use with caution.

## WORKING WITH REMOTE BRANCHES

`git branch -r`
List all remote branches.

`git branch -a`
List all local and remote branches.

`git checkout --track <alias>/<branch>`
Create a local branch with the same name as the specified remote branch and set up a tracking connection. For example: `git checkout --track origin/develop`.

`git push --set-upstream <alias> <branch>` or `git push -u <alias> <branch>`
Set the remote branch as the upstream branch for your current local branch. This allows you to use `git pull` and `git push` without specifying the remote branch.

## TAGS

`git tag -a <tag_name> -m "<message>"`
Create an annotated tag (recommended) with a message.

`git tag <tag_name>`
Create a lightweight tag (without a message).

`git tag`
List all tags.

`git show <tag_name>`
Show the information for a specific tag.

`git push --tags`
Push all tags to the remote repository.

`git checkout tags/<tag_name>`
Create a temporary branch based on a specific tag.

## SUBMODULES

`git submodule add [url]`
Add an external repository as a submodule to the current repository.

`git submodule init`
Initialize the submodules after cloning a repository that contains them.

`git submodule update`
Download the content of the submodules.

`git submodule update --init --recursive`
Initialize and update all submodules, including nested ones.

## MORE LOG OPTIONS

`git log --oneline`
Show the commit history in a single line per commit.

`git log --graph --decorate --oneline`
Show a graph of the commit history, decorate branches and tags, and show each commit on a single line.

`git log --author="[pattern]"`
Show commits made by a specific author (you can use patterns).

`git log --since="[date]"` or `git log --until="[date]"`
Show commits made after or before a specific date.

`git log -p`
Show commits with the changes (patch) they introduced.

`git log --stat`
Show commits with a summary of the modifications in each file.

## ADVANCED STASHING

`git stash branch <branch_name>`
Create a new branch from the commit where the stash was created and apply the stash changes to that new branch. Useful for working on stashed changes without affecting the current branch.

`git stash apply --index`
Attempt to apply the stash changes, including the changes that were in the staging area.

`git stash save "<description>"`
Save the changes with a description to identify them better in the list.

## MERGE CONFLICT RESOLUTION

While not a single command, it's important to mention that when there are conflicts during a merge, Git will mark the files with markers (`<<<<<<<`, `=======`, `>>>>>>>`). You need to manually edit these files to resolve the conflicts, then use `git add` to mark the files as resolved, and finally `git commit` to complete the merge.

## CHERRY-PICK

`git cherry-pick [commit]`
Apply the changes introduced by a specific commit to the current branch. Useful for bringing specific commits from other branches.

## BLAME

`git blame [file]`
Show who made the last modification to each line of a file and in which commit.

## REF LOG

`git reflog`
Show a log of actions that have updated the references (HEAD, branches, etc.) in your local repository. Useful for recovering lost commits or undoing actions.

`git reflog expire --expire=now --all && git gc --prune=now --aggressive`
Command to clean the reflog and Git's garbage collection. Useful in extreme cases to free up space or clean up history (use with caution!).
