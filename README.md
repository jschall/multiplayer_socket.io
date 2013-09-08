#multiplayer_socket.io
=====================
This is a Node.js / Socket.IO multiplayer game server experiment. In its current state, when a client connects to the server, the user is asked to select a number from 0 to 3 (four numbers, each representing one of the four character classes in the Super Gauntlet game).

Once the character class id is selected, a client side Player object is instantiated and news of this event is sent to the server. The server instantiates a client side Player object with the same properties as contained within the transmitted client Player object and stored in a players[] array.

The server then broadcasts the news of the newly-connected player to all other connected clients(if any).
The client side code then draws the localPlayer via HTML5 Canvas. The user can then move the drawn square (representing the player) in the browser by pressing the arrow keys.

Every time a new client (new browser window) connects to the server, this process is repeated and all connected clients have their Canvas updated with the addition of the new remote player.

I've been attempting to assign and transmit character class information throughout this process, but all attempts have met failure. The movement and location of each local player stays constant, but with each addition of a new player, the colors switch when they should remain constant. I cannot find the error in the code that is causing this...

##Likely Functions Causing this Behavior
In server.js: ( onNewPlayer(data) )
In super_gauntlet.js ( onNewPlayer(data) )
In public/Player.js ( draw(context) )


##Requirements to Experiment with this Code
1. Download repository folder. In console, switch to the directory
2. Install Node.js http://nodejs.org 
3. Install Node Package Manager
4. Install Socket.IO
5. Type:       node server.js
6. Open public/index.html in a browser. Select a number from 0 to 3 (representing a character class). Move the character with the arrow keys.
7. Open a seperate browser window and repeat the process with a different number to instantiate a different character class. Move the character around in the second window. Switch back and forth, and you will see the players' movements are in sync, but the colors are not correct. This needs to be fixed.


####The Character Class Colors Are:
* Fighter = 0 = Red
* Ranger = 1 = Green
* Wizard = 2 = Blue
* Cleric = 3 = Yellow

