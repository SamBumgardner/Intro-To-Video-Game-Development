# Assignment 3: Creating Heroes with Varied Behavior

## Purpose
Now that we have an idea of how HaxeFlixel is structured (and some idea of how to read its API 
documentation) it's time that we started actually making something with it!

This assignment will give you some practice creating a variety of "heroes" with different logic
and functionality.

## To Do List
The instructions below will involve using methods and classes we haven't discussed directly in 
class. Remember that the [HaxeFlixel API documentation](https://api.haxeflixel.com/) is a powerful 
resource for learning more about these unfamiliar tools - the assignment should link you to 
relevant documentation in places that I anticipate being unfamiliar, but don't hesitate to pull 
it up whenever you need some more information about what HaxeFlixel is actually doing in the 
background.

### Git Setup
For this assignment, use the same repository that we created in 
[In-Class Exercise 2](/lectures/exercises/e2_basic_haxeflixel_project.md).

Create a new branch off of `main` for your work in this assignment. **NOTE:** Don't forget to pull 
down updates from your `origin` remote first! Your local version of the branch may still need to 
catch up after you merged your branch to the GitHub repository's `main` at the end of exercise 2. 

Make sure that your branch is named appropriately for the specific work that you intend to do.

### Part 1: Warm-Up with "Hello World"
If you did the ["Hello World" tutorial in HaxeFlixel's Getting Started guide](https://haxeflixel.com/documentation/hello-world/), 
a lot of this will be pretty familiar. It's not exactly the same, though: we're layering on some 
extra functionality to get used to exploring HaxeFlixel's capabilities.

 1. Inside the `PlayState`'s create function, create 
    [an `FlxText` object](https://api.haxeflixel.com/flixel/text/FlxText.html) that contains some 
    variation of the message "hello world".
 2. Use the `PlayState`'s `add()` function to make this `FlxText` object appear on-screen when the 
    game is run.
 3. Change the `X` and `Y` parameters to the `FlxText` object to make the "hello world" message 
    appear somewhere near the middle of the screen.
 4. Change the look of the "hello world" message to be significantly different from its default 
    appearance.
    * Check out documentation for [FlxText](https://api.haxeflixel.com/flixel/text/FlxText.html) 
    or its parent class, [FlxSprite](https://api.haxeflixel.com/flixel/FlxSprite.html) to find some 
    properties and methods that you can use to adjust its appearance.

Test your work by running `lime test html5` from a command prompt navigated to your project's root directory.

When you're finished making updates, make sure to save, commit, and push your work to your branch
before moving on to the next part.

### Part 2: The "Screensaver" Hero
 1. Create a new file in the project called `ScreensaverHero.hx`.
 2. In that file, create the `ScreensaverHero` class that *extends* `FlxSprite`.
 3. Inside the `ScreensaverHero`'s constructor, use `makeGraphic()` to give it a simple 
 rectangle graphic.
    * Don't forget to call its parent's constructor with `super()` before you try to use inherited
    methods.
 4. Inside the `ScreensaverHero`'s `update()` function, set its 
 [`color` property](https://api.haxeflixel.com/flixel/FlxSprite.html#color) to a value that is 
 somehow determined by screen position (how is up to you).
    * Look at the `PlayState` class for an example of overriding and update function.
    * `color` can be a bit finicky to work with. Assigning it a 32 bit hexidecimal number (like 
    `color = 0xff00ff00`) works, or you can use [static properties defined in `FlxColor`](https://api.haxeflixel.com/flixel/util/FlxColor.html)
    if you prefer.
 5. Make `ScreensaverHero`s move automatically each frame.
 6. Randomize the direction of its movement when it is created.
    * Check out the statically available [`FlxG.random`](https://api.haxeflixel.com/flixel/FlxG.html#random) 
    property for a straightforward way to generate random numbers. For documentation on its methods, see 
    the [FlxRandom class in the API reference](https://api.haxeflixel.com/flixel/math/FlxRandom.html).
 8. Add multiple `ScreensaverHero` objects to the `PlayState`. Because their movement is randomized
 at creation time, even if they start in the same position they should split up quickly.

#### Part 2: BONUS
Completing these tasks is optional. Each task completed is worth 1 extra point, though the total 
score for the assignment cannot exceed 12 out of 10.
 1. Make `ScreensaverHero`s wrap screen vertically and horizontally, so when they move off of one 
    side of the screen, they reappear on the opposite side.
 2. Make [keyboard input](https://haxeflixel.com/documentation/keyboard/) or 
    [mouse input](https://haxeflixel.com/documentation/mouse/) influence the movement of 
    `ScreensaverHero` objects in some way.

#### Part 2: Wrap Up
Test your work by running `lime test html5` from a terminal in your project's root directory.

When you're finished making updates, make sure to save, commit, and push your work to your branch
before moving on to the next part.

### Part 3: The "Controllable" Hero
 1. Create a new file in the project called `ControllableHero.hx`.
 2. In that file, create the `ControllableHero` class that *extends* `FlxSprite`.
 3. Inside the `ControllableHero`'s constructor, use `makeGraphic()` to give it a simple 
    rectangle graphic.
    * Don't forget to call its parent's constructor with `super()` before you try to use inherited
    methods.
 4. Inside the `ControllableHero`'s update method, add logic to make it move 
    [according to keyboard input](https://haxeflixel.com/documentation/keyboard/):
    1. It should move upward if the "up arrow" key is pressed.
    2. It should move left if the "left arrow" key is pressed.
    3. It should move down if the "down arrow" key is pressed.
    4. It should move right if the "right arrow" key is pressed.
    5. It should stop moving if no arrow keys are pressed.
 5. Add a single `ControllableHero` to the `PlayState`, and (optionally) remove the `Hero` we 
 instantiated and added to the state during the in-class exercise.

#### Part 3: BONUS 
Completing these tasks is optional. Each task completed is worth 1 extra point, though the total 
score for the assignment cannot exceed 12 out of 10.
 1. Create a `Wall` class, add several to the `PlayState` and make them immovable obstacles that
    block the `ControllableHero`'s movement.
    * Make `Wall` extend `FlxSprite`, so it can use the [`immovable` property](https://api.haxeflixel.com/flixel/FlxObject.html#immovable) 
    to keep them from getting pushed around during collision.
    * Use [`FlxG.collide()`](https://api.haxeflixel.com/flixel/FlxG.html#collide) to handle 
    collision between the `ControllableHero` and `Wall`s. Since both need to be passed into the
    method, it'll be easiest to do this inside the `PlayState`'s `update()` method
 2. Add logic to the `PlayState` to check for overlaps between our `ControllableHero` and the
    `ScreensaverHero` objects we made earlier. 
    * Use [FlxG.overlap()](https://api.haxeflixel.com/flixel/FlxG.html#overlap) to notice when
    the objects touch and execute the custom logic. 
    * The `NotifyCallback` parameter on that method should be a reference to a function - the
    thing you want to have called if the overlap is detected.
    * The behavior that is in that `NotifyCallback` function can be anything you want - log a 
    message with `trace()`, `kill()` some of the objects involved, increase a `score` variable 
    you've added to the `PlayState` - anything is fine.

#### Part 3: Wrap Up
Test your work by running `lime test html5` from a terminal in your project's root directory.

When you're finished making updates, make sure to save, commit, and push your work to your branch.

### Pull Request and Review
After finishing parts 1 through 3 described above, submit your work by opening a pull request from
your branch to `main`.

After the pull request is open, request review from others, students (optional) and 
professor (required).

After receiving approval from the professor, merge. Make sure to update your local `main` branch to 
be caught up with the newly applied changes.

## Due Date 
Thursday, 2/23/2022 @ 5:30 PM 

## Deliverables
There's no external deliverable attached to this assignment. The act of opening a pull request is
your submission.

Let the professor know when your changes are ready for review via message in Discord or an email
sent to bumgardner125@live.missouristate.edu

## Grading Criteria
Opening your pull request before the due date, addressing any comments or feedback on that pull 
request, then merging it within 2 days is worth a full 10 points.

Points will be deducted for opening the pull request late (1 point lost each day) or for failing to
address pull request review comments (1 point lost per day after the post-review 2-day grace 
period).

Basically, open the PR before the due date and address any issues found promptly and you'll be fine.
