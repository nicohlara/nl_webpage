+++
date = '2025-02-19T12:22:42-05:00'
draft = false
title = 'Setting up my website'
+++

## The why

A number of years ago I took a professional development course as part of my training fellowship ([Genetics and Genomics Scholars](https://ggscholars.org/)) and was recommended to set up a personal website. Intrigued, I looked into the matter, and promptly shelved it as less important at my current stage as a first-year Ph.D. student than getting data and learning how to do analyses. 

Last year, I took another professional development class as part of the [Wheat Coordinated Agricultural Project](https://triticeaecap.ucdavis.edu/) and, again, they recommended that we set up personal websites. Now I am an Nth year Ph.D. candidate and am beginning to look for jobs, so I finally took the advice.

I am a tinkerer (and perhaps a bit of a luddite) at heart, and love a good project, so after looking into the usual commercial recommendations (wix, squarespace, etc.) I decided that the perfect thing to do while writing my thesis was to create my own webpage using HTML and self-host it on the 2008 Dell desktop I bought out of a storage unit for $70 to fix a car that is now set up as an occasionally-used home server.

Did I mention that my partner and I just had a baby?

After a 2 AM feeding my practical side put his foot down and told me that I couldn't build a website from scratch while writing a dissertation and raising a newborn, so I looked around for a compromise solution--5 minutes on a selfhosting forum on [lemmy](https://lemmy.world/c/selfhosted) (a free and open-source discussion forum compatible with the ActivityPub protocol) told me that if I was willing to have a static webpage (I am) then [Hugo](https://gohugo.io) would do most of the backend structure and legwork for me to produce a static HTML webpage that I could host on my GitHub page for free, and even point a custom domain to--perfect!

## The How

After that preamble, I am documenting the actual how--mostly as an exercise in writing to help me get into the flow of things for my thesis, but also so that in six months when I forget what I did to make my resume I can refer to something.

1. Installing Hugo and setting up the website

First of all I had to install the application. I run Fedora on my personal laptop, so I first grabbed the version from dnf--which is outdated and can't install the themes to complete the tutorial. No problem, I said--I recently learned how to build from source, so I decided to try that. Half a frustrating hour later, I had installed Go, installed Hugo, and discovered that I could run Hugo only by calling the complete /path/through/the/system/to/go/bin/hugo. Not ideal! I decided to call it a night, and had a lucky breakthrough while brushing my teeth--hadn't I heard of something called aliasing in bash that could help?

The next time I worked on the project I tried
```alias hugo="/path/to/go/bin/hugo"```
and voila! hugo works as it should.

I followed the rest of [Hugo's tutorial](https://gohugo.io/getting-started/quick-start/), then perused the available themes. After quickly becoming overwhelmed, I chose the first that jumped out at me ([paperesque](https://themes.gohugo.io/themes/paperesque/)), then followed that theme's tutorial (side note, though Fedora seems to include git subtree, I couldn't access it. The easiest way to fix the path I found was simply installing it again). I also found downstream that I had to edit the base templates (found at theme/paperesque/layouts/_default/baseof.html when an update invariably breaks this) for the paperesque theme to allow block rendering, which was not included by default. This was simply adding the line ``` {{ block "main" . }}{{ end }}``` to the body class statement.

I now had a functional but unpopulated website; now to fill it!

2. Content

After reviewing my notes from my professional development sessions and looking at a couple of online guides, I decided on a few things to prioritize:

- An about page

- An online resume for quick reference, to be added as a QR code to a business card

- When presenting, a page with my poster/presentation for others to reference afterwards

- A blog, partly as a creative writing exercise and for practice before writing journal articles or my dissertation, and partly to showcase some of the work I do that would not otherwise make it into my resume.

3. Populating

Of the above four items, the about page and a blog are built into the paperesque theme. It seems easy enough to upload an HTML or image of a poster, so I will cross that bridge when I next make it to a conference, so that leaves me with a resume page. I easily set up a markdown document with a list of items and accomplishments, but it wasn't as polished or clean looking as my real resume (crafted in google sheets of all things, because it let me play with margins and formatting best). After googling briefly, I came across an [intriguing post](https://aldra.co/blog/hugo_structured_data/) detailing how to make a database populated resume that I decided to implement.

 
