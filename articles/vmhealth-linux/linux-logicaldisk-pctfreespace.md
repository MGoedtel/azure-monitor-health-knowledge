---
title: Logical Disk Percent Free Space | Microsoft Docs
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

# Logical disk percent free space

## Summary

The percentage of free space on the logical disk (file system) is low. System performance may be adversely affected, and the ability to add or modify existing files on the file system may be at risk until additional free space is made available.

The file system space reserved for the root user is not included in the calculated free space. File system space usage is calculated with current free and total values, which may not accurately represent true usage for file systems that dynamically allocate space, such as ZFS.

## Causes

When existing files grow in size and the new files are added, the free space is taken up on a file system. When the amount of free space on the file system falls below the threshold, the state for the Logical Disk will change.

## Resolutions

To increase the amount of available disk space, do one or more of the following:

- View disk capacity by performing a Log Search. Determine if any new applications have been recently installed.
- Review any log files for logs that appear to be excessively large. If so, determine if the logs are current or historical logs. Consider creating compressed archives of historical log files.
- Back up and remove files, or delete unnecessary files from the file system. 
- Move files to another file system or to offline storage.
- Add storage capacity.