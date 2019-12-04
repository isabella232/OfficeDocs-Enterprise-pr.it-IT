---
title: Ottimizzare le immagini nelle pagine moderne di siti di SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Informazioni su come ottimizzare le immagini nelle pagine moderne di siti di SharePoint Online.
ms.openlocfilehash: 68e2f79e1f768cfc93feb4f26f8b2fbeca5d6b83
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814224"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>Ottimizzare le immagini nelle pagine moderne di siti di SharePoint Online

Questo articolo spiega come ottimizzare le immagini nelle pagine moderne di siti di SharePoint Online.

Per informazioni su come ottimizzare le immagini in siti di pubblicazione classici, vedere [Ottimizzazione delle immagini per SharePoint Online](image-optimization-for-sharepoint-online.md).

>[!NOTE]
>Per altre informazioni sulle prestazioni nei portali moderni di SharePoint Online, vedere [Prestazioni nell'esperienza moderna di SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Usare lo strumento Diagnostica pagine per SharePoint per analizzare l'ottimizzazione delle immagini

Lo **strumento Diagnostica pagine per SharePoint** è un'estensione del browser per Chrome e per la [versione 77 o successiva di Microsoft Edge](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) che consente di analizzare le pagine classiche e moderne di siti di pubblicazione di SharePoint. Per ogni pagina analizzata lo strumento fornisce un report che mostra le prestazioni della pagina rispetto a un set definiti di criteri delle prestazioni. Per installare Diagnostica pagine per SharePoint e saperne di più su questo strumento, vedere [Usare lo strumento Diagnostica pagine per SharePoint Online](page-diagnostics-for-spo.md).

Quando si analizza un sito moderno di SharePoint con lo strumento Diagnostica pagine per SharePoint, è possibile visualizzare le informazioni sulle immagini di grandi dimensioni nel riquadro _Test diagnostici_.

I risultati possibili includono:

- **Attenzione** (rosso): la pagina contiene **una o più** immagini di dimensioni superiori a 300 KB
- **Non è richiesto alcun intervento** (verde): la pagina non contiene immagini di dimensioni superiori a 300 KB

Se nella sezione dei risultati **Attenzione** viene visualizzato il risultato **Sono state rilevate immagini di grandi dimensioni**, è possibile fare clic sul risultato per visualizzare altri dettagli.

![Risultati dello strumento Diagnostica pagine](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Risolvere i problemi relativi a immagini di grandi dimensioni

Se una pagina contiene immagini di dimensioni superiori a 300 KB, selezionare il risultato **Sono state rilevate immagini di grandi dimensioni** per visualizzare le immagini di dimensioni eccessive. Nelle pagine moderne di SharePoint Online i rendering delle immagini vengono forniti e ridimensionati automaticamente a seconda delle dimensioni della finestra del browser e della risoluzione del monitor client. È consigliabile ottimizzare sempre le immagini per l'uso Web prima di caricarle in SharePoint Online. Le dimensioni e la risoluzione di immagini di grandi dimensioni verranno ridotte automaticamente e questa riduzione può influire sul rendering.

Prima di revisionare le pagine per correggere i problemi di prestazioni, prendere nota del tempo di caricamento delle pagine nei risultati dell'analisi. Eseguire di nuovo lo strumento dopo la revisione per verificare se il nuovo risultato è compreso nello standard di base e controllare il nuovo tempo di caricamento della pagina per verificare se c'è stato un miglioramento.

![Risultati del tempo di caricamento delle pagine](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Il tempo di caricamento delle pagine dipende da numerosi fattori, ad esempio il carico di rete, l'ora del giorno e altre condizioni transitorie. È consigliabile verificare il tempo di caricamento delle pagine alcune volte prima e dopo aver apportato modifiche in modo da ottenere una media dei risultati.

## <a name="related-topics"></a>Argomenti correlati

[Ottimizzare le prestazioni di SharePoint Online](tune-sharepoint-online-performance.md)

[Ottimizzare le prestazioni di Office 365](tune-office-365-performance.md)

[Prestazioni nell'esperienza moderna di SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[Reti per la distribuzione di contenuti](content-delivery-networks.md)

[Usare la rete per la distribuzione di contenuti di Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md)
