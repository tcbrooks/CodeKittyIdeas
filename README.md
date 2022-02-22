# Code Block Editor

## Can we make it ourselves?
The more I look into this, the more I feel it’s a near impossible amount of work to code this ourselves. The complexity required to have draggable blocks that are retrieved from a predefined toolbox, fit together in any way, and can be run is a lot. Let’s look at some open source libraries.

## Open Source Libraries 
The first red flag that we might not be able to make one from scratch is that google is the only real contender for this. Even Microsoft’s MakeCode and Scratch are just using modified versions of google’s Blockly. 
- https://github.com/microsoft/pxt-blockly

- https://developers.googleblog.com/2019/01/scratch-30s-new-programming-blocks.html

## Blockly
So let’s take a look at Blockly:
- https://developers.google.com/blockly/

- https://github.com/google/blockly

- https://developers.google.com/blockly/guides/overview

Now this is pretty complicated but after reading through the documentation, you can define custom blocks that will then generate code for your application to use. They provide their own tool for doing this which is pretty nice:
- https://developers.google.com/blockly/guides/create-custom-blocks/blockly-developer-tools

Unfortunately the documentation really doesn’t answer all my questions I have, here are some of the key ones:
- Running the code, pausing it, stepping through it
- step-by-step highlighting each instruction as it runs 
- how you would use it inside a game engine. 

Let’s try and answer these.

## Blockly inside a game?
Google provides some demos, including Blockly Games which do most of what we would want
- https://github.com/google/blockly-games

Unfortunately these really are just demos, they contain no documentation, and although we could possibly learn some things from these examples it would probably be easier to find something else

## Blocky-gamepad
So we head to stack overflow where we find this question:
- https://stackoverflow.com/questions/56725374/unity-and-googles-blockly-library-integration

Turns out someone has created a nice library for Blockly which allows us “interact asynchronously with Blockly using methods like **load**() & **reset**() to init the game, **play**() & **pause**() to start the game, **forward**() & **backward**() to move step-by-step through the blocks and others useful methods”

## Could we use this with PlayCanvas?
This might be possible, after some searching it seems someone has done it:
- https://github.com/enixsoft/blockly-game-laravel

I haven’t gotten around to running or picking though it yet, but it could be a good reference point if we decide we are set on PlayCanvas

## Other Engines
I wanted to look into this, because as I was doing some basic PlayCanvas tutorials and thinking about how our game could be designed I realized a few things. PlayCanvas seems to specialize more in 3D physics based games. After some research, I really feel we should scale down our engine to something simpler and more for 2D or Isometric games. Here's a few Reddit suggestions, personally I think Phaser would be our best choice.
- https://www.reddit.com/r/gamedev/comments/iincs3/what_game_engine_could_you_sugest_for_isometric/

If we were to go with Phaser, there’s actually a library and an example game that incorporates Blockly that I was able to find pretty easily. Here’s the “game” and source:
- http://gaufqwi.github.io/blockly-tests/gridworld.html

- https://github.com/gaufqwi/blockly-tests/

This is actually what Microsoft did for their Minecraft coding game you can read about it and check it out here:
- https://phaser.io/news/2015/12/minecraft-meets-hour-of-code

- https://studio.code.org/s/aquatic/lessons/1/levels/2

Unfortunately I couldn’t find the source code for this, but they do have a GitHub page with a customized version of Blockly and a demo which might be worth looking into
- https://github.com/orgs/code-dot-org/repositories?type=all

## Where should we start?
I think the first thing we would need to do is create a game that’s simple where we can control a player with the arrow keys, perform an action that could change depending on what the player has equipped bounded to some other key. A good example of this is the Minecraft Craft game which I mentioned above. They provide the source and a playable version of what they used as a base for their Blockly educational game:
- https://code-dot-org.github.io/craft/

- https://github.com/code-dot-org/craft

As you can see even using Phaser and before implementing level progression or Blockly, a simple game like this can get quite complicated. 

Now if we use level based progression, where each level presents a new slightly harder “maze” to solve, we will have our work cut out for us. Not only in coding the actual progression aspects, but in level design. Each level will need a different thought out “maze” for the player to work through and this will require us to plan out each of these very carefully. However from the beginner-friendly games I played online this was sort of the goto. This isn’t the only option though.

We aren’t required to make our game feature completely kid friendly with “training wheels” our game can be whatever we want as long as it teaches programming or makes the player think in a programmatic way. By far my favorite game I found was this:
- https://www.supercodingball.com/offline-opponents

- https://github.com/Orange-OpenSource/super-coding-ball

Having the user play a game against a computer where they choose how difficult it is, and then design their own sort of “ai” that will play against the computer. Designing our game like this could allow us to create a single game instead of multiple levels. And instead of the player writing new code to solve a new problem, we have them build off their original code to defeat the computer.

However, these are just my thoughts after looking into this for awhile. It's up to the group on how we procede, I just wanted to know what it would take to implement a visual code editor before we committed to a particular engine or game design.

