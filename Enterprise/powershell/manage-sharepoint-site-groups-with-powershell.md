---
title: Manage SharePoint Online site groups with Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Riepilogo: utilizzare Office 365 PowerShell per gestire i gruppi di siti di SharePoint Online.'
ms.openlocfilehash: a128823ba125342bd1d209ac8a2bf28334da866d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068862"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Manage SharePoint Online site groups with Office 365 PowerShell

 **Riepilogo:** Utilizzare Office 365 PowerShell per gestire i gruppi di siti di SharePoint Online.
  
Anche se è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365, è anche possibile utilizzare Office 365 PowerShell per gestire i gruppi di siti di SharePoint Online.

## <a name="before-you-begin"></a>Informazioni preliminari

Le procedure descritte in questo articolo richiedono la connessione a SharePoint Online. Per istruzioni, vedere [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Visualizzazione di SharePoint Online con Office 365 PowerShell

L'interfaccia di amministrazione di SharePoint Online offre alcuni metodi di facile utilizzo per la gestione dei gruppi di siti. Ad esempio, si supponga di voler esaminare i gruppi e i membri del gruppo per il `https://litwareinc.sharepoint.com/sites/finance` sito. Di seguito sono riportate le operazioni da eseguire per:

1. Nell'interfaccia di amministrazione di Microsoft 365 fare clic su**siti** **risorse** > e quindi sull'URL del sito.
2. Nella finestra di dialogo raccolta siti fare clic su **Vai a questo sito**.
3. Nella pagina del sito fare clic sull'icona delle **Impostazioni** (nell'angolo in alto a destra della pagina) e quindi fare clic su **Impostazioni sito**:<br/>
![Impostazioni del sito di SharePoint Online](media/spo-site-settings.png)<br/>
4. Nella pagina Impostazioni sito fare clic su **autorizzazioni siti** in **utenti e autorizzazioni**.

Ripetere quindi la procedura per il sito successivo.

Per ottenere un elenco dei gruppi con Office 365 PowerShell, è necessario utilizzare il seguente set di comandi:

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

Esistono due modi per eseguire questo set di comandi nel prompt dei comandi di SharePoint Online Management Shell:

- Copiare i comandi nel blocco note o in un altro editor di testo, modificare il valore della variabile **$SiteUrl** , selezionare i comandi e quindi incollarli nel prompt dei comandi di SharePoint Online Management Shell. Quando si esegue questa operazione, PowerShell si arresterà al **>>** prompt. Premere INVIO per eseguire il comando **foreach** .<br/>
- Copiare i comandi nel blocco note o in un altro editor di testo, modificare il valore della variabile **$SiteUrl** e quindi salvare il file di testo con un nome e l'estensione ps1 in una cartella adatta. Successivamente, eseguire lo script dal prompt dei comandi di SharePoint Online Management Shell specificando il percorso e il nome del file. Ecco un esempio di comando:

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

In entrambi i casi, dovrebbe essere visualizzato qualcosa di simile al seguente:

![Gruppi di siti di SharePoint Online](media/SPO-site-groups.png)

Questi sono tutti i gruppi che sono stati creati per il sito `https://litwareinc.sharepoint.com/sites/finance`e tutti gli utenti assegnati a tali gruppi. I nomi dei gruppi sono in giallo che consentono di separare i nomi dei gruppi dai rispettivi membri.

Un altro esempio è un set di comandi che elenca i gruppi e tutte le appartenenze a gruppi per tutti i siti di SharePoint Online.

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
    
## <a name="see-also"></a>Vedere anche

[Connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Creare siti di SharePoint Online e aggiungere utenti con PowerShell di Office 365](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gestire gli utenti e i gruppi di SharePoint Online con PowerShell di Office 365](manage-sharepoint-users-and-groups-with-powershell.md)

[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

