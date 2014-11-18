simpleWebRTCdemo
================

the most basic simpleWebRTC demo you can make- a video chat with every remote user popping up below you in your browser.  It can be run in one chrome browser with multiple tabs.

I've been attempting to teach myself Node and webRTC recently, and I need the extra functionality and customizability that simpleWebRTC provides, even though it's a bit more opaque than other Node modules designed for this task.  
Other Node modules do an excellent job abstracting away the complexity, if you're looking to simply do VoIP or video applications you should take a look at peer.js or holla.  They work easily and sound pretty good for voice, but when passing music they're compressed, distorted, and narrowband.  
With simpleWebRTC, you still have the option to dive into the SDP configuration (accessing things like bitrate, codec selection (Opus is the goto choice), etc.) so that higher quality can be valued over latency.

It's important to note that echo cancelation, typing detection, and other 'wonderful' audio filtering features are frequently enabled by default.  For Chrome, if you use the 'getUserMedia' command (which is a basic HTML5 command, and bubbles up in the higher level services like peer and holla), add a constraint like this in order to turn off some of the default behavior.

```
audio: { mandatory: { echoCancellation: false }}
```

In any case, if you're convinced you need the more advanced configuration of simpleWebRTC, this is a good starting point.


#1)
Clone/copy this repo to your computer.

#2)
Install a signal server:

To get this demo working, you must go to the terminal (with node installed), and make a directory for a signaling server.  CD into that directory and:

```
git clone https://github.com/andyet/signalmaster ./
npm install
node server.js
```

This will start a signaling server on your localhost (it should be at http://localhost:8888).  This server is used as an intermediary to establish the webRTC peer to peer connection.

#3)
Run the thing.

CD to the directory and:
```
node app.js
```

It'll pop up on http://localhost:3000



I'll probably be slashing through simpleWebRTC to try and get high quality/wide-band audio streaming, at the potential expense of latency.  If I get something interesting working I'll post.

dramsay@mit.edu
