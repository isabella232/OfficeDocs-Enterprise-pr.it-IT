---
title: Panoramica di Information Protection di Office 365 per GDPR
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: Panoramica su Information Protection di Office 365 per GDPR. Informazioni su come individuare, classificare, protegger e monitorare i dati personali.
ms.openlocfilehash: b3af91608d545b221694b9e4a18db07b85d7541a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="overview-of-office-365-information-protection-for-gdpr"></a>Panoramica di Information Protection di Office 365 per GDPR

Questa soluzione mostra come proteggere i dati riservati archiviati nei servizi di Office 365. Include suggerimenti prescrittivi per individuare, classificare, proteggere e monitorare i dati personali. Questa soluzione utilizza l'RGPD come esempio, ma è possibile applicare lo stesso processo per raggiungere la conformità con molti altri regolamenti.

L'RGPD regola la raccolta, l'archiviazione, l'elaborazione e la condivisione dei dati personali. I dati personali sono definiti in modo molto ampio nell'RGPD, come qualsiasi dato relativo a una persona fisica identificata o identificabile residente nell'Unione Europea.

Articolo 4 - Definizioni

> con "dati personali" si intende qualsiasi informazione relativa a una persona fisica identificata o identificabile ("soggetto dei dati"); una persona fisica identificabile è una persona che può essere identificata, direttamente o indirettamente, in particolare in riferimento a un identificatore come un nome, un numero di identificazione, dati sulla posizione, un identificatore online o a uno o più fattori specifici per l'identità fisica, psicologica, genetica, mentale, economica, culturale o sociale della persona fisica;

Questa soluzione vuole aiutare le organizzazioni a individuare e proteggere i dati personali in Office 365 che potrebbero essere soggetti all'RGPD. Non viene fornita come attestazione di conformità RGPD. Le organizzazioni sono tenute a garantire la propria conformità RGPD e devono consultare i propri team legali e di conformità o cercare assistenza da terze parti specializzate in conformità.

[GDPR Assessment](https://www.gdprbenchmark.com) è uno strumento rapido, online di autovalutazione che consente alle autorizzazioni di verificare gratuitamente il proprio livello di preparazione alla conformità con l'RGPD (<http://aka.ms/gdprassessment>).

## <a name="assess-and-manage-your-compliance-risk"></a>Verificare e gestire il rischio di conformità

Il primo passo per la conformità RGPD consiste nel valutare se tale regolamento è applicabile all'organizzazione e, in tal caso, in quale misura. L'analisi include la comprensione dei dati elaborati dall'organizzazione e dove questi si trovano.

### <a name="step-1--use-compliance-manager-to-view-the-regulation-requirements-and-track-your-progress"></a>Passaggio 1 - Usare Gestore conformità per visualizzare i requisiti normativi e tenere traccia dell'avanzamento

Gestore conformità offre strumenti per tenere traccia, implementare e gestire i controlli per consentire all'organizzazione di raggiungere la conformità con diversi standard, tra cui l'RGPD.

![Usare Gestore conformità per visualizzare i requisiti e tenere traccia dell'avanzamento](Media/Overview-image1.png)

Per ulteriori informazioni, vedere [Utilizzo di Gestore conformità nel Service Trust Portal](https://support.office.com/it-IT/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942). 

### <a name="step-2--use-content-search-and-sensitive-information-types-to-find-personal-data"></a>Passaggio 2 - Utilizzare Ricerca contenuto e i tipi di informazioni riservate per trovare i dati personali 

Individuare i dati personali nel proprio ambiente soggetti all'RGPD. Usare Ricerca contenuto con i tipi di informazioni riservate per:

-   Trovare e indicare dove si trovano i dati personali.

-   Ottimizzare i tipi di dati riservati e altre query per trovare tutti i dati personali nel proprio ambiente.

![Usare Ricerca contenuto e i tipi di informazioni riservate per trovare dati personali](Media/Overview-image2.png)

I tipi di informazioni riservate definiscono il modo in cui il processo automatico riconosce tipi di informazioni specifiche come i numeri di previdenza sociale e di carta di credito. Questo articolo include un set da usare come punto di partenza. Molti altri tipi di informazioni riservate saranno presto disponibili per i dati personali nei paesi dell'Unione Europea.

Per ulteriori informazioni, vedere [Cercare e trovare i dati personali](search-for-and-find-personal-data.md). 

## <a name="classify-protect-and-monitor-personal-data-in-office-365-and-other-saas-apps"></a>Classificare, proteggere e monitorare i dati personali in Office 365 e altre applicazioni SaaS

Alcune funzionalità utilizzate per la protezione delle informazioni in Office 365 possono anche essere usate per proteggere i dati riservati nelle altre applicazioni SaaS.

![Classificare, proteggere e monitorare i dati personali](Media/Overview-image3.png)

L'illustrazione seguente viene descritta ulteriormente nella sezione (passaggi da 3 a 5).

### <a name="step-3--decide-if-you-want-to-use-labels-in-addition-to-sensitive-information-types"></a>Passaggio 3 - Decidere se si desidera utilizzare le etichette, oltre ai tipi di informazioni riservate

I tipi di informazioni riservate sono una forma di classificazione. Vedere [Costruire uno schema di classificazione per i dati personali](architect-a-classification-schema-for-personal-data.md), per decidere se si desidera implementare anche le etichette. Per applicare le etichette, vedere [Applicare le etichette ai dati personali in Office 365](apply-labels-to-personal-data-in-office-365.md).

Nella figura, le etichette e i tipi di informazioni riservate funzionano in Office 365. A breve, sarà possibile utilizzarli anche con Cloud App Security per trovare i dati riservati nelle altre applicazioni SaaS, ad esempio Box e Salesforce.

### <a name="step-4--protect-personal-data-in-office-365"></a>Passaggio 4 - Proteggere i dati personali in Office 365 

La protezione dei dati personali inizia con la prevenzione della perdita dei dati di Office 365. Esistono molte altre funzionalità consigliate per proteggere l'accesso ai dati personali, tra cui Crittografia dei messaggi di Office 365 per la posta elettronica.

Queste protezioni possono essere applicate a set di dati specifici:

-   Autorizzazioni a livello di sito e raccolta

-   Criteri di condivisione esterna a livello di sito

-   Criteri di accesso al dispositivo a livello di sito

La protezione per l'accesso a Office 365 e altri servizi cloud include:

-   Protezione dell'accesso a identità e dispositivi in Enterprise Mobility + Security (EMS)

-   Gestione accessi con privilegi

-   Funzionalità di sicurezza di Windows 10

Per ulteriori informazioni sull'applicazione della protezione, vedere [Applicare la protezione ai dati personali di Office 365](apply-protection-to-personal-data-in-office-365.md).

### <a name="step-5--monitor-for-leaks-of-personal-data"></a>Passaggio 5 - Monitorare la perdita di dati personali

I report sulla prevenzione della perdita dei dati di Office 365 forniscono il livello maggiore di dettaglio per il monitoraggio dei dati riservati. È possibile configurare avvisi automatici e analizzare violazioni utilizzando il log di controllo di Office 365. Cloud App Security estende la capacità di trovare e monitorare i dati riservati ad altri provider SaaS. Per ulteriori informazioni su questi strumenti, vedere [Monitorare le violazioni dei dati personali](monitor-for-leaks-of-personal-data.md).
