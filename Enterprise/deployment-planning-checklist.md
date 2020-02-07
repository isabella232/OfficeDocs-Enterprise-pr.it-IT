---
title: Elenco di controllo per la pianificazione della distribuzione di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 5fa4f6ef-35ad-4840-91c1-4834df3df5a0
description: Questo elenco di controllo aiuterà l'organizzazione durante la pianificazione e la preparazione di una migrazione a Office 365.
ms.openlocfilehash: dbd996a21cb98fcf7831ef22b855cc8fcb1af39f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840513"
---
# <a name="deployment-planning-checklist-for-office-365"></a>Elenco di controllo per la pianificazione della distribuzione di Office 365

Quando si sposta un'organizzazione aziendale in Office 365, è importante pianificare esattamente i passaggi da eseguire, quando eseguirli e gli utenti che li eseguono. Questo elenco di controllo aiuterà l'organizzazione durante la pianificazione e la preparazione di una migrazione a Office 365. Le fasi e i passaggi dell'elenco di controllo sono allineati alle linee guida fornite dal [centro di onboarding](https://go.microsoft.com/fwlink/?LinkId=517115). È possibile adattare questo elenco di controllo alle esigenze dell'organizzazione.

## <a name="need-help-with-your-deployment"></a>Serve assistenza per la distribuzione?
È possibile ottenere assistenza per l'installazione di Office 365? È consigliabile utilizzare [FastTrack](https://fasttrack.microsoft.com/office) o i [consulenti per la distribuzione per i servizi di Office 365](deployment-advisors-for-office-365.md).

## <a name="sample-checklist-for-an-office-365-enterprise-deployment"></a>Elenco di controllo di esempio per una distribuzione di Office 365 Enterprise

||||||
|:-----|:-----|:-----|:-----|:-----|
|**Attività di distribuzione/Events** <br/> |**Data di inizio** <br/> |**Data di fine** <br/> |**Risorse** <br/> |**Dipendenze** <br/> |
|**Determinare gli obiettivi di distribuzione** <br/> |||||
| Con le parti interessate interne ed esterne:<br>  -Concordare l'ambito e la sequenza temporale <br>  -Concordare il meccanismo di verifica dei progetti  <br>  -Sviluppare criteri di successo e una [comunicazione](https://fasttrack.microsoft.com/office) / [per iniziare con Office 365](https://support.office.com/article/396b8d9e-e118-42d0-8a0d-87d1f2f055fb)|||||
|**Inventariare l'ambiente corrente e prendere decisioni di distribuzione principali** |||||
|Inventario dell'ambiente corrente |||||
| Raccogliere il numero di account utente (nomi di account di accesso, indirizzi di posta elettronica) |||||
| Raccogliere il numero e le dimensioni delle cassette postali (incluse le cassette postali condivise e le sale conferenze) |||||
| Raccogliere le versioni e le configurazioni client (browser, sistemi operativi, applicazioni di Office, versioni per dispositivi mobili e così via) |||||
| Raccogliere informazioni dettagliate sulle impostazioni di rete (host DNS, configurazione di proxy e/o firewall, connettività Internet) |||||
| Raccogliere informazioni su percorsi di archiviazione file (condivisioni di file, archiviazione di file Intranet) |||||
| Raccogliere informazioni dettagliate sui siti Intranet di cui si intende eseguire la migrazione |||||
| Raccolta di sistemi di messaggistica istantanea e riunione online pianificati per la migrazione |||||
| Raccogliere i dettagli relativi a qualsiasi applicazione integrata con sistemi esistenti (applicazioni abilitate alla posta elettronica, flusso di lavoro, CRM e così via) |||||
|Prendere decisioni di distribuzione principali |||||
| Come si [creano e/o si sincronizzano gli account](https://go.microsoft.com/fwlink/?LinkId=534819)? |||||
| Come verranno [autenticati gli account utente](https://go.microsoft.com/fwlink/?LinkId=534820)? |||||
| Verrà eseguita la migrazione di tutti i dati e in che modo verrà eseguita la migrazione ( [messaggi di posta elettronica](https://go.microsoft.com/fwlink/?LinkId=534823) e [file](https://go.microsoft.com/fwlink/?LinkId=534824))? |||||
| Vi sarà un'integrazione di breve o lungo termine [con i sistemi locali](https://go.microsoft.com/fwlink/?LinkId=534822)? |||||
| Quali [dispositivi saranno in grado di connettersi (in](https://go.microsoft.com/fwlink/?LinkId=534821) remoto, da dispositivi mobili o solo dalla rete)? |||||
|**Correzione di potenziali bloccanti per la distribuzione** |||||
|Con gli strumenti e le linee guida di Microsoft: |||||
| Pulire gli account di Active Directory ( [linee guida](https://go.microsoft.com/fwlink/?LinkId=534825) e [strumenti](https://go.microsoft.com/fwlink/?LinkId=534826)) |||||
| Preparare i dati per una migrazione ( [messaggi di posta elettronica](https://go.microsoft.com/fwlink/?LinkId=534823) e [file](https://go.microsoft.com/fwlink/?LinkId=534824)) |||||
| Preparare la rete ( [linee guida e strumenti](https://aka.ms/tune)) |||||
| Aggiornare le versioni del software client ( [linee guida](https://go.microsoft.com/fwlink/?LinkId=534827)) |||||
| Se si dispone di Active Directory Rights Management Services: preparare l'ambiente ( [indicazioni](https://go.microsoft.com/fwlink/?linkid=844967))  <br/> |||||
|**Configurare i servizi di Office 365 in modo che funzionino per l'organizzazione** |||||
|Configurare la sottoscrizione di Office 365 |||||
|[Verificare i domini che si desidera utilizzare con l'abbonamento](https://go.microsoft.com/fwlink/?LinkId=534828) |||||
| Configurare [le impostazioni dell'applicazione](https://go.microsoft.com/fwlink/?LinkId=534829) (messaggi di posta elettronica, messaggistica istantanea, riunioni online, collaborazione Web, archiviazione di file, Yammer) |||||
| Facoltativamente, [preparare la sincronizzazione della directory](https://go.microsoft.com/fwlink/?LinkId=534830) |||||
| Facoltativamente [, preparare il servizio Single Sign-on](https://go.microsoft.com/fwlink/?LinkId=534831) |||||
|Preparare l'organizzazione |||||
|[Preparare il Service Desk](https://fasttrack.microsoft.com/office) per la migrazione imminente |||||
| Testare la distribuzione e il processo di migrazione facoltativo |||||
| Informare gli utenti sulle [modifiche imminenti e su come verranno influenzate](https://fasttrack.microsoft.com/office) dall'utente |||||
|**Eseguire il rollforward per gli utenti** |||||
|Account e cassette postali di installazione |||||
| Aggiungere gli utenti e [assegnare licenze agli utenti in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc) |||||
| Facoltativamente, eseguire la migrazione dei dati ( [posta elettronica](https://go.microsoft.com/fwlink/?LinkId=534823)e [file](https://go.microsoft.com/fwlink/?LinkId=534824)e così via) |||||
|Convalidare la funzionalità e completare i passaggi finali |||||
| Eseguire la migrazione [delle impostazioni DNS in modo che puntino a Office 365](https://go.microsoft.com/fwlink/?LinkId=534835) |||||
| Informare gli utenti quando possono [iniziare a usare Office 365](https://support.office.com/article/office-365-basics-video-training-396b8d9e-e118-42d0-8a0d-87d1f2f055fb?ui=en-US&amp;rs=en-US&amp;ad=US) |||||
| Riconfigurare i sistemi client per la connessione a Office 365 ( [Office](https://go.microsoft.com/fwlink/?LinkId=534836), [Outlook](https://go.microsoft.com/fwlink/?LinkId=534837), [Outlook per Mac](https://support.office.com/article/6e27792a-9267-4aa4-8bb6-c84ef146101b#PickTab=Outlook_for_Mac), [dispositivi mobili](https://go.microsoft.com/fwlink/?LinkId=534840))  |||||
