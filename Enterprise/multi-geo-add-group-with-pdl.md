---
title: Creare un gruppo di Office 365 con una posizione preferita per i dati specifica
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come creare un gruppo di Office 365 con una posizione preferita per i dati specifica in un ambiente multi-geografico.
ms.openlocfilehash: 96c2e5513879dff291c0119ddad38a78ab91ec1a
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974088"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="93417-103">Creare un gruppo di Office 365 con una posizione preferita per i dati specifica</span><span class="sxs-lookup"><span data-stu-id="93417-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="93417-104">Quando gli utenti in un ambiente multi-geografico creano un gruppo di Office 365, la posizione preferita per i dati del gruppo viene impostata automaticamente su quella dell'utente.</span><span class="sxs-lookup"><span data-stu-id="93417-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="93417-105">Gli amministratori globali di SharePoint ed Exchange possono creare i gruppi in qualsiasi area selezionata.</span><span class="sxs-lookup"><span data-stu-id="93417-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="93417-106">Se è necessario creare un gruppo con una posizione preferita per i dati specifica, è possibile usare il cmdlet New-UnifiedGroup di Microsoft PowerShell dall'interfaccia di amministrazione di SharePoint o tramite Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="93417-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="93417-107">Quando si esegue questa operazione, il provisioning della cassetta postale del gruppo e del sito di SharePoint associato al gruppo verrà effettuato nella posizione preferita per i dati specifica.</span><span class="sxs-lookup"><span data-stu-id="93417-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="93417-108">Per creare un gruppo di Office 365 con la posizione preferita per i dati specifica, passare all'interfaccia di amministrazione di SharePoint nella posizione geografica in cui si vuole creare il sito del gruppo.</span><span class="sxs-lookup"><span data-stu-id="93417-108">To create an Office 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="93417-109">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="93417-109">For example:</span></span>

<span data-ttu-id="93417-110">Se si vuole per creare un sito del gruppo nella posizione in Australia, passare a https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span><span class="sxs-lookup"><span data-stu-id="93417-110">If you wan to create a group site in your Australtia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="93417-111">Selezionare **+ Crea**.</span><span class="sxs-lookup"><span data-stu-id="93417-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="93417-112">Seguire la procedura per creare un sito di gruppo.</span><span class="sxs-lookup"><span data-stu-id="93417-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="93417-113">Il provisioning del sito del gruppo verrà effettuato nella posizione geografica corrispondente all'interfaccia di amministrazione di SharePoint da cui è stata avviata la richiesta di creazione del sito.</span><span class="sxs-lookup"><span data-stu-id="93417-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="93417-114">Utilizzo di PowerShell di Exchange</span><span class="sxs-lookup"><span data-stu-id="93417-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="93417-115">Connettersi a PowerShell per Exchange Online e passare il parametro *-MailBoxRegion* con il codice della posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="93417-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="93417-116">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="93417-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Screenshot del cmdlet New-UnifiedGroup di PowerShell con la sintassi](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="93417-118">Si noti che il provisioning del sito del gruppo di SharePoint viene effettuato su richiesta.</span><span class="sxs-lookup"><span data-stu-id="93417-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="93417-119">Il provisioning del sito verrà effettuato la prima volta che un membro o un proprietario del gruppo prova ad accedervi.</span><span class="sxs-lookup"><span data-stu-id="93417-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="93417-120">Codici di posizione geografica</span><span class="sxs-lookup"><span data-stu-id="93417-120">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="93417-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="93417-121">See also</span></span>

[<span data-ttu-id="93417-122">Connettersi a PowerShell per Exchange Online</span><span class="sxs-lookup"><span data-stu-id="93417-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
