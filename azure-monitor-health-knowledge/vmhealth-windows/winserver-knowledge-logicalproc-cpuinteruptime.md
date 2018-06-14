---
title: Logical Processor CPU Percentage Interrupt Time | Microsoft Docs
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

# Logical Processor CPU Percentage Interrupt Time

## Summary

The % Interrupt Time (Processor Information\% Interrupt Time) for the logical processor has exceeded the threshold. Overall system performance may significantly diminish which will result in poor operating system and application performance.

% Interrupt Time is the time the logical processor spends receiving and servicing hardware interrupts during sample intervals. This value is an indirect indicator of the activity of devices that generate interrupts, such as the system clock, the mouse, disk drivers, data communication lines, network interface cards and other peripheral devices. These devices normally interrupt the processor when they have completed a task or require attention.

## Causes

A high % Interrupt Time most often indicates that there is a problem with a hardware device.

## Resolutions

The % Interrupt Time counter will not specifically identify the device that is causing a high % Interrupt Time. To identify the device use Kernrate Viewer (KrView.exe) or Process Trace Information events to determine which ISRs are being dispatched most frequently.

Once the device has been identified a ticket should be opened with Azure support to determine a final resolution.