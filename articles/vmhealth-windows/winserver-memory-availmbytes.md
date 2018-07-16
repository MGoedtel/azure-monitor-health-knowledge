---
title: Memory Available Megabytes | Microsoft Docs
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

# Memory available megabytes

## Summary

The Available MBytes (Memory\Available MBytes) for the system has fallen below threshold. Overall system performance may significantly diminish which will result in poor operating system and application performance.

Available MBytes is the amount of memory that is available for use by applications and processes.

The default memory threshold value is 100 MB.

## Causes

The amount of available memory can become low under the following circumstances:

- Too many applications are running simultaneously on the virtual machine.
- An application may be leaking memory over time.

## Resolutions

To address a low memory condition an administrator may chose one or more of the following options:

- Close or stop one or more applications, services, processes.
- Add additional Memory to the virtual machine.
- Move applications to one or more additional servers.

If the system has been adequately provisioned with memory and application load but it continually exceeds the available memory threshold over time, it is possible that an application is leaking memory. To identify an application that is leaking memory, do the following:

- This can be evaluated from either Azure Monitor using a monitoring chart or Performance Monitor to view the following system wide performance counters (metrics) over time:

    - Paging File\% Usage 
	- Paging File\%
    - Memory\Pool Nonpaged Bytes
    - Memory\Pool Paged Bytes

    If any one of these counters continually increase over time, it is possible that an application may be leaking memory. 

    
- If the system appears to be leaking memory, the specific application can be identified by monitoring the following counters for each running process:

    - Process\Page File Bytes 
	- Process\Pool Nonpaged Bytes
    - Process\Pool Paged Bytes 
	- Process\Private Bytes
    - Process\Thread Count

    If you observe a consistent and significant increase in any of these counters, it may be necessary to contact the application vendor for support.

For more information about monitoring memory counters, see the [Microsoft Windows Server performance tuning guidelines](https://docs.microsoft.com/windows-server/administration/performance-tuning/). 