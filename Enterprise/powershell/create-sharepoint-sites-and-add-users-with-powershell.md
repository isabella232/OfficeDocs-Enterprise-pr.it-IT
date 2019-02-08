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
ms.openlocfilehash: 61b9338469ed8d01abc76edbf14ed448c3ca00d3
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897169"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Creare siti di SharePoint Online e aggiungere utenti con PowerShell di Office 365

 **Riepilogo:** Utilizzare Office 365 PowerShell per creare nuovi siti di SharePoint Online e quindi aggiungere utenti e gruppi a tali siti.

Quando si utilizza Office 365 PowerShell per creare siti di SharePoint Online e aggiungere gli utenti, è possibile rapidamente e ripetutamente eseguire attività molto più rapidamente rispetto a quanto possibile in interfaccia di amministrazione di Office 356. È inoltre possibile eseguire attività che non sono possibili da eseguire nell'interfaccia di amministrazione di Office 356. 

## <a name="before-you-begin"></a>Prima di iniziare

Le procedure descritte in questo argomento richiedono per la connessione a SharePoint Online. Per ulteriori informazioni, vedere [connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Passaggio 1: Creare nuove raccolte siti con Office 365 PowerShell

Creare più siti con Office 365 PowerShell e un file csv creato utilizzando il codice riportato di seguito viene fornito e il blocco note. Per questa procedura, saranno sostituzione informazioni segnaposto indicate tra parentesi quadre con le proprie informazioni specifiche del tenant e del sito. Questo processo consente di creare un singolo file ed eseguire un comando di Office 365 PowerShell singolo che utilizza tale file. In questo modo le azioni eseguite ripetibili e portatili ed elimina molte, se non tutti gli errori che possono provenire da digitare i comandi lunghi in SharePoint Online Management Shell. Esistono due parti a questa procedura. Innanzitutto si creerà un file CSV e quindi si sarà fare riferimento file CSV con Office 365 PowerShell, che verrà utilizzato il relativo contenuto per creare i siti.

Il cmdlet PowerShell di Office 365 consente di importare il file CSV e reindirizzato a un ciclo all'interno delle parentesi graffe indicante la prima riga del file come intestazioni di colonna. Il cmdlet di Office 365 PowerShell quindi scorre i record rimanenti, crea una nuova raccolta siti per ogni record e assegna le proprietà della raccolta siti in base alle intestazioni di colonna.

### <a name="create-a-csv-file"></a>Creare un file .csv

1. Aprire Blocco note e incollare il seguente blocco di testo:<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>Dove *tenant* è il nome del tenant e *proprietario* è il nome utente dell'utente nel tenant a cui si desidera concedere il ruolo di amministratore della raccolta siti principale.<br/>(È possibile premere Ctrl + H quando si utilizza il blocco note per in blocco più velocemente replace).<br/>

2. Salvare il file sul desktop come **Sitecollections**.<br/>

> [!TIP]
> Prima di utilizzare questo o qualsiasi altro CSV o file di script di Windows PowerShell, è buona norma assicurarsi che non sono presenti caratteri non stampabili o estranee. Aprire il file di Word e nella barra multifunzione, fare clic sull'icona di paragrafo per visualizzare i caratteri non stampabili. Deve esistere nessuno dei caratteri non stampabili estranee. Ad esempio, non deve essere segni di paragrafo oltre a quello finale alla fine del file.

### <a name="run-the-windows-powershell-command"></a>Eseguire il comando di Windows PowerShell:

1. Al prompt dei comandi di Windows PowerShell, digitare o copiare e incollare il cmdlet seguente e premere INVIO:<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>Dove *MyAlias* corrisponde all'alias dell'utente.<br/>

2. Attendere il prompt dei comandi di Windows PowerShell di nuovo. Potrebbe richiedere una o due minuti.<br/>

3. Al prompt dei comandi di Windows PowerShell, digitare o copiare e incollare il cmdlet seguente e premere INVIO:<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. Nota le nuove raccolte siti nell'elenco. Verrà visualizzato le raccolte siti seguenti: **siti contosotest**, **TeamSite01**, **Blog01**e **Project01**

Questo è tutto. È stato creato un cmdlet di Windows PowerShell singolo e più raccolte siti utilizzando il file csv creato. A questo punto si è pronti creare e assegnare agli utenti di tali siti.

## <a name="step-2-add-users-and-groups"></a>Passaggio 2: aggiungere utenti e gruppi

A questo punto verranno creati gli utenti che verranno poi aggiunti a un gruppo di raccolte di sit. Si utilizzerà un file .csv per caricare in massa nuovi gruppi e utenti.

Le seguenti procedure presuppongono la corretta creazione delle raccolte di siti contosotest, TeamSite01, Blog01 e Project01.

### <a name="create-csv-and-ps1-files"></a>Creare file .csv e .ps1

1. Aprire Blocco note e incollare il seguente blocco di testo:<br/>
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
<br/>Dove *tenant* corrisponde al nome del tenant.<br/>

2. Salvare il file sul desktop come **GroupsandPermissions**.<br/>

3. Aprire una nuova istanza del blocco note e incollare il seguente blocco di testo:<br/>

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
<br/>Dove *tenant* equivale al nome del tenant e *username* equivale al nome utente di un utente esistente.<br/>

4. Salvare il file sul desktop come **Users. csv**.<br/>

5. Aprire una nuova istanza del blocco note e incollare il seguente blocco di testo:<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>Dove MyAlias corrisponde al nome utente dell'utente che ha effettuato l'accesso.<br/>

6. Salvare il file sul desktop come **UsersAndGroups.ps1**. Questo è un semplice script di Windows PowerShell.

L'utente è ora pronto a eseguire lo script UsersAndGroup.ps1 per aggiungere utenti e gruppi a più raccolte di siti.

### <a name="run-usersandgroupsps1-script"></a>Eseguire lo script UsersAndGroups.ps1

1. Tornare a SharePoint Online Management Shell.<br/>
2. Al prompt dei comandi di Windows PowerShell, digitare o copiare e incollare la riga seguente e premere INVIO:<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. Al prompt di conferma, premere **Y**.<br/>

4. Al prompt di Windows PowerShell, tipo o copia e Incolla seguenti e premere INVIO:<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>Dove *MyAlias* equivale al nome utente.<br/>

5. Attendere che il prompt risponda prima di andare avanti. Verranno innanzitutto visualizzati i gruppi man mano che vengono creati. Poi verrà visualizzato l'elenco dei gruppi ripetuto man mano che vengono aggiunti gli utenti.

## <a name="see-also"></a>Vedere anche

[Connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Gestire i gruppi del sito SharePoint Online in Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

