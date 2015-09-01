---
layout: post
category : GSoC
tagline: "Week 2 Google Summer of Code Summary"
tags : [GSoC, Processing, networking, project]
---

Its been a pretty fun week coding over here. This is the first week I struck out onto my own to write my own network streaming Processing library over UDP. At the end of the week, I was able to create a library that allows Processing users to stream webcam and sketch images over UDP.

The first half of the week was devoted to setting up the development environment and getting the structure of the library in order to really start work on the video streaming library. Of course, as any “simple” thing is in computing, it took way longer than expected as I ran into many problems. First of all, the buildpaths in the sample processing library template are all for OSX, and so it took me forever to figure out that all the slashes / need to be \\ on windows (because one \ is an escape character, so to have an actual slash you need two of them). I also ran into problems finding `tools.jar` as part of the JDK and setting up eclipse with the right versions of Java. Finally the last problem was with git submodules, as I forked the processing library template into my working directory so git wouldn’t track any new changes inside those files. These problems consumed my Monday and Tuesday, but then I was able to move onto the more exciting things.

Starting on Tuesday afternoon, I used a [UDP tutorial](http://shiffman.net/2010/11/13/streaming-video-with-udp-in-processing/) to build a simple webcam streaming example program. All the logic of the networking pieces (like setting up datagram ports, compressing the image, creating packets) is all done in my library now, so sending a frame is as simple as calling `broadcast(c)`, where c is a `Capture` object (although it could be any `PImage`). The example sketches I wrote are super super simple now, and I’m proud of how little code a Processing user will have to write to stream webcam feeds. The library code is structured into two files, `videoBroadcaster.java` and `videoReceiver.java`, which act as a server/client.

I then built on top of the `broadcast()` function to be able to share any sketch’s screen. By simply calling `screenBroadcast()` with no arguments in the draw function, whatever is currently displayed on one sketch’s screen will be streamed to the client sketch. This makes it trivial to share complex designs across different Processing sketches.

Finally, I took another look at what I built last week and modified the `serverEvent` function so that it won’t conflict/break other example code. Now there is a method `serverDisconnectEvent(Server, Client)` that is fired whenever a client disconnects. This is important now that I can keep track of individual clients, because then I can find out which exact client left. I think the code is robust enough to potentially be merged into the actual core library.

There are obviously many next steps that can be done. First, these methods are all blocking which is not ideal. Incorporating threads is an obvious next step. I also want to stream audio, because I can’t find a library that will do it. I’m going to take some mentor advice and look into [GStreamer](http://gstreamer.freedesktop.org/).

That sums up the week! Example code for my new Processing functions can be found [here](https://github.com/nconfrey/GSoC/tree/master/coreExamples), the sending and receiving classes are [here](https://github.com/nconfrey/GSoC/blob/master/videoStreaming/videoStreaming/src/processing/streaming/VideoBroadcaster.java). Drop a comment if the UDP streaming either worked really well for you or broke--either way, it's useful information!