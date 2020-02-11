---
layout: post
title:  "ffmpeg Concatination"
date:   2015-09-21 10:00:00 -0600
categories: [Software]
tags: [concatination, ffmpg, h264, mp4, video]
---

I needed to join a bunch of video files together. They had all the same dimensions (720p), same video codec (h264), and the same audio codec (AAC), so I didn’t want to reencode the files. Ffmpeg can do it. It took me a bit to find the right syntax as I’m on Windows, but I found it.

`ffmpeg.exe -i list.txt -c copy output.mp4`

Here’s an example of the list.txt (because it’s not just a list of the files):

```
file ‘file1.mp4’
file ‘file2.mp4’
file ‘file3.mp4’
```

Here is the documentation of it. I also used this stackoverflow thread. Ultimately, I had to use the file method because I couldn’t list the files in the command line and get it to work. (i.e. `ffmpeg -i ‘concat:file1.mp4|file2.mp4’ -c copy output`)
