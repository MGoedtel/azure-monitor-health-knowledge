---
title: TCP/IP NetBIOS Helper Browser Service Health | Microsoft Docs
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

# TCP/IP NetBIOS Helper Browser Service Health

## Summary

The TCPIP NetBIOS Helper Browser service enables support for NetBIOS over TCP/IP (NetBT) service and NetBIOS name resolution. If this service is stopped Windows will be unable reach virtual machines and network devices by name.

## Causes

A service can stop for many reasons, including:

- The service was stopped by an Administrator.
- The service encountered an exception that stopped the service.
- The service was improperly configured, which prevented it from starting.
- The service was prevented from starting because the user account assigned to the service could not be authenticated.

## Resolutions

The service can be restarted using the **Services** snap-in, using the **Net Start** command, or from PowerShell using **Start-Service** cmdlet.