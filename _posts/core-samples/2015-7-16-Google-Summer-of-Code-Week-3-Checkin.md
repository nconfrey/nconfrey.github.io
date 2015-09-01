---
layout: post
category : GSoC
tagline: "Week 3 Google Summer of Code Summary"
tags : [GSoC, Processing, networking, project]
---

Onto week 3. This week was a slow learning week, so I wasn’t able to write as much code as the previous weeks. That being said, let’s get into it.

Monday and Tuesday were devoted to learning about the Gstreamer framework and understanding how it worked. Wednesday I finally linked in GStreamer into Processing, and then made some [sample pipelines](https://github.com/nconfrey/GSoC/blob/master/videoStreaming%20.10/videoStreaming/src/template/library/VideoBroadcaster.java#L93) that played audio or displayed video. The goal is to use the GStreamer framework to buffer and manage the video and audio streams, and then put a `udpsink` at the end of it that will send off the stream as udp packets. I’m still struggling with integrating the udp sink.

At the end of this week, I’m much more comfortable with GStreamer but not quite where I want to be with written code. I’ll keep at it.