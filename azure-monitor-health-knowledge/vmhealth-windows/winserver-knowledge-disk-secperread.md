---
title: Disk Average Seconds Per Read | Microsoft Docs
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

# Disk Average Disk Seconds Per Read

## Summary

The Avg. Disk sec/Read (PhysicalDisk\Avg. Disk sec/Read) for the disk has exceeded the threshold. The disk and possibly even overall system performance may significantly diminish which will result in poor operating system and application performance.

The Avg. Disk sec/Read counter measures the average time of data reads on the disk

## Causes

A high Avg. Disk sec/Read performance counter value may occur due to a burst of disk read requests by either an operating system or application.

## Resolutions

To increase the available storage subsystem throughput for the disk, do one or more of the following:

- Upgrade the type of disk or performance tier.
- Switch from Unmanaged to Managed disks.

The Avg. Disk sec/Read counter is useful in gathering throughput data. If the average time is long enough, you can analyze a histogram of the array response to specific loads (queues, request sizes, and so on). If possible, you should observe workloads separately.

You can use throughput metrics to determine:

1. The behavior of a workload running on a given host system.  You can track the workload requirements for disk read requests over time. Characterization of workloads is an important part of performance analysis and capacity planning.
2. The peak and sustainable levels of performance that are provided by a given storage subsystem. A workload can either artificially or naturally be used to push a storage subsystem (in this case, a given disk) to its limits. Determining these limits provides useful configuration information for system designers and administrators.
    
However, without thorough knowledge of the underlying storage subsystem of the disk (for example, knowing whether it is a single spindle or a massive disk array), it can be difficult to provide an optimized one size fits all threshold value.

You must also consider the Avg. Disk sec/Read counter in conjunction with other read request characteristics (for example, request size and randomness/sequentially) and the equivalent counters for read disk requests.

If the Avg. Disk sec/Read counter is tracked over time and if it increases with the intensity of the workloads that are driving the read requests, it is reasonable to suspect that the disk is saturated if throughput does not increase and overall system throughput starts to degrade.

For more information about storage guidance for Azure VMs, see the [About disks storage for Azure Windows VMs](https://docs.microsoft.com/azure/virtual-machines/windows/about-disks-and-vhds).