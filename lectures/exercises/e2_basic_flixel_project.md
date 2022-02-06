# In-Class Exercise: A Basic HaxeFlixel Project

## Purpose
It's time to set up our first haxeflixel project! 

You'll need to go through this process of creating a new game project from scratch at least a few
times over the course of this semester. Working through it together gives us a chance to run into
(and solve) any strange or unexpected problems together. 

Hopefully you'll be able to refer back to this exercise as needed in the future, should you some
tricky detail of the setup process. This does assume that the machine you're working on has 
installed and set up HaxeFlixel correctly - if your environment is missing anything, you can
refer to ['getting started' documentation](https://haxeflixel.com/documentation/getting-started/)
to fix any issues that arise.

## To Do List
 1. Create a new HaxeFlixel project on your local machine
    1. Navigate your command prompt to the directory you want your new project folder to live in.
    2. Create an empty HaxeFlixel project by running the command
       ```
       haxelib run flixel tpl -n basic-flixel-project -ide vscode
       ```
       * If you run into an error when running this command (because flixel is missing the required
        add-ons library, probably) you should be able to follow the instructions given in the error
        message to correct it.

 2. Make the newly created directory into a local git repository
    1. Navigate your command prompt into the newly created project directory
       ```
       cd basic-flixel-project
       ```
    2. Initialize an empty git repository
       ```
       git init
       ```
    3. Create a `.gitignore` file - this identifies files and directories that we don't want to 
       save to version control. Here's an example of an appropriate one for a HaxeFlixel project:
       [simple gitignore](https://github.com/SamBumgardner/csc-303-game-2021/blob/main/.gitignore)

       Git will completely ignore any file or directory specified in the `.gitignore` which can be
       useful for a variety of reasons:
       * Results of a build (compiled executables and the like) can change in massive, unpredictable
         whenever any code is touched. 
         
         Keeping a directory like `export/` in git history (where flixel puts build results) means 
         all commits will have a bunch of 'noisy' changes from that directory (probably thousands of
         lines) every time code is pushed, and basically guarantees conflicts whenever different
         people try to merge changes into a shared `main` branch.

         Since build results can easily be recreated locally, there's close to no upside in 
         retaining the directory, which makes it an excellent candidate for the .gitignore.

       * Files that contain personal configuration, or are tied to a specific dev's choice of IDE
         or development environment are usually good things to ignore too. If a file is only 
         relevant to a fraction of potential developers, then it's questionable to include (it just
         wastes space for everyone else). 

         If there's any degree of personal customization in those files, including them immediately
         becomes a problem. Users with different config preferences would get overwritten by each
         other while collaborating, which is definitely a negative developer experience.
    4. Make sure all files are saved, then commit changes to the git repository.
       ```
       git status
       git add -A
       git commit -m "Initial commit"
       ```

 3. Create a new repository on GitHub to house the repo we set up locally
    1. Log in to GitHub
    2. Click the `+` in the top-right corner of any page, select the `New Repository` option.
    3. Fill in the `Create a new repository` page
       1. To avoid confusion, I recommend name you used when creating your local project
       2. Keep the "Public" option selected
       3. Leave all of the initial file options unchecked - we'll be pushing our local repository
          up instead of depending on GitHub to create things.
    4. Follow the instructions titled "...or push an existing repository from the command line" 
       shown on your new repository's page. It should involve something like
       ```
       git remote add origin <your_repository_url>
       git branch -M main
       git push -u origin main
       ```
       these commands that should look pretty familiar by now (except for `git branch -M main`, 
       which just handles branch renaming).
    5. Refresh your GitHub repository's page and confirm that your repo is all set up!

 4. Build and run the game, confirm that it works (empty screen, mouse will look fancy)
 5. Create a new branch to start development
 6. Create a new class named `Hero` (should be created in `Hero.hx` file)
 7. Update PlayState to instantiate and `add` the hero object to itself
 8. Build and run the game, confirm that the Hero object is now in the middle of the empty screen
 9. commit and push changes
 10. Make a pull request to `main` in GitHub
 11. Request review from others
 12. After review, merge

After your changes are merged, you're done!

## Post-Exercise Recommendations
