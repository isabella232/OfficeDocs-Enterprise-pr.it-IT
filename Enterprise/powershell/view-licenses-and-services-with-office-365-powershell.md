---
title: Visualizzare le licenze e i servizi con PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
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
description: Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sui piani di licenza, i servizi e le licenze disponibili nell'organizzazione di Office 365.
ms.openlocfilehash: 18444f76f312c75bc95645d17c48c996f1a3bfc7
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782036"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Visualizzare le licenze e i servizi con PowerShell di Office 365

**Riepilogo:** Viene illustrato come utilizzare Office 365 PowerShell per visualizzare informazioni sui piani di licenza, i servizi e le licenze disponibili nell'organizzazione di Office 365.
  
Ogni sottoscrizione di Office 365 è costituita dai seguenti elementi:

- **Piani di gestione delle licenze** Questi sono noti anche come piani di licenza o piani di Office 365. I piani di gestione delle licenze definiscono i servizi di Office 365 che sono disponibili per gli utenti. La sottoscrizione di Office 365 potrebbe contenere più piani di gestione delle licenze. Un esempio di piano di gestione delle licenze sarebbe Office 365 Enterprise E3.
    
- **Servizi offerti** Questi sono noti anche come piani di servizio. I servizi sono i prodotti, le caratteristiche e le funzionalità di Office 365 disponibili in ogni piano di licenze, ad esempio Exchange Online e Office Professional Plus. Gli utenti possono disporre di più licenze tramite diversi piani di licenza che garantiscono l'accesso ai diversi servizi.
    
- **Licenze** Ogni piano di gestione delle licenze contiene il numero di licenze acquistate. Assegnare licenze agli utenti in modo che possano usare i servizi di Office 365 definiti dal piano di gestione delle licenze. Ogni account utente richiede almeno una licenza da un piano di gestione delle licenze, in modo che possano accedere a Office 365 e utilizzare i servizi.
    
È possibile utilizzare Office 365 PowerShell per visualizzare i dettagli sui piani di licenza, le licenze e i servizi disponibili nella propria organizzazione di Office 365. Per ulteriori informazioni sui prodotti, le caratteristiche e i servizi disponibili in diverse sottoscrizioni di Office 365, vedere [office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usare il modulo di Azure Active Directory PowerShell per Graph

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Per visualizzare informazioni di riepilogo sui piani di gestione delle licenze e sulle licenze disponibili per ogni piano, eseguire il comando riportato di seguito:
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

I risultati contengono le seguenti informazioni:
  
- **SkuPartNumber:** Visualizza i piani di gestione delle licenze disponibili per l'organizzazione. Ad esempio, `ENTERPRISEPACK` è il nome del piano di licenza per Office 365 Enterprise E3.
    
- **Attivato:** Il numero di licenze acquistate per uno specifico piano di gestione delle licenze.
    
- **ConsumedUnits:** Il numero di licenze assegnate agli utenti da uno specifico piano di gestione delle licenze.
    
Per visualizzare i dettagli relativi ai servizi di Office 365 disponibili in tutti i piani di licenza, è necessario innanzitutto visualizzare un elenco dei piani di licenza.

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

Successivamente, archiviare le informazioni relative ai piani di licenza in una variabile.

````
$licenses = Get-AzureADSubscribedSku
````

Successivamente, visualizzare i servizi in un piano di licenza specifico.

````
$licenses[<index>].ServicePlans
````

\<index> è un valore integer che specifica il numero di riga del piano di licenza dalla visualizzazione del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando (-1).

Ad esempio, se la visualizzazione del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando è la seguente:

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

Successivamente, il comando per visualizzare i servizi per il piano di licenza di ENTERPRISEPREMIUM è il seguente:

````
$licenses[2].ServicePlans
````

ENTERPRISEPREMIUM è la terza riga. Pertanto, il valore di indice è (3-1) oppure 2.

Per un elenco completo dei piani di licenza (noti anche come nomi di prodotto), per i piani di servizio inclusi e per i nomi descrittivi corrispondenti, vedere [nomi di prodotti e identificatori di piani di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell

Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Uno script PowerShell è disponibile per rendere automatiche le procedure descritte in questo argomento. Nello specifico, lo script consente di visualizzare e disabilitare i servizi nella propria organizzazione di Office 365, tra cui Sway. Per ulteriori informazioni, vedere [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Per visualizzare informazioni di riepilogo sui piani di gestione delle licenze e sulle licenze disponibili per ogni piano, eseguire il comando riportato di seguito:
  
```
Get-MsolAccountSku
```

I risultati contengono le seguenti informazioni:
  
- **AccountSkuId:** Visualizzare i piani di gestione delle licenze disponibili per l'organizzazione utilizzando `<CompanyName>:<LicensingPlan>`la sintassi.  _<CompanyName>_ è il valore specificato quando si è registrato in Office 365 ed è univoco per l'organizzazione. Il _<LicensingPlan>_ valore è lo stesso per tutti. Ad esempio, nel valore `litwareinc:ENTERPRISEPACK`, il nome della società è `litwareinc`e il nome `ENTERPRISEPACK`del piano di gestione delle licenze, che è il nome di sistema per Office 365 Enterprise E3.
    
- **ActiveUnits:** Il numero di licenze acquistate per uno specifico piano di gestione delle licenze.
    
- **WarningUnits:** Il numero di licenze in un piano di gestione delle licenze che non sono state rinnovate e che scadranno dopo il periodo di tolleranza di 30 giorni.
    
- **ConsumedUnits:** Il numero di licenze assegnate agli utenti da uno specifico piano di gestione delle licenze.
    
Per visualizzare i dettagli relativi ai servizi di Office 365 disponibili in tutti i piani di licenza, eseguire il comando riportato di seguito:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Nella tabella seguente vengono illustrati i piani di servizio di Office 365 e i relativi nomi descrittivi per i servizi più comuni. L'elenco dei piani di servizio degli utenti potrebbe essere diverso. 
  
|**Piano di servizio**|**Descrizione**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online, piano 2  <br/> |
   
Per un elenco completo dei piani di licenza (noti anche come nomi di prodotto), per i piani di servizio inclusi e per i nomi descrittivi corrispondenti, vedere [nomi di prodotti e identificatori di piani di servizio per la gestione delle licenze](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Per visualizzare i dettagli sui servizi di Office 365 disponibili in uno specifico piano di gestione delle licenze, utilizzare la seguente sintassi.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

In questo esempio vengono illustrati i servizi di Office 365 disponibili nel piano di gestione delle licenze litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>Nuovo utente di Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Vedere anche


[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
  
[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
