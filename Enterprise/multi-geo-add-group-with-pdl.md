---
title: Creare un gruppo di Office 365 con una posizione preferita per i dati specifica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come creare un gruppo di Office 365 con una posizione preferita per i dati specifica in un ambiente multi-geografico.
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070002"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="f2778-103">Creare un gruppo di Office 365 con una posizione preferita per i dati specifica</span><span class="sxs-lookup"><span data-stu-id="f2778-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="f2778-104">Quando gli utenti in un ambiente multi-geografico creano un gruppo di Office 365, la posizione preferita per i dati del gruppo viene impostata automaticamente su quella dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f2778-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="f2778-105">Se è necessario creare un gruppo con una posizione preferita per i dati specifica, è possibile usare il cmdlet New-UnifiedGroup di Microsoft PowerShell per Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f2778-105">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="f2778-106">Quando si esegue questa operazione, il provisioning della cassetta postale del gruppo e del sito di SharePoint associato al gruppo verrà effettuato nella posizione preferita per i dati specifica.</span><span class="sxs-lookup"><span data-stu-id="f2778-106">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="f2778-107">Per eseguire questa operazione, è necessario essere un amministratore globale o un amministratore di SharePoint Online o di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f2778-107">You must be a global administrator or a SharePoint Online or Exchange Online administrator to do this.</span></span>

<span data-ttu-id="f2778-108">Per creare un gruppo di Office 365 con la posizione preferita per i dati specifica, connettersi a PowerShell per Exchange Online e passare il parametro *MailBoxRegion -* con il codice della posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="f2778-108">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="f2778-109">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f2778-109">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Screenshot del cmdlet New-UnifiedGroup di PowerShell con la sintassi](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="f2778-111">Si noti che il provisioning del sito del gruppo di SharePoint viene effettuato su richiesta.</span><span class="sxs-lookup"><span data-stu-id="f2778-111">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="f2778-112">Il provisioning del sito verrà effettuato la prima volta che un membro o un proprietario del gruppo prova ad accedervi.</span><span class="sxs-lookup"><span data-stu-id="f2778-112">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="f2778-113">Codici di posizione geografica</span><span class="sxs-lookup"><span data-stu-id="f2778-113">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="f2778-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f2778-114">See also</span></span>

[<span data-ttu-id="f2778-115">Connettersi a PowerShell per Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f2778-115">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)