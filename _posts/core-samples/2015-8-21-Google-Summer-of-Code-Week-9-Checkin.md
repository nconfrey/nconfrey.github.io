---
layout: post
category : GSoC
tagline: "Week 9 Google Summer of Code Summary"
tags : [GSoC, Processing, networking, project]
---

This is my last official status update about Google Summer of Code -- AND I MADE IT! Processing now has a library that can stream video and audio of any different formats to anything that can receive a gstreamer pipeline (like terminals, commandlines, other Processing Sketches). I'm so happy that I was finally able to complete the project I set out for myself. During this past week with help from Andres and another GSoC student Gottfried Haider, I was able to jump the final hurdles in developing my library.

Things I've been able to accomplish this summer (and things that I think will be useful to the Processing community):

* Linking GStreamer 1.0 to Processing. The video library will no longer be stuck using Java bindings developed for GStreamer 0.10. Andres is interested in rolling this project into the next core release version of the processing video library.
* Proven JNI access to C libraries usable in Processing. This method of using JNI to code with C libraries in Java seems easy enough and explainable. I can use my video streaming library as an example of a successful C->JNI->Java->Processing project.
* Video and Audio streaming library. If anyone wants to stream video from one computer to another, Processing is now a viable choice.
* Access to GStreamer pipeline launch utility. Using my library, users can run GStreamer pipeline strings which exposes all the power of GStreamer, from audio analysis to ripping CDs.

I still have things I want to do in the upcoming weeks and will continue work, but in terms of GSoC, I think I was successful!

You can read more specifics on what I've been able to accomplish on the README I plan to attach with my code sample when I submit to Google.