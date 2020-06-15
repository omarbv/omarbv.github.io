---
title: KeyLemon, bypassing face-authentication
date: 2016-06-13 00:00
author: Omar Benbouazza
tags:
 - keylemon
 - tool
 - vulnerability
---
## Information
[KeyLemon](https://www.keylemon.com/app/#app-download), is a well known application from Switzerland, that allows to enter in your session without login or password, with more than 3 million of downloads and also is involved in an [European Commission project](http://europa.eu/rapid/press-release_MEMO-13-924_en.htm) funded by more than 4 million Euros.

> “KeyLemon’s latest face recognition algorithms take full benefit of 3D depth sense cameras by efficiently combining depth, near-infrared and color information. “

<p align="center">
  <img src="https://i.imgur.com/7VeNL5h.png"/>
</p>

## Analysis

I installed the latest version, 2.75 for Mac OS X, and I tried to bypass Keylemon just using a selfie 🙂

<p align="center">
<a href="http://www.youtube.com/watch?feature=player_embedded&v=wPuVUj5mRgI
" target="_blank"><img src="http://img.youtube.com/vi/wPuVUj5mRgI/0.jpg"/></a>
</p>

I noticed how easy it was to skip the session lock, even using group photos, I contacted the company to inform them about it. In the reply, they told me that the payment licence does not allow that attack, due the anti-spoofing implementation since version 2.5 in Windows.

<p align="center">
  <img src="https://i.imgur.com/8O33s8q.png"/>
</p>

I decided to pay the $ 39 and check whether it was true or not … to my surprise, I discovered that what they call anti-spoofing, was merely a blink detector…

<p align="center">
  <img src="https://i.imgur.com/J9ehSZS.png"/>
  <img src="https://i.imgur.com/siXinkB.png"/>

</p>

It is not very difficult to imagine that a video recording or by creating a gif, would be feasible to bypass it again.

<p align="center">
<a href="http://www.youtube.com/watch?feature=player_embedded&v=pCaEJoch6Zc
" target="_blank"><img src="http://img.youtube.com/vi/pCaEJoch6Zc/0.jpg"/></a>
</p>

In addition, the Windows version also allows voice recognition … as if we could record it, right? 🙂

Nowadays  applications as an alternative to passwords should not being used. As I mentioned in my emails to the developers, I believe that the application KeyLemon is misguided in trying to replace a password, when it could be used to increase it, using both systems simultaneously, as 2FA.

- I recommend reading this paper presented at BlackHat 2009: [Your face is NOT your password](https://www.omarbv.com/wp-content/uploads/2016/06/BlackHat-DC-09-Nguyen-Face-not-your-password.pdf)
- After my analysis I found that in 2010, Biometric Solutions analyzed older versions, with similar techniques, [check here](http://www.biometric-solutions.com/software/reviews.php?story=keylemon).

## Affected versions

KeyLemon 2.7.5 for Mac OS X

KeyLemon 3.2.3 for Windows Vista/7/8

(Older versions are also vulnerable.)

## Timeline

2016-05-24: Initial disclosure to vendor

2016-05-24: Vendor responded with “KeyLemon introduced since version 2.5 antispoofing check feature. This feature requires GOLD package.” 

2016-06-06: Vendor was contacted again, regarding the vulnerability in the GOLD version. 

2016-06-07: Vendor responded with “In the current case, you are fully cooperating with the system to spoof it. This is similar as if you give your password. In KeyLemon desktop application we decided of a threshold between security and convenience.“

2016-06-13: Public disclosure

  
## Public Disclosure
https://seclists.org/fulldisclosure/2016/Jun/31
