---
layout: post
title: Bash Cheat Sheet
---

<figure><img src="/images/bash-logo-25.png" alt="bash_logo" style="width: 100px;"/></figure>
This is not the type of cheat sheet that contains the basics of shell programming or tables of commands and good practices. For these purposes I recommend [1](http://johnstowers.co.nz/pages/bash-cheat-sheet.html), [2](https://learncodethehardway.org/unix/bash_cheat_sheet.pdf) and [3](https://gist.github.com/LeCoupa/122b12050f5fb267e75f). 
Instead, here I have gathered some more complex commands that I have found useful working in the field of computer vision and machine learning. By making the commands more specific I don't mean to narrow their options but to quickly give an insight into what the command can do. Follow the respective links for access to their actual manuals.

<font size="2">
<style>
table, th, td {
    border: 2px solid grey;
    border-collapse: collapse;
}
th, td {
    padding: 10px;
}
</style>
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
    <td><code>ssh -l username 123.45.67.89 -p 22</code></td>
    <td>and the <a href="https://linux.die.net/man/1/ssh">ssh</a> man page</td>
  </tr>
  <tr>
    <td><code>scp foo.py foo2.txt username@123.45.67.89:'home/username/folder</code></td>
    <td><a href="https://ss64.com/bash/scp.html">scp</a></td>
  </tr>
  <tr>
    <td><code>nano foo.py</code></td>
    <td>simple text editor to use when in a server (for lack of emacs or vim), to save changes do C-x</td>
  </tr>
  <tr>
    <td><code>mount -t cifs -o username=myusername //123.45.67.89/folder/to/mount</code></td>
    <td><a href="https://ss64.com/bash/mount.html">mount</a></td>
  </tr>
  <tr>
    <td><code>du -sh</code></td>
    <td><a href="https://linux.die.net/man/1/du">disk usage</a> s(ummary) h(uman readable)</td>
  </tr>
  <tr>
    <td><code>du -h --max-depth=1 /path/to/folder | sort -hk1</code></td>
    <td>list all folders in /path/to/folder and their sizes in ascending order (<code>-rhk1</code> for descending order)</td>
  </tr>
  <tr>
    <td><code>cut -d: -f1 /etc/passwd</code></td>
    <td>list all local users</td>
  </tr>
  <tr>
    <td><code>lshw -short</code></td>
    <td><a href="http://manpages.ubuntu.com/manpages/xenial/man1/lshw.1.html">get hardware info</a> (CPU, RAM, GPU, Ethernet), to get only CPU info run <code>lscpu</code></td>
  </tr>
  <tr>
    <td><code>dmidecode -t bios</code></td>
    <td>get <a href="https://linux.die.net/man/8/dmidecode">info on bios</a>, works also for system, memory, processor</td>
  </tr>
  <tr>
    <td><code>grep 'ssh' /var/log/auth.log </code></td>
    <td>check ssh log, general authentication log is stored in /var/log/auth.log and older log is in auth.log1</td>
  </tr>
  <tr>
    <td><code>grep " install " /var/log/dpkg.log </code></td>
    <td>print packages recently installed through apt-get, for all intalled packages do <code>gunzip -c `ls -tr /var/log/dpkg.log.*.gz` | grep " install "</code></td>
  </tr>
  <tr>
    <td><code>tr : '\n' <<<$PATH </code></td>
    <td>pretty <a href="https://ss64.com/bash/tr.html">format</a> of $PATH var (separate per line)</td>
  </tr>
  <tr>
    <td><code>find -name "* *" -type f | rename 's/ /_/g' </code></td>
    <td>replace spaces with underscores in file names, for folder names do <code>-type d</code></td>
  </tr>
  <tr>
    <td><code>ps -p$PPID</code></td>
    <td>find out what terminal you are <a href="https://ss64.com/bash/ps.html">running</a> on, default for Ubuntu Desktop is gnome-terminal</td>
  </tr>
  <tr>
    <td><code>PS1="\D{ %F %T} \u@\h \W \$"</code></td>
    <td><a href="https://bneijt.nl/blog/post/add-a-timestamp-to-your-bash-prompt/">add a timestamp to your Bash prompt</a>, PS1 is stored in .bashrc so source it to make it permanent, this PS1 gives the following prompt: <code>2017-07-20 19:50:30 username@host ~ $</code></td>
  </tr>
</table>  
</font>



