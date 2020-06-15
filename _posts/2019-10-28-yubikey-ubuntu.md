---
title: Yubikey Neo + Ubuntu 18.04.3 LTS
date: 2019-10-28
author: Omar Benbouazza
tags:
 - yubikey
 - security
 - ubuntu
---

## Installing Yubikey module

1) Open terminal and install the [Yubikey PPA](https://developers.yubico.com/pam-u2f/), this module implements PAM over U2.
```
sudo apt-get install libpam-u2f
```
2) Insert the Yubikey and create the folder to store your Yubikey key
```
mkdir ~/.config/Yubico
pamu2fcfg > ~/.config/Yubico/u2f_keys
```
3) Yubikey Neo will start flashing, touch it! Now you have configured your key in your profile. 

## Require Yubikey for Login

1) Open a new terminal to edit the login configuration
``` 
sudo vim /etc/pam.d/gdm-password
``` 

2) Add the below after the “@include common-auth” line
``` 
auth       required   pam_u2f.so
``` 
3) Save the file, and logout the session. From now you will need to introduce the Yubikey Neo and press it once you fill the password.
