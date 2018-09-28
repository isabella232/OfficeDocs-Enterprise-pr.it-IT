---
title: Creare siti di SharePoint Online e aggiungere utenti con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Riepilogo: Utilizzare Office 365 PowerShell per creare nuovi siti di SharePoint Online e quindi aggiungere utenti e gruppi a tali siti.'
ms.openlocfilehash: 41ca26249bd494d5603a425689e47f9fe6809f1a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975204"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="961ae-103">Creare siti di SharePoint Online e aggiungere utenti con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="961ae-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="961ae-104">**Riepilogo:** Utilizzare Office 365 PowerShell per creare nuovi siti di SharePoint Online e quindi aggiungere utenti e gruppi a tali siti.</span><span class="sxs-lookup"><span data-stu-id="961ae-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="961ae-p101">Quando si utilizza Office 365 PowerShell per creare siti di SharePoint Online e aggiungere gli utenti, è possibile rapidamente e ripetutamente eseguire attività molto più rapidamente rispetto a quanto possibile in interfaccia di amministrazione di Office 356. È inoltre possibile eseguire attività che non sono possibili da eseguire nell'interfaccia di amministrazione di Office 356.</span><span class="sxs-lookup"><span data-stu-id="961ae-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="961ae-107">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="961ae-107">Before you begin</span></span>

<span data-ttu-id="961ae-p102">Le procedure descritte in questo argomento richiedono per la connessione a SharePoint Online. Per ulteriori informazioni, vedere [connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="961ae-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="961ae-110">Passaggio 1: Creare nuove raccolte siti con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="961ae-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="961ae-p103">Creare più siti con Office 365 PowerShell e un file csv creato utilizzando il codice riportato di seguito viene fornito e il blocco note. Per questa procedura, saranno sostituzione informazioni segnaposto indicate tra parentesi quadre con le proprie informazioni specifiche del tenant e del sito. Questo processo consente di creare un singolo file ed eseguire un comando di Office 365 PowerShell singolo che utilizza tale file. In questo modo le azioni eseguite ripetibili e portatili ed elimina molte, se non tutti gli errori che possono provenire da digitare i comandi lunghi in SharePoint Online Management Shell. Esistono due parti a questa procedura. Innanzitutto si creerà un file CSV e quindi si sarà fare riferimento file CSV con Office 365 PowerShell, che verrà utilizzato il relativo contenuto per creare i siti.</span><span class="sxs-lookup"><span data-stu-id="961ae-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process allows you to create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="961ae-p104">Il cmdlet PowerShell di Office 365 consente di importare il file CSV e reindirizzato a un ciclo all'interno delle parentesi graffe indicante la prima riga del file come intestazioni di colonna. Il cmdlet di Office 365 PowerShell quindi scorre i record rimanenti, crea una nuova raccolta siti per ogni record e assegna le proprietà della raccolta siti in base alle intestazioni di colonna.</span><span class="sxs-lookup"><span data-stu-id="961ae-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="961ae-119">Creare un file .csv</span><span class="sxs-lookup"><span data-stu-id="961ae-119">Create a .csv file</span></span>

1. <span data-ttu-id="961ae-120">Aprire Blocco note e incollare il seguente blocco di testo:</span><span class="sxs-lookup"><span data-stu-id="961ae-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="961ae-121">Dove *tenant* è il nome del tenant e *proprietario* è il nome utente dell'utente nel tenant a cui si desidera concedere il ruolo di amministratore della raccolta siti principale.</span><span class="sxs-lookup"><span data-stu-id="961ae-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="961ae-122">(È possibile premere Ctrl + H quando si utilizza il blocco note per in blocco più velocemente replace).</span><span class="sxs-lookup"><span data-stu-id="961ae-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="961ae-123">Salvare il file sul desktop come **Sitecollections**.</span><span class="sxs-lookup"><span data-stu-id="961ae-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="961ae-p105">Prima di utilizzare questo o qualsiasi altro CSV o file di script di Windows PowerShell, è buona norma assicurarsi che non sono presenti caratteri non stampabili o estranee. Aprire il file di Word e nella barra multifunzione, fare clic sull'icona di paragrafo per visualizzare i caratteri non stampabili. Deve esistere nessuno dei caratteri non stampabili estranee. Ad esempio, non deve essere segni di paragrafo oltre a quello finale alla fine del file.</span><span class="sxs-lookup"><span data-stu-id="961ae-p105">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="961ae-128">Eseguire il comando di Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="961ae-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="961ae-129">Al prompt dei comandi di Windows PowerShell, digitare o copiare e incollare il cmdlet seguente e premere INVIO:</span><span class="sxs-lookup"><span data-stu-id="961ae-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="961ae-130">Dove *MyAlias* corrisponde all'alias dell'utente.</span><span class="sxs-lookup"><span data-stu-id="961ae-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="961ae-p106">Attendere il prompt dei comandi di Windows PowerShell di nuovo. Potrebbe richiedere una o due minuti.</span><span class="sxs-lookup"><span data-stu-id="961ae-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="961ae-133">Al prompt dei comandi di Windows PowerShell, digitare o copiare e incollare il cmdlet seguente e premere INVIO:</span><span class="sxs-lookup"><span data-stu-id="961ae-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="961ae-p107">Nota le nuove raccolte siti nell'elenco. Verrà visualizzato le raccolte siti seguenti: **siti contosotest**, **TeamSite01**, **Blog01**e **Project01**</span><span class="sxs-lookup"><span data-stu-id="961ae-p107">Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="961ae-p108">Questo è tutto. È stato creato un cmdlet di Windows PowerShell singolo e più raccolte siti utilizzando il file csv creato. A questo punto si è pronti creare e assegnare agli utenti di tali siti.</span><span class="sxs-lookup"><span data-stu-id="961ae-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="961ae-139">Passaggio 2: aggiungere utenti e gruppi</span><span class="sxs-lookup"><span data-stu-id="961ae-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="961ae-p109">A questo punto verranno creati gli utenti che verranno poi aggiunti a un gruppo di raccolte di sit. Si utilizzerà un file .csv per caricare in massa nuovi gruppi e utenti.</span><span class="sxs-lookup"><span data-stu-id="961ae-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="961ae-142">Le seguenti procedure presuppongono la corretta creazione delle raccolte di siti contosotest, TeamSite01, Blog01 e Project01.</span><span class="sxs-lookup"><span data-stu-id="961ae-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="961ae-143">Creare file .csv e .ps1</span><span class="sxs-lookup"><span data-stu-id="961ae-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="961ae-144">Aprire Blocco note e incollare il seguente blocco di testo:</span><span class="sxs-lookup"><span data-stu-id="961ae-144">Open Notepad, and paste the following text block into it:</span></span><br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/><span data-ttu-id="961ae-145">Dove *tenant* corrisponde al nome del tenant.</span><span class="sxs-lookup"><span data-stu-id="961ae-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="961ae-146">Salvare il file sul desktop come **GroupsandPermissions**.</span><span class="sxs-lookup"><span data-stu-id="961ae-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="961ae-147">Aprire una nuova istanza del blocco note e incollare il seguente blocco di testo:</span><span class="sxs-lookup"><span data-stu-id="961ae-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/><span data-ttu-id="961ae-148">Dove *tenant* equivale al nome del tenant e *username* equivale al nome utente di un utente esistente.</span><span class="sxs-lookup"><span data-stu-id="961ae-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="961ae-149">Salvare il file sul desktop come **Users. csv**.</span><span class="sxs-lookup"><span data-stu-id="961ae-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="961ae-150">Aprire una nuova istanza del blocco note e incollare il seguente blocco di testo:</span><span class="sxs-lookup"><span data-stu-id="961ae-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="961ae-151">Dove MyAlias corrisponde al nome utente dell'utente che ha effettuato l'accesso.</span><span class="sxs-lookup"><span data-stu-id="961ae-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="961ae-p110">Salvare il file sul desktop come **UsersAndGroups.ps1**. Questo è un semplice script di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="961ae-p110">Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="961ae-154">L'utente è ora pronto a eseguire lo script UsersAndGroup.ps1 per aggiungere utenti e gruppi a più raccolte di siti.</span><span class="sxs-lookup"><span data-stu-id="961ae-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="961ae-155">Eseguire lo script UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="961ae-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="961ae-156">Tornare a SharePoint Online Management Shell.</span><span class="sxs-lookup"><span data-stu-id="961ae-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="961ae-157">Al prompt dei comandi di Windows PowerShell, digitare o copiare e incollare la riga seguente e premere INVIO:</span><span class="sxs-lookup"><span data-stu-id="961ae-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="961ae-158">Al prompt di conferma, premere **Y**.</span><span class="sxs-lookup"><span data-stu-id="961ae-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="961ae-159">Al prompt di Windows PowerShell, tipo o copia e Incolla seguenti e premere INVIO:</span><span class="sxs-lookup"><span data-stu-id="961ae-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="961ae-160">Dove *MyAlias* equivale al nome utente.</span><span class="sxs-lookup"><span data-stu-id="961ae-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="961ae-p111">Attendere che il prompt risponda prima di andare avanti. Verranno innanzitutto visualizzati i gruppi man mano che vengono creati. Poi verrà visualizzato l'elenco dei gruppi ripetuto man mano che vengono aggiunti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="961ae-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="961ae-164">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="961ae-164">See also</span></span>

[<span data-ttu-id="961ae-165">Connettersi a PowerShell per SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="961ae-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="961ae-166">Gestire i gruppi del sito SharePoint Online in Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="961ae-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="961ae-167">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="961ae-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="961ae-168">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="961ae-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

