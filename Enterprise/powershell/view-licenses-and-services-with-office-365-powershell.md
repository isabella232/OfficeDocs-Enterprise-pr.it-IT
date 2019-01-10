---
title: Visualizzare le licenze e i servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: 8efc123e2820560b4bd8547f4c99bccae242956f
ms.sourcegitcommit: 96313c3c812bae47819f603af995839f4da034c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2019
ms.locfileid: "27786152"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Visualizzare le licenze e i servizi con PowerShell di Office 365

**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sulle licenze piani, servizi e le licenze disponibili nell'organizzazione Office 365.
  
Ogni sottoscrizione a Office 365 sono disponibili i seguenti elementi:

- **Piani di gestione delle licenze** Vi sono detti anche piani di licenza o piani di Office 365. Piani di gestione delle licenze definiscano i servizi di Office 365 disponibili agli utenti. La sottoscrizione a Office 365 può contenere più piani di gestione delle licenze. Un piano di licenze di esempio è E3 Enterprise di Office 365.
    
- **Servizi** Questi sono noti anche come piani di servizio. Servizi sono i prodotti Office 365, caratteristiche e funzionalità disponibili in ogni piano di licenze, ad esempio, Exchange Online e Office Professional Plus. Gli utenti possono avere più di licenze assegnate loro da diversi piani di gestione delle licenze cui concedono l'accesso a diversi servizi.
    
- **Licenze** Ogni piano di licenze contiene il numero di licenze acquistate. Consigliabile assegnare licenze agli utenti in modo che utilizzino i servizi di Office 365 definiti per il piano di licenze. Ogni account utente deve disporre almeno una licenza da un piano di licenze affinché possano accedere a Office 365 e utilizzare i servizi.
    
È possibile utilizzare Office 365 PowerShell per visualizzare i dettagli sui piani di gestione delle licenze disponibili, le licenze e servizi all'interno dell'organizzazione Office 365. Per ulteriori informazioni sui prodotti, funzionalità e i servizi disponibili in diverse sottoscrizioni a Office 365, vedere [Opzioni di pianificazione di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Per visualizzare le informazioni di riepilogo sui piani di licenza correnti e le licenze disponibili per ciascun piano, eseguire il comando seguente:
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

I risultati contengono le seguenti informazioni:
  
- **SkuPartNumber:** Visualizza i piani di gestione delle licenze disponibili per l'organizzazione. Ad esempio `ENTERPRISEPACK` è il nome del sistema per Office 365 Enterprise E3.
    
- **Abilitato:** Numero di licenze acquistate per un piano di licenze specifico.
    
- **ConsumedUnits:** Numero di licenze assegnate agli utenti di un piano di licenze specifico.
    
Per visualizzare informazioni dettagliate sui servizi Office 365 sono disponibili in tutti i piani di licenza, prima di visualizzare un elenco di piani di licenza.

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

Successivamente, memorizzare le informazioni di piani di licenza in una variabile.

````
$licenses = Get-AzureADSubscribedSku
````

Successivamente, visualizzare i servizi in un piano di licenza specifici.

````
$licenses[<index>].ServicePlans
````

\<indice > è un numero intero che specifica il numero della riga del piano di licenza dalla visualizzazione del `Get-AzureADSubscribedSku | Select SkuPartNumber` command meno 1.

Ad esempio, se la visualizzazione del `Get-AzureADSubscribedSku | Select SkuPartNumber` si tratta di comando:

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

Quindi il comando per visualizzare i servizi per il piano di licenza ENTERPRISEPREMIUM è la seguente:

````
$licenses[2].ServicePlans
````

ENTERPRISEPREMIUM è la terza riga. Di conseguenza, il valore di indice è (3 - 1) o 2.

Per un elenco completo dei piani di licenza (noto anche come i nomi dei prodotti), i piani di servizio inclusi e i rispettivi nomi descrittivi corrispondenti, vedere [i nomi di prodotti e gli identificatori di piano di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>È disponibile uno script di PowerShell che consente di automatizzare le procedure descritte in questo argomento. In particolare, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione Office 365, tra cui oscillazione. Per ulteriori informazioni, vedere [disattivare l'accesso a oscillazione con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Per visualizzare le informazioni di riepilogo sui piani di licenza correnti e le licenze disponibili per ciascun piano, eseguire il comando seguente:
  
```
Get-MsolAccountSku
```

I risultati contengono le seguenti informazioni:
  
- **AccountSkuId:** Mostra i piani di gestione delle licenze disponibili per l'organizzazione utilizzando la sintassi `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ è il valore fornito al momento è registrato in Office 365 ed è univoco per l'organizzazione. Il _<LicensingPlan>_ valore è lo stesso per tutti gli utenti. Ad esempio, nel valore `litwareinc:ENTERPRISEPACK`, è il nome della società `litwareinc`e il nome del piano delle licenze `ENTERPRISEPACK`, ovvero il nome del sistema per Office 365 Enterprise E3.
    
- **ActiveUnits:** Numero di licenze acquistate per un piano di licenze specifico.
    
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
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online, piano 2  <br/> |
   
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


[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
