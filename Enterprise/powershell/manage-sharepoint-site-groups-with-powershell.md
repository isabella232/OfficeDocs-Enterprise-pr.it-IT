---
title: Manage SharePoint Online site groups with Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Riepilogo: utilizzare Office 365 PowerShell per gestire i gruppi di siti di SharePoint Online.'
ms.openlocfilehash: e8cde8e65b009c1ae677df6b63f416ed227f824c
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261389"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="68329-103">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="68329-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="68329-104">Anche se è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365, è anche possibile utilizzare Office 365 PowerShell per gestire i gruppi di siti di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="68329-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="68329-105">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="68329-105">Before you begin</span></span>

<span data-ttu-id="68329-106">Le procedure descritte in questo articolo richiedono la connessione a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="68329-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="68329-107">Per istruzioni, vedere [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="68329-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="68329-108">Visualizzazione di SharePoint Online con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="68329-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="68329-109">L'interfaccia di amministrazione di SharePoint Online offre alcuni metodi di facile utilizzo per la gestione dei gruppi di siti.</span><span class="sxs-lookup"><span data-stu-id="68329-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="68329-110">Ad esempio, si supponga di voler esaminare i gruppi e i membri del gruppo per il `https://litwareinc.sharepoint.com/sites/finance` sito.</span><span class="sxs-lookup"><span data-stu-id="68329-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="68329-111">Di seguito sono riportate le operazioni da eseguire per:</span><span class="sxs-lookup"><span data-stu-id="68329-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="68329-112">Dall'interfaccia di amministrazione di SharePoint, fare clic su **siti attivi**e quindi fare clic sull'URL del sito.</span><span class="sxs-lookup"><span data-stu-id="68329-112">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="68329-113">Nella pagina sito fare clic sull'icona **delle impostazioni** (nell'angolo in alto a destra della pagina) e quindi fare clic su **autorizzazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="68329-113">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="68329-114">Ripetere quindi la procedura per il sito successivo.</span><span class="sxs-lookup"><span data-stu-id="68329-114">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="68329-115">Per ottenere un elenco dei gruppi con Office 365 PowerShell, è possibile utilizzare i seguenti comandi:</span><span class="sxs-lookup"><span data-stu-id="68329-115">To get a list of the groups with Office 365 PowerShell, you can use the following commands:</span></span>

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="68329-116">Esistono due modi per eseguire questo set di comandi nel prompt dei comandi di SharePoint Online Management Shell:</span><span class="sxs-lookup"><span data-stu-id="68329-116">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="68329-117">Copiare i comandi nel blocco note o in un altro editor di testo, modificare il valore della variabile **$SiteUrl** , selezionare i comandi e quindi incollarli nel prompt dei comandi di SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="68329-117">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="68329-118">Quando si esegue questa operazione, PowerShell si arresterà al **>>** prompt.</span><span class="sxs-lookup"><span data-stu-id="68329-118">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="68329-119">Premere INVIO per eseguire il `foreach` comando.</span><span class="sxs-lookup"><span data-stu-id="68329-119">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="68329-120">Copiare i comandi nel blocco note o in un altro editor di testo, modificare il valore della variabile **$SiteUrl** e quindi salvare il file di testo con un nome e l'estensione ps1 in una cartella adatta.</span><span class="sxs-lookup"><span data-stu-id="68329-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="68329-121">Successivamente, eseguire lo script dal prompt dei comandi di SharePoint Online Management Shell specificando il percorso e il nome del file.</span><span class="sxs-lookup"><span data-stu-id="68329-121">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="68329-122">Ecco un esempio di comando:</span><span class="sxs-lookup"><span data-stu-id="68329-122">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="68329-123">In entrambi i casi, dovrebbe essere visualizzato qualcosa di simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="68329-123">In both cases, you should see something similar to this:</span></span>

![Gruppi di siti di SharePoint Online](media/SPO-site-groups.png)

<span data-ttu-id="68329-125">Questi sono tutti i gruppi che sono stati creati per il sito `https://litwareinc.sharepoint.com/sites/finance`e tutti gli utenti assegnati a tali gruppi.</span><span class="sxs-lookup"><span data-stu-id="68329-125">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="68329-126">I nomi dei gruppi sono in giallo che consentono di separare i nomi dei gruppi dai rispettivi membri.</span><span class="sxs-lookup"><span data-stu-id="68329-126">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="68329-127">Un altro esempio è un set di comandi che elenca i gruppi e tutte le appartenenze a gruppi per tutti i siti di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="68329-127">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a><span data-ttu-id="68329-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="68329-128">See also</span></span>

[<span data-ttu-id="68329-129">Connettersi a PowerShell per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="68329-129">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="68329-130">Creare siti di SharePoint Online e aggiungere utenti con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="68329-130">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="68329-131">Gestire gli utenti e i gruppi di SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="68329-131">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="68329-132">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="68329-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="68329-133">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="68329-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

