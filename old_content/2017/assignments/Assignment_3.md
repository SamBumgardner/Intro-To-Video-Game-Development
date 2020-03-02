# Assignment 3: Working with Player Input and Collision

**To Do List:**

 * Clone your forked version of csc-303-platformer-2018 to your computer (if necessary).
 * Check out your local `master` branch.
 * Pull the original repository's (upstream) branch `master` into your local `master` branch. 
 * Push your local `master` branch to your forked repository's (origin) `master` branch.
 * Make the assignment-3 branch off of your local `master` branch. Push this new branch (and all further commits) to `origin` like normal.


 * **Part 1**:
   * Change the existing `TopDownHero` class to move up, left, down, or right when the `W`, `A`, `S`, or `D` key is pressed.
     * Make sure the `TopDownHero` class does not move when no keys are pressed.
   * Change the existing `TopDownHero` class to change colors (cycling through a preset list of color options) each time the player presses the spacebar. 


 * **Part 1 Bonus**: Completing these will earn 1 extra point each. Total score for the assignment cannot exceed 12 out of 10.
   * Add a system the player can use to change which key controls which action. 
     * *Note:* There's no need to set up an instructive user interface (although you would definitely need one in a real game), just write an explanation of how it works in the project's `readme.md` file.
   * Create a `Wall` class that inherits from `FlxSprite`, then add code to accomplish the following tasks:
     * It should take an `FlxColor` as a parameter to its constructor, which determines its color. 
     * A `TopDownHero` object should collide with any `Wall` that does not match its current color.
     * Add `Wall` objects to the `PlayState`, arranged in an interesting way for the `TopDownHero` to navigate through.


 * **Part 2**:
   * Change the existing `PlatformerHero` class to automatically move as if affected by gravity.
     * This means accelerating downward vertically until reaching some terminal velocity, which it continues to fall at until otherwise interrupted.
   * Add collision between `PlatformerHero` and `Ground` objects. (Can be implemented in the `PlayState`, `PlatformerHero`, or `Ground` class)
   * Add horizontal movement to the `PlatformerHero`, controlled by the `Left` and `Right` arrow keys.
     * Neither direction of movement should have priority over the other. If both `Left` and `Right` are held, the `PlatformerHero` should act as though neither direction were pressed.
     * The `PlatformerHero` should (eventually or immediately) come to a stop when no movement buttons are pressed.
   * Add jumping to the `PlatformerHero`, controlled by the `Z` key.
     * When the `Z` key is pressed, the `PlatformerHero` should have a sudden increase in upward velocity.
     * The jump should have an adjustable height depending on how long `Z` is held / when it is released.
       * *i.e.* holding `Z` results in a higher jump than lightly tapping `Z`. 
       * The exact details of how this should work is up to you. You could emulate the behavior of a game you like, or experiment around to find a style of jumping that feels comfortable to you.
   * Add (at least) one additional player-controlled action to the `PlatformerHero`. What you do is up to you, so be creative!


 * **Part 2 Bonus**: Completing these will earn 1 extra point each. Total score for the assignment cannot exceed 12 out of 10.
   * Create a plan to implement an independent, fixed physics time step with linear interpolation as described here: https://gafferongames.com/post/fix_your_timestep/
     * Document your plan in the project's `readme.md`.
     * Actually implementing your plan isn't necessary, but I will be extremely impressed if you do complete a working prototype.
   * Create two different classes that inherit from `Ground` that alter the `PlatformerHero`'s movement while in contact with it (can affect grounded movement and/or starting a jump) and add them to the `PlayState`.


 * Make a pull request from your `assignment-3` branch to the original (non-forked) repository's `master` branch.
 * If you did any **Bonus** tasks, say which ones in the pull request.


**Due Date:** 4/9/2018 (Monday) @ 5:30 PM (start of class). I recommend that you start and ask questions early. I'll make sure I'm available throughout the weekend to answer any questions you may have!

**Submission Instructions:** Opening the pull request against my repository is all that is needed.

**Grading Criteria**
Grading criteria is as follows:

 * Git used correctly for branching and pull request: 2 points.
 * **Part 1** coding tasks: 3 points.
 * **Part 2** coding tasks: 5 points.

1 point will be deducted for each day that the assignment is late.