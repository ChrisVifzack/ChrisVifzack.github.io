---
title: Simple Racer with AI in Unreal Engine 5
author: chris
date: 2023-07-23 00:34:00 +0100
categories: [Game, Personal]
tags: [game, unreal engine]
pin: false
image:
  path: /assets/img/posts/simple_racer.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: A simple racing game with AI created in Unreal Engine 5.
---

Source code is available on [GitHub](https://github.com/ChrisVifzack/unreal-simple-racer/).

A simple racing game that shows how I typically structure my work in Unreal Engine. It serves well as a reference on how to use Unreal's game framework (Game Instance, Game Modes, Data Assets, Save Game, etc.), create a Map Selection menu with widgets, and how to setup an AI Controller with Behavior Trees.

The project includes the following features:
- Highscores are saved and loaded automatically and shown on the map selection screen.
- Vehicle Movement:
  - Vehicle can not only drive, but also jump and dash.
  - I want to handle those skills via the [Gameplay Ability System (GAS)](https://docs.unrealengine.com/latest/en-US/gameplay-ability-system-for-unreal-engine/) - but had no time to add it yet.
- Checkpoint Racing:
  - A game race game mode where the player has to complete a lap with checkpoints.
  - Once a full lap is completed the time will be saved and stored on the game instance.
- AI with PID control for dynamic spline following:
  - AI functionality is encapsuled in the RacingAI plugin.
  - Two PID controllers are used to control steering and speed respectively. (PID control works by injecting inputs to minimize the error between actual and desired state. This enables the AI to follow the spline.)
  - Once splines are placed on the map, the Spline Selection Service will find them and give them to vehicles to follow.


<br>

Video of three AI-controlled vehicles:

<video src="https://github.com/ChrisVifzack/unreal-simple-racer/assets/12095036/b96a069a-0654-4027-af20-88d97ad3b66c" type="video/mp4" width="100%" controls >
</video>
