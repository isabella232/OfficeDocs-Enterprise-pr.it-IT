---
title: Prepararsi per Office 365 Enterprise dell'organizzazione
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Se si è scelto fuori FastTrack distribuzione e non sono trovare le informazioni necessarie i passaggi di distribuzione di base, questo è il punto di partenza.
ms.openlocfilehash: 552579347ae5f4b72821d350a061f3ba8d48841b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541426"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Prepararsi per Office 365 Enterprise dell'organizzazione

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Che cosa è necessario eseguire per prepararsi per Office 365?

La maggior parte delle organizzazioni non è necessario eseguire alcuna operazione per prepararsi per Office 365. Si tratta di un'applicazione sul web e utenti siano in grado di utilizzarlo come hanno un account. Altre organizzazioni sono più percorsi, le procedure di protezione o altri requisiti che crea la necessità di pianificazione maggiori. Per le organizzazioni di livello aziendale, seguire le voci di elenco di controllo seguente per acquisire familiarità con Office 365.
  
Se si desidera della Guida in linea guida di Office 365 configurare [FastTrack](https://fasttrack.microsoft.com/office) è il modo più semplice per distribuire Office 365, è inoltre possibile accedere e utilizzare [consulenti di distribuzione per i servizi di Office 365](deployment-advisors-for-office-365.md).
  
|**Scegliere una o più per iniziare:**||
|:-----|:-----|
| [Requisiti di sistema per Office](https://products.office.com/office-system-requirements) |-Microsoft Office Professional, Office 365, Office 365 ProPlus e ogni applicazione di Office per Windows, Mac, iOS e Android specifici requisiti di sistema. Verificare che l'hardware e software meet i requisiti minimi di sistema.|
|**La maggior parte dei** clienti connettono le directory locali a Office 365. Ottenere un punto di partenza nella preparazione della directory per [l'installazione e l'esecuzione di IdFix nella rete](https://www.microsoft.com/download/details.aspx?id=36832).<br> Utilizzare [advisor AAD connettersi](https://aka.ms/aadconnectpwsync) e [che Azure Active Directory Premium configurare Guida](https://aka.ms/aadpguidance) per ottenere impostazione personalizzata e di informazioni aggiuntive. <br> |-Automatizzati verifiche della directory per [convalida di persone account correttamente sincronizzerà](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> -È consigliabile le modifiche apportate agli oggetti directory e sono disponibili automatizzare le modifiche. <br> - [Ulteriori informazioni sull'utilizzo dello strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Lettura** nostri [indicazioni sulle prestazioni di rete](https://aka.ms/tune) e utilizzare gli strumenti per verificare che sono la configurazione di connettività e le prestazioni necessaria per fornire agli utenti un'esperienza ottimale.  <br/> | -Verificare che è possibile connettersi a Office 365, se il Filtra o la scansione in uscita traffico, è consigliabile comprendere quali [Gestione endpoint di Office 365](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) significa per l'organizzazione.  <br/>  - [Modello e testare la capacità della rete](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) o spostare un circuito [ExpressRoute Azure per Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) per un'esperienza più prevedibile.  <br/> |
|**Usa** il nostro [pianificazione elenco di controllo](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) come punto di partenza per la creazione del proprio piano di distribuzione.  <br/> | -Panoramica approfondita delle possibili aree è necessario pianificare con collegamenti a informazioni di riferimento o procedure per la pianificazione.  <br/> |
|Per **utilizzare** lo [Script di grandi dimensioni dell'elemento di Exchange Server](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) per trovare gli elementi di posta elettronica che possono essere troppo grandi per eseguire la migrazione.  <br/> | -Utilizza i servizi Web Exchange per rappresentare, accedere, analizzare la cassetta postale per le dimensioni dei file specificati e dump i risultati in un file CSV. Leggere le [istruzioni dettagliate su come utilizzare lo script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx).<br/> |
|**Richiedere** vantaggio degli [esperti di distribuzione di Microsoft](https://go.microsoft.com/fwlink/?LinkId=517115) che consentono di pianificazione come tutti gli utenti iniziare a utilizzare i nuovi servizi e applicazioni.  <br/> Utilizzare le [procedure guidate di distribuzione per servizi di Office 365](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) per ottenere impostazione personalizzata e di informazioni aggiuntive.  <br/> | -Il centro di on-Boarding può essere utilizzato direttamente con i clienti e con le organizzazioni partner. Concedere una chiamata oggi.  <br/> |
|**Utilizzare** i [modelli e le risorse nell'interfaccia di successo di Office 365](https://fasttrack.microsoft.com/office/drive-value/engage) di condividere la distribuzione e on-boarding piani con le persone all'interno dell'organizzazione.  <br/> | -La comunicazione con tutti gli utenti prima, durante e dopo la transizione a Office 365 è fondamentale.  <br/> -Utilizzare i modelli, guide e stampati per migliorare le comunicazioni.  <br/> |
|**Lettura** dell'articolo [Principi di connettività di rete di Office 365](https://aka.ms/o365networkingprinciples) per acquisire familiarità con i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali.  <br/> | -In questo articolo consentono di acquisire familiarità con le indicazioni più recenti per l'ottimizzazione in modo sicuro la connettività di rete di Office 365.  <br/> |
   
Ulteriori risorse che consentono di integrare Office 365 con la strategia cloud più ampia fonti Di seguito sono [Microsoft cloud risorse sull'architettura IT](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>Se si desidera contattare il supporto?
Siamo a tua disposizione per indirizzare, [contattare il supporto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti di business.
