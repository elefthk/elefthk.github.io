---
layout: post
title: Bash Cheat Sheet (higher level) 
---

This is not the type of cheat sheet that contains the basics of shell programming or tables of commands and good practices. For these purposes I recommend [1](http://johnstowers.co.nz/pages/bash-cheat-sheet.html), [2](https://learncodethehardway.org/unix/bash_cheat_sheet.pdf) and [3](https://gist.github.com/LeCoupa/122b12050f5fb267e75f). 
Instead, here I have gathered some more complex commands that I have found useful working in the field of computer vision and machine learning. By making the commands more specific I don't mean to narrow their options but to give a fast insight into what the command can do - for others and as a reminder for me as well. For quick access to their actual manuals follow the respective links.

<font size="2">
<table>
  <col width="67%">
  <col width="33%">
  <tr>
    <td><code>convert dragon.jpg -resize 50% half_dragon.jpg</code></td>
    <td>  decrease image size by half and <a href="http://www.imagemagick.org/Usage/resize/">more</a></td>
  </tr>
  <tr>
    <td><code>ffmpeg -i video.mp4 audio.mp3</code></td>
    <td>extract audiofile from video, <a href="http://ffmpeg.org/ffmpeg.html">here</a> is the manual</td>
  </tr>
  <tr>
    <td colspan="2">and a one-liner to run this for all mp4s in a folder:<br><code>for file in *.mp4; do ffmpeg -i "$file" "/path/to/folder""${file/.mp4/.mp3}"; done</code></td>
  </tr>
  <tr>
    <td><code>ffmpeg -i video.mp4 audio.mp3</code></td>
    <td>extract audio from video, <a href="http://ffmpeg.org/ffmpeg.html">here</a> is the manual</td>
  </tr>
</table>  
</font>

<!--
<samp>convert dragon.jpg -resize 50% half_dragon.jpg</samp> | decrease image size by half and [more](http://www.imagemagick.org/Usage/resize/)
<samp>ffmpeg -i video.mp4 audio.mp3</samp> | extract audio from video, [here](http://ffmpeg.org/ffmpeg.html) is the manual
-->

continue text



