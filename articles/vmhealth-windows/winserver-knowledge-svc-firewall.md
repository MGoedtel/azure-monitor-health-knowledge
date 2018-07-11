---
title: Windows Firewall Service Health | Microsoft Docs
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

# Windows Firewall service health

## Summary

The Windows Firewall service helps protect your virtual machine by preventing unauthorized users from gaining access to your virtual machine through the Internet or a network.

## Causes

A service can stop for many reasons, including:

- The service encountered an exception that stopped the service.
- The service was improperly configured, which prevented it from starting.
- The service was prevented from starting because the user account assigned to the service could not be authenticated.

##Resolutions

If this service is stopped, the server is unprotected. The service can be restarted using the **Services** snap-in, using the **Net Start** command, or from PowerShell using **Start-Service** cmdlet.