---
date: '2025-01-07'
draft: true
title: 'WTF, CIM? My notes on the Common Information Model'
---
The Common Information Model is a data model used within the electric utility industry. Learning it is not something I would phrase beginner-friendly, hence I'm documenting my advances here.

This post is an ongoing effort to document the Common Information model. It summarizes my learnings and collects useful links.

## Purpose of the CIM

The Idea is simple: If all the data of the electricity grid and its components comes in the same format, it can be easily integrated into any application. In the image, all Transmission System Operators (TSOs) maintain the data for their part of the grid. Different applications (called studies here) can use this data to do something with it.

![Image of the CIM](/img/posts/202501-cimgoal.jpg)
*Jay Britton: Purpose of the CIM, from [youtube](https://www.youtube.com/watch?v=eIavIhZwsxA).*



## Structure of the CIM
The CIM is a set of of IEC standards. Those are:
* 61970 - for network models
* 61968 - for meters, assets, and work
* 62325 - for markets.

## Useful Links
* [CIM docs from zepben](https://zepben.github.io/evolve/docs/cim/cim100/)
* [CGMES docs from Netbeheer Nederland](https://netbeheer-nederland.github.io/im-cgmes/)