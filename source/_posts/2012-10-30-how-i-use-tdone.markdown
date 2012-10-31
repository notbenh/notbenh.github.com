---
layout: post
title: "how i use tdone to tdid todos"
date: 2012-10-30 22:02
comments: true
categories: 
---

I've recently gone on yet-another-get-my-life-in-order kick. I tend to get these once a year, I get all excited about making lists and stuff. I spend a bunch of time working out how to build a list. I get all meta, I start to get worked up over tools, I get infatuated. Then after some amount of time I come to the realization that this is way more work then is really needed for such a simple job. I stop trying at all and I still some how get stuff done. 

This time around I got mad and yet again starting building my self a todo list manager as everything I tried seemed like I was right back to my old tricks. I don't want to end up having to manage my management tool. So I though about what was the absolute minimum that I wanted: an ordered list that was simple to edit and visible from anywhere. It had to be so simple that I will still use this in a week... so I built <a href='https://github.com/notbenh/tdone'>tdone</a>. Some 50 lines of slightly wordy perl that wraps around a file. It can add a line, it can remove a line, it can sort the lines and it can display the lines of the file... that's it. This file is expected to be an env var, this way the user can manage it, not the code. 

Because I wrote this for me, there is next to nothing when it comes to syntax: any number of leading +'s are seen as a marker of priority and are used to sort the lines of the file (more first, none last). This is the only "actionable" aspect of the line, everything else is just a trip for the color-coding. I have been leading a word with : to mark it as a tag, and @ as a location. This allows me to say something like : 

  ++ :blog about :tdone @laptop

The : and @ are here only for the visual punch, they are used as markers for coloring, tags are green, locations are bold but that is all they do. 

So this is the foundation, just a file and some simple code. Now here's the magic of the simple-tool mind set. This file sits in a folder that is watched by Dropbox, thus every machine that I sit behind will have access of this list. This includes my phone, so everything is covered for me but you can build this how ever you wanted to. Wanna have some history for your list, set up a simple <a href='https://github.com/guard/guard'>guard</a> script that commits all changes to some git repo and syncs... it's simple. Hooks, notifications, just about anything is possible by hooking things with IFTTT or any of the event services. 

So this is my setup, let's see how long I stick with it. If you think this is something you would find useful, feel free to grab the code and run with it. Want something different fork it and make it your own. Have fun and be productive!
