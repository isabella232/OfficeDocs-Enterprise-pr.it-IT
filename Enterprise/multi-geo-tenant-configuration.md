---
title: Configurazione del tenant di OneDrive for Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Informazioni sulla configurazione di OneDrive for Business Multi-Geo
ms.openlocfilehash: 561025efc38199f3a92e228d5414a28df6eb12f0
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "21549967"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>Configurazione del tenant di OneDrive for Business Multi-Geo

Prima di configurare il tenant di OneDrive for Business Multi-Geo, è consigliabile leggere [Preparare l'implementazione di OneDrive for Business Multi-Geo](plan-for-multi-geo.md). Per seguire la procedura descritta in questo articolo, è necessario un elenco di tutte le posizioni che si desidera abilitare e degli utenti di prova da usare per il provisioning di tali posizioni.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Aggiungere Multi-Geo Capabilities nel piano di Office 365 del tenant

Per usare OneDrive for Business Multi-Geo, è necessario il piano _Multi-Geo Capabilities in Office 365_. Contattare il team dell'account per aggiungere questo piano al tenant. Il team dell'account a sua volta metterà in contatto l'utente con un esperto delle licenze per far configurare il tenant.

Tenere presente che il piano _Multi-Geo Capabilities in Office 365_ è un piano di servizio a livello di utente. È necessaria una licenza per ogni utente da ospitare in una posizione satellite. È possibile aggiungere più licenze nel tempo man mano che si aggiungono utenti alle posizioni satellite.

Una volta che nel tenant è stato effettuato il provisioning del piano _Multi-Geo Capabilities in Office 365_, la scheda **Posizioni geografiche** diventerà disponibile nell'[interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Impostare le posizioni dati consentite nel tenant

È necessario impostare una posizione dati consentita per SharePoint per ogni posizione geografica in cui si vuole usare OneDrive for Business. Le posizioni geografiche disponibili sono visualizzate nella tabella seguente:

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
<tr class="even">
<td align="left">Canada</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">Europa/Medio Oriente/Africa</td>
<td align="left">EUR</td>
</tr>
<tr class="even">
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

Per aggiungere una posizione geografica satellite

1. Aprire l'[interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).

2. Andare alla scheda **Posizioni geografiche**.

3. Fare clic su **Aggiungi posizione**.

4. Selezionare la posizione che si desidera aggiungere, quindi fare clic su **Avanti**.

5. Digitare il dominio da usare con la posizione geografica, quindi fare clic su **Aggiungi**. 

6. Fare clic su **Chiudi**.

Il provisioning può durare da alcune ore fino a 72 ore, a seconda delle dimensioni del tenant. Al termine del provisioning di una posizione satellite, verrà inviato un messaggio di posta elettronica di conferma. Quando la nuova posizione geografica diventa blu sulla mappa nella scheda **Posizioni geografiche** nell'interfaccia di amministrazione di OneDrive, è possibile procedere per impostare la posizione dati preferita dell'utente su tale posizione geografica. 

> [!IMPORTANT]
> La nuova posizione geografica satellite sarà configurata con le impostazioni predefinite. In questo modo sarà possibile configurare tale posizione geografica in base alle proprie esigenze di conformità locale.

## <a name="setting-users-preferred-data-location"></a>Impostazione della posizione dati preferita dell'utente
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Dopo aver abilitato i percorsi dati necessari, è possibile aggiornare gli account utente per utilizzare il percorso dati appropriato. Si consiglia di impostare una posizione dati preferita per ogni utente, anche se l'utente si trova nel percorso dati predefinito.

> [!TIP]
> Si consiglia di iniziare le convalide con un utente di test o con un gruppo limitato di utenti prima di distribuire Multi-Geo Capabilities in tutta l'organizzazione.

In AAD sono disponibili due tipi di oggetti utente: gli utenti solo cloud e gli utenti sincronizzati. Seguire le istruzioni appropriate per il tipo di utente.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Sincronizzare la posizione dati preferita dell'utente utilizzando AD Connect 

Se gli utenti dell'organizzazione vengono sincronizzati da un sistema Active Directory (AD) locale in Azure Active Directory (AAD), il relativo PreferredDataLocation deve essere popolato in Active Directory e sincronizzato in AAD. Seguire la procedura in [Sincronizzazione di Azure AD Connect: modificare la configurazione predefinita](https://docs.microsoft.com/it-IT/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) per configurare la sincronizzazione della posizione dati preferita da AD locale in AAD.

È consigliabile includere l'impostazione della posizione dati preferita dell'utente nel processo standard di creazione degli utenti.

> [!IMPORTANT]
> Per i nuovi utenti per cui non è stato eseguito il provisioning di OneDrive, attendere almeno 24 ore dopo la sincronizzazione della posizione dati preferita di un utente in ADD affinché le modifiche si propaghino prima che l'utente possa accedere a OneDrive for Business. Se si imposta la posizione dati preferita prima che l'utente acceda per completare il provisioning del proprio OneDrive for Business, il provisionig del nuovo OneDrive utente avviene sicuramente nella posizione corretta.

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Impostazione della posizione dati preferita per utenti solo cloud 

Se gli utenti dell'azienda non vengono sincronizzati da un sistema Active Directory (AD) locale ad Azure Active Directory (AAD), significa che sono stati creati in Office 365 o AAD e quindi la posizione dati preferita deve essere impostata tramite AAD PowerShell.

Le procedure descritte in questa sezione richiedono il [Modulo di Microsoft Azure Active Directory per il modulo di Windows PowerShell ](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se AAD PowerShell è già installato, assicurarsi di effettuare l'aggiornamento alla versione più recente.

1.  Aprire il modulo Microsoft Azure Active Directory per Windows PowerShell.

2.  Eseguire `Connect-MsolService` e inserire le credenziali dell'amministratore globale del tenant.

3.  Usare il cmdlet [Set-MsolUser](https://docs.microsoft.com/it-IT/powershell/msonline/v1/set-msoluser) per impostare la posizione dati preferita per ognuno degli utenti. Ad esempio:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    È possibile controllare che la posizione dati preferita sia stata aggiornata correttamente con il cmdlet Get-MsolUser. Ad esempio:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

È consigliabile includere l'impostazione della posizione dati preferita dell'utente nel processo standard di creazione degli utenti.

> [!IMPORTANT]
> Per i nuovi utenti per cui non è stato eseguito il provisioning di OneDrive, attendere almeno 24 ore dopo l'impostazione della posizione dati preferita di un utente affinché le modifiche si propaghino prima che l'utente possa accedere a SharePoint OneDrive. Se si imposta la posizione dati preferita prima che l'utente acceda per completare il provisioning del proprio OneDrive for Business, il provisionig del nuovo OneDrive utente avviene sicuramente nella posizione corretta.

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Provisioning di OneDrive e l'effetto della posizione dati preferita

Se l'utente ha già creato un sito OneDrive nel tenant, impostando la posizione dati preferita non verrà spostato automaticamente nel OneDrive esistente. Per spostare OneDrive di un utente, vedere [Spostamento geografico di OneDrive for Business](move-onedrive-between-geo-locations.md) e seguire le istruzioni sullo spostamento di OneDrive tra diverse posizioni geografiche.

Se l'utente non dispone di un sito di OneDrive all'interno del tenant, il provisioning di OneDrive verrà eseguito in base al valore della posizione dati preferita, presupponendo che la posizione dati preferita dell'utente corrisponda a una delle posizioni dati consentite della società (ADL).

## <a name="configuring-multi-geo-search"></a>Configurazione della ricerca multi-geografica

Il tenant multi-geografico aggrega le funzionalità di ricerca pertanto le query di ricerca restituiscono i risultati di tutte le posizioni all'interno del tenant.

Per impostazione predefinita, le ricerche da questi punti di ingresso restituiranno risultati aggregati, anche se ogni indice di ricerca si trova nella relativa posizione geografica rilevante:

- OneDrive for Business

- Delve

- Home page di SharePoint

- Centro ricerche

Inoltre, le funzionalità della ricerca multi-geografica possono essere configurate per applicazioni di ricerca personalizzate che utilizzano l'API del servizio di ricerca di SharePoint

Consultare [Configurare la ricerca per OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) per ottenere maggiori informazioni, comprese le limitazioni e un confronto delle funzionalità.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Convalida della configurazione di OneDrive for Business Multi-Geo

Ecco alcuni casi d'uso che è consigliabile includere nelle verifiche da effettuare prima di distribuire OneDrive for Business Multi-Geo in tutta l'azienda. Dopo aver completato questi test ed eventuali casi d'uso aggiuntivi rilevanti per la propria azienda, è possibile scegliere di continuare ad aggiungere utenti al gruppo pilota iniziale.

**OneDrive for Business**

Selezionare OneDrive dall'icona di avvio dell'app di Office 365 e verificare di essere automaticamente indirizzati alla posizione geografica appropriata per l'utente , in base alla posizione dati preferita dell'utente. OneDrive for Business ora inizia il provisioning in tale posizione. Al termine, provare a caricare e a scaricare alcuni documenti.

**App OneDrive per dispositivi mobili**

Accedere all'app per dispositivi mobili di OneDrive con le credenziali dell'account di prova. Verificare che sia possibile visualizzare i file di OneDrive for Business e di poterli usare dal dispositivo mobile.

**Client di sincronizzazione di OneDrive**

Confermare che il client di sincronizzazione di OneDrive rilevi automaticamente la posizione geografica di OneDrive for Business all'accesso. Se serve scaricare il client di sincronizzazione, è possibile fare clic su **Sincronizza** nella raccolta di OneDrive.

**Applicazioni di Office**

Verificare di riuscire ad accedere a OneDrive for Business effettuando l'accesso da un'applicazione Office, come Word. Aprire l'applicazione Office e selezionare "OneDrive – <TenantName>". Office rileverà la posizione di OneDrive e mostrerà i file che possono essere aperti.

**Condivisione**

Provare a condividere i file di OneDrive. Verificare che lo strumento di selezione delle persone mostri tutti gli utenti online di SharePoint indipendentemente dalla loro posizione geografica.
