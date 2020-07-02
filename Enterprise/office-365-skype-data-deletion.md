---
title: Eliminazione dei dati di Office 365 Skype for business
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Spiegazione dell'eliminazione dei dati in Skype for business.
ms.openlocfilehash: 7c94c5d1ddfb5a8056e139d664627dd1e7bed0de
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997796"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a>Eliminazione dei dati di Skype for business in Office 365

Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings. The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.

All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users. There is no direct control of archiving settings from within the Skype for Business admin center.

I seguenti tipi di contenuto non vengono archiviati in Skype for business:

- Trasferimenti di file peer-to-peer
- Audio e video per conferenze e messaggi istantanei peer-to-peer
- Applicazioni condivise per conferenze e messaggi immediati peer-to-peer
- Annotazioni di conferenza 

## <a name="meeting-content-retention"></a>Conservazione del contenuto della riunione

I clienti che utilizzano Skype for business possono caricare contenuti in una riunione di Skype for business come allegati, ad esempio presentazioni di PowerPoint, file OneNote e altri file. Il periodo di conservazione del contenuto caricato durante una riunione è il seguente:

- La riunione-contenuto **una tantum** viene conservata per 15 giorni a partire da quando l'ultima persona lascia la riunione.
- Il contenuto di **riunioni ricorrenti** viene conservato per 15 giorni dopo che l'ultima persona ha lasciato l'ultima sessione della riunione. Se un utente accede alla stessa sessione della riunione prima della scadenza dei 15 giorni, il tempo di conservazione viene reimpostato. Si supponga, ad esempio, che venga pianificata una riunione di Skype for business su base settimanale per un anno e che un file venga caricato alla riunione durante la prima istanza. Se almeno una persona entra a far parte della sessione di riunione ogni settimana, il file viene conservato nei server Skype for business online per tutto l'anno più 15 giorni dopo che l'ultima persona ha lasciato l'ultima riunione della serie.
- **Meet Now meeting** -Content viene conservato per 8 ore dopo l'ora di fine della riunione.

> [!NOTE]
> Se un utente non è autorizzato o disabilitato (ad esempio, se **msRTCSIP-UserEnabled** è impostato su *false*) e viene quindi riconcesso in licenza o riabilitato, il contenuto della riunione non viene mantenuto.

## <a name="meeting-expiration"></a>Scadenza della riunione

Gli utenti possono accedere a una riunione specifica dopo che è terminata in base ai seguenti periodi di scadenza:

- La riunione di **una tantum** scade 14 giorni dopo l'ora di fine della riunione pianificata.
- **Riunione ricorrente con data di fine** -la riunione scade 14 giorni dopo l'ora di fine pianificata dell'ultima riunione.
- **Meet Now meeting** -meeting scade dopo 8 ore.

## <a name="whiteboard-collaboration"></a>Collaborazione lavagna

Le annotazioni effettuate sulle lavagne verranno visualizzate da tutti i partecipanti. Quando si salva una lavagna, la lavagna e tutte le annotazioni verranno archiviate su un server Skype for business e verranno conservate sul server in base ai criteri di scadenza del contenuto delle riunioni impostati dall'amministratore.

## <a name="audio-test-service"></a>Servizio di test audio

Durante la chiamata del servizio di test audio viene registrato un campione breve (circa 5 secondi) della voce. Il campione vocale viene utilizzato dall'utente per verificare e/o verificare la qualità del suono della chiamata Skype for business in base alla qualità della registrazione. Quando viene terminata la chiamata al servizio di test audio, viene eliminato l'esempio di voce.

## <a name="persistent-group-chat"></a>Chat di gruppo persistente

Persistent Group Chat archivia il contenuto delle conversazioni di Group Chat. Se abilitato, l'amministratore può controllare il periodo di conservazione, il server in cui sono archiviate le informazioni, se la cronologia della chat di gruppo viene archiviata per la conformità o altri scopi e gestire/modificare le proprietà in una chat room. Gli utenti con ruoli diversi hanno accesso diverso ai dati permanenti, come indicato di seguito:

- Gli amministratori possono eliminare i contenuti meno recenti (ad esempio, il contenuto inserito prima di una determinata data) da qualsiasi chat room per evitare che le dimensioni del database crescano notevolmente. In alternativa, è possibile rimuovere o sostituire i messaggi considerati inappropriati per una determinata chat room (o considerati inadatti).
- Gli utenti finali, compresi gli autori dei messaggi, non possono eliminare il contenuto da una chat room.
- I responsabili della chat room possono disabilitare le sale ma non possono eliminare le sale. Solo gli amministratori possono eliminare una chat room dopo che è stata creata.