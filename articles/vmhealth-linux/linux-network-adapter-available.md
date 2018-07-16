---
title: Network Adapter Health | Microsoft Docs
description: This article provides knowledge to understand the issue reported, what are the possible causes, and how to resolve the health issue identified by Azure Monitor VM Health.
services: monitoring-and-diagnostics
documentationcenter: ''
author: mgoedtel
manager: carmonm
editor: 

ms.assetid: 
ms.service: monitoring-and-diagnostics
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 06/14/2018
ms.author: magoedte
---

# Network adapter health

## Summary

The network adapter has been disconnected from the network and no longer has network connectivity.

Network adapter health is determined by identifying network adapters that are Up or Running (as defined by the device flags: IFF_RUNNING and IFF_UP of the ioctl: SIOCGIFFLAGS). If a network adapter that was identified as Up or Running is no longer Up or Running, it is considered unhealthy.

## Causes

Your virtual machines network adapter lost its connection to the network.

The adapters connection to the network can be lost if you disable the network interface or misconfigure its network configuration. Other possible causes include network issues, firewall issues, or a malfunction of the network interface or its driver.

## Resolutions

Verify the network interface is properly configured and enabled for this virtual machine.

If the network connection is working properly, check the following possible causes and take corrective action:

- The network is down. Attempt to ping or traceroute to the host.
- The firewall on your virtual machine is blocking network broadcast traffic.
- Your virtual machines network adapter or driver is not functioning correctly. Sign on to the system as root and type `ifconfig -a` to view all available network adapters.