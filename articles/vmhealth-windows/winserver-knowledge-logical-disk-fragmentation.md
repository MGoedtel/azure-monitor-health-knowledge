---
title: Logical Disk Fragmentation Analysis | Microsoft Docs
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

# Logical disk fragmentation analysis
		
## Summary

This health criteria runs on a periodic basis to check the fragmentation levels of all logical disks.  If fragmentation levels are found to be above threshold then by default the state of the health criteria will change to **Warning**. 

## Causes

When new files are created or data is added to existing files, the file system attempts to allocate space as continuously as it can so that read operations can perform as fast as possible.  Over time, allocating space in continuous sections becomes less and less likely and the result is that files are fragmented across the disk(s).  The more fragmented the files on a disk become, the longer it will take the file system to work with those files, which can slow the overall system.

## Resolutions

>[!NOTE]
>Defragmenting a disk can be a resource intensive operation and may slow down system performance while it is being performed.  It may be preferable to defragment disks during off hours.
				
If the fragmentation threshold for the drive is appropriate then the issue can be resolved by defragmenting the disk.