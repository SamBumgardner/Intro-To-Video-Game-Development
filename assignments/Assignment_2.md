# Assignment 2: Working with FlxState and FlxSprite

**To Do List:**

 * Clone your forked version of csc-303-platformer-2018 to your computer.
 * Make the assignment-2 branch off of your local `master` branch. Push this new branch (and all further commits) to `origin` like normal.


 * **Part 1**:
   * Inside the `PlayState`'s create function, create an `FlxText` object that contains some variation of the message "hello world".
   * Use the `PlayState`'s `add()` function to make your `FlxText` object appear on-screen when the game is run.
   * Change the `X` and `Y` parameters to the `FlxText` object to make the "hello world" message appear somewhere near the middle of the screen.


 * **Part 1 Bonus**: Completing these will earn 1 extra point each. Total score for the assignment cannot exceed 12 out of 10.
   * Change the look of the "hello world" message to be significantly different from the default look. 
   * Make the hello world text move around the screen somehow. 
     * First Hint: If attempting to use `velocity` to move the `FlxText` object, you may need to look into the source code for `FlxText` to understand why it won't initially work.
	 * Second Hint: If you're really stuck, follow [this link](https://github.com/HaxeFlixel/flixel/blob/master/flixel/text/FlxText.hx#L208) to see what needs to be changed.


 * **Part 2**:
   * Create a new file in the project's source directory called `Hero.hx`.
   * In that file, create the `Hero` class that *extends* `FlxSprite`.
   * Inside the `Hero`'s `new()` function, use `makeGraphic()` to give it a simple rectangle graphic.
   * Inside the `Hero`'s `update()` function, set the `Hero` objects color to a value determined by screen position.
     * Hint: Look at the `PlayState` class for an example of overriding and update function.
   * Make `Hero`-class objects move automatically each frame.
   * Randomize the direction of its movement when it is created.
   * Add multiple `Hero` objects to the `PlayState`.


 * **Part 2 Bonus**: Completing these will earn 1 extra point each. Total score for the assignment cannot exceed 12 out of 10.
   * Make `Hero` class objects wrap screen vertically and horizontally (e.g. when going off right side of the screen, reappear on the left)
   * Make `Hero` class objects' movement changes according to keyboard or mouse input. (If doing this, randomizing movement and adding several `Hero` instances to the scene is optional).


 * Make a pull request from your `assignment-2` branch to the original (non-forked) repository's `master` branch.
 * If you did any **Bonus** tasks, say which ones in the pull request.


**Due Date:** 4/4/2018 (Wednesday) @ 5:30 PM (start of class). I recommend that you start and ask questions early. We'll spend the first few minutes of Monday's class discussing the homework, so make sure you've at least gotten started by then.

**Submission Instructions:** Opening the pull request against my repository is all that is needed.

**Grading Criteria**
Grading criteria is as follows:

 * Git used correctly for branching and pull request: 2 points.
 * **Part 1** coding tasks: 4 points.
 * **Part 2** coding tasks: 4 points.

1 point will be deducted for each day that the assignment is late.