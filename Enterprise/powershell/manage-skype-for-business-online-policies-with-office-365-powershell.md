---
title: Gestire criteri Skype for Business Online con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "Riepilogo: Utilizzare PowerShell di Office 365 per gestire le proprietà dell'account utente di Skype for Business online con i criteri."
ms.openlocfilehash: 51e402922b2a357ef29e9b2628eb25fc252e5437
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031731"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>Gestire criteri Skype for Business Online con PowerShell di Office 365

 **Sintesi:** Utilizzare PowerShell di Office 365 per gestire le proprietà dell'account utente di Skype for Business online con i criteri.
  
Per gestire molte proprietà dell'account utente per Skype for Business online, è necessario specificarle come proprietà dei criteri con PowerShell di Office 365.
  
## <a name="before-you-begin"></a>Prima di iniziare

Utilizzare queste istruzioni per ottenere la configurazione che consenta di eseguire i comandi (ignorare i passaggi già completati):
  
1. Scaricare e installare il [Modulo di Windows PowerShell per Skype for Business Online](https://www.microsoft.com/download/details.aspx?id=39366).
    
2. Aprire il prompt dei comandi Windows PowerShell ed eseguire quanto segue: 
    
```
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

Quando richiesto, immettere il nome e la password dell'account Administrator di Skype for Business online.
    
## <a name="manage-user-account-policies"></a>Gestione dei criteri dell’account utente

Molte proprietà dell'account utente di Skype for Business online sono configurate utilizzando criteri. I criteri consistono in una raccolta di impostazioni che possono essere applicate a uno o più utenti. Per esaminare la configurazione del criterio, è possibile eseguire il comando di esempio riportato per il criterio FederationAndPICDefault.
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Verrà restituito un elemento analogo al seguente:
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

In questo esempio, i valori all'interno di questo criterio determinano le operazioni che possono essere eseguite o non possono essere utilizzate per la comunicazione con gli utenti federati. Ad esempio, la proprietà EnableOutsideAccess deve essere impostata su true affinché un utente sia in grado di comunicare con utenti esterni all'organizzazione. Tenere presente che questa proprietà non viene visualizzata nell'interfaccia di amministrazione di Microsoft 365. Al contrario, la proprietà viene impostata automaticamente su true o su false in base alle altre selezioni apportate. Le altre due proprietà di interesse sono le seguenti:
  
- **EnableFederationAccess** indica se l'utente può comunicare con utenti di domini federati.
    
- **EnablePublicCloudAccess** indica se l'utente può comunicare con gli utenti di Windows Live.
    
Pertanto, non è possibile modificare proprietà correlate alla federazione negli account utente (ad esempio, **Set-CsUser -EnableFederationAccess $True**). Al contrario, a un account viene assegnato un criterio di accesso esterno che dispone dei valori di proprietà desiderati e preconfigurati. Se si desidera che un utente sia in grado di comunicare con gli utenti federati e con gli utenti di Windows Live, è necessario assegnare all'account utente un criterio che consenta questo tipo di comunicazione.
  
Se si desidera sapere se qualche utente è in grado di comunicare con utenti esterni all'organizzazione, è necessario:
  
- Determinare quali criteri di accesso esterno sono stati assegnati all'utente.
    
- Determinare le funzionalità che sono consentite o meno dal criterio.
    
Ad esempio, è possibile utilizzare il comando riportato di seguito:
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Questo comando consente di individuare il criterio assegnato all'utente, quindi di individuare le funzionalità abilitate o disabilitate all'interno del criterio.
  
Per gestire i criteri di Skype for business online con PowerShell, vedere i cmdlet per:

- [Criteri client](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Criteri conferenza](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Criteri per dispositivi mobili](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Criteri di segreteria telefonica online](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Criterio di routing vocale](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Un dial plan di Skype for Business online rappresenta un criterio in tutti i suoi aspetti, con la sola eccezione del nome. Il nome "dial plan" è stato scelto al posto di "criteri di composizione" al fine di essere compatibile con Office Communications Server e con Exchange. 
  
Ad esempio, per esaminare tutti i criteri vocali che possono essere utilizzati, eseguire tale comando:
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> Viene restituito un elenco di tutti i criteri vocali disponibili per l'utente. Tuttavia, tenere presente che non tutti i criteri possono essere assegnati a qualsiasi utente. Ciò si verifica a causa di vari limiti che riguardano le licenze e la posizione geografica. (Il "[percorso di utilizzo](https://msdn.microsoft.com/library/azure/dn194136.aspx)"). Se si desidera conoscere i criteri di accesso esterno e i criteri di conferenza che possono essere assegnati a un utente particolare, utilizzare comandi analoghi ai seguenti: 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

Il parametro ApplicableTo limita i dati restituiti ai criteri che possono essere assegnati a specifici utenti (ad esempio, Alex Darrow). A seconda dei limiti relativi alle licenze o al percorso di utilizzo, potrebbe rappresentare un sottogruppo di tutti i criteri disponibili. 
  
In alcuni casi, le proprietà dei criteri non vengono utilizzate con Office 365, mentre altre possono essere gestite solo dal personale di supporto Microsoft. 
  
Con Skype for Business online, gli utenti devono essere gestiti da un criterio di qualche tipo. Se una proprietà correlata a criteri validi è vuota, significa che l'utente in questione viene gestito da un criterio globale, ovvero un criterio che viene applicato automaticamente a un utente a meno che non venga specificamente assegnato un criterio per utente. Poiché un criterio client per un account utente non è disponibile nell'elenco, viene gestito dal criterio globale. È possibile determinare il criterio client globale con questo comando:
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Vedere anche

#### 

[Gestire Skype for Business Online con PowerShell di Office 365](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)

