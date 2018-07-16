---
title: Logical Disk Average Disk Seconds Per Read | Microsoft Docs
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

# Logical disk average disk seconds per read

## Summary

The Avg. Disk sec/Read (LogicalDisk\Avg. Disk sec/Read) for the logical disk has exceeded the threshold. The performance of applications that rely on this logical disk may be negatively impacted as the disk is taking an unusually long time to service read requests.

The Avg. Disk sec/Read counter indicates how fast data is being read on average for a specific logical disk.

## Causes

A high Avg. Disk sec/Read performance counter value may occur due to a burst of disk read requests by either an operating system or application.

## Resolutions

View recent history for the Logical Disk\Avg. Disk sec/Read performance counter.

To increase the available storage subsystem throughput for the logical disk, do one or more of the following:
- Modify the type of disks or Azure Storage performance tier to handle the increased load.
- Increase the number of disks.

The Avg. Disk sec/Read counter is useful in gathering throughput data. If the average time is long enough, you can analyze a history of the array response to specific loads (queues, request sizes, and so on). If possible, you should observe workloads separately.

You can use throughput metrics to determine:
- The behavior of a workload running on a given virtual machine. You can track the workload requirements for disk read requests over time. Characterization of workloads is an important part of performance analysis and capacity planning.
- The peak and sustainable levels of performance that are provided by a given storage subsystem. A workload can either artificially or naturally be used to push a storage subsystem (in this case, a given logical disk) to its limits. Determining these limits provides useful configuration information for system designers and administrators.

However, without thorough knowledge of the underlying storage subsystem of the logical disk (for example, knowing whether it is a single spindle or a massive disk array), it can be difficult to provide an optimized one size fits all threshold value.

You must also consider the Avg. Disk sec/Read counter in conjunction with other read request characteristics (for example, request size and randomness/sequentially) and the equivalent counters for read disk requests.

If the Avg. Disk sec/Read counter is tracked over time and if it increases with the intensity of the workloads that are driving the read requests, it is reasonable to suspect that the logical disk is saturated if throughput does not increase and overall system throughput starts to degrade.

For more information about storage architecture and driver support, see the [Storage - Architecture and Driver Support Web site](http://go.microsoft.com/fwlink/?LinkId=26156)