---
title: "First steps in Unreal Engine"
author: chris
date: 2017-06-10 00:34:00 +0100
categories: [Game, Personal]
tags: [game, unreal engine]
image:
  path: /assets/img/posts/first-unreal-game.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: First experiments in Unreal Engine in 2017. Invisible walls can be seen with flashlight.
---

My very first steps in Unreal Engine back in 2017. I already knew Unity at the time, but wanted to learn Unreal. I had a horror puzzle game in mind, however, it never became a fully playable game. Just a fun project to experiment and get my feet wet with Unreal.

I discovered how Blueprints work, made a bunch of Actors with some fun functionality, and played around with materials and particle systems.

Some features that I created:
- Holdable objects could be picked up with either `'Q'` for left hand and `'E'` for right hand.
  - A flashlight that can be turned on and off with `'F'`.
  - A "moo box" item that can be flipped around make a cow sound.
- Flickering lights to create a horror atmosphere.
- Doors that close themselves when the player walks into a room.
- A flashlight that can reveal invisible walls.
  - Invisible wall uses a material with "Translucent" blend mode and SphereMask node linked to the opacity.
  - The flashlight hit location is updating the material parameter on the invisible wall.

![img-first-unreal-2](/assets/img/posts/first-unreal-game-2.png)
_Cheese had to be placed in front of mouse hole and when player looked away it was suddenly gone._
