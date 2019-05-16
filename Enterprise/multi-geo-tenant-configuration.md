---
title: Configurazione del tenant di Office 365 Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Configurare eDiscovery per Office 365 Multi-Geo.
ms.openlocfilehash: e1e76482e6b775a2bb1b6ea4428112af738d6a5a
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070012"
---
# <a name="office-365-multi-geo-tenant-configuration"></a>Configurazione del tenant di Office 365 Multi-Geo

Prima di configurare il tenant di Office 365 Multi-Geo, assicurarsi di aver letto [Piano di Office 365 Multi-Geo](plan-for-multi-geo.md). Per eseguire la procedura descritta in questo articolo, è necessario un elenco delle posizioni geografiche che si desidera abilitare come località satelliti e gli utenti test che si desidera predisporre in queste posizioni.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Aggiungere Multi-Geo Capabilities nel piano di Office 365 del tenant

Per usare Office 365 Multi-Geo, è necessario il _Piano di Multi-Geo Capabilities in Office 365_. Rivolgersi al team dell’account per aggiungere questo piano al tuo tenant. Il team dell’account connetterà l’utente con lo specialista della licenza appropriato e configurerà il tenant.

Tenere presente che il piano _Multi-Geo Capabilities in Office 365_ è un piano di servizio a livello di utente. È necessaria una licenza per ogni utente da ospitare in una posizione satellite. È possibile aggiungere più licenze nel tempo man mano che si aggiungono utenti alle posizioni satellite.

Una volta che nel tenant è stato effettuato il provisioning del piano _Multi-Geo Capabilities in Office 365_, la scheda **Posizioni geografiche** diventerà disponibile nell'interfaccia di amministrazione di OneDrive e SharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>Aggiungere posizioni satellite al tenant

È necessario aggiungere una posizione satellite per ogni località geografica in cui si desidera memorizzare i dati. Nella tabella seguente, sono elencate le località geografiche disponibili:

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Schermata della pagina con le località geografiche nell'interfaccia di amministrazione di SharePoint](media/sharepoint-multi-geo-admin-center.png)

Per aggiungere una posizione satellite

1. Aprire l'interfaccia di amministrazione di SharePoint.

2. Andare alla scheda **Posizioni geografiche**.

3. Fare clic su **Aggiungi posizione**.

4. Selezionare la posizione che si desidera aggiungere, quindi fare clic su **Avanti**.

5. Digitare il dominio da usare con la posizione geografica, quindi fare clic su **Aggiungi**. 

6. Fare clic su **Chiudi**.

Il provisioning può durare da alcune ore fino a 72 ore, a seconda delle dimensioni del tenant. Al termine del provisioning di una posizione satellite, verrà inviato un messaggio di posta elettronica di conferma. Quando la nuova posizione geografica diventa blu sulla mappa nella scheda **Posizioni geografiche** nell'interfaccia di amministrazione di OneDrive, è possibile procedere per impostare la posizione dati preferita dell'utente su tale posizione geografica. 

> [!IMPORTANT]
> La nuova posizione satellite sarà configurata con le impostazioni predefinite. In questo modo sarà possibile configurare tale posizione satellite in base alle proprie esigenze di conformità locale.

## <a name="setting-users-preferred-data-location"></a>Impostare la posizione dati preferita dell'utente
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Dopo aver abilitato le posizioni satellite necessarie, è possibile aggiornare gli account utente per utilizzare il percorso dati preferito appropriato. Si consiglia di impostare una posizione dati preferita per ogni utente, anche se l'utente si trova in una posizione centrale.

> [!IMPORTANT]
> Se il percorso dei dati preferito dell'utente è impostato su una posizione che non sia stata configurata come posizione satellitare o posizione centrale, il sistema imposterà la posizione centrale come predefinita durante il provisioning dei siti di OneDrive, SharePoint e delle cassette postali di gruppo.

> [!TIP]
> Si consiglia di iniziare le convalide con un utente di test o con un gruppo limitato di utenti prima di distribuire le funzionalità multi-geografiche in tutta l'organizzazione.

Sono disponibili due tipi di oggetti utente in Azure Active Directory: solo utenti cloud e utenti sincronizzati. Seguire le istruzioni appropriate in base al tipo di utente.

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a>Sincronizzare la posizione dati preferita dell'utente utilizzando Azure Active Directory Connect 

Se gli utenti dell'organizzazione vengono sincronizzati da un sistema Active Directory locale in Azure Active Directory, il relativo PreferredDataLocation deve essere popolato in Active Directory e sincronizzato in AAD. Seguire la procedura in [Sincronizzazione di Azure AD Connect: configurare la posizione dei dati preferita per le risorse di Office 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) per configurare la sincronizzazione della posizione dati preferita da Active Directory locale in Azure Active Directory.

È consigliabile includere l'impostazione della posizione dati preferita dell'utente nel processo standard di creazione degli utenti.

> [!IMPORTANT]
> Per i nuovi utenti senza il provisioning di OneDrive, attendere almeno 24 ore dopo che il PDL di un utente viene sincronizzato con Azure Active Directory perché le modifiche si propaghino, prima che l'utente acceda a OneDrive for Business. (Impostare la posizione dati preferita prima che l'utente si connetta per effettuare il provisioning di OneDrive for Business consente al nuovo OneDrive dell'utentedi effettuareil provisioning nella posizione corretta.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Impostazione della posizione dati preferita per utenti solo cloud 

Se gli utenti dell'azienda non vengono sincronizzati da un sistema Active Directory locale ad Azure Active Directory, significa che sono stati creati in Office 365 o Azure Active Directory e quindi la posizione dati preferita deve essere impostata tramite Azure Active Directory PowerShell.

Le procedure descritte in questa sezione richiedono il [Modulo di Microsoft Azure Active Directory per il modulo di Windows PowerShell ](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se Azure Active Directory PowerShell è già installato, assicurarsi di effettuare l'aggiornamento alla versione più recente.

1.  Aprire il modulo Microsoft Azure Active Directory per Windows PowerShell.

2.  Eseguire `Connect-MsolService` e inserire le credenziali dell'amministratore globale del tenant.

3.  Usare il cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) per impostare la posizione dati preferita per ognuno degli utenti. Ad esempio:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    È possibile controllare che la posizione dati preferita sia stata aggiornata correttamente con il cmdlet Get-MsolUser. Ad esempio:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Screenshot della finestra di PowerShell con il iset-msoluser](media/multi-geo-tenant-configuration-image3.png)

È consigliabile includere l'impostazione della posizione dati preferita dell'utente nel processo standard di creazione degli utenti.

> [!IMPORTANT]
> Per i nuovi utenti senza il provisioning di OneDrive, attendere almeno 24 ore dopo che il PDL di un utente venga sincronizzato con Azure Active Directory perché le modifiche si propaghino, prima che l'utente acceda a OneDrive. (Impostare la posizione dati preferita prima che l'utente si connetta per effettuare il provisioning di OneDrive for Business consente al nuovo OneDrive dell'utentedi effettuareil provisioning nella posizione corretta.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Provisioning di OneDrive e l'effetto della posizione dati preferita

Se l'utente ha già un sito OneDrive creato nel tenant, impostare il PDL non sposterà automaticamente il OneDrive esistente. Per spostare il OneDrive di un utente, vedere [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md), e seguire le istruzioni come spostare OneDrive tra due località geografiche. (Si noti che la cassetta postale di Exchange dell'utente non si sposta automaticamente quando si imposta la posizione dati preferita dell'utente.)

Se l'utente non dispone di un sito di OneDrive all'interno del tenant, il provisioning di OneDrive verrà eseguito in base al valore della posizione dati preferita, presupponendo che la posizione dati preferita dell'utente corrisponda a una delle posizioni satellite della società.

## <a name="configuring-multi-geo-search"></a>Configurazione della ricerca multi-geografica

Il tenant multi-geografico aggrega le funzionalità di ricerca pertanto le query di ricerca restituiscono i risultati di tutte le posizioni all'interno del tenant.

Per impostazione predefinita, le ricerche da questi punti di ingresso restituiranno risultati aggregati, anche se ogni indice di ricerca si trova nella relativa posizione geografica rilevante:

- OneDrive for Business

- Delve

- Home page di SharePoint

- Centro ricerche

Inoltre, le funzionalità della ricerca multi-geografica possono essere configurate per applicazioni di ricerca personalizzate che utilizzano l'API del servizio di ricerca di SharePoint.

Consultare [Configurare la ricerca per OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) per ottenere maggiori informazioni, comprese le limitazioni e un confronto delle funzionalità.

## <a name="validating-the-office-365-multi-geo-configuration"></a>La convalida della configurazione di Office 365 Multi-Geo

Ecco alcuni casi di utilizzo di base che è opportuno includere nel piano di convalida prima della distribuzione di Office 365 Multi-Geo su vasta scala all’interno dell’azienda. Dopo aver completato i test e i casi di utilizzo aggiuntivi di interesse per l'azienda, è possibile procedere con l'aggiunta di utenti nel gruppo pilota iniziale.

**OneDrive for Business**

Selezionare OneDrive dall'icona di avvio dell'applicazione di Office 365 e verificare che si venga indirizzati automaticamente alla posizione geografica appropriata per l'utente, in base alla sua posizione dati preferita. OneDrive for Business dovrebbe ora iniziare il provisioning in quella posizione. Una volta effettuato il provisioning, provare a caricare e scaricare alcuni documenti.

**App OneDrive per dispositivi mobili**

Accedere all'app per dispositivi mobili di OneDrive con le credenziali dell'account di prova. Verificare che sia possibile visualizzare i file di OneDrive for Business e di poterli usare dal dispositivo mobile.

**Client di sincronizzazione di OneDrive**

Confermare che il client di sincronizzazione di OneDrive rilevi automaticamente la posizione geografica di OneDrive for Business all'accesso. Se serve scaricare il client di sincronizzazione, è possibile fare clic su **Sincronizza** nella raccolta di OneDrive.

**Applicazioni di Office**

Verificare di riuscire ad accedere a OneDrive for Business effettuando l'accesso da un'applicazione Office, come Word. Aprire l'applicazione Office e selezionare "OneDrive – <TenantName>". Office rileverà la posizione di OneDrive e mostrerà i file che possono essere aperti.

**Condivisione**

Provare a condividere i file di OneDrive. Verificare che lo strumento di selezione delle persone mostri tutti gli utenti online di SharePoint indipendentemente dalla loro posizione geografica.
