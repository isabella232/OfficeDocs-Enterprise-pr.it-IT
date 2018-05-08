---
title: Gestire i gruppi del sito SharePoint Online con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Riepilogo: Utilizzare Office 365 PowerShell per gestire i gruppi del sito SharePoint Online.'
ms.openlocfilehash: 881e67b7eb2d8bb5e04f83e28569aa54341d16b9
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="237b6-103">Gestire i gruppi del sito SharePoint Online con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="237b6-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="237b6-104">**Riepilogo:** Utilizzare Office 365 PowerShell per gestire i gruppi del sito SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="237b6-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="237b6-105">Sebbene sia possibile utilizzare l'interfaccia di amministrazione di Office 365, è inoltre possibile utilizzare Office 365 PowerShell per gestire i gruppi del sito di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="237b6-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="237b6-106">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="237b6-106">Before you begin</span></span>

<span data-ttu-id="237b6-p101">Le procedure descritte in questo articolo è necessario per la connessione a SharePoint Online. Per ulteriori informazioni, vedere [connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="237b6-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="237b6-109">Visualizzazione SharePoint Online con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="237b6-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="237b6-p102">Interfaccia di amministrazione di SharePoint Online include alcuni metodi da utilizzare per la gestione dei gruppi del sito. Ad esempio, si supponga che si desidera esaminare i gruppi e i membri del gruppo, per il protocollo https\://litwareinc.sharepoint.com/sites/finance sito. Ecco che cosa è necessario effettuare per:</span><span class="sxs-lookup"><span data-stu-id="237b6-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https\://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="237b6-113">Dall'interfaccia di amministrazione di Office 365, fare clic su **risorse** > di**siti**e quindi fare clic sull'URL del sito.</span><span class="sxs-lookup"><span data-stu-id="237b6-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="237b6-114">Nella finestra di dialogo raccolta siti, fare clic su **Vai a questo sito**.</span><span class="sxs-lookup"><span data-stu-id="237b6-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="237b6-115">Nella pagina sito fare clic sull'icona **Impostazioni** (si trova nell'angolo superiore destro della pagina) e quindi fare clic su **Impostazioni sito**:</span><span class="sxs-lookup"><span data-stu-id="237b6-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="237b6-116">![Impostazioni del sito di SharePoint Online](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="237b6-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="237b6-117">Nella pagina Impostazioni sito fare clic su **autorizzazioni di siti** in **utenti e autorizzazioni**.</span><span class="sxs-lookup"><span data-stu-id="237b6-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="237b6-118">Ripetere quindi la procedura per il sito successivo.</span><span class="sxs-lookup"><span data-stu-id="237b6-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="237b6-119">Per ottenere un elenco dei gruppi con Office 365 PowerShell, utilizzare il set di comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="237b6-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="237b6-120">Esistono due modi per eseguire questo comando impostato nel prompt dei comandi di SharePoint Online Management Shell:</span><span class="sxs-lookup"><span data-stu-id="237b6-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="237b6-p103">Copiare i comandi nel blocco note (o un altro editor di testo), modificare il valore della variabile **$siteURL** , selezionare i comandi e quindi incollarle al prompt dei comandi di SharePoint Online Management Shell. In questo caso, PowerShell verrà interrotta in una **>>** prompt dei comandi. Premere INVIO per eseguire il comando **foreach** .</span><span class="sxs-lookup"><span data-stu-id="237b6-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a **>>** prompt. Press Enter to execute the **foreach** command.</span></span></br>
- <span data-ttu-id="237b6-p104">Copiare i comandi nel blocco note (o un altro editor di testo), modificare il valore della variabile **$siteURL** e quindi salvare il file di testo con un nome e l'estensione ps1 in una cartella appropriata. Successivamente, eseguire lo script dal prompt dei comandi di SharePoint Online Management Shell specificando il percorso e nome file. Ecco un comando di esempio:</span><span class="sxs-lookup"><span data-stu-id="237b6-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="237b6-127">In entrambi i casi, verrà visualizzato qualcosa di simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="237b6-127">In both cases, you should see something similar to this:</span></span>

![Gruppi di siti di SharePoint Online](images/SPO-site-groups.png)

<span data-ttu-id="237b6-p105">Si tratta di tutti i gruppi che sono stati creati per i siti https\:/ / litwareinc.sharepoint.com/sites/finance, nonché tutti gli utenti assegnati a tali gruppi. I nomi dei gruppi sono di colore giallo che consentono di nomi di gruppi separati dai relativi membri.</span><span class="sxs-lookup"><span data-stu-id="237b6-p105">These are all the groups that have been created for the site https\://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="237b6-131">Come ulteriore esempio, di seguito è un set di comandi in cui sono elencati i gruppi e tutte le appartenenze a gruppi, per tutti i siti di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="237b6-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```
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
    
## <a name="see-also"></a><span data-ttu-id="237b6-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="237b6-132">See also</span></span>

[<span data-ttu-id="237b6-133">Connettersi a PowerShell per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="237b6-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="237b6-134">Creare siti di SharePoint Online e aggiungere utenti a Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="237b6-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="237b6-135">Gestire gli utenti e i gruppi di SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="237b6-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="237b6-136">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="237b6-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="237b6-137">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="237b6-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

