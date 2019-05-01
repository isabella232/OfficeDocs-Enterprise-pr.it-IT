---
title: Registro delle transazioni di Office 365 IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Fornisce un esempio e descrive la convenzione di denominazione e il livello di registrazione predefinito del registro delle transazioni IdFix di Office 365.
ms.openlocfilehash: c652f8dcbc23a6f0165d894ce6317443db72ceee
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490942"
---
# <a name="office-365-idfix-transaction-log"></a>Registro delle transazioni di Office 365 IdFix

Fornisce un esempio e descrive la convenzione di denominazione e il livello di registrazione predefinito del registro delle transazioni IdFix di Office 365.
  
## <a name="idfix-transaction-log-location"></a>Posizione del registro delle transazioni IdFix

Lo strumento Office 365 IdFix crea un nuovo log delle transazioni ogni volta che si fa clic su **applica** in IdFix e si applicano modifiche alla foresta di Active Directory. Il registro delle transazioni viene salvato nella stessa cartella in cui è stato installato IdFix. Per impostazione predefinita, questa cartella è C:\Deployment Tools\IDFix. Il nome del file del registro delle transazioni utilizza un formato di data e ora, ad esempio, verbose 6-1-2018 6-17-22 PM indica un file che è stato generato al 1 ° giugno 2018 alle 6:17:22 PM. Dettagli indica il livello di registrazione. 
  
## <a name="idfix-transaction-log-logging-level"></a>Il livello di registrazione del registro delle transazioni IdFix

La parola Dettagli nel file di registro della transazione indica il livello di registrazione nel file. "Dettagli" significa che la quantità massima delle informazioni viene acquisita nel registro. Questo è il livello di registrazione predefinito. In questo momento, non puoi cambiare il livello di registrazione.
  
## <a name="idfix-transaction-log-format"></a>Formato del registro delle transazioni IdFix

In IdFix i risultati di ogni azione di **aggiornamento** vengono scritti in un log delle transazioni, come illustrato nell'esempio seguente:
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```