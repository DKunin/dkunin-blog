---
layout: post
title: "Bookmarker"
date:  2018-10-06 20:39:24 +0300
categories: links
short: "There's nothing more I hate than tight coupling, so I've build a bookmark manager, coupled only to your filesystem, but not at first, first I discoved a chrome plugin..."
---


# Bookmarker

So some time ago I found Like-it-on-git [Chrome plugin](https://github.com/kamranahmedse/like-on-git), which could update a certain git repo, on command, specifically [this](https://github.com/DKunin/today-i-liked) repo.

You just hit a button - and the link you are currently on is added to the end of the list in the repo, adding date in the process. After some time I realized, that I'm coming back to this list more frequently, than to my bookmarks (in Chrome at that time). Huh, I thought, so my github repo is basically my bookmarks, that's nice, I don't have to sync it, I can update it any way I want, I can use any browser..Reading it is a little fuzzy, cause I have to open the repo and scroll all the way to the end, or use search function, but still.

So at first I decided to decouple from Chrome, and build a [command line tool](https://github.com/DKunin/bin/blob/master/like-it-on-git), that does same thing as the extention. Ok, so now I could integrate it into Alfred, or simply use the CLI. But the reading part still was no fun. So I decided to build [another tool](https://github.com/DKunin/bookmark-function) to filter the list in the github repo, and I used [https://webtask.io](https://webtask.io) to host the serverless function. So now I was fully decoupled from Chrome, but there was an external dependency with network and the git itself, there was some local caching using alfred, but still, with slow network I had to deal with very low response from my bookmarker.

Then, some time later - enter [Beaker Browser](https://beakerbrowser.com/), that is dat-first browser, which has awesome [DatArchive API](https://beakerbrowser.com/docs/apis/)...I thought: "Wow, so I can basically put my bookmarks in the same type of file locally, and access it to write, and to read it, so much easier". So I've build:
- Another [cli function](https://github.com/DKunin/bin/blob/master/like-it-on-dat) to just append bookmarks to the list
- Simple [web app](https://github.com/DKunin/bookmarks) to access my bookmarks with DatArchive API, it is available here: [dat://bookmarks.hashbase.io](dat://bookmarks.hashbase.io)
- And the bookmarks themselves are available here: [dat://36f4464956887a6808e884def577c3fb26fe1af499b2c71bbefb42b4a2a631af](dat://36f4464956887a6808e884def577c3fb26fe1af499b2c71bbefb42b4a2a631af)

Ok, so the UI is a little spartan to say the least, but hey - first function over form.

Next step will be - updating the UI is a step one, and then maybe favorites, like the Dashboard on beaker browser, and maybe the ability to add to the list, I'm not sure for now, but the possibilities opening now with Dat protocol and Beaker Browser are simply inspiring!

And ofcourse the most fun part is - you can use it yourself - just follow the instructions in the bookmarks app, create empty archive with list file, provide the link to the app - and there you go. 

p.s. by the way - this blog has a dat hosted broser, simply enter dat://dkun.in instead of https://dkun.in