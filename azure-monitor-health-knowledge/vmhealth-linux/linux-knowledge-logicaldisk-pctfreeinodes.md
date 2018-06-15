---
title: Logical Disk Percent Free Inodes | Microsoft Docs
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

# Logical Disk Percent Free Inodes

## Summary

The percentage of free inodes on the logical disk (file system) is low. System performance may be adversely affected, and the ability to add files on the file system may be at risk until additional inodes are made available.

If the file system does not use inodes, the Percent Free Inodes value is returned as 100 percent. File system inode usage is calculated with current free and total values, which may not accurately represent true usage for file systems that dynamically allocate inodes, such as JFS.

## Configuration

The following table provides the default configuration for the monitor.

|Parameter |Threshold |
|----------|----------|
|Default Value |5 |
|Interval |300 |
|Number of Samples |1 |

## Causes

An unhealthy state indicates that the percentage of free inodes is currently low. This is likely caused by an excessive number of files stored on the file system.

## Resolutions

Inodes store metadata about files and directories. If all available inodes for a file system are allocated, new files and directories cannot be created, even if free space is available. To resolve a low percent of free inodes condition, inspect the file system and look for unused files and directories that can be deleted or moved to an alternate file system.