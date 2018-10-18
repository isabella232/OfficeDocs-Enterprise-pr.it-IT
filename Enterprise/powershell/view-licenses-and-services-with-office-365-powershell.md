---
title: Visualizzare le licenze e i servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/17/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sulle licenze piani, servizi e le licenze disponibili nell'organizzazione Office 365.
ms.openlocfilehash: 21dda5bfc1bf1fa975b4a94879435c1842c383ec
ms.sourcegitcommit: 8cacedcba4627042d4bd17f1a94fddcfd87f77b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2018
ms.locfileid: "25601630"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Visualizzare le licenze e i servizi con PowerShell di Office 365

**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sulle licenze piani, servizi e le licenze disponibili nell'organizzazione Office 365.
  
Ogni sottoscrizione a Office 365 sono disponibili i seguenti elementi:

- **Piani di gestione delle licenze** Questi sono noti anche aslicense piani o piani di Office 365. Piani di gestione delle licenze definiscano i servizi di Office 365 disponibili agli utenti. La sottoscrizione a Office 365 può contenere più piani di gestione delle licenze. Un piano di licenze di esempio è E3 Enterprise di Office 365.
    
- **Servizi** Questi sono i piani di servizio noti. Servizi sono i prodotti Office 365, caratteristiche e funzionalità disponibili in ogni piano di licenze, ad esempio, Exchange Online e Office Professional Plus. Gli utenti possono avere più di licenze assegnate loro da diversi piani di gestione delle licenze cui concedono l'accesso a diversi servizi.
    
- **Licenze** Ogni piano di licenze contiene il numero di licenze acquistate. Consigliabile assegnare licenze agli utenti in modo che utilizzino i servizi di Office 365 definiti per il piano di licenze. Ogni account utente deve disporre almeno una licenza da un piano di licenze affinché possano accedere a Office 365 e utilizzare i servizi.
    
È possibile utilizzare Office 365 PowerShell per visualizzare i dettagli sui piani di gestione delle licenze disponibili, le licenze e servizi all'interno dell'organizzazione Office 365. Per ulteriori informazioni sui prodotti, funzionalità e i servizi disponibili in diverse sottoscrizioni a Office 365, vedere [Opzioni di pianificazione di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).

## <a name="before-you-begin"></a>Prima di iniziare

- Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).
    
- È disponibile uno script di PowerShell che consente di automatizzare le procedure descritte in questo argomento. In particolare, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione Office 365, tra cui oscillazione. Per ulteriori informazioni, vedere [disattivare l'accesso a oscillazione con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>Visualizzare informazioni sui piani di gestione delle licenze e sulle licenze disponibili

Per visualizzare le informazioni di riepilogo sui piani di licenza correnti e le licenze disponibili per ciascun piano, eseguire il comando seguente in Office 365 PowerShell:
  
```
Get-MsolAccountSku
```

I risultati contengono le seguenti informazioni:
  
- **AccountSkuId:** Mostra i piani di gestione delle licenze disponibili per l'organizzazione utilizzando la sintassi `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ è il valore fornito al momento è registrato in Office 365 ed è univoco per l'organizzazione. Il _<LicensingPlan>_ valore è lo stesso per tutti gli utenti. Ad esempio, nel valore `litwareinc:ENTERPRISEPACK`, è il nome della società `litwareinc`e il nome del piano delle licenze `ENTERPRISEPACK`, ovvero il nome del sistema per Office 365 Enterprise E3.
    
- **ActiveUnits:** Numero di licenze che hai gli acquisti per un piano di licenze specifico.
    
- **WarningUnits:** Numero di licenze di un piano di licenze che non sono rinnovato e che scadranno dopo il periodo di prova di 30 giorni.
    
- **ConsumedUnits:** Numero di licenze assegnate agli utenti di un piano di licenze specifico.
    
Per visualizzare informazioni dettagliate sui servizi Office 365 sono disponibili in tutti i piani di licenza, eseguire il comando seguente:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Nella tabella seguente vengono illustrati i piani di servizio di Office 365 e i relativi nomi descrittivi per i servizi più comuni. Elenco di piani di servizio potrebbe essere diverso. 
  
|**Piano di servizio**|**Descrizione**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Piano 2  <br/> |
   
Per un elenco completo dei piani di licenza (noto anche come i nomi dei prodotti), i piani di servizio inclusi e i rispettivi nomi descrittivi corrispondenti, vedere [i nomi di prodotti e gli identificatori di piano di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Per visualizzare informazioni dettagliate sui servizi Office 365 sono disponibili in un piano di licenze specifico, utilizzare la sintassi seguente.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

In questo esempio vengono illustrati i servizi di Office 365 che sono disponibili nel piano di licenze litwareinc: enterprisepack (Office 365 Enterprise E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Vedere anche

- [Visualizzare gli utenti con e senza licenza con PowerShell di Office 365](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

