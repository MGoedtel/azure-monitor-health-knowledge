---
title: Logical Disk Average Disk Seconds Per Write | Microsoft Docs
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

# Logical disk average disk seconds per write

## Summary

The Avg. Disk sec/Write (LogicalDisk\Avg. Disk sec/Write) for the logical disk has exceeded the threshold. The performance of applications that rely on this logical disk may be negatively impacted as the disk is taking an unusually long time to service write requests.

The Avg. Disk sec/Write counter indicates how fast data is being written on average for a specific logical disk.

## Causes

A high Avg. Disk sec/Write performance counter value may occur due to a burst of disk write requests by either an operating system or application.

## Resolutions

To view recent history for the Logical Disk\Avg. Disk sec/Write performance counter you can use either a monitoring metric chart in Azure Monitor or a Log Analytics log search if you need to view performance data further back in time for trend analysis.  

To increase the available storage subsystem throughput for this logical disk, do one or more of the following:

- Modify the type of disks or Azure Storage performance tier to handle the increased load.
- Switch from RAID-5 to RAID-0+1.
- Increase the number of disks.

The Avg. Disk sec/Writes counter is useful in gathering throughput data. If the average time is long enough, you can analyze a histogram of the array response to specific loads (queues, request sizes, and so on). If possible, you should observe workloads separately.

You can use throughput metrics to determine:

- The behavior of a workload running on a given host system. You can track the workload requirements for disk write requests over time. Characterization of workloads is an important part of performance analysis and capacity planning.
- The peak and sustainable levels of performance that are provided by a given storage subsystem. A workload can either be used to artificially or naturally push a storage subsystem (in this case, a given logical disk) to its limits. Determining these limits provides useful configuration information for system designers and administrators.

You must also consider the Avg. Disk sec/Writes counter in conjunction with other write request characteristics (for example, request size and randomness/sequentially) and the equivalent counters for write disk requests.

If the Avg. Disk sec/Writes counter is tracked over time and if it increases with the intensity of the workloads that are driving the write requests, it is reasonable to suspect that the logical disk is saturated if throughput does not increase and the user experiences degraded system throughput.

For more information about storage architecture and driver support, see the [Storage - Architecture and Driver Support Web site](http://go.microsoft.com/fwlink/?LinkId=26156). 