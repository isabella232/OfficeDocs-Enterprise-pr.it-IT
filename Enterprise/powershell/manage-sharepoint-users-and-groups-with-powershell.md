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
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Gestire gli utenti e i gruppi di SharePoint Online con PowerShell di Office 365

 **Riepilogo:** Utilizzare Office 365 PowerShell per gestire utenti, gruppi e siti di SharePoint Online.

Se si lavora Online di SharePoint che può essere utilizzato con elenchi di grandi dimensioni dell'account utente o gruppi e desidera gestirli in modo più semplice, è possibile utilizzare Office 365 PowerShell. 

## <a name="before-you-begin"></a>Prima di iniziare

Le procedure descritte in questo argomento richiedono per la connessione a SharePoint Online. Per ulteriori informazioni, vedere [connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>Ottenere un elenco di siti, gruppi e utenti

Prima di iniziare a gestire utenti e gruppi, è necessario ottenere gli elenchi di siti, gruppi e utenti. È quindi possibile utilizzare queste informazioni per seguire l'esempio in questo articolo.

### <a name="get-a-list-of-sites"></a>Ottenere un elenco di siti

Ottenere un elenco dei siti nel tenant con questo comando:

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>Ottenere un elenco dei gruppi

Ottenere un elenco dei gruppi nel tenant con questo comando:

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a>Ottenere un elenco degli utenti

Ottenere un elenco degli utenti nel tenant con questo comando:

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Aggiungere un utente al gruppo di amministratori della raccolta siti

Il comando **Set-SPOUser** per aggiungere un utente all'elenco degli amministratori della raccolta siti in una raccolta siti. Di seguito è illustrato l'aspetto la sintassi:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

In questo esempio vengono utilizzate le variabili per archiviare i valori e include note nello script (ad esempio "<!--This is the Tenant Name…-->") utili per comprendere quali devono essere tali valori.

Ad esempio, questo set di comandi aggiunge Opal Castillo (opalc nome utente) l'elenco di amministratori della raccolta siti nella raccolta siti ContosoTest nel tenant contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

È possibile tagliare e incollare questi comandi nel Blocco note, modificare i valori della variabile $tenant, $site e $user ai valori attuali dal proprio ambiente e quindi incollarli nella finestra di SharePoint Online Management Shell.

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>Aggiungere un utente ad altri gruppi di amministratori della raccolta siti

In questa attività, il comando **Add-SPOUser** utilizzeremo per aggiungere un utente a un gruppo di SharePoint in una raccolta siti. Di seguito è illustrato l'aspetto la sintassi:

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

Ad esempio, verrà quindi aggiunto Glen Rife (glenr nome utente) al gruppo Controllori nella raccolta siti ContosoTest nel tenant contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Creare un gruppo di raccolta siti

Il comando **Set-SPOSiteGroup** per creare un nuovo gruppo di SharePoint e come aggiungerla alla raccolta siti ContosoTest. Di seguito è illustrato l'aspetto la sintassi:

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
> Qualsiasi stringa con spazi è necessario racchiudere tra virgolette. Proprietà Group, ad esempio di livelli di autorizzazione, possono essere aggiornate in seguito utilizzando il cmdlet **Set-SPOSiteGroup** .

Ad esempio, verrà quindi aggiunto il gruppo Controllori con le autorizzazioni solo visualizzazione per la raccolta siti di prova Contoso nel tenant contoso1:

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Rimuovere gli utenti da un gruppo

In alcuni casi, è necessario rimuovere un utente da un sito o anche da tutti i siti. Forse il dipendente viene spostato da una divisione a altra o lascia l'azienda. È possibile rendere l'operazione più facile per un solo dipendente nell'interfaccia utente, ma non è facile quando si sposta una divisione completa da un sito all’altro.

Utilizzando i file CSV e SharePoint Online Management Shell, si tratta tuttavia semplice e veloce. In questa attività, si utilizzerà Windows PowerShell per rimuovere un utente da un gruppo di sicurezza di raccolta siti. Si verrà quindi utilizzare un file CSV e rimuovere una quantità elevata di utenti di siti diversi. 

È il comando **Remove-SPOUser** verranno utilizzate per rimuovere un singolo utente di Office 365 da un gruppo di raccolta siti solo per visualizzare la sintassi dei comandi. Di seguito è illustrato l'aspetto la sintassi:

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

Ad esempio, rimuovere possiamo Bobby Overby dal gruppo controllori della raccolta siti nella raccolta siti Contoso Test nel tenant contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Supporre di voler rimuovere Bobby da tutti i gruppi di fa parte. Di seguito viene mostrato come fare:

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> Serve solo a vedere come fare. Non bisogna eseguire tale comando a meno che non sia realmente necessario rimuovere un utente da tutti i gruppi, come nel caso in cui l'utente lasci la compagnia.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatizzare la gestione di elenchi di utenti e gruppi di grandi dimensioni

Per aggiungere un numero elevato di account per i siti di SharePoint e concedere autorizzazioni, è possibile utilizzare l'interfaccia di amministrazione di Office 365, i comandi PowerShell singoli o PowerShell un un file CSV. Di queste opzioni, il file CSV è il modo più rapido per automatizzare l'attività.

Il processo di base consiste nel creare un file CSV contenente intestazioni (colonne) che corrispondono ai parametri che è necessario che lo script di Windows PowerShell. È possibile creare facilmente un elenco in Excel e quindi esportarlo come file CSV. È quindi possibile utilizzare uno script di Windows PowerShell per scorrere i record (righe) nel file CSV, aggiungere gli utenti ai gruppi e i gruppi ai siti. 

Ad esempio, creare un file CSV per definire un gruppo di raccolte di siti, gruppi e autorizzazioni. Successivamente, viene creato un file CSV per popolare i gruppi di utenti. Per concludere, viene creato ed eseguito un semplice script Windows PowerShell che crea e popola i gruppi.

Il primo file CSV aggiunge uno o più gruppi a uno o più raccolte di siti e avrà la seguente struttura:

### <a name="header"></a>Intestazione:

```
Site,Group,PermissionLevels
```

### <a name="item"></a>Articolo:

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

Ecco un esempio di file:

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

Il secondo file CSV aggiunge uno o più utenti a uno o più gruppi e avrà la seguente struttura:

### <a name="header"></a>Intestazione:

```
Group,LoginName,Site
```

### <a name="item"></a>Articolo:

```
group,login,https://tenant.sharepoint.com/sites/site
```

Ecco un esempio di file:

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

Per il passaggio successivo, è necessario salvare i due file CSV sul disco. Ecco i comandi che utilizzano entrambi i file CSV e per aggiungere le autorizzazioni e l'appartenenza al gruppo:

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Lo script consente di importare il contenuto del file CSV e utilizza i valori delle colonne (in grassetto) per popolare i parametri dei comandi **New-SPOSiteGroup** e **Add-SPOUser** . In questo esempio viene stiamo risparmiando seguente sull'unità C, ma è possibile salvare desiderata.

Ora, rimuovere un gruppo di utenti per diversi gruppi di siti diversi utilizzando lo stesso file CSV. Ecco il comando:

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Generare report utente

Potrebbe essere necessario ottenere un semplice report per alcuni nuovi siti e visualizzare i rispettivi utenti, il livello di autorizzazione e altre proprietà. Questo è l'aspetto della sintassi:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Questo verrà acquisire i dati per questi tre siti e li scrive un file di testo nell'unità locale. Si noti che il parametro – Append aggiungere nuovo contenuto a un file esistente.

Ad esempio, eseguire un report nei siti ContosoTest, TeamSite01 e Project01 per il tenant Contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Si noti che è stato necessario modificare solo la variabile **$site** . La variabile **$tenant** mantiene il relativo valore tramite tutti i tre esecuzioni del comando.

Tuttavia, cosa succede se si desidera effettuare questa operazione per ogni sito? È possibile eseguirlo senza dover digitare tutti i siti Web utilizzando questo comando:

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

In questo report è piuttosto semplice ed è possibile aggiungere ulteriori codice per creare più specifiche report o un report che includono informazioni più dettagliate. Tuttavia, questa deve avere un'idea di come utilizzare SharePoint Online Management Shell per gestire gli utenti nell'ambiente di SharePoint Online.
   
## <a name="see-also"></a>Vedere anche

[Connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Gestire SharePoint Online con PowerShell di Office 365](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

