# Assignment 1: Introduction to Git, Haxe, & Haxeflixel
* Assignment: 
	1. Fork repository with nearly empty Haxeflixel project set up in it. Clone the forked repository to your local machine.
	2. Make hello-world branch off of your local `master` branch. Push this new branch (and all further changes) to your forked (`origin`) repository.
	3. Inside the `PlayState`'s `create()`, create an `FlxText` object that contains some variation of the message "hello world". 
	4. Use the `PlayState`'s `add()` function to make your `FlxText` object appear on-screen when the game is run.
	5. Change the `X` and `Y` parameters to the `FlxText` object to make the "hello world" message appear somewhere near the middle of the screen
* Bonus:
	1. Change the look of the "hello world" message to be significantly different from the default look. 
	2. Make the hello world text move around the screen somehow. 
		* Hint: If attempting to use `velocity` to move the `FlxText` object, you may need to look into the source code for `FlxText` to understand why it won't initially work.
			* Double Hint: If you're really stuck, follow [this link](https://github.com/HaxeFlixel/flixel/blob/master/flixel/text/FlxText.hx#L208) to see what needs to be changed.