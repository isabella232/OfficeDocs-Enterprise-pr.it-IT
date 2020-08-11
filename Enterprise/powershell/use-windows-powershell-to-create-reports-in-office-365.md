---
title: Usare PowerShell per creare report per Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: "Riepilogo: utilizzare PowerShell per Microsoft 365 per creare report che non è possibile produrre nell'interfaccia di amministrazione di Microsoft 365."
ms.openlocfilehash: d2d03d6ac170fef95352a2aabf6cd27176202a1e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605318"
---
# <a name="use-powershell-to-create-reports-for-microsoft-365"></a><span data-ttu-id="5d525-103">Usare PowerShell per creare report per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="5d525-103">Use PowerShell to create reports for Microsoft 365</span></span>

<span data-ttu-id="5d525-104">*Questo articolo può essere applicato sia a Microsoft 365 Enterprise che a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="5d525-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5d525-105">Sono disponibili molti report nell'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="5d525-105">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="5d525-106">Tuttavia, questi report forniscono solo determinate informazioni e talvolta è necessario aggiungerne altre.</span><span class="sxs-lookup"><span data-stu-id="5d525-106">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="5d525-107">Questo è il momento in cui è necessario PowerShell per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="5d525-107">That's when you need PowerShell for Microsoft 365</span></span>
  
<span data-ttu-id="5d525-108">Questi articoli che descrivono come utilizzare PowerShell per Microsoft 365 per ottenere informazioni dal tenant di Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="5d525-108">These articles that describe how to use PowerShell for Microsoft 365 to obtain information from your Microsoft 365 tenant:</span></span>
  
- <span data-ttu-id="5d525-109">Guida introduttiva alla creazione di report tramite PowerShell per Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="5d525-109">Getting started with reporting using PowerShell for Microsoft 365:</span></span>
    
  - [<span data-ttu-id="5d525-110">PowerShell per Microsoft 365 è in grado di rivelare informazioni aggiuntive che non sono visibili con l'interfaccia di amministrazione</span><span class="sxs-lookup"><span data-stu-id="5d525-110">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="5d525-111">PowerShell per Microsoft 365 è ottimo per filtrare i dati</span><span class="sxs-lookup"><span data-stu-id="5d525-111">PowerShell for Microsoft 365 is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="5d525-112">PowerShell per Microsoft 365 rende più semplice la stampa o il salvataggio dei dati</span><span class="sxs-lookup"><span data-stu-id="5d525-112">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="5d525-113">Report degli account utente e delle licenze:</span><span class="sxs-lookup"><span data-stu-id="5d525-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="5d525-114">Visualizzare le licenze e i servizi di Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-114">View Microsoft 365 licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="5d525-115">Visualizzare gli utenti con licenza e senza licenza di Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-115">View Microsoft 365 licensed and unlicensed users with PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="5d525-116">Visualizzare le informazioni sulle licenze e i servizi di Microsoft 365 account con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-116">View Microsoft 365 account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="5d525-117">Visualizzare gli account utente di Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-117">View Microsoft 365 user accounts with PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="5d525-118">Report di SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="5d525-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="5d525-119">Guida introduttiva a SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="5d525-119">Get started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
    
  - [<span data-ttu-id="5d525-120">Gestire i gruppi di siti di SharePoint Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-120">Manage SharePoint Online site groups with PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="5d525-121">Report di Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="5d525-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="5d525-122">Visualizzare le informazioni sulle cassette postali di Exchange Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-122">Display Exchange Online mailbox information with PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="5d525-123">Visualizzare i report di Exchange Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-123">Display Exchange Online reports with PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="related-topics"></a><span data-ttu-id="5d525-124">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="5d525-124">Related topics</span></span>

[<span data-ttu-id="5d525-125">Gestire Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-125">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5d525-126">Guida introduttiva a PowerShell per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="5d525-126">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="5d525-127">Gestire SharePoint Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-127">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="5d525-128">Gestire gli account utente, le licenze e i gruppi di Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d525-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
