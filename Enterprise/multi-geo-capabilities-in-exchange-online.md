---
title: Exchange Multi-Geo
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Informazioni sulle funzionalità multi-Geo in Exchange Online.
ms.openlocfilehash: 70db45bb7626c49a2c9cd6ec827bff6ca16d4673
ms.sourcegitcommit: 5e85536a6f53262136acfaac640f5d109a65f643
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/10/2019
ms.locfileid: "31765068"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Funzionalità Multi-Geo in Exchange Online

In un ambiente multi-geografico, è possibile selezionare il percorso del contenuto delle cassette postali di Exchange Online (dati a riposo) in base ai singoli utenti.

È possibile inserire le cassette postali nelle posizioni geografiche satellitari per:

- Creazione di una nuova cassetta postale di Exchange Online direttamente in una posizione geografica satellitare.

- Spostamento di una cassetta postale di Exchange Online esistente in una posizione geografica satellite modificando la posizione dei dati preferita dell'utente.

- Onboarding di una cassetta postale da un'organizzazione di Exchange locale direttamente in una posizione geografica satellitare.

## <a name="mailbox-placement-and-moves"></a>Posizionamento e spostamenti delle cassette postali

Dopo aver completato la procedura di configurazione multi-Geo prerequisita, Exchange Online onorerà l'attributo **PreferredDataLocation** per gli oggetti utente in Azure ad.

Exchange Online Sincronizza la proprietà **PreferredDataLocation** da Azure ad nella proprietà **MailboxRegion** nel servizio directory di Exchange Online. Il valore di **MailboxRegion** determina la posizione geografica in cui verranno posizionate le cassette postali degli utenti e le cassette postali di archiviazione associate. Non è possibile configurare la cassetta postale principale e le cassette postali di archiviazione di un utente per risiedere in posizioni geografiche diverse. È possibile configurare una sola posizione geografica per ogni oggetto utente.

- Quando **PreferredDataLocation** viene configurato in un utente con una cassetta postale esistente, la cassetta postale viene inserita in una coda di rilocazione e spostata automaticamente nella posizione geografica specificata.

- Quando **PreferredDataLocation** viene configurato in un utente senza una cassetta postale esistente, quando si esegue il provisioning della cassetta postale, verrà eseguito il provisioning nella posizione geografica specificata.

- Quando **PreferredDataLocation** non è specificato su un utente, quando si esegue il provisioning della cassetta postale, verrà eseguito il provisioning nella posizione geografica centrale.

- Se il codice **PreferredDataLocation** non è corretto (ad esempio, un tipo di Nan anziché Nam), la cassetta postale verrà provisionata nella posizione geografica centrale.

**Note**: multi-Geo Capabilities e Skype for business online riunioni ospitate a livello regionale entrambi utilizzano la proprietà **PreferredDataLocation** su oggetti utente per individuare i servizi. Se si configurano i valori di **PreferredDataLocation** per gli oggetti utente per le riunioni ospitate regionalmente, la cassetta postale per tali utenti verrà automaticamente spostata nella posizione geografica specificata dopo che è stata abilitata la multi-Geo sul tenant di Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitazioni relative alle funzionalità per multi-Geo in Exchange Online

- Le funzionalità di sicurezza e conformità, ad esempio controllo e eDiscovery, disponibili nell'interfaccia di amministrazione di Exchange (EAC) non sono disponibili nelle organizzazioni multi-Geo. Al contrario, è necessario utilizzare il [centro conformità _AMP_ sicurezza di Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) per configurare le funzionalità di sicurezza e conformità.

- Gli utenti di Outlook per Mac potrebbero subire una perdita temporanea di accesso alla cartella dell'archivio online mentre si spostano le cassette postali in una nuova posizione geografica. Questa condizione si verifica quando le cassette postali primarie e di archiviazione dell'utente sono ubicate in posizioni geografiche diverse, perché le cassette postali Cross-Geo possono essere completate in momenti diversi.

- Gli utenti non possono condividere le *cartelle delle cassette postali* tra le posizioni geografiche in Outlook sul Web (in precedenza noto come Outlook Web App o OWA). Ad esempio, un utente nell'Unione europea non è in grado di utilizzare Outlook sul Web per aprire una cartella condivisa in una cassetta postale che si trova negli Stati Uniti. Tuttavia, gli utenti di Outlook sul Web possono aprire *altre cassette postali* in diverse posizioni geografiche utilizzando una finestra del browser separata, come descritto in [aprire la cassetta postale di un'altra persona in una finestra del browser distinta in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

  **Nota**: la condivisione della cartella delle cassette postali tra Geo è supportata in Outlook su Windows.

- Le cartelle pubbliche sono supportate nelle organizzazioni multi-Geo. Tuttavia, le cartelle pubbliche devono rimanere nella posizione geografica centrale. Non è possibile spostare le cartelle pubbliche in posizioni geografiche satellitari.
