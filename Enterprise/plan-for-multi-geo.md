---
title: Preparare l'implementazione di OneDrive for Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su OneDrive for Business Multi-Geo, come funziona il tenant multi-geografico e quali posizioni geografiche sono disponibili per l'archiviazione dei dati.
ms.openlocfilehash: de856bdeb0c0f1ca8e718439ddb98d738843bc5a
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200719"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Preparare l'implementazione di OneDrive for Business Multi-Geo

Questa guida è utile agli amministratori di società multinazionali che stanno preparando l'espansione del tenant di SharePoint Online in altre aree geografiche in base alla presenza dell'azienda per soddisfare i requisiti di residenza dei dati.

Nella configurazione OneDrive Multi-Geo, Office 365 è costituito da una posizione centralizzata e una o più posizioni geografiche satellite. Si tratta di un singolo tenant che comprende diverse posizioni geografiche. In OneDrive Multi-Geo, le informazioni del tenant, incluse le posizioni geografiche, vengono gestite in Azure Active Directory (AAD). 

Ecco un glossario dei termini principali per facilitare la comprensione della configurazione multi-geografica:

-   **Tenant**: rappresentazione di un'organizzazione nel cloud di Office 365 che in genere contiene uno o più domini associati (ad esempio http://contoso.sharepoint.com). 

-   **Posizioni geografiche**: le posizioni geografiche disponibili per ospitare i dati in un tenant di Office 365.

-   **Posizioni satellite**: le posizioni geografiche configurate per ospitare i dati nel tenant di Office 365. I tenant multi-geografici coprono più di una posizione geografica, ad esempio Nord America ed Europa.

-   **Posizione dati preferita (PDL)**: la posizione geografica in cui sono archiviati i dati di OneDrive di un singolo utente. Questa funzione può essere impostata dall'amministratore in una delle posizioni dati consentite configurate per il tenant. Se si cambia la PDL di un utente che ha già un sito di OneDrive, i dati di OneDrive non vengono spostati automaticamente nella nuova posizione geografica. Per ulteriori informazioni vedere [Spostare un sito di OneDrive in un'altra posizione geografica](move-onedrive-between-geo-locations.md).

Per abilitare Multi-Geo sono necessarie quattro attività:

1.  Collaborare con il team responsabile dell'account per aggiungere il piano servizi _Multi-Geo Capabilities in Office 365 _.

2.  Scegliere le posizioni satellite desiderate e aggiungerle al tenant.

3.  Impostare la posizione dati preferita dell'utente nella posizione satellite desiderata. Quando viene eseguito il provisioning di un nuovo sito di OneDrive per un utente, viene eseguito il provisioning sulla relativa PDL.

4.  Eseguire la migrazione dei siti di OneDrive esistenti dalla posizione centrale alla posizione dati preferita in base alle esigenze.

Vedere [Configurare OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) per informazioni dettagliate su ognuno di questi passaggi.

> [!IMPORTANT]
> Office 365 Multi-Geo non è progettato per i casi di ottimizzazione delle prestazioni, ma per soddisfare i requisiti di residenza dei dati. Per informazioni sull'ottimizzazione delle prestazioni per Office 365, vedere [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o contattare il servizio di supporto tecnico.

È possibile configurare una delle posizioni seguenti come posizione satellite in cui ospitare i file di OneDrive. Nella pianificazione multi-geografica, è opportuno creare un elenco delle posizioni che si desidera aggiungere al tenant di Office 365. È consigliabile iniziare con una o due posizioni satellite e poi aggiungere gradualmente altre posizioni geografiche, se necessario.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Posizione</strong></th>
<th align="left"><strong>Codice</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asia-Pacifico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australia</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Canada</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">Europa/Medio Oriente/Africa</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Francia</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">India</td>
<td align="left">IND</td>
</tr>
<tr class="odd">
<td align="left">Giappone</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Corea</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">Nord America</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">Regno Unito</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Quando si configura un tenant multi-geografico, valutare l'opportunità di consolidare l'infrastruttura locale durante la migrazione a Office 365. Ad esempio, se si dispone di farm locali a Singapore e in Malesia, è possibile consolidarle nella posizione satellite APC, a condizione che i requisiti di residenza dei dati consentano di farlo.

## <a name="best-practices"></a>Procedure consigliate

È consigliabile creare un utente test in Office 365 per eseguire alcuni test iniziali. Verranno eseguiti alcuni passaggi di verifica con questo utente prima di procedere a caricare utenti della produzione in OneDrive Multi-Geo.

Dopo aver completato la verifica con l'utente test, selezionare un gruppo pilota, magari dal proprio reparto IT, per utilizzare OneDrive in una nuova posizione geografica per la prima volta. Per questo primo gruppo, selezionare gli utenti che non hanno ancora OneDrive. È consigliabile inserire non più di cinque persone in questo gruppo iniziale e aumentare gradualmente il numero, seguendo un approccio di implementazione a fasi.

Ogni utente deve avere una *posizione dati preferita* (PDL) impostata in modo che Office 365 possa determinare in quale posizione geografica effettuare il provisioning di OneDrive. La posizione dati preferita dell'utente deve corrispondere alla località satellite selezionata o alla posizione centrale. Il campo PDL non è obbligatorio ma è consigliabile impostare una PDL per tutti gli utenti. Verrà eseguito il provisioning in posizione centrale dei carichi di lavoro di un utente senza una PDL.   

Creare un elenco degli utenti e includere il nome dell'entità utente (UPN) e il codice di posizione per la posizione dati preferita appropriata. Includere l'utente test e il gruppo pilota iniziale per cominciare. Tale elenco è necessario per le procedure di configurazione.

Se gli utenti vengono sincronizzati da un sistema di Active Directory locale per Azure Active Directory, è necessario impostare la posizione dati preferita per gli utenti sincronizzati tramite la connessione di Azure Active Directory. È possibile configurare direttamente la posizione dati preferita per gli utenti sincronizzati con Azure Active Directory PowerShell. I passaggi per configurare la PDL in AD e sincronizzarla sono trattati in [Sincronizzazione di Azure Active Directory Connect: configurare la posizione dati preferita per le risorse di Office 365](https://docs.microsoft.com/it-IT/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

L'amministrazione di un tenant multi-geografico può essere diverso da un tenant non multi-geografico, dal momento che la maggior parte delle impostazioni SharePoint e OneDrive e i servizi hanno funzionalità multi-geo. È consigliabile consultare [Amministrazione di un ambiente multi-geografico](administering-a-multi-geo-environment.md) prima di procedere con la configurazione.

Leggere [Esperienza utente in un ambiente multi-geografico](multi-geo-user-experience.md) per i dettagli riguardanti l'esperienza degli utenti finali in un ambiente multi-geografico.

Per iniziare a configurare OneDrive for Business Multi-Geo, vedere [Configurare OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).

Dopo aver completato la configurazione, è necessario [eseguire la migrazione delle raccolte OneDrive dell'utente](move-onedrive-between-geo-locations.md) per consentire agli utenti di lavorare dalla propria posizione dati preferita.
