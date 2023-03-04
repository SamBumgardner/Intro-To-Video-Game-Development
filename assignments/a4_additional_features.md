# Bonus Assignment: Exploring Additional HaxeFlixel Features

## Purpose
We'll be getting into our Midterm Project soon, but there are still some features of HaxeFlixel that we haven't explored.

This bonus assignment is meant to function as a catch-all reference for these features, including basic instructions to implement them and suggested tasks to tes your understanding.

## To Do List

### Git Setup
For this (bonus) assignment, use the same repository that we created in 
[In-Class Exercise 2](/lectures/exercises/e2_basic_haxeflixel_project.md).

Create a new branch off of `main` for your work in this assignment. **NOTE:** Don't forget to pull 
down updates from your `origin` remote first! Your local version of the branch may still need to 
catch up after you merged your branch to the GitHub repository's `main` at the end of exercise 2. 

Make sure that your branch is named appropriately for the specific work that you intend to do.

### Topic 0: Fireball!
Let's create a "Fireball" class for use in the other topics. It should move toward some selected point or object (you can choose which to implement).

1. Create a new `FlxSprite`-inheriting class named `Fireball`
2. Take additional parameter in the constructor for what the fireball should move toward - could use `FlxPoint` or `FlxSprite`
3. sets velocity to move toward a point or object (using `FlxVelocity.moveTowardsPoint()` / `FlxVelocity.moveTowardsObject()`)
   1. **NOTE:** if you want the fireball to continue following its target, you'll want to put the `moveTowards<whatever>` call into the `update()` method instead.
4. Add several to the `PlayState`, passing in an appropriate parameters to help them stay on target.
5. Build and run the game, and confirm that the new Fireball objects behave as expected.

### Topic 1: Graphics & Animation
Let's make our `Fireball` class pretty!

**Prerequisites:**
* Topic 0: Fireball!

Follow the steps below to add a static graphic to our Fireball class, then swap-in something fancy and animatable instead. 
1. Copy the [Fireball.png](/assignments/assets/images/Fireball.png) and [Fireball_Sheet.png](/assignments/assets/images/Fireball_Sheet.png) to your project's `assets/images` folder.
2. Update the `Fireball` class to use the static `Fireball.png` graphic.
   
   In the constructor, call [FlxSprite's LoadGraphic() method](https://api.haxeflixel.com/flixel/FlxSprite.html#loadGraphic), passing in `AssetPaths.Fireball__png` as the `FlxGraphicAsset` argument.
3. Build and run the game in debug mode (command: `haxelib run lime test html5 -debug`). 
   
   Press the `~` key to open the debug view, then click on the cube symbol in the top-right corner of the screen to see the size of objects' collision boxes - this helps give you an idea of how large the fireball is logically, which is a bit bigger than its visual representation.
4. Make the Fireball's logical size a bit smaller than its graphic (think of the pirhana plant example in Super Mario Bros.)
   
   You control the size of the collision box with `FlxObject`'s `height` and `width` properties. After reducing those numbers as you see fit, you'll also need to update the `offset.x` and `offset.y` properties from `FlxSprite` to shift the new, smaller collision box to the center of its graphic.
5. Build and run the game in debug mode again and confirm that the fireball's graphic and collision box look as expected.
6. To set up animation for our `Fireball`, we still use `loadGraphic` but with a "sheet"-style image like `Fireball_Sheet.png`. 
   
   Think of it like a flip-book animation - each 32x32 section of the larger images represents a single picture that we expect to play in sequence.

   To ensure `loadGraphic` interprets our image properly (treats it as a series of frames instead of a single large picture), pass in `true` for the `isAnimated` argument, and `32` for the height and width arguments.
7. After `loadGraphic` is called, we can use the `FlxSprite` property `animation`'s [`add()`](https://api.haxeflixel.com/flixel/animation/FlxAnimationController.html#add) and [`play()`](https://api.haxeflixel.com/flixel/animation/FlxAnimationController.html#play) methods.
   1. When we call `animation.add()` you provide a "name" for the animation - it's a sort of identifier, like a dictionary or hashmap key. When we want to trigger the animation later, we'll pass in that name to indicate which animation we'd like to play.

      `add` also requires an array of integers as a parameter, which it calls `Frames`. Imagine our `Fireball_Sheet.png` as a three-item array of images. The numbers we provide to `add` is the sequence we want those images to play in. 

      For example, if we wanted to play the three images in-order one after another we'd pass in `[0, 1, 2, 3]`. If we really, really liked image `2` for some reason, we could pass in an array that features it many times - `[2, 0, 2, 1, 2, 2, 3, 2]` is a valid input, it'd just use that last fireball image a ton of times.

      `add` also allows us to decide the framerate that the animation should play at (in frames-per-second). You can fiddle around with this number as you'd like - for this particlar graphic, I think it looks better with a slow framerate like `5`.
   2. `animation.play()` is relatively simple to use - we just provide the "name" we picked when calling `animation.add()` and it'll play back the animation we prepared.
8. Build and test the game one more time to confirm that the `Fireball` is animating beautifully.

### Topic 2: Custom Overlap Logic
Let's try executing custom logic when `Fireball`s and `ControllableHero`s overlap!

**Prerequisites:**
* Topic 0: Fireball!

Rough outline of the steps involved:
1. Create a method for handling overlap between Controllable Hero and Fireball class - just have it `trace("Worlds Collide!")` or something similar at first. 
2. Call FlxG.overlap, passing in controllable hero, an FlxGroup of our Fireballs, and our new method
3. Play around with different kinds of logic - for instance, `kill()` the `Fireball`, `hurt()` the `ControllableHero`.

### Topic 3: Infinite Fireballs
Running out of `Fireball`s makes for a short game - let's find a way to keep our supply from running out in a performant way.

**Prerequisites:**
* Topic 0: Fireball!
* Topic 2: Custom Overlap Logic

Rough outline of the steps involved:
1. Start inefficient - just figure out how to make new fireballs get created periodically during the `PlayState`'s `update()`
2. Clean up fireballs after they're not useful anymore - call `kill()` after they overlap with player or go offscreen
3. Override `Fireball.reset()` logic. If we've got a `Fireball` that's dead, `reset()` can be a method to make it alive, reset position and velocity, etc. so it can be reusued.
4. Change inefficient logic in `PlayState.update()` that we created at first. Instead of creating new `Fireball`s periodically, use the `getFirstDead()` method of the `FlxGroup` that contains fireballs. If one was successfully retrieved, we can call `reset()` on it to make it not-dead and execute the logic you prepared in step 3.

### Topic 4: Sound
Add some audio fun to the game by playing a sound effect when overlaps occur.

**Prerequisites:**
* Topic 0: Fireball!
* Topic 2: Custom Overlap Logic

Rough outline of the steps involved:
1. Copy [Shoop.wav](/assignments/assets/sound/shoop.wav) to your project's `assets/sound` folder
2. In the custom overlap function created during Topic 2, add a call to [`FlxG.sound.play()`](https://api.haxeflixel.com/flixel/system/frontEnds/SoundFrontEnd.html#play). Pass in `AssetPaths.shoop__wav` as the `embeddedSound` parameter.
3. [`FlxG.sound.playMusic()`](https://api.haxeflixel.com/flixel/system/frontEnds/SoundFrontEnd.html#playMusic) is a convenient way to set up a looping song in the background. `closeStars_v6.wav` and `schemingAnew_v11.ogg` are two short songs you can try integrating into the project if you would like.

### Pull Request(s) and Review
I recommend opening pull requests for your work as a way to keep track of everything you did.

Feel free to send any my way if you'd like review as well, though it's certainly not required.

## Grading Criteria
This assignment will not be collected for a grade, it's meant as a practice exercise that may be useful to refer back to as we work on our midterm project.
