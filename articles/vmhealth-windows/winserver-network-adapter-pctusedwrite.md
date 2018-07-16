---
title: Network Adapter Percent Bandwidth Used Write | Microsoft Docs
description: This article provides knowledge to understand the issue reported, what are the possible causes, and how to resolve the health issue identified by Azure Monitor VM Health.
services: monitoring-and-diagnostics
documentationcenter: ''
author: mgoedtel
manager: carmonm
editor: 

ms.assetid: 
ms.service: monitoring-and-diagnostics
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 06/14/2018
ms.author: magoedte
---

# Network adapter percent bandwidth used write

## Summary

The volume of bytes received per second on the network interface has exceeded the threshold percentage of the interface total bandwidth, over multiple samples.

## Causes

Either the system has recently experienced a significant increase in network activity, and this spike has resulted in exceeding the threshold, or the system network utilization has been steadily increasing over time and has finally reached a point of going over the threshold.

The other possibility is that the network interface is set to automatically renegotiate the current bandwidth, and the bandwidth that was automatically negotiated is lower.

## Resolutions

To further investigate the issue determine the following:

- Is the network interface configured for automatic negotiation?  If so, has the bandwidth changed recently?
- Have the data volumes recently jumped or has the increase been progressively growing over time?  If the collection rule for this counter is enabled, then review the historical data for this counter in views or reports.
- What source(s) are sending data to the system?  Do multiple systems account for the incoming data, or is it coming from relatively few sources?  Use the "IO Read" counter of the "Process" object in performance monitor to identify which processes are receiving large amounts of data.  Also, tools like NETSTAT.EXE and Network Monitor, can help in identifying what systems are connecting and how much data they are sending in. 

Based on the findings from further investigation, resolutions may vary and could include one of the following:

- Reconfigure the network interface and/or the networking device port that it is connected, to ensure that the network bandwidth is maximized.
- Scale back the volume of data that the system is receiving from external sources.
- Upgrade the network interface or the underlying network that the interface is connected to, to allow for the increased traffic.