---
title: Gestire gli utenti e i gruppi di SharePoint Online con PowerShell di Office 365
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
description: 'Riepilogo: Utilizzare Office 365 PowerShell per gestire utenti, gruppi e siti di SharePoint Online.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="a515d-103">Gestire gli utenti e i gruppi di SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a515d-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="a515d-104">**Riepilogo:** Utilizzare Office 365 PowerShell per gestire utenti, gruppi e siti di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a515d-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="a515d-105">Se si lavora Online di SharePoint che può essere utilizzato con elenchi di grandi dimensioni dell'account utente o gruppi e desidera gestirli in modo più semplice, è possibile utilizzare Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a515d-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="a515d-106">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="a515d-106">Before you begin</span></span>

<span data-ttu-id="a515d-p101">Le procedure descritte in questo argomento richiedono per la connessione a SharePoint Online. Per ulteriori informazioni, vedere [connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="a515d-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="a515d-109">Ottenere un elenco di siti, gruppi e utenti</span><span class="sxs-lookup"><span data-stu-id="a515d-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="a515d-p102">Prima di iniziare a gestire utenti e gruppi, è necessario ottenere gli elenchi di siti, gruppi e utenti. È quindi possibile utilizzare queste informazioni per seguire l'esempio in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="a515d-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="a515d-112">Ottenere un elenco di siti</span><span class="sxs-lookup"><span data-stu-id="a515d-112">Get a list of sites</span></span>

<span data-ttu-id="a515d-113">Ottenere un elenco dei siti nel tenant con questo comando:</span><span class="sxs-lookup"><span data-stu-id="a515d-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="a515d-114">Ottenere un elenco dei gruppi</span><span class="sxs-lookup"><span data-stu-id="a515d-114">Get a list of groups</span></span>

<span data-ttu-id="a515d-115">Ottenere un elenco dei gruppi nel tenant con questo comando:</span><span class="sxs-lookup"><span data-stu-id="a515d-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="a515d-116">Ottenere un elenco degli utenti</span><span class="sxs-lookup"><span data-stu-id="a515d-116">Get a list of users</span></span>

<span data-ttu-id="a515d-117">Ottenere un elenco degli utenti nel tenant con questo comando:</span><span class="sxs-lookup"><span data-stu-id="a515d-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="a515d-118">Aggiungere un utente al gruppo di amministratori della raccolta siti</span><span class="sxs-lookup"><span data-stu-id="a515d-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="a515d-p103">Il comando **Set-SPOUser** per aggiungere un utente all'elenco degli amministratori della raccolta siti in una raccolta siti. Di seguito è illustrato l'aspetto la sintassi:</span><span class="sxs-lookup"><span data-stu-id="a515d-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="a515d-121">In questo esempio vengono utilizzate le variabili per archiviare i valori e include note nello script (ad esempio "<!--This is the Tenant Name…-->") utili per comprendere quali devono essere tali valori.</span><span class="sxs-lookup"><span data-stu-id="a515d-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="a515d-122">Ad esempio, questo set di comandi aggiunge Opal Castillo (opalc nome utente) l'elenco di amministratori della raccolta siti nella raccolta siti ContosoTest nel tenant contoso1:</span><span class="sxs-lookup"><span data-stu-id="a515d-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="a515d-123">È possibile tagliare e incollare questi comandi nel Blocco note, modificare i valori della variabile $tenant, $site e $user ai valori attuali dal proprio ambiente e quindi incollarli nella finestra di SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="a515d-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="a515d-124">Aggiungere un utente ad altri gruppi di amministratori della raccolta siti</span><span class="sxs-lookup"><span data-stu-id="a515d-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="a515d-p104">In questa attività, il comando **Add-SPOUser** utilizzeremo per aggiungere un utente a un gruppo di SharePoint in una raccolta siti. Di seguito è illustrato l'aspetto la sintassi:</span><span class="sxs-lookup"><span data-stu-id="a515d-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="a515d-127">Ad esempio, verrà quindi aggiunto Glen Rife (glenr nome utente) al gruppo Controllori nella raccolta siti ContosoTest nel tenant contoso1:</span><span class="sxs-lookup"><span data-stu-id="a515d-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="a515d-128">Creare un gruppo di raccolta siti</span><span class="sxs-lookup"><span data-stu-id="a515d-128">Create a site collection group</span></span>

<span data-ttu-id="a515d-p105">Il comando **Set-SPOSiteGroup** per creare un nuovo gruppo di SharePoint e come aggiungerla alla raccolta siti ContosoTest. Di seguito è illustrato l'aspetto la sintassi:</span><span class="sxs-lookup"><span data-stu-id="a515d-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> <span data-ttu-id="a515d-p106">Qualsiasi stringa con spazi è necessario racchiudere tra virgolette. Proprietà Group, ad esempio di livelli di autorizzazione, possono essere aggiornate in seguito utilizzando il cmdlet **Set-SPOSiteGroup** .</span><span class="sxs-lookup"><span data-stu-id="a515d-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="a515d-133">Ad esempio, verrà quindi aggiunto il gruppo Controllori con le autorizzazioni solo visualizzazione per la raccolta siti di prova Contoso nel tenant contoso1:</span><span class="sxs-lookup"><span data-stu-id="a515d-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="a515d-134">Rimuovere gli utenti da un gruppo</span><span class="sxs-lookup"><span data-stu-id="a515d-134">Remove users from a group</span></span>

<span data-ttu-id="a515d-p107">In alcuni casi, è necessario rimuovere un utente da un sito o anche da tutti i siti. Forse il dipendente viene spostato da una divisione a altra o lascia l'azienda. È possibile rendere l'operazione più facile per un solo dipendente nell'interfaccia utente, ma non è facile quando si sposta una divisione completa da un sito all’altro.</span><span class="sxs-lookup"><span data-stu-id="a515d-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="a515d-p108">Utilizzando i file CSV e SharePoint Online Management Shell, si tratta tuttavia semplice e veloce. In questa attività, si utilizzerà Windows PowerShell per rimuovere un utente da un gruppo di sicurezza di raccolta siti. Si verrà quindi utilizzare un file CSV e rimuovere una quantità elevata di utenti di siti diversi.</span><span class="sxs-lookup"><span data-stu-id="a515d-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="a515d-p109">È il comando **Remove-SPOUser** verranno utilizzate per rimuovere un singolo utente di Office 365 da un gruppo di raccolta siti solo per visualizzare la sintassi dei comandi. Di seguito è illustrato l'aspetto la sintassi:</span><span class="sxs-lookup"><span data-stu-id="a515d-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

<span data-ttu-id="a515d-143">Ad esempio, rimuovere possiamo Bobby Overby dal gruppo controllori della raccolta siti nella raccolta siti Contoso Test nel tenant contoso1:</span><span class="sxs-lookup"><span data-stu-id="a515d-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="a515d-p110">Supporre di voler rimuovere Bobby da tutti i gruppi di fa parte. Di seguito viene mostrato come fare:</span><span class="sxs-lookup"><span data-stu-id="a515d-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="a515d-p111">Serve solo a vedere come fare. Non bisogna eseguire tale comando a meno che non sia realmente necessario rimuovere un utente da tutti i gruppi, come nel caso in cui l'utente lasci la compagnia.</span><span class="sxs-lookup"><span data-stu-id="a515d-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="a515d-148">Automatizzare la gestione di elenchi di utenti e gruppi di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="a515d-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="a515d-p112">Per aggiungere un numero elevato di account per i siti di SharePoint e concedere autorizzazioni, è possibile utilizzare l'interfaccia di amministrazione di Office 365, i comandi PowerShell singoli o PowerShell un un file CSV. Di queste opzioni, il file CSV è il modo più rapido per automatizzare l'attività.</span><span class="sxs-lookup"><span data-stu-id="a515d-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="a515d-p113">Il processo di base consiste nel creare un file CSV contenente intestazioni (colonne) che corrispondono ai parametri che è necessario che lo script di Windows PowerShell. È possibile creare facilmente un elenco in Excel e quindi esportarlo come file CSV. È quindi possibile utilizzare uno script di Windows PowerShell per scorrere i record (righe) nel file CSV, aggiungere gli utenti ai gruppi e i gruppi ai siti.</span><span class="sxs-lookup"><span data-stu-id="a515d-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="a515d-p114">Ad esempio, creare un file CSV per definire un gruppo di raccolte di siti, gruppi e autorizzazioni. Successivamente, viene creato un file CSV per popolare i gruppi di utenti. Per concludere, viene creato ed eseguito un semplice script Windows PowerShell che crea e popola i gruppi.</span><span class="sxs-lookup"><span data-stu-id="a515d-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="a515d-157">Il primo file CSV aggiunge uno o più gruppi a uno o più raccolte di siti e avrà la seguente struttura:</span><span class="sxs-lookup"><span data-stu-id="a515d-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="a515d-158">Intestazione:</span><span class="sxs-lookup"><span data-stu-id="a515d-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="a515d-159">Articolo:</span><span class="sxs-lookup"><span data-stu-id="a515d-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="a515d-160">Ecco un esempio di file:</span><span class="sxs-lookup"><span data-stu-id="a515d-160">Here is an example file:</span></span>

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="a515d-161">Il secondo file CSV aggiunge uno o più utenti a uno o più gruppi e avrà la seguente struttura:</span><span class="sxs-lookup"><span data-stu-id="a515d-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="a515d-162">Intestazione:</span><span class="sxs-lookup"><span data-stu-id="a515d-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="a515d-163">Articolo:</span><span class="sxs-lookup"><span data-stu-id="a515d-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="a515d-164">Ecco un esempio di file:</span><span class="sxs-lookup"><span data-stu-id="a515d-164">Here is an example file:</span></span>

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

<span data-ttu-id="a515d-p115">Per il passaggio successivo, è necessario salvare i due file CSV sul disco. Ecco i comandi che utilizzano entrambi i file CSV e per aggiungere le autorizzazioni e l'appartenenza al gruppo:</span><span class="sxs-lookup"><span data-stu-id="a515d-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="a515d-p116">Lo script consente di importare il contenuto del file CSV e utilizza i valori delle colonne (in grassetto) per popolare i parametri dei comandi **New-SPOSiteGroup** e **Add-SPOUser** . In questo esempio viene stiamo risparmiando seguente sull'unità C, ma è possibile salvare desiderata.</span><span class="sxs-lookup"><span data-stu-id="a515d-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="a515d-p117">Ora, rimuovere un gruppo di utenti per diversi gruppi di siti diversi utilizzando lo stesso file CSV. Ecco il comando:</span><span class="sxs-lookup"><span data-stu-id="a515d-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="a515d-171">Generare report utente</span><span class="sxs-lookup"><span data-stu-id="a515d-171">Generate user reports</span></span>

<span data-ttu-id="a515d-p118">Potrebbe essere necessario ottenere un semplice report per alcuni nuovi siti e visualizzare i rispettivi utenti, il livello di autorizzazione e altre proprietà. Questo è l'aspetto della sintassi:</span><span class="sxs-lookup"><span data-stu-id="a515d-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="a515d-p119">Questo verrà acquisire i dati per questi tre siti e li scrive un file di testo nell'unità locale. Si noti che il parametro – Append aggiungere nuovo contenuto a un file esistente.</span><span class="sxs-lookup"><span data-stu-id="a515d-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="a515d-176">Ad esempio, eseguire un report nei siti ContosoTest, TeamSite01 e Project01 per il tenant Contoso1:</span><span class="sxs-lookup"><span data-stu-id="a515d-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="a515d-p120">Si noti che è stato necessario modificare solo la variabile **$site** . La variabile **$tenant** mantiene il relativo valore tramite tutti i tre esecuzioni del comando.</span><span class="sxs-lookup"><span data-stu-id="a515d-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="a515d-p121">Tuttavia, cosa succede se si desidera effettuare questa operazione per ogni sito? È possibile eseguirlo senza dover digitare tutti i siti Web utilizzando questo comando:</span><span class="sxs-lookup"><span data-stu-id="a515d-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="a515d-p122">In questo report è piuttosto semplice ed è possibile aggiungere ulteriori codice per creare più specifiche report o un report che includono informazioni più dettagliate. Tuttavia, questa deve avere un'idea di come utilizzare SharePoint Online Management Shell per gestire gli utenti nell'ambiente di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a515d-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="a515d-183">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a515d-183">See also</span></span>

[<span data-ttu-id="a515d-184">Connettersi a PowerShell per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a515d-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="a515d-185">Gestire SharePoint Online con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a515d-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="a515d-186">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a515d-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a515d-187">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a515d-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

