---
title: Logical Disk Availability | Microsoft Docs
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

# Logical Disk Availability 

## Summary

A logical disk (file system) that was previously online is no longer available.

File system health is determined by inspecting the mount table to identify permanent, mounted file systems. If a mounted file system identified in a previous iteration is not included in the current enumeration, it is considered unhealthy.

## Causes

An unhealthy state indicates that a file system has gone offline. This may be caused by a disk being unmounted.

## Resolutions

Manually mount the file system on the affected host with the `mount` command.