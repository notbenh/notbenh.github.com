---
layout: post
title: "RANT: FUCK YOU OCTOPRESS"
date: 2012-03-15 18:46
comments: false
categories: rant
---

WTF: Why do developers of software hate there users so much that they activly decide to make the simple and expected things hard when they should be easy! For example user.github.com gh-pages expect to deploy to master, and I'm sure that just about every other self hosted thing will expect that master is the production branch... So it seems that Octopress, the blogging package for "Hackers" would follow suit? ~GASP~ they don't, they have this sources branch, THAT THEY DON'T CREATE FOR YOU, that you have to read thru the Rakefile to even figure out WTF is going on?!?

So thanks to [@jhelwig](https://twitter.com/#!/jhelwig) that got sorted by renaming master to source and then the rake magic seems to build master under the hood. I don't even understand why this was a good idea, other then master now only has the generated code and not everything else. If the point was to "hide passwords" then you can simply just add the config files to the ignore file. Unless I'm completely miss the obvious it seems like we are inventing a new workflow just for the fun of it.

With the core of things up and apparently running... we now get to creat a post: 

    > rake new\_post["silly name for a post"] 
    Creating new post: source/_posts/2012-03-15-silly-name-for-post.markdown

~sigh~ really last time I checked most unix tools only complain on error, so building a script that's telling me that it's going to think about something is completely pointless. Further more what my expectation was is that I wanted to create a new post, with your blog softwarez, as in I want to type... thus why are you now expecting me to COPY that file name and then tell vim (currently set as $EDITOR bu the way) to fucking edit that file. I'm guessing that it would be all of what 1 possibly 2 lines to make that a system call in the rake file. So again why not make this simple for the user? Oh that's right this is a tool kit for hackers so we expect that all the users of this toolkit have the ablilty to solve this problem for us so we don't need to care about them. =(

Problems are designed for fixing, so lets first take care of that **HORRABLE** fuck rake and it's silly pass me prams like nothing else. As a perl dev let's make this simple by making a '[new](https://github.com/notbenh/notbenh.github.com/blob/source/new)' script. Now all I have to say is : 

    > new post another silly post
    Creating new post: source/_posts/2012-03-15-another-silly-post.markdown

That's progress, so now can we tell rake to just do what I wanted and not tell me that it was able to create a file, OH LOOK, the rake file says that it wrote the file before it writes the file... FAIL. Lets [fix that up](https://github.com/notbenh/octopress/commit/61701815ed97d2509264f4d00b9d2536d4d70cde)... so that's done. Now lets have the Rakefile actually DO something usefull for me by having it kick start this file with my [$EDITOR](https://github.com/notbenh/octopress/commit/c5c1e3ff88451efafd7d37a35e97206935aeccb2).

There... now I have a system that's WAY more user freindly... and it only took what an hour... and I'm not a ruby dev. Thanks again to [@jhelwig](https://twitter.com/#!/jhelwig) for talking me off the ledge and letting me know that most of this could be worse.

-- notbenh~

