# CherryTree App — Reference Draft v2
# (Direction only — rewrite this in your own words)

---

I've done a lot of talking to people about career options after leaving university. One question comes up a lot: "Can you code?" It's always stumped me. On one hand I'd been exposed to programming — R for statistics, numpy for linear algebra, matplotlib for visualising differential equations. On the other hand I'd never had formal computer science training. No algorithms, no data structures. My answer was usually so convoluted it amounted to a "no."

That changed in Wellington.

I was doing data entry for a retail company called Cherrytree — a membership scheme where members get discounts at partner businesses around New Zealand. The boss, Simon, mentioned almost in passing that their app had broken years ago and never been fixed. His frustration wasn't really with the technology. It was with the people. Developers were expensive, hard to reach, opaque about their work, and the results broke quickly. He didn't need a genius. He needed someone who could sit with him, understand what he actually wanted, and see it through from idea to finished product. I said I'd give it a go.

First call I made was to Vin — my girlfriend's dad, a software engineer. He walked me through what a stack is, how to set up VS Code, how to execute code in the terminal. That afternoon I had a basic web page that pulled data and displayed something on screen. It was the ugliest thing I'd ever seen and it was the most satisfying thing I'd ever built.

The first real problem: there was no API. All the partner data — 101 businesses across Wellington, Auckland, Waikato, and the South Island — lived inside Cherrytree's internal admin portal, locked behind a login. So I built a scraper. Python and Playwright to automate the browser login, BeautifulSoup to pull the data off each page, running five partners at a time. It produced a single JSON file with every partner's name, description, categories, logo, and region. That JSON became the foundation of everything else.

With the data in hand I built a backend: Node.js, Express, SQLite. A simple REST API that served partner listings, handled member login, and stored test accounts so I could simulate real members while the real ones weren't connected yet. I also built a quick web prototype — just a grid of partner cards — to confirm visually that the backend actually worked before building the mobile app. It did. That was the point where it stopped feeling like tinkering.

The mobile app is React Native with Expo, written in JavaScript. Six screens: login, a region selector, a partner list with a live search bar, a partner detail page, a digital membership card, and a contact form. The card was the most satisfying screen to build — it shows the member's name, their tier (Silver, Gold, or Platinum, each with its own colour scheme), their membership number, and a countdown to expiry that turns orange then red as the date approaches. It looks like a credit card. It replaces the physical one.

For the server I chose AWS EC2 over simpler options deliberately. SSH-ing into a real Linux server, setting up PM2 to keep the process running, allocating a static IP — none of that was strictly necessary, but all of it is how it's actually done in the industry and I wanted to know how it worked. When Simon sat down for the first demo and the app loaded partner data live off a server I'd set up, that felt significant.

Getting the app onto a real Android device was its own education. The first build failed on login — the server was unreachable, even though everything worked in the emulator. It took four builds to understand why: Android blocks plain HTTP traffic in production apps, but the dev testing tool bypasses that silently. The fix was a single config flag. Finding out which file it needed to go in — and that the wrong file is silently ignored — took longer.

The biggest shift came when it was time to connect the real data. Cherrytree's web company had an API but the documentation was incomplete. I had to open Chrome DevTools on the live Cherrytree website and watch the network traffic — seeing what calls the website was actually making and working backwards from that. The authentication was PHP session-based. The partner endpoint names weren't documented. The member tier values came back as lowercase strings. None of it was hard once I knew what it was. Finding out what it was required a different kind of thinking — not following instructions, but reading a system that wasn't written for me to read.

Once the live data was integrated I shut down the AWS server. It had served its purpose. The app now calls Cherrytree's API directly. It's heading to the app stores.

---

## Suggested paragraph: "Translating back into the real world"

Getting the software working was one thing. Getting it into my boss's hands was another. Simon thought of an app as something that just lives on a phone — he didn't know what a build was, or why I needed him to accept a TestFlight invite before he could install it. So I sideloaded the APK onto my own Android so I had something physical to put in front of him. Then I walked him through TestFlight on iOS and Google's closed testing track on Android, both of which required creating developer accounts, paying the fees, and navigating review processes I hadn't encountered before. Eventually I submitted to the App Store and Google Play properly. There were rejections — Apple flagged a missing privacy policy, Google wanted a privacy policy URL in the store listing — small things that felt enormous at the time because I didn't know where they'd end. But they ended. Both apps passed review. The first time I searched "Cherrytree" in the App Store and it came up was a strange moment. It looked like a real app because it was one.

---

## Suggested paragraph: Takeaways

What I learned doing this isn't really about React Native or AWS or how to submit to the App Store. It's about what it actually means to build something in the real world. The code was maybe 30% of the work. The rest was figuring out what to build, convincing someone to let me build it, reading systems that weren't documented, and translating between what a non-technical person wanted and what a computer needed. That gap — between a human problem and a technical solution — is where most of the interesting work lives. AI tools made the writing part faster, but they didn't close that gap. Understanding it was still on me. That's the skill I came out of this with, and it's the one that transfers.

---

## Structure notes for Felix's version:

- **Opening** — keep the "can you code?" hook, already written and strong
- **Vin** — name him, say who he is, and say what that first afternoon felt like
- **The scraper** — before there was an API, you built your own data source. That's the cleverest part of the story
- **Backend + web demo** — quick paragraph. The web demo as a sanity check before the real build
- **The mobile app** — describe the screens, especially the membership card
- **AWS** — say plainly it was a deliberate learning choice
- **Android build failure** — four builds, don't skip it
- **Live data integration** — the Chrome DevTools detective work is where it became a real piece of software
- **Closing** — AWS shut down, heading to the stores

## Things only you can write:
- What did Vin actually say to you, and what did it feel like to suddenly understand how it all fits together?
- What did the first afternoon's web page look like?
- What did Simon say at the demo?
- Was there a moment during the Android debugging where you nearly gave up?
- What does it feel like to open the app on your phone now?
