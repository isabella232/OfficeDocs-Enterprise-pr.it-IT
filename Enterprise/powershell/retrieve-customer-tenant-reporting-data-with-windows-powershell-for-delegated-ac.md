---
title: Recuperare i dati di report dei tenant dei clienti con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Riepilogo: utilizzare Windows PowerShell remoto per Microsoft Exchange Online per recuperare i report da tenant dei clienti individuali.'
ms.openlocfilehash: d764f34b89ee55fd7015f01c0c48446fc73a6ac0
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
ms.locfileid: "17114665"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Recuperare i dati di report dei tenant dei clienti con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)

 **Sintesi:** Utilizzare Windows PowerShell remoto per Microsoft Exchange Online per recuperare i report da tenant dei clienti individuali.
  
Per i Partner di Syndication e Cloud Solution Provider (CSP) è possibile accedere ai dati dei report dei tenant dei clienti direttamente tramite Windows PowerShell remoto per Exchange Online PowerShell. Ciò consente ai partner di raccogliere e salvare i dati di report, per poi eseguire operazioni su di essi. Dopo avere aperto una connessione remota, il recupero dei dati di report relativi al tenancy di un cliente è identico all'esecuzione di qualsiasi cmdlet per il tenancy di un cliente.
  
In questo articolo, viene utilizzato Windows PowerShell remoto per Exchange Online per connettersi al tenancy di un singolo cliente e recuperare un report. Per impostazione predefinita, Windows PowerShell non supporta l'aggregazione dei dati di report dai tenancy di più clienti. I report recuperati con questa procedura sono solo per il  _DelegatedOrg_ al quale ci si connette.
  
Se si desidera recuperare un singolo report per i tenancy di tutti i clienti, è disponibile uno script di esempio in [Aggregare i dati di report dei clienti tramite Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .
  
## <a name="before-you-begin"></a>Prima di iniziare

- È necessario connettersi al tenant Exchange Online tramite Windows PowerShell remoto. Per istruzioni, vedere [Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Eseguire il cmdlet di esempio Get-StaleMailboxReport

Dopo avere aperto una sessione remota in Exchange Online, eseguire questo comando per recuperare il cmdlet **Get-StaleMailboxReport** per l'intervallo di date compreso tra il 25/03/2015 e il 31/03/2015.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Sono disponibili molti altri cmdlet di report per Exchange Online, Lync Online e SharePoint Online, e altri per il controllo dei messaggi. Per ulteriori informazioni sui cmdlet di report disponibili e sul servizio Web per la creazione di report di Office 365, vedere gli argomenti riportati nella sezione seguente.
  
## <a name="see-also"></a>Vedere anche

#### 

[Servizio Web per la creazione di report di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlet per la creazione di report in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[Guida per partner](https://go.microsoft.com/fwlink/p/?LinkID=533477)

