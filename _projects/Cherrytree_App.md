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

So what would this app look like? The brief from what the user end should look like was fairly concrete, an inital login, pages to display the discounts offered and a way for members to prove their membership. I had a good idea of how I wanted this to look in my head which was key. This was the perfect place to use new LLMs that can cut down the time it takes to write lengthy scripts. I made sure I new exactly what I wanted and have the logical flow of how everything shuld interact. I installed the claude code plugin and started tentitively. I made sure to provie good context using a claude.md file and built the thing.

I needed actualy partner data so I build a python web scraper as a subproject and made my own backend database which I hosted on AWS EC2. I then got in contact with the website developer team for their APIs and integrated into the live database. 

There were tweaks and bugs along the way but I finally had in working.

## Translating back into the real world

Now I had done the software and learned all this stuff it still wasnt any use to my boss. Like I did before he just thought of an app as something that lives on your phone, so I had to package what I had back up for him. more messy real-world stuff that I have now learned. 

Side loaded it into my phone so I had a physical copy to show him and then used TestFlight and a Google's closed testing to give him acess on his own devices. Ended up with making accounts and getting it up on the apple app store and google play.

## Takeaways

What it means to be able to code in the modern world with AI is all about understanding the structures. The writing and debugging was only a small part of this project. It was working mainly at the interface of a client and the tech that posed the most problems and where I learned the most.