# Assignment 2: Working with FlxState and FlxSprite
**Note: this assignment will be due in two parts.** 
 * Part 1 is due on Monday, April 6th at the start of class (5:30 PM CST)
 * Part 2 is due on Wednesday, April 8th at the start of class (5:30 PM CST)

### Git Setup
 * Create a new repository in GitHub named haxeflixel-practice (or something similar). Initialize it with an empty readme (this should be the default choice) so you can start using it right away.
 * Clone your new haxeflixel-practice repository to your computer.
 * Make a branch named `assignment-2` off of your local `master` branch. As you work and commit, push this new branch to `origin`.
 * Create a new haxeflixel project template in your local git repo with the same name as the repository.
   * To do this, navigate to the directory **outside** of the cloned repository, then run the command `haxelib run flixel tpl -n haxeflixel-practice -ide vscode`
   * When given the following prompt, `Directory exists - do you want to delete it first? [y/n]?` reply with `n` to avoid wiping out your local git history. 
 * Create a file named `.gitignore` in the project with contents like [this](https://github.com/SamBumgardner/Running-Game/blob/master/.gitignore)
   * This makes sure you don't accidentally commit the executables you build or any ide-specific files. If interested in discussing why, bring it up at the start of next class!
 * Add, commit, then push all of the changes you've made so far. Continue to commit and push work as you continue through the assignment.

### Part 1 - Hello World
**Due Date: Monday, 4/6/2020**
 * Inside the `PlayState`'s create function, create an `FlxText` object that contains some variation of the message "hello world".
 * Use the `PlayState`'s `add()` function to make your `FlxText` object appear on-screen when the game is run.
 * Change the `X` and `Y` parameters to the `FlxText` object to make the "hello world" message appear somewhere near the middle of the screen.


#### Part 1 Bonus
Completing these will earn 1 extra point each. Total score for the assignment cannot exceed 12 out of 10.

 * Change the look of the "hello world" message to be significantly different from the default look. 
 * Make the hello world text move around the screen somehow. 
     * First Hint: If attempting to use `velocity` to move the `FlxText` object, you may need to look into the source code for `FlxText` to understand why it won't initially work.
     * Second Hint: If you're really stuck, follow [this link](https://github.com/HaxeFlixel/flixel/blob/master/flixel/text/FlxText.hx#L208) to see what needs to be changed.


### Part 2 - Adding Hero Class
**Due Date: Wednesday, 4/8/2020**
 * Create a new file in the project's source directory called `Hero.hx`.
 * In that file, create the `Hero` class that *extends* `FlxSprite`.
 * Inside the `Hero`'s `new()` function, use `makeGraphic()` to give it a simple rectangle graphic.
 * Inside the `Hero`'s `update()` function, set the `Hero` objects' color to a value determined by screen position.
     * Hint: Look at the `PlayState` class for an example of overriding and update function.
     * Hint: `color` is a finicky property. Assigning it a 32 bit hexidecimal number (like `this.color = 0xff00ff00`) will be the way to go.
 * Make `Hero`-class objects move automatically each frame.
 * Randomize the direction of its movement when it is created.
 * Add multiple `Hero` objects to the `PlayState`.


#### Part 2 Bonus
Completing these will earn 1 extra point each. Total score for the assignment cannot exceed 12 out of 10.
 * Make `Hero` class objects wrap screen vertically and horizontally (e.g. when going off right side of the screen, reappear on the left)
 * Make `Hero` class objects' movement changes according to keyboard or mouse input. (If doing this, randomizing movement and adding several `Hero` instances to the scene is optional).

### Turn-in Instructions
 * Make a pull request from your `assignment-2` branch to your repository's `master` branch. All of this should be done through GitHub. 
 * Send me a message when your pull request is ready to go.
 * If you did any **Bonus** tasks, say which ones in the pull request.

**Due Dates:**
 * Part 1 is due on Monday, April 6th at the start of class (5:30 PM CST)
 * Part 2 is due on Wednesday, April 8th at the start of class (5:30 PM CST)

I recommend that you start and ask questions early.

**Grading Criteria**
Grading criteria is as follows:

 * Git used correctly for branching and pull request: 2 points.
 * **Part 1** coding tasks: 4 points.
 * **Part 2** coding tasks: 4 points.

1 point will be deducted for each day that the assignment is late.
