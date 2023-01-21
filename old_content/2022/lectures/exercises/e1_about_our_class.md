# In-Class Exercise: About Our Class

## Purpose
Let's get some hands-on practice using Git and Github to contribute to a project directly!

We've been talking through the theoreticals of using Git for a while now. This exercise should 
help anchor what we've talked about previously to something concrete.

## To Do List
 1. Post a link to your github user to our lecture's chat - I need to know who to should have write
   access to our shared project.
 2. Clone the class repository to your local machine 
    * `git clone https://github.com/SamBumgardner/Intro-To-Video-Game-Development.git`
 3. Navigate into the newly cloned repository, then create & checkout your own branch off of master.
    * `cd Intro-To-Video-Game-Development`
    * `git checkout -b '<your_name>-about-me'`
 4. Use a text editor to open the `about_our_class.md` file that's inside the project's root
    directory.
 5. Add your name to the file and some interesting fact(s) about you. Refer to the "Example Name" 
    entry in the file if you're stuck for ideas, but don't feel shackled to its format.
 6. Save the file, stage your changes, and commit them
    * `git add -A`
    * `git commit -m '<insert_witty_and_insightful_commit_message_here>'`
 7. Push your change to the class repository (which will create your branch on our remote repo too).
    * `git push -u origin '<your_branch_name>'`
 8. Navigate to the class repository in GitHub and open a pull request from your branch to `master`.
 9. After receiving approval, merge your changes.
    * BONUS: when other students' pull requests are merged to `master`, make sure to pull the most
      recent version of `master` into your branch. If conflicts have occurred, resolve them manually
      before committing and pushing the merge.
      * `git pull origin master` (performed while on your branch)
      * If merge conflicts occurred, clean up the marked conflicts then use `git add` and 
        `git commit` to complete the process.

After your changes are merged, you're done!

## Post-Exercise Recommendations
If you have extra time left over, I recommend getting a head-start on learning Haxe. 
 * [Learn X in Y minutes](https://learnxinyminutes.com/docs/haxe/) is a useful resource for a 
   quick practical rundown. Fair warning, we'll be taking an abridged tour through this in a 
   future class.
 * If you're interested in the big-picture theoretical side, I recommend checking out 
   [Haxe's online documentation](https://haxe.org/documentation/introduction/). It's an 
   interesting read!

