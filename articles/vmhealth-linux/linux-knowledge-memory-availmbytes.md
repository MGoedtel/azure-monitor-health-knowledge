---
title: Memory Available Megabytes | Microsoft Docs
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

# Memory Available Megabytes

## Summary

Available megabytes of memory is low. System performance may be adversely affected.

The available megabytes memory value represents the sum of MemFree, Buffers and Cached as reported by the operating system.

## Causes

The amount of available memory can become low under the following circumstances:

- Too many applications/processes are running simultaneously on the virtual machine.
- An application may be leaking memory over time.

## Resolutions

To address a low memory condition, an administrator may choose one or more of the following options:

- Stop or kill one or more applications or processes. To inspect resources used by processes, use the `top` command and enter the interactive command `m` to see memory utilization.
- Add memory to the virtual machine.
- Move applications to one or more additional servers.