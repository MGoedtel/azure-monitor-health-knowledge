---
title: Windows Remote Management (WinRM) Service Health | Microsoft Docs
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

# Windows Remote Management (WinRM) service health

## Summary

Windows Remote Management (WinRM) service implements the WS-Management protocol for remote management. WS-Management is a standard web services protocol used for remote software and hardware management. The WinRM service listens on the network for WS-Management requests and processes them. The WinRM Service needs to be configured with a listener using winrm.cmd command line tool or through Group Policy in order for it to listen over the network. The WinRM service provides access to WMI data and enables event collection. Event collection and subscription to events require that the service is running. WinRM messages use HTTP and HTTPS as transports. The WinRM service does not depend on IIS but is preconfigured to share a port with IIS on the same machine.  The WinRM service reserves the /wsman URL prefix. To prevent conflicts with IIS, administrators should ensure that any websites hosted on IIS do not use the /wsman URL prefix.

## Causes

A service can stop for many reasons, including:

- The service encountered an exception that stopped the service.
- The service was improperly configured, which prevented it from starting.
- The service was prevented from starting because the user account assigned to the service could not be authenticated.

##Resolutions

If this service is stopped, you will not be able to remotely connect to and manage your server. If restarting the service doesn't resolve the issue and the Operating System is unable to boot in Normal Mode, the configuration of the service may need to be updated in Safe Mode. Once in Safe Mode the service should be configured with a startup type of **Automatic** the Log On configuration should be set to **Local System**.