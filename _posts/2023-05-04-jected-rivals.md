---
title: Jected Rivals
author: chris
date: 2023-05-04 00:34:00 +0100
categories: [Game, Professional]
tags: [game, unreal engine, steam]
pin: true
image:
  path: /assets/img/posts/jected_rivals_header.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: Jected Rivals developed by Pow Wow Entertainment.
---

Released [on Steam](https://store.steampowered.com/app/1366850/Jected__Rivals/) in May 2023.

A fast-paced multiplayer game where characters get ejected from vehicles and can use gadgets in the air.
Players compete in a varity of Game Modes (e.g. Stuntrace, Glider Race, Crash Derby).

I worked ~2 years as a full-time gameplay programmer on this game—using [Unreal Engine](https://www.unrealengine.com/) and C++ with [JetBrains' Rider](https://www.jetbrains.com/rider/) as IDE and [Perforce](https://www.perforce.com/products/helix-core) for version control.

As a programmer, I am first and foremost a problem solver. I enjoy diving deep into complex technical problems to find elegant and simple solutions that fit well with existing systems and overall software design. My work principle is to always maintain a clean codebase, refactor if necessary, and keep the project well-structured.

For Jected Rivals, I was primarily responsible for:
- 3C (Character, Controls, Camera):
    - Ejecting the character from the vehicle
    - Character Locomotion + In-Air behavior (animation and physics)
    - Responsive controls in multiplayer (especially when switching from vehicle to character and vice versa)
- Vehicle & Character AI:
    - Behavior trees, blackboard and AI Controller
    - Spline following and spline selection BTService (fitness calculated using weighted sum)
    - Target selection for Crash Derby mode
- Ingame Audio:
    - Character Voice and SFX
    - Commentary System (moderators commenting on current events in the game)

Aside from my programming tasks, I was frequently involved in planning meetings to discuss feature requirements, estimate efforts and align with designers, artists and other team members to ensure that we achieve our goals.

<br>

<iframe src="https://store.steampowered.com/widget/1366850/" frameborder="0" width="646" height="190"></iframe>