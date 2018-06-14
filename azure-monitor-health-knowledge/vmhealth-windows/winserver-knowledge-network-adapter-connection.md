---
title: Network Adapter Connection Health | Microsoft Docs
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

# Network Adapter Connection Health

## Summary

This monitor generates an alert when Windows detects that the network adapter has been disconnected from the network and no longer has network connectivity.

If the virtual machine has only a single network adapter, this alert arrives only after network connectivity has been reestablished. In this case, you can resolve the alert without taking any additional action.

If the virtual machine has multiple network adapters, the alert may arrive before network connectivity for the effected adapter has been reestablished. However, remote clients and applications may still have difficulty accessing resources on the virtual machine despite the other adapter or adapters. In addition, the local virtual machine may not be able to access some network resources.

## Causes

Your virtual machine's network adapter lost its connection to the network.

You might experience connectivity problems if the adapter is misconfigured, blocked by a Network Security Group (NSG) or User-Defined Route (UDR), firewall or network issues, or a malfunction of the network adapter or its driver.

## Resolutions

Confirm that the network adapter is enabled under Virtual Machine settings.

If the network connection is working properly, check the following possible causes and take corrective action:

- The network is down.
- The firewall on your virtual machine is blocking network broadcast traffic.
- Your virtual machine's network adapter or driver is not functioning correctly.