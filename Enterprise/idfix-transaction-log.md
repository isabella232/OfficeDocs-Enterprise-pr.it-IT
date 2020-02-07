---
title: Log delle transazioni IdFix di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Fornisce un esempio e descrive la convenzione di denominazione e il livello di registrazione predefinito del registro delle transazioni IdFix di Office 365.
ms.openlocfilehash: fb294095dc5b163965660546f5033a845d6cb0b4
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840113"
---
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="9120a-103">Log delle transazioni IdFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="9120a-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="9120a-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="9120a-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="9120a-105">Fornisce un esempio e descrive la convenzione di denominazione e il livello di registrazione predefinito del registro delle transazioni IdFix di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9120a-105">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="9120a-106">Posizione del registro delle transazioni IdFix</span><span class="sxs-lookup"><span data-stu-id="9120a-106">IdFix transaction log location</span></span>

<span data-ttu-id="9120a-107">Lo strumento Office 365 IdFix crea un nuovo log delle transazioni ogni volta che si fa clic su **applica** in IdFix e si applicano modifiche alla foresta di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9120a-107">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="9120a-108">Il registro delle transazioni viene salvato nella stessa cartella in cui è stato installato IdFix.</span><span class="sxs-lookup"><span data-stu-id="9120a-108">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="9120a-109">Per impostazione predefinita, questa cartella è C:\Deployment Tools\IDFix.</span><span class="sxs-lookup"><span data-stu-id="9120a-109">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="9120a-110">Il nome del file del registro delle transazioni utilizza un formato di data e ora, ad esempio, verbose 6-1-2018 6-17-22 PM indica un file che è stato generato al 1 ° giugno 2018 alle 6:17:22 PM.</span><span class="sxs-lookup"><span data-stu-id="9120a-110">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="9120a-111">Dettagli indica il livello di registrazione.</span><span class="sxs-lookup"><span data-stu-id="9120a-111">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="9120a-112">Il livello di registrazione del registro delle transazioni IdFix</span><span class="sxs-lookup"><span data-stu-id="9120a-112">IdFix transaction log logging level</span></span>

<span data-ttu-id="9120a-p102">La parola Dettagli nel file di registro della transazione indica il livello di registrazione nel file. "Dettagli" significa che la quantità massima delle informazioni viene acquisita nel registro. Questo è il livello di registrazione predefinito. In questo momento, non puoi cambiare il livello di registrazione.</span><span class="sxs-lookup"><span data-stu-id="9120a-p102">The word verbose in the transaction log file name indicates the level of logging in the file. Verbose means that the maximum amount of information is captured in the log. This is the default logging level. At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="9120a-117">Formato del registro delle transazioni IdFix</span><span class="sxs-lookup"><span data-stu-id="9120a-117">IdFix transaction log format</span></span>

<span data-ttu-id="9120a-118">In IdFix i risultati di ogni azione di **aggiornamento** vengono scritti in un log delle transazioni, come illustrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="9120a-118">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
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