---
title: Configurazione del tenant multi-geografico di OneDrive for Business
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
ms.openlocfilehash: 29e69fa6e5a9715360b61024ee41dee4cd4b95b1
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>Configurazione del tenant multi-geografico di OneDrive for Business

Prima di configurare il tenant di OneDrive for Business Multi-Geo, assicurarsi di aver letto [Pianificazione di OneDrive for Business Multi-Geo](plan-for-multi-geo.md). Per seguire al procedura descritta in questo articolo, è necessario un elenco di tutte le posizioni che si desidera abilitare e testare gli utenti per i quali effettuare il provisioning di tali posizioni.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Aggiungere la funzionalità Multi-Geo nel piano di Office 365 del tenant

Per usare OneDrive for Business Multi-Geo, è necessario il piano _Funzionalità Multi-Geo in Office 365_. Lavorare con il team dell'account per aggiungere questo piano al tenant. Il team dell'account connetterà l'utente con lo specialista delle licenza appropriato per far configurare il tenant.

Tenere presente che il piano _Funzionalità Multi-Geo in Office 365_ è un piano di servizio a livello di utente. È necessaria una licenza per ogni utente da ospitare in una posizione satellite. È possibile aggiungere più licenze nel tempo man mano che si aggiungono utenti alle posizioni satellite.

Una volta che nel tenant è stato effettuato il provisioning del piano _Funzionalità Multi-Geo in Office 365_, la scheda **Posizioni geografiche** diventerà disponibile nell'[interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Impostare i percorsi dati consentiti nel tenant

È necessario impostare un percorso dati consentito per SharePoint per ogni posizione geografica in cui si vuole usare OneDrive for Business. Le posizioni geografiche disponibili sono visualizzate nella tabella seguente:

<table>
<thead>
<tr class="header">
<th align="left"><strong>Posizione</strong></th>
<th align="left"><strong>Codice</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Nord America</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">Europa/Medio Oriente/Africa</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Asia-Pacifico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australia</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Giappone</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Canada</td>
<td align="left">CAN</td>
</tr>
<tr class="odd">
<td align="left">Regno Unito</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">Corea</td>
<td align="left">KOR</td>
</tr>
</tbody>
</table>

Per aggiungere una posizione geografica satellite

1. Aprire l'[interfaccia di amministrazione di OneDrive](https://admin.onedrive.com).

2. Andare alla scheda **Posizioni geografiche**.

3. Fare clic su **Aggiungi percorso**.

4. Selezionare la posizione che si desidera aggiungere, quindi fare clic su **Avanti**.

5. Digitare il dominio da usare con la posizione geografica, quindi fare clic su **Aggiungi**. 

6. Fare clic su **Chiudi**.

Il provisioning potrebbe richiedere dalle poche alle 72 ore, a seconda delle dimensioni del tenant. Al termine del provisioning di una posizione satellite, verrà inviato un messaggio di posta elettronica di conferma. Quando la nuova posizione geografica diventa blu sulla mappa nella scheda **Posizioni geografiche** nell'interfaccia di amministrazione di OneDrive, è possibile procedere per impostare il percorso dati preferito dell'utente su tale posizione geografica. 

> [!IMPORTANT]
> La nuova posizione geografica satellite sarà configurata con le impostazioni predefinite. In questo modo sarà possibile configurare tale posizione geografica in base alle proprie esigenze di conformità locale.

## <a name="setting-users-preferred-data-location"></a>Impostazione del percorso dati preferito dell'utente
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Dopo aver abilitato i percorsi dati necessari, è possibile aggiornare gli account utente per utilizzare il percorso dati appropriato. Si consiglia di impostare un percorso dati preferito per ogni utente, anche se l'utente si trova nel percorso dati predefinito.

> [!TIP]
> Si consiglia di iniziare le convalide con un utente di test o con un gruppo limitato di utenti prima di distribuire le funzionalità Multi-Geo in tutta l'organizzazione.

In AAD sono disponibili due tipi di oggetti utente: gli utenti solo cloud e gli utenti sincronizzati. Seguire le istruzioni appropriate per il tipo di utente.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Sincronizzare il percorso dati preferito dell'utente utilizzando AD Connect 

Se gli utenti dell'organizzazione vengono sincronizzati da un sistema Active Directory (AD) locale in Azure Active Directory (AAD), il relativo PreferredDataLocation deve essere popolato in Active Directory e sincronizzati in AAD. Seguire la procedura in [Sincronizzazione di Azure AD Connect: modificare la configurazione predefinita](https://docs.microsoft.com/it-IT/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) per configurare la sincronizzazione del percorso dati preferito da AD locale in AAD.

È consigliabile includere l'impostazione del percorso dati preferito dell'utente nel flusso di lavoro di creazione di un utente standard.

> [!IMPORTANT]
> Per i nuovi utenti per cui non è stato eseguito il provisioning di OneDrive, attendere almeno 24 ore dopo la sincronizzazione del percorso dati preferito di un utente in ADD affinché le modifiche si propaghino prima che l'utente possa accedere a OneDrive for Business. Impostare il percorso dati preferito prima che l'utente acceda a l provisioning del proprio OneDrive for Business garantisce che il provisionig del nuovo OneDrive utente avvenga nella posizione corretta).

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Impostazione del percorso dati preferito per utenti solo cloud 

Se gli utenti dell'azienda non vengono sincronizzati da un sistema Active Directory (AD) locale ad Azure Active Directory (AAD), il che significa che sono stati creati in Office 365 o AAD, allora il percorso dati preferito deve essere impostato tramite AAD PowerShell.

Le procedure descritte in questa sezione richiedono il [Modulo di Microsoft Azure Active Directory per il modulo di Windows PowerShell ](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se AAD PowerShell è già installato, assicurarsi di effettuare l'aggiornamento alla versione più recente.

1.  Aprire il modulo Microsoft Azure Active Directory per Windows PowerShell.

2.  Eseguire `Connect-MsolService` e inserire le credenziali dell'amministratore globale del tenant.

3.  Usare il cmdlet [Set-MsolUser](https://docs.microsoft.com/it-IT/powershell/msonline/v1/set-msoluser) per impostare il percorso dati preferito per ognuno degli utenti. Ad esempio:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    È possibile controllare per verificare che il percorso dati preferito sia stato aggiornato correttamente con il cmdlet Get-MsolUser. Ad esempio:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

È consigliabile includere l'impostazione del percorso dati preferito dell'utente nel flusso di lavoro di creazione di un utente standard.

> [!IMPORTANT]
> Per i nuovi utenti per cui non è stato eseguito il provisioning di OneDrive, attendere almeno 24 ore dopo l'impostazione del percorso dati preferito di un utente affinché le modifiche si propaghino prima che l'utente possa accedere a SharePoint OneDrive. Impostare il percorso dati preferito prima che l'utente acceda a l provisioning del proprio OneDrive for Business garantisce che il provisionig del nuovo OneDrive utente avvenga nella posizione corretta).

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Provisioning di OneDrive e l'effetto del percorso dati preferito

Se l'utente ha già creato un sito OneDrive nel tenant, impostando il percorso dati preferito non verrà spostato automaticamente nel OneDrive esistente. Per spostare OneDrive di un utente, vedere [Spostamento geografico di OneDrive for Business](move-onedrive-between-geo-locations.md) e seguire le istruzioni sullo spostamento di OneDrive tra diverse posizioni geografiche.

Se l'utente non dispone di un sito di OneDrive all'interno del tenant, il provisioning di OneDrive verrà eseguito in base al valore del percorso dati preferito, presupponendo che il percorso dati preferito dell'utente corrisponda a uno dei percorsi dati consentiti della società (ADL).

## <a name="configuring-multi-geo-search"></a>Configurazione della ricerca multi-geografica

Il tenant multi-geografico aggregherà le funzionalità di ricerca consentendo a una query di ricerca di restituire risultati da una qualsiasi posizione nel tenant.

Per impostazione predefinita, le ricerche da questi punti di ingresso restituiranno risultati aggregati, anche se ogni indice di ricerca si trova nella relativa posizione geografica rilevante:

- OneDrive for Business

- Delve

- Home page di SharePoint

- Centro ricerche

Inoltre, le funzionalità della ricerca multi-geografica possono essere configurate per applicazioni di ricerca personalizzate che usano l'API Ricerca di SharePoint.

Consultare [Configurare la ricerca per OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) per istruzioni che includono limitazioni e differenze.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Convalida della configurazione di OneDrive for Business Multi-Geo

Di seguito sono illustrati alcuni casi d'uso che si potrebbe voler includere nel piano di convalida prima di distribuire ampiamente OneDrive for Business Multi-Geo nell'azienda. Dopo aver completato questi test ed eventuali casi d'uso aggiuntivi rilevanti per la propria azienda, è possibile scegliere di continuare ad aggiungere utenti al gruppo pilota iniziale.

**OneDrive for Business**

Selezionare OneDrive dall'icona di avvio dell'app di Office 365 e verificare di essere automaticamente indirizzati alla posizione geografica appropriata per l'utente , in base al percorso dati preferito dell'utente. OneDrive for Business ora inizia il provisioning in tale posizione. Al termine, provare a caricare e a scaricare alcuni documenti.

**App OneDrive per dispositivi mobili**

Accedere all'app per dispositivi mobili di OneDrive con le credenziali dell'account di prova. Verificare che sia possibile visualizzare i file di OneDrive for Business e di poterli usare dal dispositivo mobile.

**Client di sincronizzazione di OneDrive**

Confermare che il client di sincronizzazione di OneDrive rilevi automaticamente la posizione geografica di OneDrive for Business all'accesso. Se serve scaricare il client di sincronizzazione, è possibile fare clic su **Sincronizza** nella raccolta di OneDrive.

**Applicazioni di Office**

Verificare di riuscire ad accedere a OneDrive for Business effettuando l'accesso da un'applicazione Office, come Word. Aprire l'applicazione Office e selezionare "OneDrive – <TenantName>". Office rileverà la posizione di OneDrive e mostrerà i file che possono essere aperti.

**Condivisione**

Provare a condividere i file di OneDrive. Verificare che lo strumento di selezione delle  persone mostri tutti gli utenti online di SharePoint indipendentemente dalla loro posizione geografica.
