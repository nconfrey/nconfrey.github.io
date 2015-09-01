---
layout: post
category : GSoC
tagline: "Audio Streaming over GStreamer UDP"
tags : [GSoC, Processing, networking, project]
---

Onto the progress report: This past week I was able to get [Audio streaming](https://github.com/nconfrey/GSoC/blob/master/videoStreaming/videoStreaming/src/processing/streaming/Streaming.java#L258) to work over UDP using GStreamer 1.0! Thanks to Andres Colubri and a sample library he wrote in C/JNI, I was able to link Processing with GStreamer 1.0 using JNI, opening up many new possibilities for Processing and my own video library. We now have access to the `gst_parse_launch()` function in GStreamer, which takes a pipeline string and parses it out into a functioning pipeline. Advanced users of Processing will now be able to take advantage of everything in the latest version of GStreamer.

I've then used this functionality to finally be able to build audio streaming from one Processing sketch to another. The nice thing about finally being built in to GStreamer is the wealth of options for decoding different kinds of files. I can use a `decodebin` to work with many different kinds of audio files before sending them out over UDP. 

I'm very excited but there are a couple things that need to get tightened up still. First, I need to thread the pipeline implementation so the sketch can do other things at the same time as sending audio. Second, and perhaps most importantly, I need to work on portability and testing. Given how much of a nightmare developing on Windows was, I hope using what I have now won't be too difficult to make a version that also runs on Windows. Lastly, there is documentation. I've already written very simple tutorial example sketches that just send a song back and forth, but I'd like to develop a more sophisticated demo.

And, of course, there is also video streaming. The tricky part about video is that GStreamer uses its own window sinks, meaning that it will open a new window to display the video, rather than being contained in the Processing sketch window. Andres and Gottfried, another GSoC student, have already been trying to tackle this problem by using an appsink and appsrc pipeline elements to remove data from the pipeline. As soon as I further tighten up my audio streaming, I'm going to jump in with them and see if we can get videos to be displayed in the Processing window.

Seems like my project is finally hitting its stride! I do hope that I will be able to continue working until I iron out the last details and create something that will really help the Processing community!