---
title: Processor Percent Interrupt Time | Microsoft Docs
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

# Processor Percent Interrupt Time

## Summary

The percentage of interrupt time (for a single processor) is high. System performance may be adversely affected.

Processor interrupt time is the time that a single processor spent receiving and servicing hardware interrupts. This value is an indirect indicator of the activity of devices that generate interrupts, such as the clock, the mouse, storage controllers, data communication lines, network interfaces and other peripheral devices. These devices normally interrupt the processor when they have completed a task or require attention. Normal thread execution is suspended during interrupts.

## Configuration

The following table provides the default configuration for the monitor.

|Parameter |Threshold |
|----------|----------|
|Threshold |10 |
|Interval |300 |
|Number of Samples |3 |

## Causes

A high interrupt time condition most often indicates that there is a problem with a hardware device.

## Resolutions

System log files should be checked to identify device errors.