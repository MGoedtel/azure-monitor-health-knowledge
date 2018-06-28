---
title: Disk Percent Idle Time | Microsoft Docs
description: This article provides knowledge to understand the issue reported, what are the possible causes, and how to resolve the health issue identified by Azure Monitor VM Health.
services: monitoring-and-diagnostics
documentationcenter: ''
author: MGoedtel
manager: carmonm
editor: 

ms.assetid: 
ms.service: monitoring-and-diagnostics
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 06/14/2018
ms.author: magoedte
---

# Disk Percent Idle Time

## Summary
The disk has a lot of activity occurring on it and as a result the percentage of the idle time has fallen below the threshold value for multiple consecutive samples.

## Causes

Either the disk has recently experienced a significant increase in activity, and this spike has resulted in exceeding the threshold, or disk utilization has been steadily increasing over time and has finally reached a point of going over the threshold.

The other possibility is that some portion of the underlying disks or the disk subsystem is malfunctioning or misconfigured, impairing the performance of the disk.

## Resolutions

To further investigate the issue consider the following:

- Review the System event log on the system, to see if there are any error indicating problems with the disk, disks or the storage subsystem. 
- Review the history of current queue length for this disk using either a monitoring metric chart in Azure Monitor or a Log Analytics log search. This will help in determining if the issue has started recently or if the activity has been steadily increasing over a longer period of time. 
- Review the other performance counters for the disk such as Disk Read Time, Disk Write Time, Disk Reads/sec and Disk Writes/sec to understand what types of I/O are driving the overall disk utilization. 
- Review the Process\performance counters such as IO Data Operations/sec to identify which processes are contributing most significantly to the overall I/O on the system.  Once the top processes are identified the IO Read Operations/sec and IO Write Operations/sec counters will help in further in determining the type of I/O that the process is doing. 

Based on the findings from further investigation, resolutions may vary and could include one of the following:

- Address any issues with the storage subsystem. 
- Scale back the rate of I/O occurring on the system or distribute the workload across more disks. 
- Upgrade the drives or storage subsystem to handle the increased load.
- If the increased load is acceptable then the threshold of the monitor can be changed to be less restrictive.  Likewise the number of consecutive samples can be increased to force the monitor to only change state when utilization is sustained over longer periods of time.