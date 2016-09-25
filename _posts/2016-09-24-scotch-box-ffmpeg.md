---
layout: post
title: "ffmpeg in Scotch Box"
categories: linux video
---

["Scotch Box is a preconfigured Vagrant Box with a full array of LAMP Stack features to get you up and running with Vagrant in no time."](https://box.scotch.io/)

But it doesn't come with [ffmpeg](https://ffmpeg.org/).   While working small project taking the sound from one video and "pasting" it onto a video that just shows the presenting monitor,
[stack overflow said](http://stackoverflow.com/questions/12938581/ffmpeg-mux-video-and-audio-from-another-video-mapping-issue)
to do this:

```
ffmpeg -i presentation_monitor_no_sound.mp4 -i room_video_and_audio.mp4 -c copy -map 0:0 -map 1:1 -shortest output.mp4
```

and it worked great!

[![title]({{site.url}}/static_files/ffmpeg_diagram_2016_09_24.png){:class="img-responsive"}](http://stackoverflow.com/questions/12938581/ffmpeg-mux-video-and-audio-from-another-video-mapping-issue)

Scotch Box comes with a lot of great stuff, but no ffmpeg.   Since Scotch Box is running Ubuntu 14.04 LTS (Trusty Tahr).  
It took a few minutes to install ffmpeg.  Here's a note to my future self on google helped me discover how to do it.

1. apt-get install ffmpeg
   1. this failed.
1. cat /etc/issue
   1. this shows that it's Ubuntu 14.04.   This allowed for googling that pointed to:
1. add-apt-repository ppa:mc3man/trusty-media
1. apt-get update
1. echo $?
1. apt-get install ffmpeg
   1. Things worked this time :-)
