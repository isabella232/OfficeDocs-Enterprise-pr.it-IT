---
title: Preparare l'organizzazione per Office 365 Enterprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Se si è scelto di non eseguire la distribuzione di FastTrack e non si trovano le informazioni necessarie nei passaggi di distribuzione di base, questo è il punto di partenza.
ms.openlocfilehash: a15bd73efe2fd2e2dfd13b3a444f77b9d0bfc764
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085375"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Preparare l'organizzazione per Office 365 Enterprise

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Che cosa è necessario fare per prepararsi per Office 365?

La maggior parte delle organizzazioni non ha bisogno di fare nulla per prepararsi per Office 365. Si tratta di un'applicazione sul Web e gli utenti sono in grado di utilizzarlo non appena dispongono di un account. Altre organizzazioni dispongono di altre posizioni, procedure di sicurezza o altri requisiti che creano la necessità di una maggiore pianificazione. Per le organizzazioni a livello aziendale, seguire gli elementi di elenco di controllo riportati di seguito per iniziare a usare Office 365.
  
Se si desidera ricevere assistenza per la configurazione di Office 365, [FastTrack](https://fasttrack.microsoft.com/office) è il modo più semplice per distribuire Office 365; è anche possibile utilizzare gli [assistenti per la distribuzione per i servizi di Office 365](deployment-advisors-for-office-365.md).
  
|**Scegliere uno o più per iniziare:**||
|:-----|:-----|
| [Requisiti di sistema per Office](https://products.office.com/office-system-requirements) |-Microsoft Office Professional, Office 365, Office 365 ProPlus e tutte le applicazioni di Office per Windows, Mac, iOS e Android dispongono di requisiti di sistema specifici. Verificare che l'hardware e il software soddisfino i requisiti minimi di sistema.|
|**La maggior parte dei** clienti collega la propria directory locale a Office 365. Ottenere un vantaggio sulla preparazione della directory tramite [l'installazione e l'esecuzione di IdFix nella rete](https://www.microsoft.com/download/details.aspx?id=36832).<br> Utilizzare il sistema di [consulenza AAD Connect Advisor](https://aka.ms/aadconnectpwsync) e la [Guida set up di Azure ad Premium](https://aka.ms/aadpguidance) per ottenere una guida di configurazione personalizzata. <br> |-I controlli automatici sulla directory per [convalidare gli account delle persone verranno sincronizzati correttamente](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> -Consiglia le modifiche apportate agli oggetti directory e offre di automatizzare le modifiche apportate. <br> - [Ulteriori informazioni sull'utilizzo dello strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Leggere** le [informazioni sulle prestazioni di rete](https://aka.ms/tune) e utilizzare gli strumenti necessari per garantire la connettività e la configurazione delle prestazioni necessarie per offrire agli utenti la migliore esperienza possibile.  <br> | -Verificare che sia possibile connettersi a Office 365, se si filtra o si esegue l'analisi del traffico in uscita, è necessario capire cosa significa [gestire gli endpoint di office 365](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) per la propria organizzazione.  <br>  - [Model and test your network Capacity](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) o Move to a [Azure ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) Circuit per un'esperienza più prevedibile.   |
|**Utilizzare** l' [elenco di controllo di pianificazione](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) come punto di partenza per la creazione di un piano di distribuzione personalizzato.  <br> | -Panoramica dettagliata delle aree possibili che è necessario pianificare con collegamenti a informazioni di riferimento o How-to utili per la pianificazione. |
|**Utilizzare** lo script degli elementi di [grandi dimensioni di Exchange Server](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) per individuare gli elementi di posta che potrebbero essere troppo grandi per la migrazione.  <br> | -Utilizza i servizi Web Exchange per impersonare, accedere, analizzare la cassetta postale per le dimensioni dei file specificate e scaricare i risultati in un file CSV. Leggere le [istruzioni dettagliate su come utilizzare lo script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**** Approfitta degli [esperti della distribuzione di Microsoft](https://go.microsoft.com/fwlink/?LinkId=517115) che possono aiutarti a pianificare l'utilizzo di tutti i nuovi servizi e applicazioni.  <br> Utilizzare le [procedure guidate per la distribuzione di Office 365 Services](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) per ottenere indicazioni sulla configurazione personalizzate.  <br> | -L'onboarding Center funziona direttamente con i clienti e con le organizzazioni partner. Date loro una chiamata oggi. |
|**Utilizzare** i [modelli e le risorse disponibili in Office 365 Success Center](https://www.microsoft.com/fasttrack/resources) per condividere i piani di distribuzione e onboarding con gli utenti dell'organizzazione.  <br> | -La comunicazione con tutti gli utenti prima, durante e dopo la transizione a Office 365 è critica.  <br> -Utilizzare i modelli, le guide e gli stampati per migliorare le comunicazioni. |
|**Leggere** l'articolo [Office 365 criteri di connettività di rete](https://aka.ms/o365networkingprinciples) per comprendere i principi di connettività per la gestione sicura del traffico di Office 365 e per ottenere le migliori prestazioni possibili.  <br> | -In questo articolo vengono fornite informazioni sulle linee guida più recenti per ottimizzare in modo sicuro la connettività di rete di Office 365. |
   
Si desiderano ulteriori risorse che consentono di integrare Office 365 con una strategia cloud più ampia? Di seguito sono riPORTAte le [risorse dell'architettura IT di Microsoft Cloud](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>Vuoi parlare con il supporto?

Siamo qui per aiutare, [contattare il supporto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti per le aziende.
