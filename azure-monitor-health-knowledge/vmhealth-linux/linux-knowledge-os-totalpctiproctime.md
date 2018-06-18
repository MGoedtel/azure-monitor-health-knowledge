---
title: Total Percent Processor Time | Microsoft Docs
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

# Total Percent Processor Time

## Summary

The total percentage of processor time (for all processors) is high. System performance may be adversely affected.

Total processor time is the time that all processors spent running a non-idle thread. Each processor has an idle thread that consumes cycles when no other threads are ready to run. This metric is the primary indicator of processor activity, and displays the average percentage of busy time observed.

## Configuration

The following table provides the default configuration for the monitor.

|Parameter |Threshold |
|----------|----------|
|Threshold |95 |
|Interval |300 |
|Number of Samples |3 |

## Causes

An unhealthy state indicates that the processor utilization is currently high. This may be caused by an application using excessive processor resources.

## Resolutions<

To address high processor time conditions choose one or more of the following options:

- Identify processes that are running when the processor time is at the highest.
- Stop or kill any unnecessary identified processes.
- Add processors or memory to the virtual machine.
- Move applications to one or more additional virtual machines.