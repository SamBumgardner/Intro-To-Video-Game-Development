# Working with Haxeflixel: Graphics and Sound
The notes here assume that we're familiar with creating the core functionality of a game (things 
like an update loop, input handling, overlap calculation, collision resolution). It's definitely 
possible to build something fun with just the basics, but adding more interesting graphics and 
sound can add a lot to our game!

**Note:** As a whole, this lesson is a lot more HaxeFlixel specific; these lessons won't 
necessarily be very portable to other game engines. To offset that, we lead in with a broader 
discussion of the graphics pipeline.

## Graphics Pipeline Overview
While it is possible to make a game without knowing anything about how your computer's graphics 
pipeline works (in fact, it's pretty easy with all of the cool engines available nowadays) the 
terminology and concepts related to it are commonly used enough that we can't really afford to 
ignore it. Also, the rendering of graphics can have a very significant impact on any game's 
performance. At least knowing how to start talking about it is important.

From a high-level perspective, your computer only needs a few things to start drawing pictures on 
your screen:
 * A series of points in space (vertexes)
 * A strategy for connecting these points into shapes
 * Information about how to color these shapes.

In graphics programming, our work is basically just providing this info to our computer via a 
graphics API (a library of code, more or less) like OpenGL or DirectX. The process of the computer
applying that information to generate an image is what we call "the graphics pipeline."

Here's a basic visualization of [the OpenGL graphics pipeline](https://learnopengl.com/img/getting-started/pipeline.png)

And here's some explanation for what each of those steps in the pipeline are doing:
 * **Vertex Shader**: Given some coordinate information, output altered or transformed coordinates 
 that represent final screen position.
 * **Shape Assembly**: Connect related vertices together into shapes (often, triangles)
 * **Geometry Shader**: Given a connected shape, do additional calculations to output another shape.
 * **Rasterization**: Convert shapes with positions specified by a coordinate system into 
 individual pixels on a screen.
 * **Fragment Shader**: Given a single pixel, do additional calculations to determine final color.
 * **Tests and Blending**: Checks and calculations for depth and transparency (for when things are 
 drawn in front of one another)

As a graphics programmer, we control the inputs to this pipeline and the functionality of the 
Vertex, Geometry, and Fragment shader. Through these shaders, we decide how to do transformations 
on the position of individual points (vertex shader), we can use shape information to do further 
calculations (geometry shader), and we can do all sorts of fun things to determine the final color 
(fragment shader). When we talk about lighting, shadow, or most other "fancy" effects in graphics, 
these are basically all computed in the fragment shader. Things can get more complicated, but it's 
a decent understanding for our purposes.

These "shaders" are actually separate programs from your main game, which the graphics library 
compiles and loads onto your graphics card - all processing that shaders do is handled there rather 
than in the CPU.

To get a deeper understanding of this topic and others, I really recommend working through the 
[Learn OpenGL tutorial series](https://learnopengl.com/). It's an excellent resource that covers 
this deep topic much more thoroughly and effectively than I can.

## Graphics in HaxeFlixel
### Static Images
**Note:** Our discussion about HaxeFlixel today will focus on simple, practical usage of the 
engine's features. Do note that the engine does expose some lower-level graphics functionality 
that gives you more control over performance.

When using HaxeFlixel, most basic interactions with the graphics system happen through FlxSprite 
and its associated classes. Up to this point, we've just used FlxSprite's MakeGraphic(). 

It's useful for quick tests, or for providing a simple visual representation of an object's 
physical space. It's also very boring.

When you have an image you'd like to use instead, we'll want use FlxSprite's 
[loadGraphic()](https://api.haxeflixel.com/flixel/FlxSprite.html#loadGraphic) method. The value we 
provide as the `Graphic` argument will be one of the generated fields of the `AssetPaths` 
class. 

If not animated, can stop there. Just have a static graphic associated with the sprite. Note that 
your object's width and height will automatically change to match that of the loaded graphic. 
If you'd like them to be different, adjust FlxObject's width, height, and offset variables as 
needed.


### Using AssetPaths
We'll discuss `AssetPaths` more in class, but the basic idea is that any files that you've put under 
the `assets/` directory in your project can be referenced via `AssetPaths.<your_file_name_here>`,
with any `.` in the filename (like in the filename extension) replaced with two underscores (`__`)

To give an example, the csc-303-game-2021 project has [an image named `Fireball.png`](https://github.com/SamBumgardner/csc-303-game-2021/blob/main/assets/images/Fireball.png)
stored under the `assets/` directory, specifically at `assets/images/Fireball.png`. To use this 
simple graphic in the `Fireball.hx` class, the project simply has:
```
loadGraphic(AssetPaths.Fireball__png);
```
([see it in-project](https://github.com/SamBumgardner/csc-303-game-2021/blob/main/source/actors/enemies/Fireball.hx#L15))

HaxeFlixel's AssetPaths class is using clever preprocessor work to make sure that the `AssetPaths`
class will correctly route to any kind of resources stored inside your `assets/` directory 
(graphics, fonts, sounds, text files, etc.).

### Animated Images
To animate a graphic in HaxeFlixel, you first need a graphic in a "sprite sheet" format: a series 
of equally sized images arranged in a row or grid, each image representing a single frame of 
animation. Here's an example, [a set of Castlevania character sprites](https://github.com/SamBumgardner/csc-303-platformer-2018/blob/master/assets/images/HeroSpritesheet.png)
arranged into a single sheet.

After you have a sprite sheet, the code starts similarly to how we handled a "static image" before.
Here's how the process differs:
 1. In `LoadGraphic()` Set `Animated` parameter to true, and `Width` and `Height` to width and 
 height of an individual frame in pixels. 
   * This prepares each frame of animation for use, but the game doesn't know how to use them (yet).
 2. Set up each animation that want to be able to play. This is handled through the 
 `FlxAnimationController` class. Each `FlxSprite` has one created and assigned to its `animation` 
 variable (it's almost like the component pattern!).
   * To do this, call [`animation.add()`](https://api.haxeflixel.com/flixel/animation/FlxAnimationController.html#add) 
   to set up a new animation. Make sure that you remember what you pass in as the `name` argument 
   each time (or better yet, make it a static, constant variable).

An example of how this could look in code:
```
loadGraphic(AssetPaths.HeroSpritesheet__png, true, 48, 48);

animation.add(STAND_ANIMATION, [0], 1, false);
animation.add(RUN_ANIMATION, [1, 2, 3, 1, 4, 5], 10);
animation.add(SKID_ANIMATION, [6, 7, 7, 8], 8, false);
animation.add(CROUCH_ANIMATION, [17, 18], 8, false);
animation.add(RISING_AIR_ANIMATION, [19, 20], 8, false);
animation.add(FALLING_AIR_ANIMATION, [21, 22, 23], 6, false);
```
Where the variables `STAND_ANIMATION` etc. are constant string variables. (see full code in 
[csc-303-platformer-2018's Player class](https://github.com/SamBumgardner/csc-303-platformer-2018/blob/master/source/player/Player.hx#L59-L70))

After animations are added, simply use `animation.play(<animation_name>)`: 
```
animation.play(STAND_ANIMATION);
```

## Sound in HaxeFlixel
Programming with sound, like graphics, is an expansive enough topic to fill a class. In the 
interest of time, we're going to just focus on simple, practical usage in HaxeFlixel. It's a bit
easier for us to get away with a hand-wavey explanation, I think, because in smaller games simple 
sound works fine without presenting the same dangerous processing bottleneck as graphics.

Some games have really impressive and impactful sound design and programming at work, games like 
*DOOM (2016)*'s reactive soundtrack or *Warhammer: End Times - Vermintide*'s directional audio 
that's used to communicate vital gameplay information. (As you might guess) Haxeflixel doesn't 
present any complex system for mimicking those fancy implementations.

We basically just get a simple system for loading and playing back sound files at various volumes.
Anything much fancier than that will need some legwork to make happen.

Here's how we'll work with the basics:
 1. Access a shared instance of [`SoundFrontEnd`](https://api.haxeflixel.com/flixel/system/frontEnds/SoundFrontEnd.html) 
 via `FlxG`'s static fields
   * `FlxG.sound`
 2. (OPTIONAL) Use the [`cache()` function](https://api.haxeflixel.com/flixel/system/frontEnds/SoundFrontEnd.html#cache) 
 to prepare sounds before they're needed.
   * Use `AssetPaths` to get a reference to a sound file stored in your `assets/` directory, that's 
   what should be passed as `EmbeddedSound`
 1. For simplest usage, you can just use the `SoundFrontEnd`'s [`play()` method](https://api.haxeflixel.com/flixel/system/frontEnds/SoundFrontEnd.html#play). 
 It'll attempt to load the sound if it wasn't loaded before, then it'll play it according to the 
 provided parameters.
 4. If you want to play a long, looping background track, [`SoundFrontEnd.playMusic()`](https://api.haxeflixel.com/flixel/system/frontEnds/SoundFrontEnd.html#playMusic) 
 provides an even simpler interface to make it work without much extra effort.

It's worth noting that the larger your sound file is, the more of a performance hit your game will
take when it's loaded into memory. If you don't want a large sound disrupting the flow of gameplay,
use  `cache()` method when a scene's created (or even earlier) so you can control when 
performance will take a dip.

### File Formats
There's not too much to say here. HaxeFlixel supports a variety of sound formats, but the 
recommended way to handle formats is to use `.wav` files for smaller sound effects and `.ogg` files 
for longer background music tracks.

`.wav` files are fast to load and process, but are less memory efficient. `.ogg` take the side of 
the tradeoff - they are much more compressed and space efficient, but are more processing intensive.

It won't be the end of the world if you misuse file formats, but it's worth using each tool for 
what it's best suited for.