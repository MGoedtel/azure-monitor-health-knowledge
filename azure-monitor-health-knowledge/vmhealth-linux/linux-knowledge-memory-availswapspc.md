---
title: Memory Available Megabytes Swap Space | Microsoft Docs
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

# Memory Available Megabytes Swap Space

## Summary

Available megabytes of swap space is low. System performance may be adversely affected.

The available megabytes of swap space value represents the free swap space, as reported by the operating system.

## Configuration

The following table provides the default configuration for the monitor.

|Parameter |Threshold |
|----------|----------|
|Threshold |2.5 |
|Interval |300 |
|Number of Samples |3 |

## Causes

An unhealthy state indicates that the swap space utilization is currently high. Circumstances that may cause this condition:

- Processes using excessive memory resources.
- Writing to a temp file system.
- Too many applications are running simultaneously on the virtual machine.
- An application may be leaking memory over time.

## Resolutions

Stop or kill one or more applications or processes. To inspect resources used by processes, use the `top` command and enter the interactive command `m` to see memory utilization.

- Add swap space. Using `mkfile`, create a file for local swap area. To create a 1GB swap file, execute: `dd if=/dev/zero of=/swapfile bs=1k count=1048576`. Issue the command to make it a swap file:` mkswap /swapfile`. Issue the command to activate the swap file: `swapon /swapfile`. You can run the `free` command to see all available swap space.

- Add memory to the virtual machine.