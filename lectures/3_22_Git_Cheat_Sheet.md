# Git Cheat Sheet

We covered quite a bit of information about how to use git & GitHub effectively during class time on 3/22. 
To help reinforce the lessons we learned, I decided to put together this Git Cheat Sheet to outline the process we discussed and used
in our hands-on exercise. The instructions are written for people using SourceTree, but should be relatively easy to apply to command-
line git as well.

An important detail that we didn't really talk about in class is that this particular strategy for using git and GitHub is only one
of [many valid and useful workflows](https://www.atlassian.com/git/tutorials/comparing-workflows) that you may encounter in the future.
After you feel comfortable with our class's particular workflow, I encourage you to explore other options to get a better idea of how
git's structure can be leveraged to make building and managing code easier.

## Cheat Sheet

### First-Time Set Up

#### When you find a repository on GitHub owned by someone else that you'd like to contribute to:

1. Click the "fork" button in the top-right corner of the repository 
2. When asked "where should we fork this repository to?" click yourself

#### When you want to make changes to a repository on GitHub and don't already have the code on your local computer:

1. Navigate to the GitHub page of the repository you want to change
    * Note: if you're wanting to contribute to someone else's repository, go to your fork of the repository that we created earlier
2. Click the green "Clone or Download" button on the right side of the repository's main page
3. Copy the provided URL
4. Open SourceTree
5. Click the clone/new button in the upper-left area of the window
6. Paste the URL that you copied earlier into the pop-up window's Source Path / URL box
7. Click the "Clone" button in the bottom-right corner of the pop-up window
    * Note: The destination path and name should fill in automatically. You can mess around with other settings in the pop-up window, but
    I recommend against it until you feel comfortable with the basic git process.

#### If you just finished cloning down a forked repository:

1. Navigate to the GitHub page of the root repository that you originally forked from
    * Your fork should have a link back to the root reposistory just under the original repository's title.
2. Click the green "Clone or Download" button on the right side of the repository's main page
3. Copy the provided URL
4. Right click inside the left column of sourceTree's inner window (where the branches and Origin are listed)
5. Select the "Add new remote" option
6. Paste the copied URL into the Source Path / URL box
7. Name the new remote "upstream"

### Updating a Local Repository

#### If your repository is a fork of a different repository

1. Fetch changes from all remotes
2. For each local branch that is behind its counterpart in the "upstream" remote...
     1. Checkout the local branch by double clicking its name
     2. Click the "Pull" button in the top section of the SourceTree window
     3. In the pop-up window, select to pull the corresponding branch from remote "upstream" into your current branch.
3. For each local branch that is behind its counterpart in the "origin" remote...
     1. Checkout the local branch by double clicking its name
     2. Click the "Pull" button in the top section of the SourceTree window
     3. In the pop-up window, select to pull the corresponding branch from remote "origin" into your current branch.
4. For each local branch whose base branch was updated during one of the previous two steps... 
*(e.g. changes from the "upstream" master branch were pulled into your local master branch, so each branch that came off of master must 
also be updated)*
     1. Checkout the local branch by double clicking its name
     2. Right click the recently-updated base branch and select "merge _____ into current branch"
     3. Click OK in the pop-up window
     4. If necessary, resolve any merge conflicts.

Now your local repository is up-to-date!

#### If you own the repository you're working on (no forking involved)

1. Fetch changes from all remotes
2. For each local branch that is behind its counterpart in the "origin" remote...
     1. Checkout the local branch by double clicking its name
     2. Click the "Pull" button in the top section of the SourceTree window
     3. In the pop-up window, select to pull the corresponding branch from remote "origin" into your current branch.
3. For each local branch whose base branch was updated during one of the previous two steps... 
*(e.g. changes from the "origin" master branch were pulled into your local master branch, so each branch that came off of master must 
also be updated)*
     1. Checkout the local branch by double clicking its name
     2. Right click the recently-updated base branch and select "merge _____ into current branch"
     3. Click OK in the pop-up window
     4. If necessary, resolve any merge conflicts.

Now your local repository is up-to-date!

### Local Work Cycle



### Making Pull Requests/Merging in Work


