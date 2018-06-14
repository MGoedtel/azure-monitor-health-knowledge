---
title: Logical Disk Free Space Percent Low | Microsoft Docs
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


# Logical Disk Free Space Percent Low

## Summary

The Logical Disk Percent Free Space monitor enables operators to set varying threshold values for system and non-system logical disk volumes. In addition separate threshold values can be set for Warning and Error states.

## Configuration

Monitoring Logical Disk Free Space is highly configurable by enabling operators to set varying threshold values for system and non-system logical disk volumes. In addition separate threshold values can be set for Warning and Error states.

Since logical disk volumes may vary in size from a few gigabytes to many terabytes or more, the Logical Disk Free Space health monitor requires that an Operator indicate the Megabyte based threshold values that must be passed before the Warning and Error thresholds reached.

The default threshold values for the Logical Disk Free Space monitoring routine include:

System Drive Free Space Thresholds (Defaults)

|Parameter |Default Value | 
|----------|--------------| 
|System Drive Error Percent Threshold |5 | 
|System Drive Warning Percent Threshold |10 |  

Non-System Drive Free Space Thresholds (Defaults) 

|Parameter |Default Value | 
|----------|--------------| 
|Non-System Drive Error Percent Threshold |5 | 
|Non-System Drive Warning Percent Threshold |10 | 

## Causes

When existing files grow in size and the new files are added, the free space is taken up on a logical disk.  When the amount of free space on the logical disk falls below the threshold, the state for the logical disk will change.

## Resolutions

To increase the amount of available disk space, do one or more of the following:

- Run Disk Cleanup to gain more free space on the disk. 
- Back up and remove files, or delete unnecessary files from the disk. 
- Move files to another disk or to offline storage.
- Purchase additional storage or switch to a larger disk.