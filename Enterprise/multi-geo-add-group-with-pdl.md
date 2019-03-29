---
title: Creare un gruppo di Office 365 con una posizione preferita per i dati specifica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come creare un gruppo di Office 365 con una posizione preferita per i dati specifica in un ambiente multi-geografico.
ms.openlocfilehash: a46a34d9fd5be9b3acda5ee3859f4eed08797b7c
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934026"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>Creare un gruppo di Office 365 con una posizione preferita per i dati specifica

Quando gli utenti in un ambiente multi-geografico creano un gruppo di Office 365, la posizione preferita per i dati del gruppo viene impostata automaticamente su quella dell'utente. Se è necessario creare un gruppo con una posizione preferita per i dati specifica, è possibile usare il cmdlet New-UnifiedGroup di Microsoft PowerShell per Exchange Online. Quando si esegue questa operazione, il provisioning della cassetta postale del gruppo e del sito di SharePoint associato al gruppo verrà effettuato nella posizione preferita per i dati specifica.

Per eseguire questa operazione, è necessario essere un amministratore globale o un amministratore di SharePoint Online o di Exchange Online.

Per creare un gruppo di Office 365 con la posizione preferita per i dati specifica, connettersi a PowerShell per Exchange Online e passare il parametro *MailBoxRegion -* con il codice della posizione geografica.

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