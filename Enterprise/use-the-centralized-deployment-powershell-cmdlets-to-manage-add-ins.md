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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilizzare i cmdlet di PowerShell per la distribuzione centralizzata per facilitare la distribuzione e la gestione dei componenti aggiuntivi di Office per l'organizzazione di Office 365.
ms.openlocfilehash: 72f7ad69f1154c65ee5f6bd608770461ae775257
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030861"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Usare i cmdlet di PowerShell della distribuzione centralizzata per gestire i componenti aggiuntivi

In qualità di Microsoft 365 Global o amministratore di Exchange, è possibile distribuire i componenti aggiuntivi di Office agli utenti tramite la caratteristica di distribuzione centralizzata (vedere [Deploy Office Add-ins in the Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Oltre a distribuire i componenti aggiuntivi di Office tramite l'interfaccia di amministrazione di Microsoft 365, è anche possibile utilizzare Microsoft PowerShell. Installare il [modulo di distribuzione del componente aggiuntivo centralizzato di O365 per Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

Dopo aver scaricato il modulo, aprire una normale finestra di Windows PowerShell ed eseguire il cmdlet seguente:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>Connettersi utilizzando le credenziali di amministratore

Prima di poter utilizzare i cmdlet di distribuzione centralizzata, è necessario eseguire l'accesso.
  
1. Avviare PowerShell.
    
2. Connettersi a PowerShell mediante le credenziali di amministratore della società. Eseguire il cmdlet seguente.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. Nella pagina **Immetti le credenziali** , immettere le credenziali di amministratore globale di Office 365. In alternativa, è possibile immettere le credenziali direttamente nel cmdlet. 
    
    Eseguire il cmdlet seguente specificando le credenziali di amministratore dell'azienda come oggetto PSCredential.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Per ulteriori informazioni sull'utilizzo di PowerShell, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Caricare un manifesto del componente aggiuntivo

Eseguire il cmdlet **New-organizzazionecomponenti-in** per caricare un manifesto del componente aggiuntivo da un percorso, che può essere un percorso o un URL di file. Nell'esempio seguente viene illustrato un percorso di file per il valore del parametro _ManifestPath_ . 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

È inoltre possibile eseguire il cmdlet **New-organizzazionecomponenti-in** per caricare un componente aggiuntivo e assegnarlo direttamente agli utenti o ai gruppi tramite il parametro _Members_ , come illustrato nell'esempio seguente. Separare gli indirizzi di posta elettronica dei membri con una virgola. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Caricare un componente aggiuntivo da Office Store

Eseguire il cmdlet **New-OrganizationAddIn** per caricare un manifesto da Office Store.
  
Nell'esempio seguente, il cmdlet **New-OrganizationAddIn** consente di specificare il AssetID per un componente aggiuntivo per un sito e un mercato del contenuto degli Stati Uniti.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Per determinare il valore per il parametro _AssetID_ , è possibile copiarlo dall'URL della pagina Web di Office Store per il componente aggiuntivo. AssetIds inizia sempre con "WA" seguito da un numero. Nell'esempio precedente, ad esempio, l'origine per il valore AssetId di WA104099688 è l'URL della pagina Web di Office Store per il componente aggiuntivo: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
I valori per il parametro _locale_ e per il parametro _ContentMarket_ sono identici e indicano il paese o l'area geografica in cui si sta tentando di installare il componente aggiuntivo. Il formato è en-US, fr-FR. e così via. 
  
> [!NOTE]
> I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Ottenere informazioni dettagliate su un componente aggiuntivo

Eseguire il cmdlet **Get-OrganizationAddIn** come illustrato di seguito per ottenere informazioni dettagliate su tutti i componenti aggiuntivi caricati nel tenant, incluso un ID prodotto del componente aggiuntivo.
  
```powershell
Get-OrganizationAddIn
```

Eseguire il cmdlet **Get-OrganizationAddIn** con un valore per il parametro _ProductID_ per specificare il componente aggiuntivo di cui si desidera recuperare i dettagli. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Per ottenere informazioni complete su tutti i componenti aggiuntivi più gli utenti e i gruppi assegnati, eseguire il piping dell'output del cmdlet **Get-OrganizationAddIn** al cmdlet Format-List, come illustrato nell'esempio seguente.
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Attivazione o disattivazione di un componente aggiuntivo

Per disattivare un componente aggiuntivo in modo che gli utenti e i gruppi a esso assegnati non avranno più accesso, eseguire il cmdlet **set-OrganizationAddIn** con il parametro _ProductID_ e il parametro _Enabled_ impostato su `$false`, come illustrato nell'esempio seguente.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Per attivare di nuovo un componente aggiuntivo, eseguire lo stesso cmdlet con il parametro _Enabled_ impostato su `$true`.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Aggiungere o rimuovere utenti da un componente aggiuntivo

Per aggiungere utenti e gruppi a un componente aggiuntivo specifico, eseguire il cmdlet **set-OrganizationAddInAssignments** con i parametri _ProductID_, _Add_e _Members_ . Separare gli indirizzi di posta elettronica dei membri con una virgola. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Per rimuovere utenti e gruppi, eseguire lo stesso cmdlet utilizzando il parametro _Remove_ . 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Per assegnare un componente aggiuntivo a tutti gli utenti nel tenant, eseguire lo stesso cmdlet utilizzando il parametro _AssignToEveryone_ con il valore impostato su `$true`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Per non assegnare un componente aggiuntivo a tutti e ripristinare gli utenti e i gruppi precedentemente assegnati, è possibile eseguire lo stesso cmdlet e disattivare il parametro _AssignToEveryone_ impostando il relativo valore su `$false`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Aggiornare un componente aggiuntivo

Per aggiornare un componente aggiuntivo da un manifesto, eseguire il cmdlet **set-OrganizationAddIn** con i parametri _ProductID_, _ManifestPath_e _locale_ , come illustrato nell'esempio seguente. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store. 
  
## <a name="delete-an-add-in"></a>Eliminare un componente aggiuntivo

Per eliminare un componente aggiuntivo, eseguire il cmdlet **Remove-OrganizationAddIn** con il parametro _ProductID_ , come illustrato nell'esempio seguente. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a>Personalizzare i componenti aggiuntivi di Microsoft Store per l'organizzazione

È necessario personalizzare il componente aggiuntivo prima di distribuirlo nell'organizzazione. I componenti aggiuntivi precedenti alla versione 1,1 non sono supportati da questa funzionalità. 

È consigliabile distribuire innanzitutto un componente aggiuntivo personalizzato per assicurarsi che funzioni come previsto prima di distribuirlo all'intera organizzazione.

Tenere presente anche le restrizioni seguenti:
- Tutti gli URL devono essere assoluti (Includi http o HTTPS) e validi.
- *DisplayName* non deve superare 125 caratteri 
- *DisplayName*, *Resources* and *AppDomains* non deve includere i caratteri seguenti: 
 
    - \<
    -  \>
    -  ;
    -  =   

Se si desidera personalizzare un componente aggiuntivo distribuito, è necessario disinstallarlo nell'interfaccia di amministrazione e vedere [rimuovere un componente aggiuntivo dalla cache locale](#remove-an-add-in-from-local-cache) per i passaggi da rimuovere da ogni computer in cui è stata distribuita.

Per personalizzare un componente aggiuntivo, eseguire il cmdlet **set-OrganizationAddInOverrides** con il *ProductID* come parametro, seguito dal tag che si desidera sovrascrivere e dal nuovo valore. Per informazioni su come ottenere il *ProductID* , vedere [ottenere i dettagli di un componente aggiuntivo](#get-details-of-an-add-in) in questo articolo. Ad esempio:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
Per personalizzare più tag per un componente aggiuntivo, aggiungere tali tag alla riga di comando:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> È necessario applicare più tag personalizzati a un componente aggiuntivo come un comando. Se si personalizzano i tag uno alla volta, verrà applicata solo l'ultima personalizzazione. Inoltre, se si personalizza un tag per errore, è necessario rimuovere tutte le personalizzazioni e ricominciare.

### <a name="tags-you-can-customize"></a>Tag che è possibile personalizzare

| Tag                  | Descrizione          |
| :------------------- | :------------------- |
| \<> di IconURL   </br>| URL dell'immagine utilizzata come icona del componente aggiuntivo (nell'interfaccia di amministrazione). </br> |
| \<> DisplayName| Il titolo del componente aggiuntivo (nell'interfaccia di amministrazione).|
| \<> host| Elenco delle app che supportano il componente aggiuntivo.|
| \<> di SourceLocation | URL di origine a cui si connette il componente aggiuntivo.| 
| \<> AppDomain | Un elenco di domini in cui il componente aggiuntivo è in grado di connettersi. | 
| \<> di SupportURL| URL che gli utenti possono utilizzare per accedere alla guida e al supporto tecnico. | 
| \<> risorse  | Questo tag contiene una serie di elementi, inclusi titoli, descrizioni comandi e icone di dimensioni diverse.| 
|
### <a name="customize-resources-tag"></a>Personalizza Tag risorse

Qualsiasi elemento del <Resources> tag del manifesto può essere personalizzato in modo dinamico. Prima di tutto, è necessario controllare il manifesto per individuare l'ID elemento a cui assegnare un nuovo valore. Il <Resources> tag è simile al seguente:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In questo caso, l'ID elemento dell'immagine è "img16icon" e il valore associato è "http:<i></i>//site. <i> </i>com/img. jpg ".

Dopo aver identificato gli elementi che si desidera personalizzare, utilizzare il seguente comando in PowerShell per assegnare nuovi valori agli elementi:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

È possibile personalizzare il numero di elementi con il comando che è necessario.

### <a name="remove-customization-from-an-add-in"></a>Rimuovere la personalizzazione da un componente aggiuntivo

L'unica opzione attualmente disponibile per l'eliminazione delle personalizzazioni consiste nell'eliminarle tutte contemporaneamente:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a>Visualizzare le personalizzazioni del componente aggiuntivo

Per visualizzare un elenco delle personalizzazioni applicate, eseguire il cmdlet **Get-OrganizationAddInOverrides** . Se viene eseguito **Get-OrganizationAddInOverrides** senza un *ProductID* , viene restituito un elenco di tutti i componenti aggiuntivi con sostituzioni applicate.  

```powershell
Get-OrganizationAddInOverrides 
```
Se ProductId è specificato, viene restituito un elenco di sostituzioni applicato al componente aggiuntivo. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a>Rimuovere un componente aggiuntivo dalla cache locale

Se è stato distribuito un componente aggiuntivo, è necessario rimuoverlo dalla cache in ogni computer prima che possa essere personalizzato. Per Remive un componente aggiuntivo dalla cache:

1. Passare alla cartella "utenti" in C:\ 
1. Passare alla cartella utente
1. Passare a AppData\Local\Microsoft\Office e selezionare la cartella associata alla versione di Office
1. Nella cartella *WEF* eliminare la cartella *manifests* .

## <a name="get-detailed-help-for-each-cmdlet"></a>Ottenere informazioni dettagliate su ogni cmdlet

È possibile esaminare la guida dettagliata per ogni cmdlet utilizzando il cmdlet Get-Help. Ad esempio, il cmdlet seguente fornisce informazioni dettagliate sul cmdlet Remove-OrganizationAddIn.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


