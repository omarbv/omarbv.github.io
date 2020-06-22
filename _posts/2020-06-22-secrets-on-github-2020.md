---
title: Secrets on Github, a plage
date: 2020-06-22
author: Omar Benbouazza
tags:
 - software
 - github
 - security
---

## Introduction

Software Engineers are humans. Humans make mistakes, and anything that can go wrong, will eventually go wrong.

There is a known and big issue in Git and SVN platforms where developers push their code, sharing sometimes more than they should. Most of the times this is fully visible by anyone on the internet. The most known is Github, that has a public and an enterprise version.

Security awareness and training is important, but the fact is that this can happen to almost anyone. I have seen cases where developers using the company account makes an error pushing the code using the personal one.

Awareness needs to be complemented with tools, as they are needed in order to prevent commits with secrets or sensitive data, or scanners that flags any suspicious code already pushed.

Using the examples below, an attacker could exploit the information and, in few cases, get access to a service/server. In the best case, a researcher will notify to the company or developer, giving a second chance.

In most of the cases this is not a critical risk unless the attacker can exploit and make use of the credentials. But if the sensitive data also includes IP addresses or hostnames, and these are available from internet... the chaos is approaching.

## Just a browser

Although there are many options and tools to find out sensitive information, for now I am going to do manual checks, as is a simple method and fruitful.

Dorks:
API KEY, API SECRET, API TOKEN…
ROOT PASSWORD, ADMIN PASSWORD…
COMPANYNAME SECRET, COMPANYNAME ROOT…
GCP SECRET, AWS SECRET…
"username password" extension:sql, “private” extension:pgp...

Opening our browser and launching Github.com, we can search as example ["root password"](https://github.com/search?o=desc&q=root+password&s=indexed&type=Code), and sorting by "Recently indexed". By doing this, in case we find something interesting it will be recent, and credentials could be still valid.

Github will return millions of results for code searches. But before focusing on "code", let's take a look at "commits".


<p align="center">
  <img src=" https://i.imgur.com/XGSzu8l.png"/>
</p>
<p align="center">
  <img src=" https://i.imgur.com/aMpoMEw.png"/>
</p>


Frequently, people notice about credentials exposure and try to remove the content by modifying the code. This will never happen unless they remove the file. Any change will be reflected and will show what was removed/added.

<p align="center">
  <img src=" https://i.imgur.com/6F2Ctdp.png"/>
</p>
<p align="center">
  <img src=" https://i.imgur.com/NuE1j1Y.png"/>
</p>
<p align="center">
  <img src=" https://i.imgur.com/4UML7Ca.png"/>
</p>


Same can work with "code" results, but with millions of results the analysis can be pretty hard. A good way is to set a target, for example the company name or service you are searching for.

For example: Amazon Web Services ;)

In this case we can search for "AWS_SECRET_ACCESS_KEY", sorting by "Recently indexed". It won't be very hard to find something "useful" and in many cases getting the endpoint as well.

<p align="center">
  <img src=" https://i.imgur.com/HUqZnGs.png"/>
</p>


## Awareness and tooling

This is not new, and few companies tired of this happening again and again, have been working in a proactive mode. Trying to find out the secrets before the "bad guys", or blocking any commit containing sensitive data. 

It is very important to have awareness sessions with developers and introduce them best practices. Maybe you have heard about [SDLC](https://en.wikipedia.org/wiki/Systems_development_life_cycle). If you are developer, you MUST learn it.

There is no need to reinvent the wheel; tools and scanners have been developed and freely available and should be integrated in your CI/CD.

-	[git-secrets](https://github.com/awslabs/git-secrets), developed by AWS Labs and focused on AWS.

-	[gittyleaks](https://github.com/kootenpv/gittyleaks), a python-based tool to find sensitive strings.

-	[truffle hog](https://github.com/dxa4481/truffleHog), the perfect tool to find secrets on branches and commit history

SAST tools such as Coverity or SonarQube can also identifies sensitive information, and should be mandatory before any code is in PROD.

## Reaction

If the awareness activities and tech solutions didn’t help to avoid publishing secrets, then is time to react quickly. 

First of all, credentials must be blocked and rotated. And in a second step, the repository owner should be contacted to request removing the sensitive content. 

Developer email address is something [easy to get]( https://omarbv.com/github-email-search.html). So does not matter if he/she is a contractor, or the nickname has nothing to do with his/her real username.

If that option does not work, you always can contact Github Support, and request their help to remove the repository.

If the push was done long time ago, maybe you should consider reviewing logs and accesses.


## Conclusion

In a high-speed setting where Software Engineers put the focus in the “delivery” and not in the quality, this kind of fails will rise. There is a need to strike a balance between speed and quality in continuous delivery and understand the risks. 

The security team must support and guide everyone to achieve excellence, as well as providing the tools to find and remove sensitive data.

