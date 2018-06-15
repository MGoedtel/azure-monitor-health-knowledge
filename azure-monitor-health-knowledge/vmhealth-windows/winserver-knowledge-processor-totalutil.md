---
title: Total CPU Utilization Percentage | Microsoft Docs
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

# Total CPU Utilization Percentage

## Summary

The CPU Utilization (Processor Information\%Processor Time\_Total and System Queue Length) for the system processor(s) has exceeded the threshold. Once exceeded overall system performance may diminish significantly which will result in poor operating system and application performance.

## Configuration

The Total CPU Utilization monitoring routine is a high configurable solution that enables Operators to set threshold values for both the System\Processor Queue and the Processor\% Processor Time\_Total performance counters. When values for both counters have exceeded the defined thresholds for several consecutive samples a state change will occur for the monitor. The number of consecutive samples that must be sampled above the threshold before changing state is also configurable.

The default threshold values for the Total CPU Utilization monitoring routine monitoring routine include:

|Parameter |Default Value |
|----------|--------------|
|CPU Queue Length Threshold |15 |
|CPU Percentage Threshold |95 | 
|Num Samples |3 |


## Causes

When a virtual machine is under substantial load for a sustained period of time it can be caused by any of the following conditions:

- The resource requirements for the application set installed on the virtual machine exceeds the capabilities of the virtual machines hardware configuration.
- Demand on the virtual machine resources has increased over time and the virtual machine hardware configuration is no longer able to satisfy increasing demand.
- An application that is running on the virtual machine may have entered into an unhealthy state and is now demanding irregular volumes of system resources.

## Resolutions

From Azure Monitor, use a monitoring chart to view the performance counters (metrics) over time.

To resolve this issue an administrator can perform the following tasks:

1. Evaluate the % Processor Utilization counter for each of the processes running on the server. This can be done by using either Azure Monitor, Task Manager, or Performance Monitor. Determine which process(s) are consuming the most resources and monitor them over time to determine whether they appear to be returning to normal performance ranges. If not, addition application specific diagnostics should be performed to determine the most appropriate way to resolve the issue.
2. If it is determined that client load has increased over time and the virtual machine is simply no longer able to satisfy demand, perform additional performance monitoring procedures to determine if basic hardware upgrades can enable the virtual machine to return to optimal performance ranges.
3. If it has been determined that the application has entered into an unhealthy state, possibly due to a product defect, it might be necessary to restart the application. If the issue persists, you might need to contact the application vendor.