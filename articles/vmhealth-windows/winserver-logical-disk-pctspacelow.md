---
title: Logical Disk Free Space Percent Low | Microsoft Docs
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


# Logical disk free space percent low

## Summary

Logical Disk Percent Free Space monitoring includes separate thresholds for system and non-system logical disk volumes in order to properly evaluate available free space. 

## Causes

When existing files grow in size and the new files are added, the free space is taken up on a logical disk.  When the amount of free space on the logical disk falls below the threshold, the state for the logical disk will change.

## Resolutions

To increase the amount of available disk space, do one or more of the following:

- Run Disk Cleanup to gain more free space on the disk. 
- Back up and remove files, or delete unnecessary files from the disk. 
- Move files to another disk or to offline storage.
- Purchase additional storage or switch to a larger disk.