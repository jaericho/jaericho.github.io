---
layout: post
title:  "Scripting HandbrakeCLI"
date:   2019-04-09 20:33:36 -0600
categories: [Powershell]
tags: [Handbrake]
---

I wanted to shrink down a bunch of video files, (I wasn’t too concerned with losing quality so re-encoding them is fine with me) and I decided to try scripting it with HandbrakeCLI instead of just powering thru all the files and adding them to the queue in the GUI.

This site has a very good example. However, I used the GUI to build up a profile and then export that to a file. The only thing I had to add was setting the first subtitle stream to be enabled by default. (I don’t know why that setting isn’t preserved in the presets.)

{% highlight posh %}
$src = "path\to\source"
$dest = "path\to\destination"
 
foreach ($ep in (Get-content filelist.txt)) {
    .\HandBrakeCLI.exe --preset-import-file "MyCustomPreset.json" `
                       -Z "MyCustomPreset" `
                       --subtitle-default=1 `
                       -i "$src\$ep" `
                       -o "$dest\$ep"
}
{% endhighlight %}

If you specify a preset file you must also specify the preset name in that file. Because a preset file could contain more than one preset.

It was much easier to do it this way than try to figure out all the CLI switches for filters, x264 settings, audio streams, and all that other stuff. Plus, we all know that command line scrolling text is much sexier than a GUI progress bar.