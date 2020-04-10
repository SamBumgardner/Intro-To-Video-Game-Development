# Assignment 3: Working with Collision and Player Input
This assignment is more freeform than previous ones. The requirements below are intentionally 
pretty bare-bones, and were written with the intent of allowing plenty of creativity. Have fun 
with this, and keep in mind that extra effort is rewarded with a deeper understanding of the 
material we've learned!

### Git Setup
 * For this assignment, do your work in the same haxeflixel-practice repoitory that you used 
for assignment 2. The instructions below assume the repository is already created and cloned to
your local machine.
 * Make a branch named `assignment-3` off of your local `master` branch. As you work and commit, 
push this new branch to `origin`.

### Assignment Specifications
Copy all classes used during our in-class example of collision and input on Wednesday into your 
project. Feel free to rename the copied classes however you would like if you want to preserve your 
repository's existing `Playstate` and `Hero` classes.

This example code is available in the `master` branch of my 
[haxeflixel-practice repository](https://github.com/SamBumgardner/haxeflixel-practice).

Using the copied code as a starting point, create a simple game. This game must have an objective
and player-controlled input, and should additionally implement at least **2** new features that
weren't in our example code. 

Here are some example ideas of "features" to help you get started:

 * Give the game a "fail state", a situation where the player has lost. When the "fail state" 
occurs, give the player some way of restarting the game to try again.
 * Add at least 2 new behaviors to the player controlled character that didn't exist in the example
code.
 * Expand the game's FlxState to include objects that begin "off-camera". Also, make the game's
main `FlxCamera` follow the player-controlled character so the player can explore these environments.
 * Visually represent information about the player's status somewhere on the screen. Could include
remaining health, score, abilities, or other things. Pick whatever's relevant to your game.
 * If the player achieves the game's objective, switch active `FlxStates` to a congratulatory 
"you win!" screen. Also Give the player some way of switching back to the original `FlxState`.
 * Add a new type of non-player controlled entity to the game - either helpful or harmful. 

Feel free to come up with your own ideas for cool features to put in the game. Feel free to propose
your feature ideas to me if you'd like, I can help you get an idea of how complex the work might be 
if you're unsure.

### Turn-in Instructions
 * Make a pull request from your `assignment-3` branch to your repository's `master` branch. 
All of this should be done through GitHub. 
 * In the pull request description, tell me what new features you implemented. Also, please tell me
about the game's objective, the player's controls, and any fail states that can occur.
 * Send me a message when your pull request is ready to go. I will review it before you merge it.

**Due Dates:**
The entire assignment is due on Wednesday, April 15th at the start of class (5:30 PM CST).

Waiting until the last day (or hours) before class to complete this assignment greatly diminishes 
the value you get out of it. If you need to, just pretend that it's due **Monday** instead.

Please ask questions as needed throughout your work on the assignment.

**Grading Criteria**
Grading criteria is as follows:

 * Git used correctly for branching and pull request: 2 points.
 * Game has an objective: 1 point.
 * Game accepts and uses player-controlled input: 1 point.
 * Implemented first unique feature: 3 points.
 * Implemented second unique feature: 3 points.

1 point will be deducted for each day that the assignment is late.
