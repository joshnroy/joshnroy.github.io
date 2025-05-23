---
layout: single
title: "Why old software continues to exist & why software feels old"
slug: why-old-software-continues-to-exist
date: 2025-05-19
categories: blog
tags: [software-engineering, legacy-software, ux, ui, user-experience]
excerpt: "Earlier this week, I was working on understanding the process for filing taxes for both individuals and corporations in order to figure out how to best optimize it."
author_profile: true
---

Earlier this week, I was working on understanding the process for filing taxes for both individuals and corporations in order to figure out how to best optimize it.

It's no secret that most tax software (aside from turbotax) is old — it feels like it is written in visual basic for a windows application circa 2009 and reminded me of my childhood interfaces in Windows XP.

![CCH Access interface shown on a laptop computer](/assets/images/blog/cch-access-interface.png)
*[CCH Access](https://www.wolterskluwer.com/en/solutions/cch-axcess) Interface*

As I was watching accountants navigate (and lament the age of) this software I pondered as to why this software continued at the age it did and why it hasn't been updated.

![Windows XP Start Menu](/assets/images/blog/windows-xp-start-menu.png)
*[Windows XP Start Menu](https://www.neowin.net/news/a-quick-and-personal-look-back-at-the-windows-start-menu/)*

Native windows applications in visual basic are no mystery to me, at a previous job, I had written native windows interfaces for smart cameras, though we had some good reasons:

- We were writing for deployment on internet-disabled PCs running in factories: no web-apps, no servers
- Since assembly lines and shipping centers might be quite old, we couldn't guarantee the hardware, OS, or software running locally: electron may pose installation or compatibility issues
- Legacy code and practices: The company had been around for 30+ years, with many of the same clients — there was no reason to introduce friction into customer relations for the purpose of a new tech stack

However, despite this, we continued to update the UI, UX, and best practices — using design and implementation concepts from modern apps such as single-page paradigms (partial page reloads) and modern interface components (ex: hamburger menus, [material design](https://m3.material.io/)-esque patterns).

Tax software like CCH access is the complete opposite — it requires internet, only has to support computers in the standard distribution of office PCs, and its clients have adopted to new practices in all other software (such as their email web interface). Plus, the existence of turbo-tax and it's hyper-modern interface is proof.

![Modern TurboTax Interface](/assets/images/blog/turbotax-interface.png)
*[Modern TurboTax Interface](https://www.appcues.com/blog/how-turbotax-makes-a-dreadful-user-experience-a-delightful-one)*

As I continued watching, I found a few reasons this software continues to operate the way it does:

- Complexity: Tax Software is not difficult, but it is complex— after seeing the accountant navigate many pages of conditional dropdowns based on filing codes and entered text fields, I realized the tree of possible configurations is *enormous*.
- Unchanging Needs: Tax hasn't changed — for the most part, what you do in tax is enter information to be populated in a (mostly unchanging in the face of time) government form. Sometimes there are helpful form validations to perform, such as address validation, but nothing hugely different
- Feature Completeness: The software does everything it needs to do: especially if your userbase (Certified Public Accountants in this case) adapts to and is trained to your software, there's not much point in updating it

Furthermore, there's no real economic incentive to completely overhaul the software — it would be an expensive undertaking due to the huge complexity, avoid introducing anything fundamentally new, and a reskinned interface can only make so much money.

However, there are incremental changes that build over time. For example, navigating dropdown menus is currently not a challenge, but as future generations get used to searchable or even declarative interfaces, this may pose a challenge and there may be a market need for new UI/UX.

As an example, we can look at Uber — Taxi services were also complex, unchanging, and feature complete. You could call a taxi on the street or schedule one ahead of time, but as technology literacy grew, a market of tech-savvy individuals who wanted phone-ified taxi services also grew. And thus Uber was born. Once the company's reputation was cemented, it even began taking over other completely functional services, such as airport shuttles ([uber shuttle](https://www.uber.com/global/en/r/airports/lga/shuttle/)).

Time will have to tell, but I suspect there will be opportunities for re-doing some of these older software platforms to cater to future users, particularly with regards to User Experience, not just in tax, but beyond.