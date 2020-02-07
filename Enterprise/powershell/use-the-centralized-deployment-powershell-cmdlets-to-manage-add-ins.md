---
title: Usare i cmdlet di PowerShell della distribuzione centralizzata per gestire i componenti aggiuntivi
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilizzare i cmdlet di PowerShell per la distribuzione centralizzata per facilitare la distribuzione e la gestione dei componenti aggiuntivi di Office per l'organizzazione di Office 365.
ms.openlocfilehash: 586b66ac3632a5d86a63014a50f3c605b1c005e7
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844157"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Usare i cmdlet di PowerShell della distribuzione centralizzata per gestire i componenti aggiuntivi

Come amministratore di Office 365, è possibile distribuire i componenti aggiuntivi di Office agli utenti tramite la caratteristica di distribuzione centralizzata (vedere [gestire la distribuzione dei componenti aggiuntivi di office 365 nell'](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)interfaccia di amministrazione). Oltre a distribuire i componenti aggiuntivi di Office tramite l'interfaccia di amministrazione, è anche possibile utilizzare Microsoft PowerShell. [Scaricare](https://go.microsoft.com/fwlink/p/?linkid=850850) i cmdlet di PowerShell per la distribuzione centralizzata dall'area download Microsoft. 
  
## <a name="what-do-you-want-to-do"></a>Operazione desiderata

[Connettersi utilizzando le credenziali di amministratore](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[Caricare un manifesto del componente aggiuntivo](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Caricare un componente aggiuntivo da Office Store](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[Ottenere informazioni dettagliate su un componente aggiuntivo](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[Attivazione o disattivazione di un componente aggiuntivo](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[Aggiungere o rimuovere utenti da un componente aggiuntivo](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[Aggiornare un componente aggiuntivo](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[Eliminare un componente aggiuntivo](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[Ottenere informazioni dettagliate su ogni cmdlet](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>Connettersi utilizzando le credenziali di amministratore
<a name="BKMK_Connect"> </a>

Prima di poter utilizzare i cmdlet di distribuzione centralizzata, è necessario eseguire l'accesso.
  
1. Avviare PowerShell.
    
2. Connettersi a PowerShell mediante le credenziali di amministratore della società. Eseguire il cmdlet seguente.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Nella pagina **Immetti le credenziali** , immettere le credenziali di amministratore globale di Office 365. In alternativa, è possibile immettere le credenziali direttamente nel cmdlet. 
    
    Eseguire il cmdlet seguente specificando le credenziali di amministratore dell'azienda come oggetto PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Per ulteriori informazioni sull'utilizzo di PowerShell, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Caricare un manifesto del componente aggiuntivo
<a name="BKMK_UploadManifest"> </a>

Eseguire il cmdlet New-Organizzazionecomponenti-in per caricare un manifesto del componente aggiuntivo da un percorso, che può essere un percorso o un URL di file. Nell'esempio seguente viene illustrato un percorso di file per il valore del parametro _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

È inoltre possibile eseguire il cmdlet New-Organizzazionecomponenti-in per caricare un componente aggiuntivo e assegnarlo direttamente agli utenti o ai gruppi tramite il parametro _Members_ , come illustrato nell'esempio seguente. Separare gli indirizzi di posta elettronica dei membri con una virgola. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Caricare un componente aggiuntivo da Office Store
<a name="BKMK_UploadAddin"> </a>

Eseguire il cmdlet New-OrganizationAddIn per caricare un manifesto da Office Store.
  
Nell'esempio seguente, il cmdlet New-OrganizationAddIn consente di specificare il AssetId per un componente aggiuntivo per un sito e un mercato del contenuto degli Stati Uniti.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Per determinare il valore per il parametro _AssetID_ , è possibile copiarlo dall'URL della pagina Web di Office Store per il componente aggiuntivo. AssetIds inizia sempre con "WA" seguito da un numero. Nell'esempio precedente, ad esempio, l'origine per il valore AssetId di WA104099688 è l'URL della pagina Web di Office Store per il componente aggiuntivo: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
I valori per il parametro _locale_ e per il parametro _ContentMarket_ sono identici e indicano il paese o l'area geografica in cui si sta tentando di installare il componente aggiuntivo. Il formato è en-US, fr-FR. e così via. 
  
> [!NOTE]
> I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Ottenere informazioni dettagliate su un componente aggiuntivo
<a name="BKMK_GetDetails"> </a>

Eseguire il cmdlet Get-OrganizationAddIn come illustrato di seguito per ottenere informazioni dettagliate su tutti i componenti aggiuntivi caricati nel tenant, incluso un ID prodotto del componente aggiuntivo.
  
```
Get-OrganizationAddIn
```

Eseguire il cmdlet Get-OrganizationAddIn con un valore per il parametro _ProductID_ per specificare il componente aggiuntivo di cui si desidera recuperare i dettagli. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Per ottenere informazioni complete su tutti i componenti aggiuntivi più gli utenti e i gruppi assegnati, eseguire il piping dell'output del cmdlet Get-OrganizationAddIn al cmdlet Format-List, come illustrato nell'esempio seguente.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Attivazione o disattivazione di un componente aggiuntivo
<a name="BKMK_TurnOnOff"> </a>

Per disattivare un componente aggiuntivo in modo che gli utenti e i gruppi a esso assegnati non avranno più accesso, eseguire il cmdlet Set-OrganizationAddIn con il parametro _ProductID_ e il parametro _Enabled_ impostato su `$false`, come illustrato nell'esempio seguente.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Per attivare di nuovo un componente aggiuntivo, eseguire lo stesso cmdlet con il parametro _Enabled_ impostato su `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Aggiungere o rimuovere utenti da un componente aggiuntivo
<a name="BKMK_AddRemove"> </a>

Per aggiungere utenti e gruppi a un componente aggiuntivo specifico, eseguire il cmdlet Set-OrganizationAddInAssignments con i parametri _ProductID_, _Add_e _Members_ . Separare gli indirizzi di posta elettronica dei membri con una virgola. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Per rimuovere utenti e gruppi, eseguire lo stesso cmdlet utilizzando il parametro _Remove_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Per assegnare un componente aggiuntivo a tutti gli utenti nel tenant, eseguire lo stesso cmdlet utilizzando il parametro _AssignToEveryone_ con il valore impostato su `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Per non assegnare un componente aggiuntivo a tutti e ripristinare gli utenti e i gruppi precedentemente assegnati, è possibile eseguire lo stesso cmdlet e disattivare il parametro _AssignToEveryone_ impostando il relativo valore su `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Aggiornare un componente aggiuntivo
<a name="BKMK_UpdateAddin"> </a>

Per aggiornare un componente aggiuntivo da un manifesto, eseguire il cmdlet Set-OrganizationAddIn con i parametri _ProductID_, _ManifestPath_e _locale_ , come illustrato nell'esempio seguente. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store. 
  
## <a name="delete-an-add-in"></a>Eliminare un componente aggiuntivo
<a name="BKMK_Delete"> </a>

Per eliminare un componente aggiuntivo, eseguire il cmdlet Remove-OrganizationAddIn con il parametro _ProductID_ , come illustrato nell'esempio seguente. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Ottenere informazioni dettagliate su ogni cmdlet
<a name="BKMK_GetHelp"> </a>

È possibile esaminare la guida dettagliata per ogni cmdlet utilizzando il cmdlet Get-Help. Ad esempio, il cmdlet seguente fornisce informazioni dettagliate sul cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


