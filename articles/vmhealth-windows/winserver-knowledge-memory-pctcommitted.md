---
title: Memory Percent Committed Memory in Use | Microsoft Docs
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

# Memory Percent Committed Memory in Use

## Summary

The % Committed Bytes in Use (Memory\% Committed Bytes in Use) for the system has exceeded the threshold. Overall system performance may significantly diminish which will result in poor operating system and application performance.

The % Committed Bytes in Use performance counter represents the ratio of Memory\Committed Bytes to the Memory\Commit Limit. Committed Bytes is the amount of committed virtual memory while Commit Limit is the amount of virtual memory that can be committed without having to extend the paging file(s).

When this performance threshold has been exceeded, it often indicates that the page file could not be expanded, or expanded fast enough, to satisfy application memory requirements.

## Causes

The amount of available memory can become low under the following circumstances:

- Too many applications are running simultaneously on the virtual machine.
- An application may be leaking memory over time.

## Resolutions

To confirm whether excessive paging is occurring, add the Avg. Disk sec/Transfer (a physical disk counter) and Pages/sec counter values. If the product of these counters exceeds 0.1, paging is taking more than 10 percent of disk access time. If this occurs over a long period, you probably need more memory. 

Next, check for excessive paging due to running applications. If possible, stop the application with the highest working set value, and see if that dramatically changes the paging rate. If you suspect excessive paging, check the Pages/sec counter in System Monitor. This counter, which is part of the Memory object type, shows the number of pages that had to be read from disk because they were not in memory. (Notice the difference between this counter and Page Faults/sec, which indicates only that data was not immediately available in the specified working set in memory.)

To address a low memory condition an administrator may chose one or more of the following options:

- Close or stop one or more applications, services, processes
- Add additional Memory to the virtual machine
- Move applications to one or more additional virtual machines (applicable to Servers only)

If the system has been adequately provisioned with memory and application load but it continually exceeds the available memory threshold over time itӳ possible that an application is leaking memory. To identify an application that is leaking memory an administrator can do the following:

- This can be evaluated from either Azure Monitor using a monitoring chart or Performance Monitor to view the following system wide performance counters (metrics) over time:  
    - Paging File\% Usage
    - Paging File\%
    - Memory\Pool Nonpaged Bytes
    - Memory\Pool Paged Bytes

    If any one of these counters continually increase over time it is possible that an application may be leaking memory. To view recent history for these metrics you can view them in Azure Monitor or from a log search.

- If the system appears to be leaking memory, the specific application can be identified by monitoring the following counters for each running process:

    - Process\Page File Bytes
    - Process\Pool Nonpaged Bytes
    - Process\Pool Paged Bytes
    - Process\Private Bytes
    - Process\Thread Count

    If a consistent and significant increase in any of these counters is observed it may be necessary to contact the application vendor for support.