---
title: Logical Processor CPU DPC Time Percentage | Microsoft Docs
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

# Logical Processor CPU DPC Time Percentage

## Summary

The % DPC Time (Processor\% DPC Time) for the logical processor has exceeded the threshold. Overall system performance may significantly diminish which will result in poor operating system and application performance.

% DPC Time is the percentage of time that the logical processor spends receiving and servicing deferred procedure calls (DPCs). DPCs are interrupts that are run at a lower priority than standard interrupts. If a high % DPC Time is sustained there may be a logical processor bottleneck or an application or hardware related issue that can significantly diminish overall system performance.

## Causes

A high % DPC Time value can be caused by one or more of the following:

- Logical Processor bottleneck
- Software-related problem
- Hardware or device driver related problem<

## Resolutions

To determine the root cause of a high DPC, rate follow the process outlined below.

Observe the proportion of the processor time that is spent servicing interrupts and DPCs. To do this with Azure Monitor, use a monitoring chart to view the following performance counters (metrics) over time:

- Processor\% Processor Time
- Processor\% Interrupt Time
- Processor\% DPC Time 

Compare the values of the % Interrupt Time and % DPC Time counters to Processor\% Processor Time for each processor instance.

If a logical processor instance is running a sustained % Processor Time that is greater than 85% and it is also spending greater than 15% of that time servicing Interrupts and/or DPCs, the processor is probably the source of a performance bottleneck. This bottleneck can be addressed by upgrading or adding additional processors to the virtual machine.

If the logical processor is running a sustained % Processor Time of less than 85% and it is also spending less than 15% of that time servicing interrupts and/or DPCs, the performance issue may be the result of either an application or hardware related issue.

Where a hardware device is the root cause, an administrator will find that the % DPC Time has probably increased substantially over a short period time. This will often occur when new hardware is installed or drivers have been upgraded. If the administrator can isolate the issue to a hardware/device driver issue, it can be addressed by working with the vendor.

In cases where you are administering a multiprocessor system that does not distribute interrupts symmetrically, you can often improve the distribution of the processor workload by adding network adapters so that there is one adapter for every processor. Generally, you only add adapters when you need to improve the throughput of your system. Network adapters, like any additional hardware, have some intrinsic overhead. However, if one of the processors is nearly always active (that is, if Processor Information: % Processor Time = 100) and more than half of its time is spent servicing DPCs (if Processor Information: % DPC Time > 50), then adding an adapter is likely to improve system performance, as long as the available network bandwidth is not already saturated.

Where an application is the root cause, you will find that DPCs are probably being blocked by an application that has issued a call that is taking a substantial amount of time to complete. During this time DPCs are blocked and will be queued. To determine which application is the root cause, you must run advanced performance, tracing, and diagnostics to pin point the exact application that is responsible for the performance issue.