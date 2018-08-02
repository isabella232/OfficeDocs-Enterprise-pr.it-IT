---
title: Eseguire la pianificazione di OneDrive for Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su OneDrive for Business Multi-Geo, sulla funzionalità multi-geo e su quali posizioni geografiche sono disponibili per l'archiviazione dei dati.
ms.openlocfilehash: 26dc9d1b0f0f78e1740088036be4b77bea3ce176
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "21549987"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Eseguire la pianificazione di OneDrive for Business Multi-Geo

Questa guida è utile agli amministratori di società multinazionali (MNC) che stanno preparando l'espansione del tenant di SharePoint Online in altre aree geografiche in conformità con la presenza dell'azienda per soddisfare i requisiti di residenza dei dati.

In un tenant di configurazione OneDrive Multi-Geo, Office 365 è costituito da una posizione centralizzata (nota anche come posizione predefinita) e una o più posizioni geografiche satellite. Si tratta di un singolo tenant che si estende su più posizioni geografiche. In OneDrive Multi-Geo, le informazioni del tenant, inclusa la località geografica, vengono gestite in Azure Active Directory (AAD). 

Di seguito sono riportati alcuni termini chiave riguardanti la funzionalità multi-geo per facilitare la comprensione dei concetti base della configurazione:

-   **Tenant**: rappresentazione di un'organizzazione nel cloud di Office 365 che in genere contiene uno o più domini associati (ad esempio http://contoso.sharepoint.com). 

-   **Località geografiche**: le località geografiche in cui sono ospitati i dati del tenant. I tenant con funzionalità multi-geo coprono più di un luogo geografico, ad esempio il Nord America e l'Europa.

-   **Percorsi dati consentiti (ADL)**: le posizioni geografiche per cui il tenant è stato configurato per ospitare dati di OneDrive e SharePoint.

-   **Percorso dati preferito (PDL)**: la posizione geografica in cui sono archiviati i dati di OneDrive di un singolo utente. Questa funzione può essere impostata dall'amministratore a uno dei Percorsi dati consentiti configurati per il tenant. Se si cambia il PDL di un utente che ha già un sito di OneDrive, i dati di OneDrive non vengono spostati automaticamente nella nuova posizione geografica. Per ulteriori informazioni vedere [Spostare un sito di OneDrive in un'altra posizione geografica](move-onedrive-between-geo-locations.md).

L'abilitazione di Multi-Geo richiede quattro passaggi principali:

1.  Collaborare con il team responsabile dell'account per aggiungere il piano servizi _ Funzionalità Multi-Geo in Office 365 _.

2.  Scegliere le posizioni geografiche satellite e aggiungerle al tenant.

3.  Impostare il percorso dati preferiti dell'utente nella posizione geografica satellite desiderata. Quando viene eseguito il provisioning di un nuovo sito di OneDrive per un utente, viene eseguito il provisioning sul relativo PDL.

4.  Eseguire la migrazione dei siti di OneDrive esistenti degli utenti dal percorso principale al percorso dati preferito in base alle esigenze.

Vedere [Configurare OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) per informazioni dettagliate su ognuno di questi passaggi.

> [!IMPORTANT]
> Le funzionalità Multi-Geo di Office 365 non sono progettate per i casi di ottimizzazione delle prestazioni, ma per soddisfare i requisiti di residenza dei dati. Per informazioni sull'ottimizzazione delle prestazioni per Office 365, vedere [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o contattare il servizio di supporto tecnico.

È possibile configurare uno dei seguenti percorsi in posizioni geografiche satellite in cui è possibile ospitare file di OneDrive. Mentre si pianifica la funzionalità multi-geo, creare un elenco delle posizioni che si desidera aggiungere al tenant di Office 365. È consigliabile iniziare con uno o due posizioni satellite e poi di espandersi gradualmente in più posizioni geografiche, se necessario.

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

Prossime località geografiche:
  
- India

Quando si configura multi-geo, prendere in considerazione l'opportunità di consolidare l'infrastruttura locale durante la migrazione a Office 365. Ad esempio, se si dispone di farm locali a Singapore e in Malesia, è possibile consolidarle nella posizione satellite APC, a condizione che i requisiti di residenza dei dati consentano di farlo.

## <a name="best-practices"></a>Procedure consigliate

È consigliabile creare un utente test in Office 365 per eseguire alcuni test iniziali. Verranno eseguiti alcuni passaggi di verifica con questo utente prima di procedere di caricare utenti della produzione nella funzionalità OneDrive Multi-Geo.

Dopo aver completato la verifica con l'utente test, selezionare un gruppo pilota, magari dal proprio reparto IT, per utilizzare OneDrive in una nuova posizione geografica per la prima volta. Per questo primo gruppo, selezionare gli utenti che non hanno ancora OneDrive. È consigliabile inserire non più di cinque persone in questo gruppo iniziale e di aumentare gradualmente il numero, seguendo un approccio di implementazione in batch.

Ogni utente deve avere un *percorso dati preferito* (PDL) impostato in modo che Office 365 possa determinare in quale posizione geografica effettuare il provisioning di OneDrive. Il percorso dati preferito dell'utente deve corrispondere alla località satellite selezionata o alla posizione centrale. Il campo PDL non è obbligatorio ma è consigliabile che un PDL venga impostato per tutti gli utenti. Verrà eseguito il provisioning in posizione centrale dei carichi di lavoro di un utente senza un PDL in base alla logica Multi-Geo.   

Creare un elenco degli utenti e includere il nome dell'entità utente (UPN) e il codice di posizione per il percorso dati preferito appropriato. Includere l'utente test e il gruppo pilota iniziale per cominciare. Tale elenco è necessario per le procedure di configurazione.

Se gli utenti vengono sincronizzati da un sistema di Active Directory locale (AD) per Azure Active Directory (AAD), è necessario impostare il percorso dati preferito per gli utenti sincronizzati tramite la connessione di Azure Active Directory. È possibile configurare direttamente il percorso dati preferito per gli utenti sincronizzati con Azure Active Directory PowerShell. I passaggi per configurare PDL in AD e sincronizzarlo sono trattati in [Sincronizzazione di Azure Active Directory Connect: configurare il percorso dati preferito per le risorse di Office 365](https://docs.microsoft.com/it-IT/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

L'amministrazione di un tenant con funzionalità multi-geo può essere diverso da un tenant non multi-geo, dal momento che la maggior parte delle impostazioni SharePoint e OneDrive e i servizi hanno funzionalità multi-geo. È consigliabile consultare [Amministrazione di un ambiente multi-geo](administering-a-multi-geo-environment.md) prima di procedere con la configurazione.

Leggere [Esperienza utente in un ambiente multi-geo](multi-geo-user-experience.md) per i dettagli riguardanti l'esperienza degli utenti finali in un ambiente multi-geo.

Per iniziare a configurare OneDrive for Business Multi-Geo, vedere [Configurare OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).

Dopo aver completato la configurazione, è necessario [eseguire la migrazione delle raccolte OneDrive dell'utente](move-onedrive-between-geo-locations.md) per consentire agli utenti di lavorare dal proprio percorso dati preferito.
