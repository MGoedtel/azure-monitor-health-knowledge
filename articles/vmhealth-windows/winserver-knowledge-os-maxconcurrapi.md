---
title: Max Concurrent API Monitor | Microsoft Docs
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

# Max Concurrent API Monitor

## Summary

Customers can experience a Windows Authentication, Exchange, SharePoint and line of business application outage due to a low default value for MaxConcurrentAPI, which is a ceiling for the maximum NTLM or Kerberos PAC password validations a server can process at a time.

Consider the following scenario:

- You have one or more forests that have multiple domains.
- There are combinations of users and resources (such as applications or proxy servers) in different domains.
- There are lots of NTLM logon requests from remote domain users to a resource server that is running Windows Server.
- In this scenario, the NTLM requests time out. For example, Exchange clients do not authenticate to the Exchange server when this issue occurs. Therefore, users cannot access their mailboxes, and Microsoft Outlook seems to stop responding.

## Causes

This issue occurs because the NTLM API throttling limit is reached.

## Resolutions

- Raise the MaxConcurrentApi registry value on the server or servers which are seeing the issue. To change the MaxConcurrentApi setting, follow these steps:

   1. Click Start, click **Run**, type **regedit**, and then click **OK**.
   2. Locate and then click the following registry subkey: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters`.
   3. From the Edit menu, select **New**, and then click **DWORD Value**.
   4. Type **MaxConcurrentApi**, and then press **Enter**.
   5. From the Edit menu, select **Modify**.
   6. Type the new MaxConcurrentApi setting in decimal, and then click **OK**.
   7. From a command prompt, type the following command, and then press Enter: `net stop netlogon`.
   8. Type the following command, and then press Enter: `net start netlogon`.

- Verify that the network between the server and its domain controllers (or trusted domain controllers if the condition was seen on a domain controller) is not seeing any latency. Network latency can cause or exacerbate the concern.
- For applications and services that are using NTLM, just configure them to use Kerberos authentication instead. The methods to do that will be unique to those applications.
- If Kerberos PAC validation is seen as a symptom, disable Kerberos PAC validation if the service allows this. This should be done on the server that has the Kerberos sourced system event is appearing.

>[!NOTE]
>Kerberos PAC validation cannot be disabled for IIS application pools or for some Exchange-related services. In order to decide what value to set for the MaxConcurrentApi setting in your environment refer to [Knowledge Base Article 2688798](http://social.technet.microsoft.com/wiki/contents/articles/9759.configuring-maxconcurrentapi-for-ntlm-pass-through-authentication.aspx).
>