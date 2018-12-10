---
title: Amministrare un ambiente multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni sull'amministrazione di servizi SharePoint e OneDrive in un ambiente multi-geo.
ms.openlocfilehash: 823b3a4c1d063a4d398b7f734c2171e856ee1244
ms.sourcegitcommit: 4a1d6c43da44b559136f2bf422a531bea5f48dbb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2018
ms.locfileid: "27210124"
---
# <a name="administering-a-multi-geo-environment"></a>Amministrare un ambiente multi-geo

Di seguito viene descritto come funzionano i servizi OneDrive e SharePoint in un ambiente multi-geo.

#### <a name="onedrive-administrator-experience"></a>Esperienza dell'amministratore OneDrive

L'[Interfaccia di amministrazione di OneDrive](https://admin.onedrive.com) è una scheda di **posizioni geografiche** nel riquadro di spostamento di sinistra che include una mappa delle posizioni geografiche in cui è possibile visualizzare e gestire le proprie posizioni geografiche. Utilizzare questa pagina per aggiungere o eliminare posizioni geografiche nel tenant.

#### <a name="taxonomy"></a>Tassonomia

Microsoft offre supporto per una [tassonomia](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificata per i metadati gestiti dell'organizzazione tra più posizioni geografiche, ospitando la scheda nella posizione centrale dell'azienda. È consigliabile gestire la tassonomia globale da una posizione centrale e aggiungere solo termini specifici sulla posizione alla tassonomia delle posizioni satellite. I termini di tassonomia globale verranno sincronizzati con le posizioni satellite.

#### <a name="sharing"></a>Condivisione

Gli amministratori possono impostare e gestire criteri di condivisione per ognuna delle posizioni. I siti di OneDrive in ogni posizione geografica rispetteranno solo le impostazioni di condivisione specifiche per posizioni geografiche corrispondenti. Ad esempio, è possibile consentire la [condivisione esterna](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) per la posizione centrale, ma non per la posizione satellite o viceversa. Si noti che le impostazioni di condivisione non consentono la configurazione delle limitazioni per la condivisione tra le posizioni geografiche.

Per OneDrive Multi-Geo, è necessario gestire le impostazioni di condivisione in tutte le posizioni geografiche, poiché queste non sono sincronizzate tra tenant. Per gestire la condivisione, visitare la pagina relativa alle [impostazioni di condivisione dell'interfaccia di amministrazione di OneDrive](https://admin.onedrive.com/?v=SharingSettings). Per impostazione predefinita la condivisione esterna è disponibile per qualunque utente in ogni posizione satellitare.

#### <a name="user-profile-application"></a>Applicazione profilo utente

Esiste un'[applicazione profilo utente](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in ogni posizione geografica. Le informazioni del profilo di ogni utente si trovano nella relativa posizione geografica e sono a disposizione dell'amministratore per tale posizione.

Se si dispone di proprietà personalizzate del profilo, è consigliabile usare lo stesso schema del profilo tra le aree geografiche e popolare le proprietà personalizzate del profilo anche in tutte le posizioni geografiche o laddove necessario. Per istruzioni su come popolare i dati dei profili utente a livello di programmazione, fare riferimento a [API di aggiornamento del profilo utente in blocco](https://docs.microsoft.com/it-IT/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)

#### <a name="bcs-secure-store-apps"></a>BCS, Archiviazione sicura, App

Tutti i servizi BCS, Archiviazione sicura e App presentano istanze separate in ogni posizione satellite, pertanto l'amministratore di SharePoint Online deve gestirli e configurarli separatamente da ogni posizione satellite.

#### <a name="security-and-compliance-admin-center"></a>Centro sicurezza e conformità

Per il tenant Multi-Geo esiste un centro di conformità centrale: [Centro sicurezza e conformità di Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Criteri di protezione delle informazioni (IP) e prevenzione della perdita di dati (DLP) 

È possibile impostare i criteri IP e DLP per OneDrive for Business nel Centro sicurezza e conformità, per cercare i criteri necessari per l'intero tenant o per gli utenti validi. Ad esempio: se si desidera selezionare un criterio per un utente di OneDrive in una località satellite, selezionare questa opzione per applicare i criteri a un OneDrive specifico e immettere l'url OneDrive dell'utente. Per indicazioni generali sulla creazione di criteri, vedere [Panoramica dei criteri di prevenzione della perdita dei dati](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).

I criteri DLP vengono sincronizzati automaticamente in base alle loro applicabilità per ciascuna posizione geografica.

Non è possibile implementare i criteri di prevenzione della perdita dei dati e di protezione delle informazioni a tutti gli utenti in una posizione geografica attraverso l'interfaccia utente, è invece necessario selezionare gli account OneDrive applicabili per il criterio o applicare i criteri a livello globale a tutti gli account OneDrive.

#### <a name="ediscovery"></a>eDiscovery 

Per impostazione predefinita, un manager o amministratore di eDiscovery di un tenant multi-geo potrà eseguire eDiscovery solo nella posizione centrale di tale tenant. Per supportare la possibilità di eseguire eDiscovery per le posizioni satelliti, è disponibile un nuovo parametro filtro di sicurezza di conformità denominato "Area" tramite PowerShell.

L'amministratore globale di Office 365 deve assegnare le autorizzazioni di manager di eDiscovery per consentire ad altri di eseguire eDiscovery e assegnare un parametro "Area" nel filtro di sicurezza e conformità applicabile per specificare l'area per l'esecuzione di eDiscovery come posizione satellite, in caso contrario nessuna istanza di eDiscovery verrà eseguita per la posizione geografica satellite.

Quando è impostato il ruolo di manager o amministratore di eDiscovery per una posizione satellite specifica, sarà possibile eseguire operazioni di ricerca eDiscovery solo per i siti di SharePoint e OneDrive che si trovano in tale posizione satellite. Se un manager o amministratore di eDiscovery tenta di cercare siti di SharePoint o OneDrive all'esterno della posizione satellite specificata, non visualizzerà alcun risultato. Inoltre, quando il manager o amministratore di eDiscovery di una posizione satellite attiva un'esportazione, i dati vengono esportati nell'istanza di Azure di quest'area. Ciò consente alle organizzazioni di rimanere conformi, non permettendo di esportare contenuti oltre i confini controllati.

> [!NOTE]
> Tuttavia, se dovesse essere necessario per un manager di eDiscovery effettuare una ricerca in più posizioni satellite di SharePoint, sarà necessario creare un altro account utente per il manager di eDiscovery, specificando la posizione satellite alternativa in cui si trovano i siti di OneDrive o SharePoint.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Posizioni geografiche supportate da Multi-Geo</strong></th>
<th align="left"><strong>I dati esportati in eDiscovery per SharePoint saranno disponibili in questa posizione dati Blob di Azure...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Datacenter Asia orientale o sudorientale</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">Datacenter Asia orientale o sudorientale</td>
</tr>
<tr class="even">
<td align="left"><strong>CAN</strong></td>
<td align="left">Datacenter Stati Uniti</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">Datacenter Europa</td>
</tr>
<tr class="odd">
<td align="left"><strong>FRA</strong></td>
<td align="left">Datacenter Europa</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Datacenter Europa</td>
</tr>
<tr class="even">
<td align="left"><strong>IND</strong></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">Datacenter Asia orientale o sudorientale</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN </strong></td>
<td align="left">Datacenter Asia orientale o sudorientale</td>
</tr>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">Datacenter Stati Uniti</td>
</tr>
</tbody>
</table>

Per impostare il filtro di sicurezza di conformità per un'area geografica:

1.  Aprire Windows PowerShell

2.  Immettere  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    Ad esempio: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

Vedere l’articolo [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) per ulteriori parametri e sintassi

#### <a name="audit-log-search"></a>Ricerca dei log di controllo

Un [log di controllo](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) per tutte le posizioni satellite è disponibile dalla pagina di ricerca dei log di controllo di Office 365. Sono disponibili tutte le voci di log di controllo tra le varie aree geografiche, ad esempio, attività di utenti dell'area geografica NAM e EUR verranno visualizzate in un'unica vista dell'organizzazione e sarà possibile applicarvi i filtri esistenti per vedere le attività di un utente specifico.
