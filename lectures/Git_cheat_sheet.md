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


### Working on a local repository

*Note: The following instructions assume that your local repository is up-to-date.*

#### If you want to begin developing a new feature (or set of related features)

1. Checkout whatever local branch you want your new feature to be developed from.
     * If you're following the workflow described here, you should probably use your local "master" as your base branch
2. Click the "Branch" button in the top section of the SourceTree window
3. Pick a name for the new branch that briefly describes what features you plan to develop on it
     * I believe the preferred branch-naming style is to use all lower-case words connected by hyphens, like "lecture-notes"
4. Click the "Create Branch" button in the bottom-right corner of the pop-up window.
5. Begin the three-part cycle of work, described below

#### If you want to continue developing an already-existing feature branch

1. Checkout the local version of the branch that you'd like to develop
     * If you don't have a local version of the branch, simply double-click the branch you'd like to checkout in SourceTree's Log/History graph
2. Begin the three-part cycle of work, described below

#### The three-part cycle of work

1. Make changes to your local files
     * Remember that you can find you local files by navigating to whatever directory you originally cloned them into, 
	 or by right clicking your local repository's box on the left side of SourceTree and selecting the "Show in Explorer" option
2. Stage changes to your local files
     1. First, click on the "File Status" tab at the bottom of the SourceTree window
     2. Select all files you would like to stage from the "Unstaged files" section
          * Hunks and lines of code may be committed instead of the whole file. To do this, click on the file's name in the "Unstaged files" section,
            and select particular hunks or lines of code to stage from the selections that appear on the right side of the SourceTree window
     3. Click the "Stage Selected" button on the right side of the "Unstaged files" section's header
     4. Check that *only* the content you wanted to stage is now in the "Staged files" section
          * files/hunks/lines may be unstaged through a process very similar to staging them. Just make sure you press the "Unstage" buttons instead
3. Commit your staged changes 
     1. Type out a commit message in the large text field at the bottom of the SourceTree window
          1. Type a short (80 char. max) message outlining the overall result of the commit
		  2. Press enter twice (for a double line break), then enter any additional information you'd like to include about the commit
     2. Do one last check that everything is correct
     3. Click the "Commit" button in the bottom-right corner of the SourceTree window
4. Repeat steps 1-3 as desired, move on when finished
5. Click the "Push" button in the top section of the SourceTree window
6. Make sure that the "Push to repository" drop-down box at the top of the pop-up window says "origin".
7. Find the name of the branch you've been working on locally, and put a check the box to the left of its name
     * After you've done this once for SourceTree, you probably won't have to do it again
8. Click the "Push" button in the bottom-right corner of the pop-up window
     * **WARNING:** If at all possible, avoid pushing incorrect commits. They become much more difficult to fix after being pushed into a remote repository.


### Making Pull Requests

*Note: The following instructions assume that your repository/fork's feature branch has had all relevant changes pushed to it from your local machine.*

#### If you want to merge changes from your fork's feature branch into the original repository's master branch

1. Navigate to your fork on GitHub.
2. If you recently pushed commits to that fork, GitHub may give you a button to automatically set up a pull request. If so, click on it! Otherwise, you should follow these steps:
     * Click on the "New pull request" button on the fork's main page.
     * On the new "Open a pull request" page, ensure that the "base fork" drop-down menu has the original repository selected, 
     and the "base" drop-down menu next to it has "master" (or whatever branch you're wanting to change) selected.
     * Check that the "head fork" drop-down menu shows your fork's name.
     * Set the "compare" drop-down menu to select your feature branch.
     * Click the green "Open pull request" button.
3. If necessary, change the title of the pull request to reflect the changes that it's bringing to the main repository.
4. In the body of the pull request, include the following information:
     * An overview of what merging the pull request will do to the main repository.
     * Why merging the pull request is a good idea.
     * A list of individual features included in the pull request.
     * Any special notes about the pull request.
     * Information about how to test it (if necessary).
5. For our class, make sure to request a review from your assigned reviewer.
6. Preview the pull request and fix any issues you notice.
7. Click the green button below to submit the pull request for review!
     
