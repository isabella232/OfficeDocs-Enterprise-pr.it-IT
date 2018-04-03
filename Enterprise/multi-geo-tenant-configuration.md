---
title: OneDrive per la configurazione tenant Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informazioni su come configurare OneDrive per Business Multi-Geo.
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive per la configurazione tenant Business Multi-Geo

Prima di configurare il tenant di OneDrive per Business Multi-Geo, è necessario che leggere [Plan for OneDrive per Business Multi-Geo](plan-for-multi-geo.md). Per eseguire la procedura descritta in questo articolo, è necessario un elenco di utenti di test che si desidera eseguire il provisioning per i percorsi e i percorsi che si desidera abilitare.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Aggiungere la funzionalità Multi-Geo nel piano di Office 365 tenant di

Per utilizzare OneDrive per Business Multi-Geo, è necessario pianificare _Funzionalità Multi-Geo in Office 365_ . Lavorare con il team di account da aggiungere questo piano per il tenant. Il team di account verrà la connessione con lo specialista di licenze appropriato e ottenere il tenant configurato.

Si noti che il piano di _Funzionalità Multi-Geo in Office 365_ è un piano di servizio a livello utente. È necessaria una licenza per ogni utente che si desidera ospitare in una posizione setellite. È possibile aggiungere altre licenze nel tempo mentre si aggiungono utenti nelle posizioni satellitari.

Una volta tenant è stato fornito con il piano di _Funzionalità Multi-Geo in Office 365_ , la scheda **percorsi Geo** diventerà disponibile nell' [interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Impostare consentito dati posizioni (ADL) per il tenant

È necessario impostare una posizione di dati consentita per SharePoint per ogni località geografica cui si desidera utilizzare OneDrive for Business. Località geografica disponibili sono illustrate nella tabella seguente:

<table>
<thead>
<tr class="header">
<th align="left"><strong>Percorso</strong></th>
<th align="left"><strong>Codice</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Nord America</td>
<td align="left">NOME</td>
</tr>
<tr class="even">
<td align="left">Europa / Allinea al centro est / Africa</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Asia-Pacifico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australia</td>
<td align="left">AUSTRALIA</td>
</tr>
<tr class="odd">
<td align="left">Giappone</td>
<td align="left">GIAPPONESE</td>
</tr>
<tr class="even">
<td align="left">Canada</td>
<td align="left">POSSIBILE</td>
</tr>
<tr class="odd">
<td align="left">Regno Unito</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">Corea</td>
<td align="left">(COREANO)</td>
</tr>
</tbody>
</table>

Per aggiungere una posizione geografica satellitari

1. Aprire l' [interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).

2. Passare alla scheda **Geo predefinite** .

3. Fare clic su **Aggiungi percorso**.

4. Selezionare il percorso che si desidera aggiungere e quindi fare clic su **Avanti**.

5. Digitare il dominio che si desidera utilizzare con la posizione geografica e quindi fare clic su **Aggiungi**.

6. Fare clic su **Chiudi**.

Una volta completato il provisioning di una posizione satellitare, si riceverà una conferma di posta elettronica. Quando viene visualizzata nella nuova posizione geografica in blu nella mappa nella scheda **percorsi Geo** nell'interfaccia di amministrazione OneDrive, è possibile procedere impostare il percorso preferito dati degli utenti a tale posizione geografica. 

> [!IMPORTANT]
> La nuova posizione geografica satellitari configurerà con le impostazioni predefinite. In questo modo è possibile configurare tale posizione geografica in base alle proprie esigenze di conformità locale.

## <a name="setting-users-preferred-data-location"></a>Impostazione della posizione preferita dati degli utenti
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Una volta che si abilita le posizioni dei dati necessarie, è possibile aggiornare gli account utente per utilizzare il percorso di dati appropriato. Si consiglia di impostare un percorso dati preferita per tutti gli utenti, anche se l'utente è soggiorno nel percorso dei dati predefinito.

> [!TIP]
> È consigliabile iniziare convalida con un utente di test o di un piccolo gruppo di utenti prima di implementare le funzionalità Multi-Geo nell'organizzazione più ampia.

AAD sono disponibili due tipi di oggetti utente: cloud solo gli utenti e gli utenti sincronizzati. Seguire le istruzioni appropriate per il tipo di utente.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Sincronizzazione preferito percorso dell'utente dati tramite la connessione Active Directory 

Se gli utenti della società vengono sincronizzati da un sistema di Active Directory (AD) locale per Azure Active Directory (AAD), le PreferredDataLocation deve essere popolata in Active Directory e sincronizzati con AAD. Attenersi al processo di [sincronizzazione di Azure Active Directory Connect: apportare una modifica alla configurazione predefinita](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) configurare preferito della sincronizzazione di percorso dati in Active Directory locale per AAD.

È consigliabile includere l'impostazione percorso dati preferito dell'utente come parte del flusso di lavoro creazione utente standard.

> [!IMPORTANT]
> Per i nuovi utenti con alcun OneDrive il provisioning, attendere almeno 24 ore dopo PDL dell'utente viene sincronizzato con AAD le modifiche di propagare prima che l'utente accede a OneDrive for Business. (Impostazione dei dati Preferiti percorso prima che l'utente accede a fornire loro OneDrive for Business assicura di cui eseguire il provisioning nuovo OneDrive dell'utente nella posizione corretta.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>L'impostazione percorso dati preferito per il cloud solo gli utenti 

Se gli utenti della società non sono sincronizzati da un sistema di Active Directory (AD) locale per Azure Active Directory (AAD), vale a dire che vengono creati in Office 365 o AAD, quindi PDL deve essere impostata utilizzando PowerShell AAD.

Le procedure descritte in questa sezione richiedono [Microsoft modulo Azure Active Directory Module per Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se si dispone già di PowerShell AAD installati, accertarsi di aggiornare per la versione più recente.

1.  Aprire il modulo di Microsoft Azure Active Directory per Windows PowerShell.

2.  Eseguire `Connect-MsolService` e immettere le credenziali di amministratore globale per il tenant.

3.  Utilizzare il cmdlet [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) per impostare il percorso dei dati preferito per ogni utente. Per esempio:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    È possibile controllare per verificare che il percorso dei dati preferito sia stato aggiornato in modo corretto utilizzando il cmdlet Get-MsolUser. Per esempio:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

È consigliabile includere l'impostazione percorso dati preferito dell'utente come parte del flusso di lavoro creazione utente standard.

> [!IMPORTANT]
> Per i nuovi utenti con alcun OneDrive il provisioning, attendere almeno 24 ore dopo aver impostato le modifiche di propagare prima che l'utente accede a SharePoint OneDrive PDL dell'utente. (Impostazione dei dati Preferiti percorso prima che l'utente accede a fornire loro OneDrive for Business assicura di cui eseguire il provisioning nuovo OneDrive dell'utente nella posizione corretta.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Il provisioning di tipo OneDrive e l'effetto di PDL

Se l'utente dispone già di un sito di OneDrive creato nel tenant, l'impostazione loro PDL non passerà automaticamente loro OneDrive esistente. Per spostare OneDrive un utente, vedere [OneDrive for Business Geo spostare](move-onedrive-between-geo-locations.md) , segui le istruzioni in OneDrive lo spostamento tra le posizioni geo.

Se l'utente non dispone di un sito di OneDrive nel tenant, OneDrive eseguire il provisioning per essi in base al valore PDL supponendo che PDL per l'utente corrispondente a uno dei percorsi dei dati consentiti dell'azienda (ADLs).

## <a name="configuring-multi-geo-search"></a>Configurazione della ricerca Multi-Geo

Tenant Multi-Geo avranno funzionalità di ricerca aggregazione che consente una query di ricerca per restituire risultati da qualsiasi posizione all'interno del tenant.

Per impostazione predefinita, le ricerche di questi punti di ingresso restituirà risultati aggregati, anche se ogni indice di ricerca si trova all'interno di posizione geografica pertinenti:

- OneDrive per aziende

- Delve

- Home page di SharePoint

- Centro ricerche

Inoltre, le funzionalità di ricerca Multi-Geo è possibile configurare per le applicazioni di ricerca personalizzate che utilizzano l'API di ricerca di SharePoint.

Per istruzioni, incluse eventuali differenze e limitazioni, vedere [Configurare la ricerca di OneDrive per Business Multi-Geo](configure-search-for-multi-geo.md) .

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Convalida di OneDrive for Business Multi-Geo configurazione

Di seguito sono alcuni casi di utilizzo di base da includere nel piano di convalida prima largamente distribuzione OneDrive per Business Multi-Geo alla società. Dopo aver completato questi test e qualsiasi casi di utilizzo aggiuntivi rilevanti per l'azienda, è possibile procedere con l'aggiunta di utenti nel gruppo pilota iniziale.

**OneDrive for Business**

Selezionare il servizio di avvio di applicazioni di Office 365 OneDrive e confermare che si verrà indirizzati automaticamente nella posizione geografica appropriata per l'utente, basato su PDL dell'utente. OneDrive for Business deve iniziare il provisioning in tale posizione. Una volta eseguito il, provare a caricare e scaricare alcuni documenti.

**Applicazione Mobile OneDrive**

Accedere a App per dispositivi mobili di OneDrive con le credenziali dell'account di test. Verificare che è possibile visualizzare il OneDrive per i file di business e possono interagire con essi dal dispositivo mobile.

**Client di sincronizzazione OneDrive**

Verificare che il client di sincronizzazione OneDrive rileva automaticamente le OneDrive for Business geo-percorso dopo l'accesso. Se è necessario scaricare il client di sincronizzazione, è possibile fare clic su **Sincronizza** nella libreria di OneDrive.

**Applicazioni di Office**

Verificare di poter accedere a OneDrive for Business mediante l'accesso da un'applicazione di Office, ad esempio Word. Aprire Office dell'applicazione e seleziona "OneDrive- <TenantName>". Office rileva la posizione di OneDrive e visualizzare i file che è possibile aprire.

**Sharing**

Provare a condividere i file di OneDrive. Verificare che la selezione utenti Mostra tutti gli utenti di online SharePoint indipendentemente dalla posizione geografica.
