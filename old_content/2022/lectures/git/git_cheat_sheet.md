# Git Cheat Sheet
This document's purpose is to provide a simple reference for basic git information. It'll mostly
focus on defining terminology and explaining how to use some basic commands. A reference section
at the bottom will link to some more detailed information, in case you really need to dive deep
on functionality.

Feel free to open your own pull requests to update this document - let's do what we can to help it
be more useful while keeping it relatively clean and easy to read.

## Terminology
**Repository**
 * In general, think of it as a "project" that is managed by git.
 * Technically, a repository is just a directory (containing whatever arbitrary files we want) that
has its history and state tracked in some special files hidden away in a nested folder named `.git`
 * Repositories can be stored online (hosted by a website like GitHub, for example) or on a local 
computer.
 * A version of repository that isn't stored locally (and is hosted online somewhere instead) is 
called a `Remote` (as in, remote repository).

**Commit**
 * A commit is a set of changes that can be saved to a repository. 
 * All repositories start with an initial commit, which is whatever base state the project began
in. Lots of projects begin as a single folder containing a `README.md` file. All subsequent commits
are modifications to this starting point.
 * As you work within a repository, you can save what you've done in the repository's history by
"committing" the changes you've made (using the `git commit` command).
 * Because committed changes are stored in the repository's history, they can be shared (via the 
`git push` command) with remote versions of the repository.

**Commit Message**
 * Whenever someone commits a change to a repository, they are prompted to provide some sort of
comment on the changes made (this is called a commit message).
 * Commit messages help explain why a particular change was made to a repository, to provide useful
context for anyone who reviews the repository's history in the future.
 * If you ever wonder why a particular line (or file) looks the way it does, the answer might lie
within the last commit message that updated it. Sometimes it won't, poor commit messages are a
pretty common (and infamous) problem wherever git is used.

**Branch**
 * A branch is kinda like an alternte timeline version of a repository.
 * Repositories have a main branch, likely called `main` (might be called `master` in older 
projects). The state of the repository in this branch is considered to be the most "real" version.
 * New branches can use any commit in the repository's history as a starting point, but usually
they'll be made from the `main` branch's most recent commit.
 * Side-branches can be used to work on features, save them, and share them all without touching 
the "most real" `main` branch. Branches used in this way are called "feature branches"
 * Commits added to a feature branch are usually applied to the `main` branch of an online-hosted 
repository via a "pull request," a system for reviewing and approving code built into hosting 
services like github. 

## Useful commands
`git status` - a handy way to check info about the current state of the local repository. Includes
handy information like the currently checked out branch / commit and the state of any files (both 
staged and unstaged).

`git checkout <branch_name>` - switch the "active" timeline for your repository over to the selected
branch.

`git checkout -b <new_branch_name>` - create a new branch of the currently-checked-out commit, then
switch over to that branch. Most convenient way to start working on a feature branch, I think.

`git branch <new_branch_name>` - create a new branch based off of the currently-checked-out commit.
You will not be "switched over" to that branch yet, execute a `git checkout` command to move over 
to it.

`git branch --list` - display a list of branches that are tracked by the local repository. Good for 
checking what's going on locally if you're confused.

`git add <path_to_some_file>` - stage changes in a specific file or directory. Changes must be 
staged before they'll be noticed by `git commit` commands.

`git add -A` - stage all changes within the project.

`git commit -m "some commit message"` - commit all staged changes (things prepped by running the
`git add` command). By providing the `-m` followed by a message in quotes, you can provide a 
commit message without getting kicked to a potentially confusing command-line text editor.

`git push` - apply all local commits on your branch to its counterpart in the remote repository.

`git push -u origin <current_branch_name>` - create a new branch in the "origin" remote repository
with the specified name, and make your local repository remember it as the target for future pushes
from this branch.

`git merge <other_branch>` applies all commits found on the specified `<other_branch>` to the 
current branch. Commonly used after pulling down external updates to the `main` branch - while 
checked out on a feature branch, run `git merge main` to also apply those changes to your local
feature branch.

`git pull` checks your branch's counterpart on the 'upstream' remote, retrieves any new commits
that aren't found locally, and applies them to your current branch.
