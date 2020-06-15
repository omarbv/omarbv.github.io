---
title: Is Protonmail "proxied" by an Israel company?
date: 2015-11-16 00:00
author: Omar Benbouazza
tags:
 - protonmail
 - israel
 - analysis
---
## Introduction

Last November 11, [Cryptome](http://www.cryptome.org/), a very well-known leak information website, [published an article](https://cryptome.org/2015/11/protonmail-ddos.htm) talking that behind [ProtonMail](https://protonmail.com/) services, there was an Israeli company offering proxy services, after the last DDoS attacks suffered by the swiss company.

Information was collected from TRACEROUTE requests to the ProtonMail domain, and doing some WHOIS requests to the IP addresses obtained in the different hops.

<p align="center">
  <img src="https://i.imgur.com/wicJJL4.jpg"/>
</p>

According to the Cryptome analysis, on hop 7 there was a server with the IP Address 149.6.141.150, could be owned by “Internet Binat”, Israeli company based that might have business with [“Bynet Data Communications“](http://www.bynet.co.il/en/expertise/defense/), the company which built the [Israeli Defense Forces](http://www.israeldefense.co.il/en/content/defense-sector-will-switch-cloud-computing-nevertheless) “cloud” server farm.

## Analysis

Launching a WHOIS request to that IP Address, the information collected shows an addressing that from 1992 is owned by an American company called PSINet, owned at the same time from 2002 by Cogent Communications.

```
NetRange: 149.6.0.0 - 149.6.255.255
CIDR: 149.6.0.0/16
NetName: COGENT-149-6-16
NetHandle: NET-149-6-0-0-1
Parent: NET149 (NET-149-0-0-0-0)
NetType: Direct Assignment
OriginAS: AS174
Organization: PSINet, Inc. (PSI-1)
RegDate: 1992-01-28
Updated: 2014-05-09
Comment: Reassignment information for this block is
Comment: available at rwhois.cogentco.com port 4321
Ref: http://whois.arin.net/rest/net/NET-149-6-0-0-1

OrgName: PSINet, Inc.
OrgId: PSI-1
Address: 2450 N Street NW
City: Washington
StateProv: DC
PostalCode: 20037
Country: US
RegDate: 1992-01-28
Updated: 2015-06-04
Ref: http://whois.arin.net/rest/org/PSI-1
ReferralServer: rwhois://rwhois.cogentco.com:4321
```

Only doing a [web request](http://www.predkosci.pl/ipinfo,149.6.141.150), it is shown that the network where the proxy is installed, in fact belongs to the Israeli company mentioned previously:

```
network:ID:NET4-95068D941E
network:Network-Name:NET4-95068D941E
network:IP-Network:149.6.141.148/30
network:Org-Name:Internet Binat
network:Street-Address:Habarzel 27 Tel Aviv Or Building A 69710 Israel
network:City:tel aviv
network:Country:IL
network:Tech-Contact:ZC108-ARIN
network:Updated:2015-07-08 17:07:25
```

From a Finnish DSL network, the last hops are related to the [CDN Limelight](https://www.limelight.com/). Connecting through  VPN connection from other countries such as Sweden or Netherlands, it is possible to see that IP address, as Cryptome says in the article:

```
traceroute to protonmail.com (185.70.40.182), 64 hops max, 52 byte packets
 1  10.121.1.1 (10.121.1.1)  11.015 ms  12.407 ms  10.739 ms
 2  130.185.155.129 (130.185.155.129)  11.449 ms  11.618 ms  11.995 ms
 3  5.153.233.253 (5.153.233.253)  12.758 ms  12.754 ms  12.795 ms
 4  5.157.4.9 (5.157.4.9)  11.014 ms
    5.157.4.25 (5.157.4.25)  11.060 ms
    5.157.4.9 (5.157.4.9)  11.053 ms
 5  83.231.187.185 (83.231.187.185)  11.770 ms  11.735 ms  12.524 ms
 6  ae-21.r02.amstnl02.nl.bb.gin.ntt.net (129.250.7.12)  38.367 ms  41.002 ms
    ae-6.r02.frnkge03.de.bb.gin.ntt.net (129.250.7.16)  31.677 ms
 7  be3049.agr21.fra03.atlas.cogentco.com (130.117.15.109)  36.083 ms  34.091 ms  32.916 ms
 8  149.6.141.150 (149.6.141.150)  31.783 ms  31.821 ms  31.893 ms
 9  * be2261.ccr41.fra03.atlas.cogentco.com (154.54.37.30)  42.488 ms
    be2262.ccr42.fra03.atlas.cogentco.com (154.54.37.34)  42.098 ms
10  be2184.agr21.fra03.atlas.cogentco.com (130.117.48.69)  43.908 ms
    be2188.agr21.fra03.atlas.cogentco.com (130.117.48.113)  40.907 ms
    be2184.agr21.fra03.atlas.cogentco.com (130.117.48.69)  41.151 ms
11  185.70.40.182 (185.70.40.182)  41.814 ms !Z  43.077 ms !Z  41.678 ms !Z
```
