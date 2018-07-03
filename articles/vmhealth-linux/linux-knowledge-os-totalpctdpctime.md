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
ms.date: 07/02/2018
ms.author: magoedte
---

# Total Percent DPC Time

## Summary

The total percentage of DPC time (for all processors) is high. System performance may be adversely affected.

Total DPC time is the time that all processors spent receiving and servicing deferred procedure calls (DPCs). DPCs are interrupts that run at a lower priority than standard interrupts. % DPC Time is a component of % Privileged Time because DPCs are executed in privileged mode. If a high % DPC Time is sustained, there may be a processor bottleneck or an application or hardware related issue that can significantly diminish overall system performance.

## Causes

A high DPC time condition can be caused by one or more of the following:

- Processor bottleneck
- Software-related problem<
- Hardware or device driver related problem<

## Resolutions

To determine the root cause of a high DPC time condition, follow the process outlined below. Observe the proportion of the processor time that is spent servicing interrupts and DPCs. To do this, monitor the following metrics:

= Processor\% Processor Time (_Total)
- Processor\% Interrupt Time (_Total)
- Processor\% DPC Time (_Total)

Compare the values of the % Interrupt Time (_Total) and % DPC Time (_Total) metrics to % Processor Time (_Total).

If the sustained % Processor Time (_Total) is > 85% and the % Interrupt Time (_Total) or % DPC Time (_Total) is > 15%, the processors are probably the source of a performance bottleneck. This bottleneck can be addressed by upgrading or adding processors to the virtual machine.

If the sustained % Processor Time (_Total) is < 85% and the % Interrupt Time (_Total) or Total % DPC Time (_Total) is > 15%, the performance issue may be the result of either an application or hardware related issue.
