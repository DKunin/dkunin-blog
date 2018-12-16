---
layout: post
title: "Nativifier vs Go webview"
date:  2018-12-14 23:12:42 +0300
categories: links
short: "How I've found a nice way to package web app into super small 'native' app"
---


# Nativifier vs Go webview

I love the web, I am a web developer at heart, that's why the first time I discovered Electron it was like discovering a superpower. What, I can build "native" apps and they are cross platform, and I can use the power of node and have access to the filesystem?! My mind and heart were racing. 
Since that time I build some apps for personal usage for myself, friends and sometimes clients. Lately it became even simpler, since I found [Nativefier](https://github.com/jiahaog/Nativefier). It's a simple app that does most of the magic for you - if you have a webapp ready, or want to package any webapp as a native app - just call a command: 
		
		nativefier web.whatsapp.com

And that's it, you have a new, shiny app, that you can run locally without any browser...well with one browser - Chromonium, which is a legacy that burdens you with 70 to more then 100 megabytes of size. 
It didn't bother me...what's a hundred megs, when you are using 500gb drive.
The revelation and the downside came to me, when my wife asked me to build her a specific timer, which I did, no problem with my good friend Electron... I sent her a link to download the app, and she looked at me like I am a moron... "128 megs for a simple timer...really"... That was quite embarrassing, so I decided to check out alternatives, and what I've found was quite interesting.

Enter [zserge/webview](https://github.com/zserge/webview), a simple golang app, which can be used to build webviews.

Like this:

		package main

		import "github.com/zserge/webview"

		func main() {
			// Open wikipedia in a 800x600 resizable window
			webview.Open("Todoist",
				"https://todoist.com", 800, 600, true)
		}

Then just build the program, run it...and here you go, 4.8 megabytes instead of hundred...That is quite an improvement. 

Still I had to build the app package for osx by hand, which was still worth it. There was one downside - built into an app - for some reason everything was blurry, which was solved by quick search, the solution:

Create Info.plist with attribute:

		    <key>NSHighResolutionCapable</key>
    		<true/>

And this is how you get super small "native" web app.

Here you can find full example of the mentioned Todoist app : [Todoist-go](git@github.com:DKunin/todoist-go.git)