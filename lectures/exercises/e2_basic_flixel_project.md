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

 4. Build and run the game to confirm that everything's been set up properly
    1. On your command line (within your project directory), run 
       ```
       haxelib run lime test neko
       ```
    2. Check that the game builds successfully - it should create a window, show the HaxeFlixel
       logo, then show an empty black screen. Your mouse will look different within the pane.

 5. Create (and check out) a new branch, you'll be using it to create a simple `Hero` class. Make 
    sure it's named according to its purpose.

 6. Create a new file named `Hero.hx`, implement the `Hero` class inside of it. 
 
    At a minimum, the `Hero` class should inherit from the `FlxSprite` class. Optionally, you may
    implement a constructor and create
    1. If you'd like to keep things organized, you can create folder(s) to hold it. Just creating
       it inside `source/` is okay too.
    2. Write the `package` line at the top of the file.
       * If you created the `Hero.hx` file inside our root directory, `source/`, then the package 
         will be empty:
         ```
         package;
         ```
       * If you created the `Hero.hx` file inside some kind of nested folder structure, then the
         package name should reflect its location. For example, if the file is located at 
         `source/entities/player/Hero.hx`, then the package would be:
         ```
         package entities.player;
         ```
    3. Declare the `Hero` class.
    4. Optional: Implement a constructor. Don't forget to use `super()` (and pass in appropriate 
       arguments) to invoke the parent class's constructor!
    1. Optional: Override [the inherited update() method](https://api.haxeflixel.com/flixel/FlxBasic.html#update)
       to give the `Hero` class some sort of behavior

 7. Update the `PlayState` class's `create()` method to instantiate and `add()` a `Hero` object.
    1. After `super.create()` is called...
    2. Create a new `Hero` object, passing in X and Y coordinates somewhere between 100 - 200. This
       will give the hero a position that's somewhere in the middle of the screen (instead of the)
       top-left corner, where (0, 0) is.

 8. Build and run the game (using the same commands as before) and confirm that the Hero object is 
    now located somewhere on the screen.
    
    Assuming you haven't done anything extra to set up a graphic for it, it'll look like a tiny
    HaxeFlixel logo.

 9. Commit and push your changes to your `origin` remote repository.
   
 10. Open a pull request from your feature branch to `main` in GitHub.

 11. Request review from others, students or professor.

 12. After receiving some kind of review, merge. Make sure to update your local `main` branch to be
     caught up with the newly applied changes.

After your changes are merged and your local repo's up-to-date, you're done!

## Post-Exercise Recommendations
We're just barely scratching the surface of development here, most of our work is just getting used
to the process of setting up a new project. 

If you're interested in getting a head-start on learning more about how we can use HaxeFlixel, the
[Haxeflixel Handbook](https://haxeflixel.com/documentation/haxeflixel-handbook/) gives a nice, 
consise breakdown of features we'll be using a lot. We'll also cover the important topics in class,
but getting info from a different source can be a good way to broaden your understanding.

The [tutorial provided on the HaxeFlixel website](https://haxeflixel.com/documentation/tutorial/) 
is nice too. Plenty of practical examples of basic HaxeFlixel features in action, which can 
balance out some of the theoretical info and discussion we'll have during lecture. 

Striking out into the wilds of HaxeFlixel and just trying things out yourself can be another great
way to learn more about our new toolset. If you're taking this path, digging around in the 
[HaxeFlixel Demos'](https://haxeflixel.com/demos/) and source code (linked from each demo's page)
can be a great way to find inspiration. 

Getting comfortable with the nuts and bolts of the HaxeFlixel library by diving into the 
[API](https://api.haxeflixel.com/) is great too. There's no better way to figure out exactly what 
properties and methods are available for you to use.

Understand what kind of learning works best for you, and let me know if there's any kind of support 
missing that you wish you had - I'll do my best to address the gap in the best way possible.
