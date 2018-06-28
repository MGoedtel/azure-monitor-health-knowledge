---
title: Physical Disk Average Disk Read Time | Microsoft Docs
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

# Physical Disk Average Read Time

## Summary

The average time per read (for the disk) is high. System performance may be adversely affected.

The average disk time per read is measured in seconds. A disk that is developing a bottleneck might cause the entire system to slow.

## Default Configuration

The following table provides the default configuration for the monitor.

|Parameter |Threshold |
|----------|----------|
|Threshold |0.05 |
|Interval (seconds) |300 |
|Number of Samples |5 |

## Causes

An unhealthy state indicates that the disk average time per read is currently high.

Circumstances that may cause this condition:

- High processor utilization can cause slowdowns when doing large data transfers.
- The data disk's interface speed can form a bottleneck to overall performance if it is too low for the data disk's maximum sustained transfer rate.
- When available memory is low, the Virtual Memory Manager writes more pages to swap, resulting in increased disk activity.

## Resolutions

- Upgrade to a faster processor or add processors.
- Confirm virtual machine has the highest performing data disk that it can support.
- Add memory.