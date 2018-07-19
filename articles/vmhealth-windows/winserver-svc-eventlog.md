---
title: Event Log Service Health | Microsoft Docs
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

# Event Log service health

## Summary

The Event Log service enables event log messages issued by Windows-based programs and components to be viewed in Event Viewer. The service can be stopped through administrative action and is required for the Operating System to function.

## Causes

A service can stop for many reasons, including:

- The service encountered an exception that stopped the service.
- The service was improperly configured, which prevented it from starting.
- The service was prevented from starting because the user account assigned to the service could not be authenticated.

## Resolutions

If this service is stopped, the Operating System should be restarted. If restarting the service doesn't resolve the issue and the Operating System is unable to boot in Normal Mode the configuration of the service may need to be updated in Safe Mode. Once in Safe Mode the service should be configured with a startup type of **Automatic** and the Log On configuration should be set to **Local System**.