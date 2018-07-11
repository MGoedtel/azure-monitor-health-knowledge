---
title: Memory Free System Page Table Entries | Microsoft Docs
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

# Memory free system page table entries

## Summary

A page table is the data structure used by the Windows Virtual Memory Manager (VMM) to store the mapping between virtual addresses and physical addresses in memory. The performance counter Free System Page Table Entries is the number of page table entries not currently used by the virtual machine. 

When a virtual machine starts running low on free page table entries, applications or drivers might have requests for memory denied, or the virtual machine may stop responding to network requests, seeming to disappear from the network.  Attempts to log onto the virtual machine may not be possible, because it may not be able to respond.

## Causes

Generally speaking, the issue is caused by high memory utilization.  The issue may be more common on 32 bit systems or systems using special boot switches to change the default memory management behaviors of the operating system.

## Resolutions<

Possible resolutions include the following:

- Ensure that that the operating system, drivers and the significant applications on the virtual machine have the most recent patches applied.
- Determine if any special boot switches are being used for the operating system in the BOOT.INI, which may impact how the system managed virtual memory.  If so, then ensure they are necessary and implemented in the best possible way. 

For very detailed instructions on how to diagnose issues with free system page table entries depletion refer to the document [Detection, Analysis, and Corrective Actions for Low Page Table Entry Issues](http://go.microsoft.com/fwlink/?LinkId=201347). If the issue continues and the system is 32 bit and/or running on an operating system prior to Windows Server 2016, consider upgrading to Microsoft Windows Server 2016 or greater and/or moving the workload to a 64 bit system.