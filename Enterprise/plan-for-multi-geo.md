---
title: Plan for OneDrive for Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informazioni su OneDrive per Business Multi-livello geografico, funzionamento multi-geo e le posizioni geo sono disponibili per l'archiviazione dei dati.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Plan for OneDrive for Business Multi-Geo

Questa guida è destinata agli amministratori di società multinazionale (MNCs) responsabili di preparare i tenant di SharePoint Online per essere ingrandita a ulteriori aree geografiche in conformità con presenza dell'azienda per soddisfare i requisiti di residenza dati.

In una configurazione Multi-Geo OneDrive tenant Office 365 è costituita da una posizione centralizzata (noto anche come il percorso predefinito) e uno o più percorsi geo satellitari. Si tratta di un singolo tenant che si estende su più località geografica. OneDrive Multi-Geo, le informazioni di tenant, inclusi i percorsi geografica, sia gestite in Azure Active Directory (AAD). 

Ecco alcuni termini chiave multi-geo utili per comprendere i concetti di base della configurazione:

-   **Tenant** – rappresentazione dell'organizzazione nel cloud che in genere presenta uno o più domini che Office 365 (ad esempio http://contoso.sharepoint.com). 

-   **Percorsi Geo** da posizioni geografiche ospitati dati del tenant. Multi-geo tenant estendersi su più di una posizione geografica, ad esempio Nord America ed Europa.

-   **Percorsi di dati consentito (ADL)** – i percorsi geo per cui è stato configurato il tenant per ospitare dati OneDrive e SharePoint.

-   **Percorso preferito di dati (PDL)** – località geografica cui sono archiviati i dati di OneDrive un singolo utente. Può essere impostato dall'amministratore per uno dei percorsi dati consentiti che sono stati configurati per il tenant. Si noti che se si modifica il PDL per un utente che dispone già di un sito di OneDrive, i dati di OneDrive non viene spostati nella nuova posizione geografica automaticamente. Per ulteriori informazioni, vedere [spostare una raccolta di OneDrive in un'altra posizione geografica](move-onedrive-between-geo-locations.md) .

Abilitazione della Multi-Geo richiede quattro passaggi principali:

1.  Collaborare con il team amministrativo per aggiungere il piano di servizio _Multi-Geo disponibili in Office 365_ .

2.  Scegliere il desiderata satellitare posizione geografica e aggiungerli al tenant.

3.  Impostare percorso dati preferito degli utenti alla posizione geografica satellitari desiderato. Quando viene eseguito il provisioning di un nuovo sito di OneDrive per un utente, viene effettuato il provisioning di loro PDL.

4.  Eseguire la migrazione siti OneDrive esistenti degli utenti dal percorso principale relativo percorso dati preferita in base alle esigenze.

Per informazioni dettagliate su ciascuno di questi passaggi, vedere [Configurare OneDrive per Business Multi-Geo](multi-geo-tenant-configuration.md) .

> [!IMPORTANT]
> Si noti che le funzionalità Multi-Geo di Office 365 non progettate per i casi di ottimizzazione delle prestazioni, sono stati progettati per soddisfare i requisiti di residenza dati. Per informazioni sull'ottimizzazione delle prestazioni per Office 365, vedere [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o contattare il supporto.

È possibile configurare una delle seguenti posizioni da località geografica in cui ospitare i file di OneDrive. Durante la pianificazione per la multi-geo, creare un elenco dei percorsi che si desidera aggiungere al tenant di Office 365. È consigliabile a partire da uno o due percorsi satellitari e quindi gradualmente l'espansione in più posizioni geo, se necessario.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Percorso</strong></th>
<th align="left"><strong>Codice</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asia-Pacifico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Europa / Allinea al centro est / Africa</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Nord America</td>
<td align="left">NOME</td>
</tr>
<tr class="even">
<td align="left">Australia</td>
<td align="left">AUSTRALIA</td>
</tr>
<tr class="odd">
<td align="left">Canada</td>
<td align="left">POSSIBILE</td>
</tr>
<tr class="odd">
<td align="left">Giappone</td>
<td align="left">GIAPPONESE</td>
</tr>
<tr class="even">
<td align="left">Corea</td>
<td align="left">(COREANO)</td>
</tr>
<tr class="odd">
<td align="left">Regno Unito</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Prossime località geografiche:
  
- Francia
- India

Quando si configura multi-geo, prendere in considerazione avere l'opportunità di consolidamento dell'infrastruttura locale durante la migrazione a Office 365. Ad esempio, se si dispone di farm locale in Singapore e Malaysia, quindi è possibile consolidare loro posizione satellitare APC, requisiti di residenza dati consentono di eseguire questa operazione.

## <a name="best-practices"></a>Procedure consigliate

È consigliabile creare un utente di test in Office 365 per eseguire alcuni test iniziale. Verrà esaminato alcuni passaggi di testing e la verifica con l'utente prima di procedere con gli utenti di produzione incorporato nella funzionalità Multi-Geo OneDrive.

Dopo aver completato il test con l'utente di test, selezionare un gruppo pilota – forse il reparto IT: la prima di utilizzare OneDrive in una nuova posizione geografica. Per il primo gruppo, selezionare gli utenti che non hanno ancora un OneDrive. È consigliabile non più di cinque utenti nel gruppo iniziale e gradualmente espandere dopo un approccio di implementazione in batch.

Ogni utente deve avere un *percorso dati preferito* (PDL) impostato in modo che Office 365 può determinare in quale posizione geografica per fornire loro OneDrive. Percorso dei dati Preferiti dell'utente deve corrispondere a uno dei percorsi di satellitari scelti o la posizione centrale. Mentre il campo PDL non è obbligatorio, è consigliabile che un PDL da impostare per tutti gli utenti. Eseguire il provisioning dei carichi di lavoro di un utente senza un PDL nella posizione centrale in base alla Multi-Geo logica.   

Creare un elenco degli utenti e includere il nome dell'entità utente (UPN) e il codice di posizione per il percorso dati preferito appropriato. Includere per iniziare con l'utente di test e il gruppo pilota iniziale. In questo elenco sono necessari per le procedure di configurazione.

Se gli utenti vengono sincronizzati da un sistema di Active Directory (AD) locale per Azure Active Directory (AAD), è necessario impostare il percorso dati preferito per gli utenti sincronizzati tramite la connessione di Azure Active Directory. È possibile configurare direttamente il percorso dati preferito per gli utenti sincronizzati con Azure Active Directory PowerShell. I passaggi per configurare PDL in Active Directory e sincronizzarlo sono trattati nei [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

L'amministrazione di un tenant multi-geo può essere diverso da un tenant di livello geografico multi, la maggior parte delle impostazioni SharePoint e OneDrive e i servizi sono multi-geo. È consigliabile consultare [amministrazione di un ambiente multi-geo](administering-a-multi-geo-environment.md) prima di procedere con la configurazione.

Per informazioni dettagliate sull'esperienza degli utenti finali in un ambiente multi-geo, leggere [l'esperienza utente in un ambiente multgeo](multi-geo-user-experience.md) .

Per iniziare a configurare OneDrive per Business Multi-Geo, vedere [Configurare OneDrive per Business Multi-Geo](multi-geo-tenant-configuration.md).

Dopo aver completato la configurazione, ricordarsi di [eseguire la migrazione di raccolte di OneDrive degli utenti](move-onedrive-between-geo-locations.md) in base alle esigenze per ottenere gli utenti lavorano dai percorsi dei dati preferito.
