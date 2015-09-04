---
layout: post
category : GSoC
tagline: "Week 7 Google Summer of Code Summary"
tags : [GSoC, Processing, networking, project]
---

Finished up with Week 7 and I hope to be making some serious progress.

This week I've been developing on Linux, which was wonderful and has made everything move a lot more smoothly. The first half of the week I learned how to use JNI using some basic programs that just passed strings back and forth. After compiling and working with JNI, I felt confident enough to move forward with the project.

The current plan is to do most of the heavy lifting with C, and work naively with GStreamer. That way it'll be really easy to work with the pipeline elements if I need to change things to get the data into Processing. The java file will just be a wrapper around the C which will just call the method that I've already written in C. Starting this week, I've written both the C and the java wrapper, and the Makefile that compiles them both. However, I'm having troubles running the Java which is supposed to take a string on the command line and pass it to the C to make a pipeline for it. I'm getting `UnsatisfiedLinkError: no gstreamer-1.0 in java.library.path` when I try to run the Java. The goal for this week is to overcome the link error. Then I'll just need to make it into a library for Processing!

I'm looking forward to a good week.