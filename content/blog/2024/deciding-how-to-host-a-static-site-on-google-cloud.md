+++
title="Google Cloud static site hosting options"
date=2024-02-26
last_updated=""
[taxonomies] 
post_type=["log"]
[extra] 
summary="Goal: simple static hosting with some flexibility, automatically updated from Git commits. There are a lot of options, all with different tradeoffs." 
+++

Like a lot of folks recently, I finally decided to setup a personal website/blog. You're reading it now! :) This post covers different options for hosting a static site on Google Cloud and what I decided in the end. Teaser: I picked something that isn't usually considered for static sites and I'm really happy with how it worked out. 

## Why bother hosting your own blog? 

I'll quote Scott Hanselman here:  

> **I would encourage you *all* to blog more. Tweet less.** Blogs are owned by you. They are easily found, easily linked to, and great conversations happen with great blog posts. The river of social media rushes on and those conversations are long forgotten. **A great blog post is forever.**
> 
> ["Your Blog is the Engine of Community"](https://www.hanselman.com/blog/your-blog-is-the-engine-of-community) -- Scott Hanselman

Also, I'm inspired by folks like [Julia Evans](https://jvns.ca/) and [Simon Willison](https://simonwillison.net/) who learn in public and share what they've learned as they go. 

I want to do more learning in public and ... because I know myself... I need make that as easy as possible or I will get distracted troubleshooting shiny tech stuff. 

## Goals / Constraints

Context always matters. Here are some goals and constraints I had in mind while making this decision, so you can see how they map to yours.

- **hosted on Google Cloud** \
  It's the environment I know best. (I work there).
- **text file based authoring, stored in a version control system** \
<<<<<<< Updated upstream
  I'm a software developer and want to use tools I'm familar with.
=======
  I'm a software developer and want to use tools I'm familiar with.
>>>>>>> Stashed changes
- **low administration overhead, hopefully zero maintenance** \
  I've done a lot of infrastructure work so it's really easy to spend time fiddling with stuff instead of writing words. Writing words is hard. The more reliable things are, the less time I'll spend fiddling with software instead of writing words. 
- **easy site updates** \
  It should be as easy as possible to update the site once I'm OK with the writing.
- **static site (mostly)** \
  Static sites are just a set of files, which should help simplify all of the above goals. But... I will likely want to add a few interactive bits someday... so "mostly". 

## Solutions Considered & Tradeoffs

Here are the options I considered and their tradeoffs (for this goal). 

### Google Cloud Storage

[Cloud Storage](https://cloud.google.com/storage/docs/introduction) is my favorite Google Cloud Service. There, I said it. Sorry, other services. You give it a file and a name, it keeps it for you. When you give it the name later, it gives you the file again. That's the contract. It's *very* reliable. [Cloud Storage is designed for 99.999999999% (11 9's) annual durability](https://cloud.google.com/storage/docs/availability-durability). It's fast and affordable. 

<<<<<<< Updated upstream
It's also... a bit fiddly when used for direct web hosting. It can do it, and there are solutions for most things you probably want to do... [but it's fiddly](https://cloud.google.com/storage/docs/static-website). I was also a bit worried about things getting out of sync as I add and remove files over time. `gsutil rsync` would solve that... but I'm still diffing a collection of files for each deployment, I'd love atomic deployments and rollbacks. The big bummer for my use-case is that you can't directly serve HTTPS traffic via a custom domain without paying an time-based (rather than usage based) fee for a load balancer. Drat.
=======
It's also... a bit fiddly when used for direct web hosting. It can do it, and there are solutions for most things you probably want to do... [but it's fiddly](https://cloud.google.com/storage/docs/static-website). I was also a bit worried about things getting out of sync as I add and remove files over time. `gsutil rsync` would solve that... but I'm still diffing a collection of files for each deployment, I'd love atomic deployments and rollbacks. The big bummer for my use-case is that you can't directly serve HTTPS traffic via a custom domain without paying a time-based (rather than usage based) fee for a load balancer. Drat.
>>>>>>> Stashed changes

> If you'd like to try it out, this is a nice tutorial [exploring static sites on Cloud Storage](https://cloud.google.com/storage/docs/hosting-static-website)

### Firebase Hosting

Well, why not [Firebase Hosting](https://firebase.google.com/docs/hosting) then? It's pretty much Cloud Storage underneath with a UX focused on hosting websites. Plus a CDN (content delivery network... local cached copies of the site for people around the world), neat! It handles HTTPS for custom domains, and has lots of options for previewing sites, integrating Cloud Functions, Cloud Run, GitHub integration, it can "...rewrite URLs for client-side routing, set up custom headers, and even serve localized content." and, more. It's awesome. 

As someone new to it, though... it also seemed like... maybe more than I need for a small site. And even though their developer tooling UX is *excellent*... there are still a lot of features to think about. 

> Try it out: [Getting started with Firebase](https://firebase.google.com/docs/hosting/quickstart) tutorial.

### Google Cloud Run

"[Google Cloud Run](https://cloud.google.com/run/docs/overview/what-is-cloud-run) is a managed compute platform that lets you run containers..." ... so... why am I looking at a container hosting platform for my static site? Well... partly because I'm a programmer and I'm just sure I'll want some kind of dynamic content at some point. Yes... even when trying to keep things simple, I can't help myself. 

<<<<<<< Updated upstream
But keeping things to static site hosting... It handles HTTPS certificate generation and termination. Scaling up and (especially important for this blog) down to zero. Containers are designed for ecapsualtion, so I get atomic deployments and rollbacks. You can point Cloud Run at a GitHub repository and it will automatically build and deploy a new version of the site after every push to a branch. Neat. This seemed like a complexity sweetspot for me. 
=======
But keeping things to static site hosting... It handles HTTPS certificate generation and termination. Scaling up and (especially important for this blog) down to zero. Containers are designed for encapsulation, so I get atomic deployments and rollbacks. You can point Cloud Run at a GitHub repository and it will automatically build and deploy a new version of the site after every push to a branch. Neat. This seemed like a complexity sweetspot for me. 
>>>>>>> Stashed changes

> Several [Cloud Run quickstart tutorials](https://cloud.google.com/run/docs/quickstarts)

## Decision

After a bit of research and fiddling, I ended up with a nice pattern for deploying a static site to Cloud Run. The core idea is wrapping the static site data up together with a single file webserver into a docker image. With a couple of small config files checked into the repository, it will build the site HTML/JS/CSS, wrap it and the webserver into a container image and deploy it. On every push to the repository. 

Now that it's all set up, I edit text files and preview locally, then push when I'm ready to publish. Everything after that happens automatically. I've been running it this way for over a year, and haven't had to think about it or troubleshoot anything. I consider that a win! (for this kind of site! :) )

In a future post, I'll walk through the details of setting it up. In the mean time, you can check out the [source here](https://github.com/briandorsey/til.cafe). In particular, the `Dockerfile` and `Caddyfile` are all that's needed to host the output of pretty much any static site generator via Cloud Run. 


