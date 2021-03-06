<h1>Chiquitita</h1>

Inspired by "TwitchPlaysPokemon", this is a way for multiple users to simultaneously play a remote SNES emulator via a web interface. Invite your friends to join in and try to play the game at the same time, resulting in much confusion and anguish. Screencast the game for even more fun!


<h3>Install and Run</h3>
<hr />

To install:

<pre>
sudo apt-get install nodejs npm zsnes xdotool git
git clone https://github.com/nathanharper/Chiquitita.git
cd Chiquitita
npm install
</pre>

This command will start up the zsnes emulator, start a server at http://localhost:12345, and open it in a browser window. You can theoretically use other snes emulators, or basically anything that runs in an X window. Should work on Linux and Mac, though dependency installation method will obviously vary.

<pre>./run_http.sh super_mario.smc</pre>

To just start the server with ZSNES already running, do this (replacing [PORT] with the port to run the server on):

<pre>node server/server.js "$(xdotool search --class ZSNES|awk 'NR==1{print $1}')" [PORT] http</pre>


<h3>Configuration</h3>
<hr />

If you're not using the default ZSNES configuration scheme, or you're trying to configure this for another emulator, you can change the server/keys.json file. It's a straightforward JSON array of char/key codes and the button name associated with each (for more details on the codes, check out jQuery's documentation for event.which).


<h3>TODO</h3>
<hr />

* I'd like to make it so that subsequent keypresses always trump the prior one, to make the multi-player support a bit wackier.
* Might be worth it to make a native Node binding to libxdo instead of delegating to shell.


<h3>Special Thanks</h3>
<hr />

I yoinked the wonderful HTML/CSS snes controller from <a href="http://codepen.io/TimPietrusky/pen/oJIcy">Tim Pietrusky on Codepen</a>!
