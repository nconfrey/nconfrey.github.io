---
layout: post
category : GSoC
tagline: "Windows Bugs part 1"
tags : [GSoC, Processing, networking, project]
---

Moving into week 6 now, and after last week I have a new direction to move in.I have decided to move forward on option #1, working on GStreamer now so that it has the largest effect on Processing. I’ve never been one to shy away from a challenge, and the fact that this is definitely the more difficult route is not that much of a downside. Ideally this way I’ll be able to make a more lasting contribution to Processing in a way that I will be proud about my accomplishments this summer.

I have identified three major sections for my project going forward and aim to space them out in the time I have left. First, I need to get GStreamer working in its native C to do what I want, namely use the UDP elements to transfer frames and audio. Second, I need to wrap the functions I’ve used in JNI, Java Native Interface, to be able to call the C functions from Java. Lastly, I need to build the Java into my Processing Library.

Last week I struggled with step 1. What promised to be an easy endeavor was decidedly not. Given that GStreamer was written in C, I thought using the built-in functions would be straightforward. The first hurdle was compiling the tutorial code against the GStreamer libraries. I generally use GCC as my C compiler, but there was no obvious way to include the dependencies and header files the code needed. I spent an afternoon hunting through the GStreamer file hierarchy, and then subsequently having issues with the Windows Installer utility to install the files I needed. I learned a lot more about GCC and including files, directories and library files. Finally, I got the sample tutorial to compile.

However, that tutorial was written for GStreamer .10 (the very version I am trying to transition away from). I thought compiling against version 1.0 would be as simple as switching the library files in my Makefile, but unfortunately ran into problems here as well. After much head scratching and lots of failed attempts, I used a dependency walker to look at the executable I was compiling and found out that GCC has erroneously added a x86 version of the C++ runtime library rather than the x86_64 version which caused my program to die without any errors. I backtracked against my system environment variables and finally fixed the problem, allowing the version 1.0 to compile and run my sample program!

However, even using 1.0 and written in C I can’t send packets over the network. I’m using the launch utility which promised to be the same as the command line interface (which I did get to send packets over the network). After I send this message, I’ll go back to trying to figure out why the pipeline fails without error and doesn’t actually send the UDP packets.

It has definitely been more on-my-feet troubleshooting than actually writing code. I’m heartened by the fact that this is probably really good experience for other real-life developing projects, but I look forward to the next phase of this project where I get to write more code and don’t need to battle so much with Windows or compatibility issues. I have a clear step by step guide of where I’m going now, I just need to push through and keep battling these issues!