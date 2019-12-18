---
title: Creare un gruppo di Office 365 con una posizione preferita per i dati specifica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come creare un gruppo di Office 365 con una posizione preferita per i dati specifica in un ambiente multi-geografico.
ms.openlocfilehash: 96870923c00cebc247609b67378fd39011077d45
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072378"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>Creare un gruppo di Office 365 con una posizione preferita per i dati specifica

Quando gli utenti in un ambiente multi-geografico creano un gruppo di Office 365, la posizione preferita per i dati del gruppo viene impostata automaticamente su quella dell'utente. Gli amministratori globali di SharePoint ed Exchange possono creare i gruppi in qualsiasi area selezionata. 

Se è necessario creare un gruppo con una posizione preferita per i dati specifica, è possibile usare il cmdlet New-UnifiedGroup di Microsoft PowerShell dall'interfaccia di amministrazione di SharePoint o tramite Exchange Online. Quando si esegue questa operazione, il provisioning della cassetta postale del gruppo e del sito di SharePoint associato al gruppo verrà effettuato nella posizione preferita per i dati specifica.

Per creare un gruppo di Office 365 con la posizione preferita per i dati specifica, passare all'interfaccia di amministrazione di SharePoint nella posizione geografica in cui si vuole creare il sito del gruppo.

Ad esempio:

Se si vuole per creare un sito del gruppo nella posizione in Australia, passare a https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Selezionare **+ Crea**.
2. Seguire la procedura per creare un sito di gruppo.

Il provisioning del sito del gruppo verrà effettuato nella posizione geografica corrispondente all'interfaccia di amministrazione di SharePoint da cui è stata avviata la richiesta di creazione del sito. 

Utilizzo di PowerShell di Exchange 

Connettersi a PowerShell per Exchange Online e passare il parametro *-MailBoxRegion* con il codice della posizione geografica.

Ad esempio: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Screenshot del cmdlet New-UnifiedGroup di PowerShell con la sintassi](media/multi-geo-new-group-with-pdl-powershell.png)

Si noti che il provisioning del sito del gruppo di SharePoint viene effettuato su richiesta. Il provisioning del sito verrà effettuato la prima volta che un membro o un proprietario del gruppo prova ad accedervi.

## <a name="geo-location-codes"></a>Codici di posizione geografica

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>Vedere anche

[Connettersi a PowerShell per Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
