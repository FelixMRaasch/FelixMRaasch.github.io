---
layout: page
title: CherryTree App
description: Building from scratch
img: assets/img/cherrytree_hero.jpg
importance: 1
category: work
# published: false
---

{% include figure.liquid loading="eager" path="assets/img/cherrytree_hero.jpg" class="img-fluid rounded z-depth-1" %}

## The 'Why?'

I've done a lot of talking to people about the next thing to work on after leaving university. One question that comes up a lot in conversation is "Can you code?". It's a question that's always stumped me. I'd been exposed to programming: R for statistics, numpy for linear algebra, matplotlib for visualising differential equations; however, this had always been in a limited academic setting where programming was a tool for exploring mathematics. I'd never actually built anything myself. My answer was usually so convoluted it amounted to a "no."

That changed recently in Wellington. I was doing data entry for a retail company called Cherrytree and the boss mentioned, almost in passing, that their app had broken years ago and never been fixed. For someone looking for a challenging project to work on, the opportunity to build my own piece of software and deploy it in a live commercial setting was tempting. I was still unsure about the jump from writing code for homework assignments to delivering in a professional setting, but I wanted to bridge that gap. I said I'd give it a go.

## Defining the project

The first step was getting myself set-up. Unlike in university where pre-made jupyter notbooks set out easily defined problems, I had little to work from. The source code from the old app was lost. All I had was my laptop and the user-end iOS app (which only worked on my iPad) as a guide to what needed to be rebuilt. I needed to figure out what tools software developers used, what an "app" really was, and what I needed to download on my computer so that I could program one. I jumped onto FaceTime with with Vin, my girlfiend's dad and an experienced software developer. He told me to download VSCode, explained the concepts behind git and terminal commands, and we discussed some of the common app frameworks that people use. After that call I spent the day downloading extensions, initialising a git repository, and picking react native as my app framework. I downloaded Node.js and ran terminal commands to initialise a React Native Web project with Expo. I now had a blank app framework ready for me to mould into the cross-platform Cherrytree membership app I had promised my boss.

## Building the software

<div style="float: right; width: 25%; min-width: 180px; max-width: 260px; margin: 0 0 1rem 1.5rem;">
  {% include figure.liquid loading="lazy" path="assets/img/Phone_screenshot.png" alt="CherryTree app screenshot" class="img-fluid rounded z-depth-1" caption="App screenshot" %}
</div>

So what would this app look like? The brief from what the user end should look like was fairly concrete, an inital login, pages to display the discounts offered and a way for members to prove their membership. I had a good idea of how I wanted this to look in my head which was key. This was the perfect place to use new LLMs that can cut down the time it takes to write lengthy scripts. I made sure I new exactly what I wanted and have the logical flow of how everything shuld interact. I installed the claude code plugin and started tentitively. I learned a lot about working with AI agents to build code, and saw its quirks. Over the next few weeks I built my frontend app piece by piece using claude agents. I found I got better at defining the tasks at hand and learned to resist the urge to rush too far beyond my own understanding as this is where you can get into a frustrating and unproductive loops.

The first real problem: I had no data. All the partner data — 101 businesses across Wellington, Auckland, Waikato, and the South Island — lived inside Cherrytree's internal admin portal, locked behind a login. So I built a scraper. Python and Playwright to automate the browser login, BeautifulSoup to pull the data off each page, running five partners at a time. It was crazy to see my own laptop seemly operating by itself due to scripts I'd written, independently opening chrome tabs and logging in and scraping from the website.

After getting this data, I chose to host my server in the cloud using AWS EC2. I did this instead of a simpler option deliberately, to get experience hosting a backend server how it's actually done in the industry. I then sat down for the first demo and the app loaded partner data live off a server I'd set up, which felt significant.

I had confirmed my frontend app worked. I got in contact with the website developer team for their APIs and integrated into the live database. I finally had it working and live.

## Translating back into the real world

Getting the software working was one thing. Getting it into my boss's hands was another. Just me at the start of this process, he thought of an app as something that just lives on his phone. He didn't know what a build was, or a script, or a .jks file, and why should he care? He just wanted a working product. So I went through the fiddly process of making an Android developer account uploading the APK, adding supporting documents, signing the app, creating a closed test of members... I then went through the same lengthy submission process with Apple. 

There were rejections. Apple flagged a missing privacy policy, Google wanted a URL in the store listing: small things that felt enormous at the time because I didn't know where they'd end. But they ended. Both apps passed review after some tweaks and I finally had something that my boss and any non-techincal person would understand, a link to download the app off the app store.

## Takeaways

What it means to be able to code in the modern world with AI is all about understanding the structures. The writing and debugging was only a small part of this project. It was working mainly at the interface of a client and the tech that posed t

What I learned doing this isn't really about React Native or AWS or how to submit to the App Store. It's about what it actually means to build software in the real world. Writing code and debugging was maybe 30% of the work. The rest was figuring out what to build, convincing someone to let me build it, and translating between what a non-technical person wanted and what a computer needed. That gap, between a human problem and a technical solution, is where most of the work lives. AI tools made the writing part faster, but they didn't close that gap. Understanding the problem, directing those tools effectively and translating the output into solutions that touch the real world is still on you.