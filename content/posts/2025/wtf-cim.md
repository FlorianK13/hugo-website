---
date: '2025-04-04'
draft: false
title: 'WTF, CIM? My notes on the Common Information Model'
---
The Common Information Model is a data model used within the electric utility industry. Learning it is not something I would phrase beginner-friendly, hence I'm documenting my advances here.

This post is an ongoing effort to document the Common Information Model. It summarizes my learnings and collects useful links.

## Purpose of the CIM

The Idea is simple: If all the data of the electricity grid and its components comes in the same format, it can be easily integrated into any application. In the image, all Transmission System Operators (TSOs) maintain the data for their part of the grid. Different applications (called studies here) can use this data to do something with it.

![Image of the CIM](/img/posts/202501-cimgoal.jpg)
*Jay Britton: Purpose of the CIM, from [youtube](https://www.youtube.com/watch?v=eIavIhZwsxA).*



## Structure of the CIM
The CIM is a set of of IEC standards. Those are:
* 61970 - for network models
* 61968 - for meters, assets, and work
* 62325 - for markets.

Often people talk about CGMES instead of CIM. CGMES is a subset of CIM defined by [entso-e](https://www.entsoe.eu/data/cim/cim-for-grid-models-exchange/). So CIM contains CGMES, but CGMES does not contain CIM.

## Useful Links
* [CIM docs from zepben](https://zepben.github.io/evolve/docs/cim/cim100/)
* [CGMES docs from Netbeheer Nederland](https://netbeheer-nederland.github.io/im-cgmes/)
* [CIM Space: A Data Viewer for CIM Data](https://derrickoswald.github.io/CIMSpace)
* [CIM Draw: Another Data Viewer for CIM Data](https://danielepala.github.io/CIMDraw/index.html#)
* The [CIMReader](https://derrickoswald.github.io/CIMSpark/doc/scaladocs/ch/ninecode/model/index.html) is also some sort of documentation of CIM. If you scroll down a bit to the `Filter all members` search field you can search for any class of the CIM and get some info. Very Useful!
* The docs of [powsybl](https://powsybl.readthedocs.io/projects/powsybl-core/en/stable/grid_exchange_formats/cgmes/index.html) also have some useful information on CGMES