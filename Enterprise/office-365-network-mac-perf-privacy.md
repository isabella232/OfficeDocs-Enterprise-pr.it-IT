---
title: Privacy e condizioni di utilizzo di Office 365 Network Insights (Preview)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Privacy e condizioni di utilizzo di Office 365 Network Insights (Preview)
ms.openlocfilehash: 9c47149ebef1e8b1614b26ad90fb60335783cfd0
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "42891495"
---
# <a name="office-365-network-insights-privacy-and-terms-of-use-preview"></a>Privacy e condizioni di utilizzo di Office 365 Network Insights (Preview)

L'interfaccia di amministrazione di Microsoft 365 ora Mostra **informazioni dettagliate sulla rete e sulle prestazioni**, che sono raccolte dal tenant di Office 365 e disponibili per la visualizzazione solo da parte di utenti amministrativi del tenant. La connettività di rete organizzativa è progettata per ogni percorso di Office tramite una posizione di uscita di rete su Internet. La connettività client di Office 365 utilizza tale route e quindi su Internet per i server front door di Microsoft Service. Identificare le posizioni di Office è fondamentale per poter mostrare queste informazioni sulla rete.

## <a name="location-in-network-measurements"></a>Posizione in misure di rete

L'amministratore di un'organizzazione può optare per la posizione per l'inclusione nelle misure di rete utilizzate da questa funzionalità. In questo modo, viene abilitata l'individuazione automatica della città in cui si trova ogni ufficio. Le informazioni sulla posizione non sono precise e sono offuscate a 300m e categorizzate in base alla città. Al momento in cui la posizione viene acquisita su un dispositivo Windows, viene visualizzata un'icona di **posizione in uso** nel vassoio degli strumenti e gli amministratori possono decidere di notificare gli utenti. Con questa elaborazione, la posizione viene trattata come la posizione dell'ufficio dell'organizzazione e non la posizione di un utente o di un dispositivo. È possibile visualizzare le informazioni di rete in queste città ubicate nell'ufficio individuate. Se si desidera una maggiore accuratezza dei suggerimenti, un amministratore può immettere indirizzi di posizione specifici di Office e le informazioni sulla rete verranno aggregate a quelle. I percorsi di Office non possono essere aggregati più strettamente di 300 metri.

## <a name="location-in-the-microsoft-365-admin-center"></a>Posizione nell'interfaccia di amministrazione di Microsoft 365

Nell'interfaccia di amministrazione di Microsoft 365, i controlli Bing Map vengono utilizzati per mostrare dove sono ubicate le posizioni dell'organizzazione e per visualizzare la topologia perimetrale di rete per una posizione di Office selezionata. Quando un amministratore aggiunge informazioni specifiche sull'indirizzo per i percorsi di Office, Bing Maps viene utilizzato anche per suggerire gli indirizzi per semplificare l'immissione dei dati.

## <a name="terms-of-use"></a>Condizioni per l'utilizzo

Qualsiasi contenuto fornito tramite Bing Maps, inclusi i geocodici, può essere utilizzato solo all'interno del prodotto tramite il quale viene fornito il contenuto. L'utilizzo da parte del cliente della caratteristica dei servizi di interfaccia di amministrazione di M365, Powered by Bing Maps, è regolato dalle _condizioni di utilizzo dell'utente finale di Bing Maps_ disponibili all'indirizzo <https://go.microsoft.com/?linkid=9710837> e dall' _informativa sulla privacy di Microsoft_ disponibile all'indirizzo<https://go.microsoft.com/fwlink/?LinkID=248686.>

Questa funzionalità, fornita tramite Bing Maps, è supportata anche da **qui Technologies**. La modalità di utilizzo dei servizi di localizzazione forniti da qui Technologies è regolata dai _termini del servizio qui Technologies_ disponibili all'indirizzo <https://legal.here.com/en-gb/terms>.
