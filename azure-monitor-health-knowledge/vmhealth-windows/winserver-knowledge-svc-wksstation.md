---
title: Workstation Service Health | Microsoft Docs
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

# Workstation Service Health

## Summary
The Workstation service creates and maintains client network connections to remote servers. If this service is stopped access to network resources such as file shares will be unavailable.

## Causes
A service can stop for many reasons, including:

- The service was stopped by an Administrator.
- The service encountered an exception that stopped the service.
- The service was improperly configured, which prevented it from starting.
- The service was prevented from starting because the user account assigned to the service could not be authenticated.

## Resolutions

The service can be restarted using the **Services** snap-in, using the **Net Start** command, or from PowerShell using **Start-Service** cmdlet.