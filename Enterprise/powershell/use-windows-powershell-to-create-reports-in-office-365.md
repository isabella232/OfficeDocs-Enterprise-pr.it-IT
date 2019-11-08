---
title: Utilizzo di Windows PowerShell per creare rapporti in Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/22/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: "Sintesi: Utilizzare PowerShell di Office 365 per creare report che non è possibile produrre nell'interfaccia di amministrazione di Microsoft 365."
ms.openlocfilehash: e620ecffc89bd5b93de7b608be55bf68721b80af
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031681"
---
# <a name="use-windows-powershell-to-create-reports-in-office-365"></a><span data-ttu-id="c7a1d-103">Utilizzo di Windows PowerShell per creare rapporti in Office 365</span><span class="sxs-lookup"><span data-stu-id="c7a1d-103">Use Windows PowerShell to create reports in Office 365</span></span>

 <span data-ttu-id="c7a1d-104">**Sintesi**: Utilizzare PowerShell di Office 365 per creare report che non è possibile produrre nell'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c7a1d-104">**Summary:** Use Office 365 PowerShell to create reports that you cannot produce in the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="c7a1d-105">Sono disponibili molti report nell'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c7a1d-105">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="c7a1d-106">Tuttavia, questi report forniscono solo determinate informazioni e talvolta è necessario aggiungerne altre.</span><span class="sxs-lookup"><span data-stu-id="c7a1d-106">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="c7a1d-107">In questi casi, è necessario disporre di PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c7a1d-107">That's when you need Office 365 PowerShell</span></span>
  
<span data-ttu-id="c7a1d-108">Gli articoli seguenti descrivono come utilizzare PowerShell di Office 365 per ottenere informazioni dal tenant di Office 365:</span><span class="sxs-lookup"><span data-stu-id="c7a1d-108">These articles that describe how to use Office 365 PowerShell to obtain information from your Office 365 tenant:</span></span>
  
- <span data-ttu-id="c7a1d-109">Guida introduttiva alla creazione di report mediante PowerShell di Office 365:</span><span class="sxs-lookup"><span data-stu-id="c7a1d-109">Getting started with reporting using Office 365 PowerShell:</span></span>
    
  - [<span data-ttu-id="c7a1d-110">PowerShell di Office 365 può rivelare informazioni aggiuntive che non sono visibili con l'interfaccia di amministrazione</span><span class="sxs-lookup"><span data-stu-id="c7a1d-110">Office 365 PowerShell can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="c7a1d-111">PowerShell di Office 365 è molto utile per il filro dei dati</span><span class="sxs-lookup"><span data-stu-id="c7a1d-111">Office 365 PowerShell is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="c7a1d-112">PowerShell di Office 365 facilita la stampa e il salvataggio dei dati</span><span class="sxs-lookup"><span data-stu-id="c7a1d-112">Office 365 PowerShell makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="c7a1d-113">Report degli account utente e delle licenze:</span><span class="sxs-lookup"><span data-stu-id="c7a1d-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="c7a1d-114">Visualizzare le licenze e i servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c7a1d-114">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="c7a1d-115">Visualizzare gli utenti con e senza licenza con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c7a1d-115">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="c7a1d-116">Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7a1d-116">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="c7a1d-117">Visualizzare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7a1d-117">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="c7a1d-118">Report di SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="c7a1d-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="c7a1d-119">Gestire gli utenti e i gruppi di SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c7a1d-119">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx)
    
  - [<span data-ttu-id="c7a1d-120">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7a1d-120">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="c7a1d-121">Report di Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="c7a1d-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="c7a1d-122">Display Exchange Online mailbox information with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7a1d-122">Display Exchange Online mailbox information with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="c7a1d-123">Display Exchange Online reports with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7a1d-123">Display Exchange Online reports with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="c7a1d-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c7a1d-124">See also</span></span>

#### 

[<span data-ttu-id="c7a1d-125">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c7a1d-125">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c7a1d-126">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c7a1d-126">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="c7a1d-127">Gestire SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="c7a1d-127">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="c7a1d-128">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7a1d-128">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
