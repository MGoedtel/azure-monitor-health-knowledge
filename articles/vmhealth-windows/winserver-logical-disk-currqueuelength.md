---
title: Logical Disk Current Disk Queue Length | Microsoft Docs
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
ms.date: 07/02/2018
ms.author: magoedte
---

# Logical disk current disk queue length

## Summary

The disk has had a consistently high value for the Current Queue Length counter over multiple consecutive samples.  As a result, I/O requests latency will most likely increase on this disk.

Current Disk Queue Length is the number of requests outstanding on the disk at the time the performance data is collected.  This means that the disk is not able to honor I/O requests as fast as they are being made.

## Causes

Either the disk has recently experienced a significant increase in activity, and this spike has resulted in exceeding the threshold, or disk utilization has been steadily increasing over time and has finally reached a point of going over the threshold.

The other possibility is that some portion of the underlying disks or the disk subsystem is malfunctioning or misconfigured, impairing the performance of the disk.

## Resolutions

To further investigate the issue consider the following:

- Review the System event log on the system, to see if there are any error indicating problems with the disk or the storage subsystem.
- Review the history of current queue length for this disk using either a monitoring metric chart in Azure Monitor or a Log Analytics log search.  This will help in determining if the issue has started recently or if the activity has been steadily increasing over a longer period of time.
- Review the other performance counters for the disk such as Disk Bytes/sec, Disk Reads/sec, and Disk Writes/sec to understand what types of I/O are driving the overall disk utilization.
- Review the Process\performance counters such as IO Data Operations/sec to identify which processes are contributing most significantly to the overall I/O on the system.  Once the top processes are identified the IO Read Operations/sec and IO Write Operations/sec counters will help in further in determining the type of I/O that the process is doing.

Based on the findings from further investigation, resolutions may vary and could include one of the following:

- Address any issues or misconfigurations with the storage subsystem.
- Scale back the rate of I/O occurring on the system or distribute the workload across more disks.
- Upgrade the drives or storage subsystem to handle the increased load.
- If the increased load is acceptable then the threshold of the health criteria can be changed to be less restrictive.  Likewise the number of consecutive samples can be increased to force the health criteria to only change state when utilization is sustained over longer periods of time.