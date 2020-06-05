# 2DPlayerController

2D Player Controller for Platform Game Type in Unity. 

This is the code for the first platform game that I built on Unity. 

Here's the link to play the game - https://simmer.io/@harirockstar97/draco-s-adventure 

For the Play/Retry Buttons to work, Unity scenes need to be in the right order. The first scene consists of the main menu which is followed by the main game. 

PLAYER CONTROLLER

It took me a lot of tries to get the player movement to "feel" right. Try experimenting with different physics parameters such as friction, gravity and velocity. The player uses default RigidBody 2D Physics inbuilt in Unity.

The movement controls are fairly basic, with simple velocity values for x-axis. Jump is allowed only when the player's 2D Collider is in contact with surfaces that have the specific tag of "ground". 

Tip: Use FixedUpdate to ensure smooth movement of character

The script uses a Finite State Model, which is basically a way of instructing the computer which "state" the player is in, such as running, jumping or attacking. With every frame, the MovementState() function checks which state the player is in. This is accomplished using a string of if statements 

First condition is checking whether the player's velocity is x direction is greater than 2. In this case the player is running, since a player's velocity will be greater than 0 is if the arrow keys (for movement are pressed. However, when the player is "hurt", a negative velocity is imparted which too satisfies this >2 condition and therefore this has to be accounted for in the "if" statement conditions. 

Similarly, vertical velocity values are checked to determine if player is jumping or landing 

Similarly, when the player presses "F" button to attack, the state is that of attacking and player movement is restricted.

ELSE IF, player is idle. 

All of these statements have been included in functions outside of the main update() loop. The update loop takes player movement, checks state and lastly plays the appropriate animation. 

In case you're wondering what the Hurttimer or attacktimer are, those are simply to keep track of time (this is NOT the most efficient method though) so that animation can be played and movement resumed. 

And then there is a function which checks health to see if the player has died and GameOver() is called. 
