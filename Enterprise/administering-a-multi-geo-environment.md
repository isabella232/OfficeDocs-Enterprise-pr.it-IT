---
title: Amministrazione di un ambiente multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informazioni sull'amministrazione di servizi di SharePoint e OneDrive in un ambiente multi-geo.
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a>Amministrazione di un ambiente multi-geo

Di seguito vengono esaminate funzionamento OneDrive e SharePoint services in un ambiente multi-geo.

#### <a name="onedrive-administrator-experience"></a>Esperienza dell'amministratore OneDrive

[Interfaccia di amministrazione di OneDrive](https://admin.onedrive.com) è disponibile una scheda **percorsi Geo** nel riquadro di spostamento sinistra le caratteristiche di mappare una località geografica dove è possibile visualizzare e gestire le posizioni geo. Utilizzare questa pagina per aggiungere o eliminare geo percorsi per il tenant.

#### <a name="taxonomy"></a>Tassonomia

È supportata una [tassonomia](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificato per i metadati aziendali gestiti da diverse ubicazioni geo, con il master ospitato in una posizione centralizzata per la propria azienda. È consigliabile gestire la tassonomia globale da una posizione centrale e tassonomia dell'ubicazione geografica satellitari solo aggiungere condizioni specifiche di una posizione. Termini tassonomia globali verranno sincronizzati per i percorsi di geo satellitari.

#### <a name="sharing"></a>Condivisione

Gli amministratori possono impostare e gestire i criteri di condivisione per ognuno dei rispettivi percorsi. I siti di OneDrive in ogni località geografica rispetta solo il corrispondente geo specifiche impostazioni di condivisione. Ad esempio, è possibile consentire [condivisione esterna](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) per la propria posizione centrale, ma non per la viceversa satellitari posizione o viceversa. Per OneDrive Multi-Geo, è necessario gestire le impostazioni di condivisione in ogni punto geo come questi non sono sincronizzati tra il tenant.

Per gestire condivisione visita la pagina di [interfaccia di amministrazione di OneDrive impostazioni di condivisione](https://admin.onedrive.com/?v=SharingSettings) . Per impostazione predefinita condivisione esterna è compatibile con tutti gli utenti in ogni punto satellitari.

#### <a name="user-profile-application"></a>Applicazione profili utente

In ogni località geografica esiste un' [applicazione profili utente](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) . Informazioni sul profilo di ogni utente è ospitati nella posizione geografica e disponibili per l'amministratore di tale posizione geografica.

Se si dispone di proprietà di profilo personalizzate, è consigliabile utilizzare lo stesso schema di profili in aree geografiche e popolare la proprietà di profilo personalizzate in tutti i percorsi geo o in caso di necessità.

#### <a name="bcs-secure-store-apps"></a>Servizi di integrazione Applicativa, servizio di archiviazione sicura, App

Servizi di integrazione Applicativa, servizio di archiviazione sicura e App presenti istanze geo separato, pertanto l'amministratore di SharePoint Online deve gestire e configurare questi servizi da ogni istanza geografica in cui si desidera visualizzarli deve essere presente.

#### <a name="security-and-compliance-admin-center"></a>Sicurezza e conformità Admin Center

Non esiste un solo centro conformità centrale per il tenant Multi-Geo: [centro conformità e sicurezza di Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Criteri di criterio DLP perdita di dati di informazioni protezione IP)

È possibile impostare il DLP IP criteri relativi a OneDrive for Business in Centro protezione e la conformità ambito criteri in base alle esigenze per il tenant intero o a utenti applicabili. Ad esempio: se si desidera selezionare un criterio per un utente di OneDrive in una posizione satellitare, selezionare questa opzione per applicare il criterio a una specifica OneDrive e immettere il nome utente dell'url OneDrive. Per indicazioni generali per la creazione di criteri DLP, vedere [Panoramica di criteri di prevenzione della perdita di dati](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) .

I criteri DLP sono sincronizzati automaticamente in base alle loro applicabilità per ogni località geografica.

L'implementazione dei criteri di prevenzione della perdita di dati e la protezione delle informazioni per tutti gli utenti in una posizione geografica, non è un'opzione disponibile nell'interfaccia utente, ma è necessario selezionare l'account OneDrive applicabile per il criterio o applicare i criteri a livello globale per tutti gli account OneDrive.

#### <a name="ediscovery"></a>eDiscovery 

Per impostazione predefinita, una ricerca eDiscovery responsabile o amministratore di un tenant multi-geo sarà in grado di condurre eDiscovery solo in una posizione centrale che tenant. Per supportare la possibilità di eseguire eDiscovery per i percorsi satellitare, è disponibile tramite PowerShell un nuovo parametro di filtro di sicurezza per conformità denominato "Region".

Amministratore globale di Office 365 necessario assegnare le autorizzazioni di gestione di eDiscovery per consentire ad altri eseguire eDiscovery e assegnare un parametro "Region" nel loro applicabile filtro di protezione di conformità per specificare il paese per eseguire eDiscovery come satellitari posizione, in caso contrario che non eDiscovery verranno eseguite per la posizione satellitare.

Quando il ruolo di responsabile o amministratore di eDiscovery è impostato per una posizione geografica particolare, eDiscovery responsabile o amministratore solo sarà in grado di eseguire operazioni di ricerca di eDiscovery contro i siti di SharePoint e i siti OneDrive disponibile in tale posizione geografica. Se un amministratore o eDiscovery Manager tenta di cercare i siti di SharePoint o OneDrive all'esterno della regione specificato, non verrà restituito alcun risultato. Inoltre, quando eDiscovery responsabile o amministratore di un'area attiva un'esportazione, dati vengono esportati in Azure istanza di tale area. Consente alle organizzazioni di mantenere in conformità non consentendo contenuto tra i bordi controllati da esportare.

> [!NOTE]
> Se è necessario che una responsabile per la ricerca in più aree di SharePoint di eDiscovery, sarà necessario un account utente diverso da creare per la gestione che specifica la regione alternativa in cui si trovano i siti di SharePoint o OneDrive eDiscovery.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Multi-Geo supportati Geo percorsi</strong></th>
<th align="left"><strong>sarà eDiscovery per SharePoint esportati i dati in questo percorso di dati Blob di Azure...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NOME</strong></td>
<td align="left">Usa Data Center</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">Europa Data Center</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Sud-Est o centri dati Asia orientale</td>
</tr>
<tr class="even">
<td align="left"><strong>POSSIBILE</strong></td>
<td align="left">Usa Data Center</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUSTRALIA</strong></td>
<td align="left">Sud-Est o centri dati Asia orientale</td>
</tr>
<tr class="even">
<td align="left"><strong>(COREANO)</strong></td>
<td align="left">Percorso dei dati del tenant predefinito</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Europa Data Center</td>
</tr>
<tr class="even">
<td align="left"><strong>GIAPPONESE</strong></td>
<td align="left">Sud-Est o centri dati Asia orientale</td>
</tr>
</tbody>
</table>

Per impostare il filtro di protezione di conformità per un'area:

1.  Apri Windows PowerShell

2.  Immetti   
    $s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -credenziali $cred-autenticazione base - AllowRedirection - SessionOption (PSSessionOption New - SkipCACheck - SkipCNCheck - SkipRevocationCheck)

    $un = Import-PSSession $s - AllowClobber  

3.  **Nuovo ComplianceSecurityFilter** **-Azione** TUTTO **- FilterName** EnterTheNameYouWantToAssign **-area** EnterTheRegionParameter **-utenti** EnterTheUserPrincipalName

    Ad esempio: **Nuovo ComplianceSecurityFilter-azione** NAMEDISCOVERYMANAGERS **- FilterName** tutti **-area** nome **-gli utenti** adwood@contosodemosx.onmicrosoft.com

Vedere l'articolo [New ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) per altri parametri e sintassi

#### <a name="audit-log-search"></a>Ricerca dei log di controllo

Un unificato di [Registro di controllo](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) per tutti i percorsi geo è disponibile nella pagina ricerca di Office 365 audit log. È possibile visualizzare tutte le voci del Registro di controllo da tra geos, ad esempio, attività nomi & EUR geo degli utenti verrà visualizzata in una singola visualizzazione org e quindi è possibile applicare filtri esistenti per visualizzare le attività dell'utente specifico.
