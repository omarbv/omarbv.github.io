---
title: Norwegian Air, playing with VOD system
date: 2016-09-20 00:00
author: Omar Benbouazza
tags:
 - vulnerability
 - norwegian
 - vod
---

## Overview

This post is excerpted from the talk presented at the **CyberSecurity Meetup Helsinki**, about vulnerabilities and bad implementations in several products.

<p align="center">
  <img src="https://i.imgur.com/QroO2cb.png"/>
</p>

After trying to contact **Norwegian** in multiple times receiving **no response**, and as there is nothing related to aviation safety, it was decided to publish this article. 

## Analisys

On a trip to London, by chance something interesting was discovered and decided to play a bit with the entertainment system, based on a WIFI to which the user terminals, mobile, tablets, laptops are connected…

<p align="center">
  <img src="https://i.imgur.com/5h6juqL.png"/>
</p>

Once the plane takes off, and light off the “belted seat” Norwegian WIFI starts working on the aircraft. Then, the captive portal home page will display flight information and entertainment options.

<p align="center">
  <img src="https://i.imgur.com/aYeJxNK.png"/>
</p>

In the main menu, we can see many options, most of them for free… others like the movies are not free, at the moment 🙂

We have information about the flight:

<p align="center">
  <img src="https://i.imgur.com/3LKMBLE.png"/>
</p>

The map position of the aircraft:

<p align="center">
  <img src="https://i.imgur.com/zEyFYMj.png"/>
</p>

Series… just a chapter of each, not useful for long trips:

<p align="center">
  <img src="https://i.imgur.com/E8e9gK8.png"/>
</p>

And movies… many films, some of them new, and some very very old, but at a price of 5 €:

<p align="center">
  <img src="https://i.imgur.com/Inwdsmm.png"/>
  <img src="https://i.imgur.com/4obbj5x.png"/>
</p>

Startied to look at the source code while watching an episode of a documentary, and a nice URL was found:

<p align="center">
  <img src="https://i.imgur.com/SWobVyx.png"/>
  <img src="https://i.imgur.com/Q7pvw5V.png"/>
  <img src="https://i.imgur.com/HbzTPfI.png"/>
</p>

Game over! In addition to obtain the folder URL, this is wide opened, and it is possible to display the video directly from the file m3u8 and can also browse other content.

But let’s see if we can also access premium content such as movies, for example Tokarev, whose code in the URL is 4149:

<p align="center">
  <img src="https://i.imgur.com/VynYpmY.png"/>
</p>

Bingo! 🙂 We can enjoy with Nicolas Cage for free.

<p align="center">
  <img src="https://i.imgur.com/IlL6XC0.png"/>
  <img src="https://i.imgur.com/wcgGf5v.png"/>
</p>

There is no need to pay for the film:

<p align="center">
  <img src="https://i.imgur.com/TZRtkb8.png"/>
</p>

And so with all movies in the database… also to mention that it would be possible to download the splitted files of the movie, they are stored in the dropf_code_ * folder, but for lack of time and tools the analysis was stopped at that point.

<p align="center">
  <img src="https://i.imgur.com/L9lHpsK.png"/>
  <img src="https://i.imgur.com/h1UsPTs.png"/>
  <img src="https://i.imgur.com/NCicARe.png"/>
</p>
