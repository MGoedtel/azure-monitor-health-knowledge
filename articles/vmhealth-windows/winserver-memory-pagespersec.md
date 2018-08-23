---
title: Memory Pages Per Second | Microsoft Docs
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
ms.date: 08/22/2018
ms.author: magoedte
---

# Memory pages per second

## Summary

The rate at which the system is paging memory to and/or from disk is too high. This monitoring is based on the Memory\Pages/sec counter, which is a primary indicator of the kinds of faults that cause system-wide delays. Overall system performance may significantly diminish.

Pages/sec is the rate at which pages are read from or written to disk to resolve hard page faults.

## Causes

One or more applications are using memory heavily, and the system is having to page data to and from disk to meet the demand.

## Resolutions

To identify which processes are driving up the overall memory utilization on the system and the paging rates, use the following counters from the Process object in Azure Monitor or Performance Monitor:

- Page Faults/sec: Page Faults/sec is the rate at which page faults by the threads executing in this process are occurring.  A page fault occurs when a thread refers to a virtual memory page that is not in its working set in main memory. This may not cause the page to be fetched from disk if it is on the standby list and hence already in main memory, or if it is in use by another process with whom the page is shared.
- Pool Non paged Bytes: Pool Non paged Bytes is the size, in bytes, of the non paged pool, an area of system memory (memory used by the operating system) for objects that cannot be written to disk, but must remain in memory as long as they are allocated.  Memory\Pool Nonpaged Bytes is calculated differently than Process\Pool Nonpaged Bytes, so it might not equal Process\Pool Nonpaged Bytes\_Total.  This counter displays the last observed value only; it is not an average.
- Pool Paged Bytes: Pool Paged Bytes is the size, in bytes, of the paged pool, an area of system memory (memory used by the operating system) for objects that can be written to disk when they are not being used.  Memory\Pool Paged Bytes is calculated differently than Process\Pool Paged Bytes, so it might not equal Process\Pool Paged Bytes\_Total. This counter displays the last observed value only; it is not an average.

Based on the findings from further investigation resolutions will vary and could include one of the following

- Apply updates to the operating system or the applications to ensure that any known memory issues are fixed.
- Scale back the number of applications running on the virtual machine, or the amount of load that the virtual machine is undertaking.
- Add more memory to the virtual machine.