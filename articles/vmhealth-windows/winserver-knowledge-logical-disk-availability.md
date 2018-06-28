---
title: Logical Disk Availability Health | Microsoft Docs
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

# Logical Disk Availability Health

## Summary

NTFS has reported that the logical disk is either corrupted or completely unavailable. Some data stored on the volume may be inaccessible.

## Causes

A logical disk may become corrupted or inaccessible due to a number of reasons some of which include:<

- A disk related to the logical disk has been removed or failed
- A disk related to the logical disk has become corrupt (for example; bad sectors) or inoperable
- The disk driver may have encountered an issue

## Resolutions

Check the status of your host for any failures. In most cases, the system log contains additional events from the lower-level storage drivers that indicate the cause of the failure.

After you have isolated and resolved the host problem:

1. Open the Disk Management snap-in.
2. Rescan the disks and then reactivate any disks with errors.
3. Run chkdsk on any reactivated volumes.