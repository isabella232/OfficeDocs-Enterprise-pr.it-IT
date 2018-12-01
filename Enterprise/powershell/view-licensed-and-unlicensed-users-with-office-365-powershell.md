---
title: Visualizzare gli utenti con e senza licenza con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Viene spiegato come utilizzare PowerShell di Office 365 per visualizzare gli account utente con e senza licenza.
ms.openlocfilehash: 61f94664a62b6a5cb178579c1a5777b208d0b2ec
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123363"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="ccd69-103">Visualizzare gli utenti con e senza licenza con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="ccd69-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="ccd69-104">**Sintesi:** Viene spiegato come utilizzare PowerShell di Office 365 per visualizzare gli account utente con e senza licenza.</span><span class="sxs-lookup"><span data-stu-id="ccd69-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="ccd69-p101">Gli account utente nell'organizzazione di Office 365 possono disporre di alcune, tutte o nessuna licenza in base ai piani di gestione delle licenze nell'organizzazione. È possibile utilizzare PowerShell di Office 365 per individuare rapidamente gli utenti dotati di licenza o meno all'interno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="ccd69-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="ccd69-107">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="ccd69-107">Before you begin</span></span>

- <span data-ttu-id="ccd69-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ccd69-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="ccd69-110">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _-All_, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="ccd69-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="viewing-licensed-and-unlicensed-users"></a><span data-ttu-id="ccd69-111">Visualizzazione degli utenti con licenza e senza licenza</span><span class="sxs-lookup"><span data-stu-id="ccd69-111">Viewing licensed and unlicensed users</span></span>

<span data-ttu-id="ccd69-112">Per visualizzare l'elenco di tutti gli account utente e dei relativi stati di licenza nell'organizzazione, eseguire il comando seguente in PowerShell di Office 365:</span><span class="sxs-lookup"><span data-stu-id="ccd69-112">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="ccd69-113">Per visualizzare l'elenco di tutti gli account utente senza licenza nell'organizzazione, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ccd69-113">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="ccd69-114">Per visualizzare l'elenco di tutti gli account utente con licenza nell'organizzazione, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ccd69-114">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="ccd69-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ccd69-115">See also</span></span>

<span data-ttu-id="ccd69-116">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="ccd69-116">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="ccd69-117">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="ccd69-117">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="ccd69-118">Where-Object</span><span class="sxs-lookup"><span data-stu-id="ccd69-118">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

