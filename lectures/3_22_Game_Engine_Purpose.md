# A Game Engine's Purpose

Before we start using a game engine, it's important to understand what they're supposed to do.

Here are a few feature trailers for modern game engines:
 * [Unreal Engine 4](https://www.youtube.com/watch?v=l88n8a4Yphw)
 * [Unity 5](https://www.youtube.com/watch?v=AJ6Mkx1KEns)
 
Based on the information from those videos, we might say that game engines...
 * provide a GUI interface for viewing, editing, and testing a game
 * implement systems for lighting, particle effects, materials, and other graphics-related features
 * implement systems for audio loading and mixing.
 * provide a system for creating, editing, and viewing cutscenes
 * implement systems for online multiplayer
 * handle the translation of one game's code to multiple console targets
 * provide a system for adding and controlling animations
 * provide a system for creating, connecting, and using various UI elements
 * provide profiling tools for monitoring game performance
 * provide a cloud-building system independent of a particular machine.
 * and a bunch of other things that weren't shown in the trailers.
 
I tried to think of something all of those features had in common, but it was hard to think of any big idea that tied them all together. All that I've managed to pick out is the fact that they all might be useful when making a game. But really, that's the key to it all: the purpose of a game engine is to make the process of building games easier.
 
## Building a Game Without an Engine

It's a daunting task. Seriously. To make a 3D game with a bare minimum set of features expected in a modern 3D game, you'd need to gather and learn a set of libraries similar to the following list:
* Graphics Library - OpenGL
* Load models - Assimp
* Load textures - stb image library
* Load and play sound files - irrklang (requires licence if used for a commercial product)
* Skeletal animation system - cal3d (maybe - it might be terrible. I haven't used it before)

And this doesn't include any systems that abstract away the work of any subsystem described above. You'd have to write your own rendering system, a physics system, a networking system (probably involves building a protocol on top of UDP for speed's sake) and much, much more. For reference, here's a nice image of the layers of code needed to implement [everything in a modern game engine](https://www.gamedev.net/uploads/monthly_11_2013/post-216159-0-35067600-1385676201.png).
