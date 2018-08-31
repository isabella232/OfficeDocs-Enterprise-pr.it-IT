---
title: Utilizzare i cmdlet PowerShell di distribuzione centralizzato per gestire i componenti aggiuntivi
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilizzare i cmdlet PowerShell di distribuzione centralizzato per distribuire e gestire Office componenti aggiuntivi per l'organizzazione Office 365.
ms.openlocfilehash: 6199ad2d37a11166155b898b52d52304836599d0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541362"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Utilizzare i cmdlet PowerShell di distribuzione centralizzato per gestire i componenti aggiuntivi

Come un amministratore di Office 365, è possibile distribuire i componenti aggiuntivi di Office per gli utenti tramite la distribuzione centralizzata funzionalità (vedere [componenti aggiuntivi di distribuzione di Office in Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Oltre a distribuzione di componenti aggiuntivi a Office tramite l'interfaccia di amministrazione di Office 365, è inoltre possibile utilizzare Microsoft PowerShell. [Scaricare](https://go.microsoft.com/fwlink/p/?linkid=850850) i cmdlet di PowerShell distribuzione centralizzati da Microsoft Download Center. 
    
## <a name="connect-using-your-admin-credentials"></a>Connettersi utilizzando le credenziali di amministrazione

Prima di poter utilizzare i cmdlet di distribuzione centralizzata, è necessario eseguire l'accesso.
  
1. Avviare PowerShell.
    
2. Connettersi a PowerShell utilizzando le credenziali di amministratore di società. Eseguire il cmdlet seguente.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Nella pagina **Immettere le credenziali** , immettere le credenziali di amministratore globale di Office 365. In alternativa, è possibile immettere le credenziali direttamente nel cmdlet. 
    
    Eseguire il cmdlet seguente che specifica la società le credenziali di amministratore come un oggetto PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Per ulteriori informazioni sull'utilizzo di PowerShell, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Caricare un manifesto del componente aggiuntivo

Eseguire il cmdlet New-OrganizationAdd-In per caricare un manifesto del componente aggiuntivo da un percorso, che può essere un percorso o URL. Nell'esempio seguente viene illustrato un percorso di file per il valore del parametro _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

È inoltre possibile eseguire il cmdlet New-OrganizationAdd-In per caricare un componente aggiuntivo e assegnarlo a utenti o gruppi in modo diretto utilizzando il parametro _Members_ , come illustrato nell'esempio seguente. Separare gli indirizzi di posta elettronica dei membri con una virgola. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Caricare un componente aggiuntivo da Office Store

Eseguire il cmdlet New-OrganizationAddIn per caricare un manifesto da Office Store.
  
Nell'esempio seguente, il cmdlet New-OrganizationAddIn specifica AssetId per un componente aggiuntivo per il mercato percorso e il contenuto degli Stati Uniti.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Per determinare il valore del parametro _AssetId_ , è possibile copiarlo dall'URL dell'archivio di Office a pagina Web per il componente aggiuntivo AssetIds iniziano sempre con "WA" seguito da un numero. Nell'esempio precedente, ad esempio, l'origine per il valore AssetId del WA104099688 è l'URL della pagina Web di Office Store per il componente aggiuntivo: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
I valori per il parametro _Locale_ e il parametro _ContentMarket_ sono identici e indicano il paese/area geografica da che si sta tentando di installare il componente aggiuntivo. Il formato è en-US, fr-FR. e così via. 
  
> [!NOTE]
> Componenti aggiuntivi caricati da Office Store verranno aggiornata automaticamente entro pochi giorni dalla data dell'ultimo aggiornamento viene disponibili in Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Ottenere i dettagli di un componente aggiuntivo

Eseguire il cmdlet Get-OrganizationAddIn come indicato di seguito per visualizzare i dettagli di tutti i componenti aggiuntivi caricati tenant, incluso ID del prodotto. di un componente aggiuntivo
  
```
Get-OrganizationAddIn
```

Eseguire il cmdlet Get-OrganizationAddIn con un valore per il parametro _IDProdotto_ per specificare quali componenti aggiuntivi che si desidera recuperare dettagli relativi a. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Per ottenere informazioni dettagliate su tutti i componenti aggiuntivi oltre l'assegnati agli utenti e gruppi, eseguire il piping dell'output del cmdlet Get-OrganizationAddIn al cmdlet Format-List, come illustrato nell'esempio seguente.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Attivare o disattivare un componente aggiuntivo

Per disattivare un componente aggiuntivo in modo che gli utenti e gruppi che sono assegnati a esso non disporrà più accesso, eseguire il cmdlet Set-OrganizationAddIn con il parametro _ProductId_ e il parametro _Enabled_ impostato su `$false`, come illustrato nell'esempio seguente.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Per riattivare un componente aggiuntivo, eseguire il cmdlet stesso con il parametro _Enabled_ impostato su `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Aggiungere o rimuovere utenti dal componente aggiuntivo

Per aggiungere utenti e gruppi a un componente aggiuntivo specifico, eseguire il cmdlet Set-OrganizationAddInAssignments con i parametri _IDProdotto_, _Aggiungi_e _membri_ . Separare gli indirizzi di posta elettronica dei membri con una virgola. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Per rimuovere utenti e gruppi, eseguire il cmdlet stesso utilizzando il parametro _rimuovere_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Per assegnare un componente aggiuntivo a tutti gli utenti del tenant, eseguire il cmdlet stesso utilizzando il parametro _AssignToEveryone_ con il valore impostato su `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Per non assegnare un componente aggiuntivo per tutti gli utenti e ripristinare precedentemente assegnati agli utenti e gruppi, è possibile eseguire il cmdlet stesso e consente di disattivare il parametro _AssignToEveryone_ impostando il valore su `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Aggiornare un componente aggiuntivo

Per aggiornare un componente aggiuntivo da un manifesto, eseguire il cmdlet Set-OrganizationAddIn con _IDProdotto_, _ManifestPath_e parametri _delle impostazioni locali_ , come illustrato nell'esempio seguente. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Componenti aggiuntivi caricati da Office Store verranno aggiornata automaticamente entro pochi giorni dalla data dell'ultimo aggiornamento viene disponibili in Office Store. 
  
## <a name="delete-an-add-in"></a>Elimina un componente aggiuntivo

Per eliminare un componente aggiuntivo, eseguire il cmdlet Remove-OrganizationAddIn con il parametro _ProductId_ , come illustrato nell'esempio seguente. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Ottenere informazioni dettagliate per ogni cmdlet

È possibile esaminare la Guida dettagliata relativi a ciascun cmdlet utilizzando il cmdlet Get-help. Ad esempio, il cmdlet seguente vengono fornite informazioni dettagliate sul cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


