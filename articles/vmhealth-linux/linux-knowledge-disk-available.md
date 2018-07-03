---
title: Disk Availability Health | Microsoft Docs
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
ms.date: 07/02/2018
ms.author: magoedte
---

# Disk Availability Health 
		
## Summary

A disk that was previously available is no longer available.

Disk health is determined by inspecting the disks associated with mounted file systems. If a disk that was available in a previous iteration is not included in the current enumeration, it is considered unhealthy.

## Causes

An unhealthy state indicates that a disk has gone offline. A disk may become inaccessible due to a number of reasons some of which include:

- A disk related to the logical disk has been removed or failed
- A disk related to the logical disk has become corrupt (for example; bad sectors) or inoperable
- The disk driver may have encountered an issue.

## Resolutions

Analyze system logs to determine the cause of the failure.