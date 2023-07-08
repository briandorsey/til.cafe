+++
title="Playdate development is easy and fun"
date=2023-07-07
[taxonomies] 
post_type=["log"]
[extra] 
summary="Walkthrough my first experiment and think about *why* their developer experience is so good." 
+++

I recently got a quirky little handheld gaming device, called [Playdate](https://play.date). I had a fantastic early experience developing for it. It's gotten me more excited about programming than anything else in years. And... I don't understand exactly why. This is my attempt to think it through.

![alt text][playdate_image]
<br>*A Playdate gaming handheld. So small!*

[playdate_image]: playdate_backyard_rain.jpeg "A Playdate gaming handheld. So small!"

This was one of those supplychain delayed orders, so I'd mostly forgotten about it by the time it arrived. And while I was planning to use it for distraction gaming, I'm somehow finding myself developing software for it! I had no plans to make any games... but somehow the developer experience is *so* good, that I've almost accidentally started, and can't seem to stop now! This post is about the initial dev experience and how great it is. 

The first evening I played with it, I [posted this](https://hachyderm.io/@briandorsey/110625886762741255):
> "Super impressed with the #playdate SDK. I'm a programer, but I've never done game dev. Had an idea for a... well more of a fidget toy than a game. An hour later and it's running on the physical device. Was able to merge two of the examples and find a few additional functions to call from the docs and ... done!?!
>
> The Playdate devs have done *really* nice work. Docs are good, tooling is good, *everything worked*. Stellar first impression!"

## the story

Let's walk through that in more detail. I got the device during a work week, fiddled with a few games and set it aside. A few evenings later, I thought... 

> "They have development tools for it, right? I wonder if I could make a logo spin?"

Not sure why I was thinking about that exactly, but... I decided to try. Opened the [Playdate developer site](https://play.date/dev/) and it looks like they have three options: Lua and C APIs with a local simulator, and an online authoring tool called [Pulp](https://play.date/pulp/). 

I decided to go with Lua, since I've been meaning to learn it to script other software. Downloaded the SDK, installed, and poked around at the examples. Created a folder with a copy of `PlaydateSDK/Examples/Game Template` and that seemed to run. Started reading [the reference docs](https://sdk.play.date/inside-playdate), which are quite clear and to-the-point. 

After getting that first thing running in the simulator, I spent about 45 minutes reading docs, poking at examples and searching the [developer forums](https://devforum.play.date).

I'm recreating this from memory, but I think these are the main sources I used: 

* `PlaydateSDK/Examples/Single File Examples/crank.lua`
* [https://devforum.play.date/t/basic-crank-rotate-sprite/8422](https://devforum.play.date/t/basic-crank-rotate-sprite/8422)

Combine those into one program... and... with that, I had everything I needed. 

> "It's working?!?"

Not what I expected. I'm used to long research side quests and yak-shaving. I got something working on the device in an hour? This is fun. OK, and the crank on the side just feels good. 

I have to admit that I did spend the next two hours fiddling with image dithering (for the 1-bit actually-only-black-and-white screen) and fiddling with crank response timing, adding additional button handlers, etc. 

## thoughts

OK, but... *why* was this so much easier to get started and more fun than I expected? After thinking about it and talking it over with colleages for a few days... I think... it's not magic, the Panic folks have done all the fundamentals really well. 

Things that worked well for me (first time Playdate developer): 

* I could choose between multiple tools which support different levels of abstraction and programming experience. 
* The simualator works well and allows quick iterations. 
* The reference docs are accurate, comprehensive, concise and ... crucially: all in one place. I just scrolled up and down the same page with an occasional search-in-page. 
* Constraints simplify. The device and APIs are very focused. It think it could be possible to... just learn them all. Most dev tools feel like they're growing faster than I can keep up.
* Seeing something you just made on a physical device in your hand just feels good. 
* I'm of an age where 1-bit visuals are super nostalgic, so I'm sure that helps.
* And maybe most of all: fast feedback loops. In Lua at least, pretty much everything I tried just worked or failed right away. Edit, save, view, repeat. Once things are working well enough, it only takes 15-20 seconds to get that build from the simulator to the physical device. 

## your turn

I want everyone to experience this! ... but... today at least, they're backordered for many months. That said, the [local dev tools](https://play.date/dev/#cardSDK) and [Pulp](https://play.date/pulp/) (online authoring tool) are free and work without a device. Consider playing around with them.

If you're at all curious (and can afford to), order one and forget about it until it arrives. Your future self will thank you. 


