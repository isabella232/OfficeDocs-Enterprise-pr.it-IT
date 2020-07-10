---
title: Configurazione del tenant di Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Informazioni su come configurare Microsoft 365 Multi-Geo.
ms.openlocfilehash: 928033dcbec0ad0b52f24bd0bec4dd6b9f9331bc
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052569"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Configurazione del tenant di Microsoft 365 Multi-Geo

Prima di configurare il tenant per Microsoft 365 Multi-Geo, assicurarsi di aver letto [Piano per Microsoft 365 Multi-Geo](plan-for-multi-geo.md). Per eseguire la procedura descritta in questo articolo, è necessario un elenco delle posizioni geografiche che si desidera abilitare come località satelliti e gli utenti test che si desidera predisporre in queste posizioni.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Aggiungere Multi-Geo Capabilities nel piano di Microsoft 365 del tenant

Per usare Office 365 Multi-Geo, è necessario il piano _Multi-Geo Capabilities in Microsoft 365_. Rivolgersi al team dell’account per aggiungere questo piano al tuo tenant. Il team dell’account connetterà l’utente con lo specialista della licenza appropriato e configurerà il tenant.

Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.

Una volta che nel tenant è stato effettuato il provisioning del piano _Multi-Geo Capabilities in Microsoft 365_, la scheda **Posizioni geografiche** diventerà disponibile nell'interfaccia di amministrazione di OneDrive e SharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>Aggiungere posizioni satellite al tenant

È necessario aggiungere una posizione satellite per ogni località geografica in cui si desidera memorizzare i dati. Nella tabella seguente, sono elencate le località geografiche disponibili:

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Schermata della pagina con le località geografiche nell'interfaccia di amministrazione di SharePoint](media/sharepoint-multi-geo-admin-center.png)

Per aggiungere una posizione satellite

1. Aprire l'interfaccia di amministrazione di SharePoint.

2. Andare alla scheda **Posizioni geografiche**.

3. Fare clic su **Aggiungi posizione**.

4. Selezionare la posizione che si desidera aggiungere, quindi fare clic su **Avanti**.

5. Digitare il dominio da usare con la posizione geografica, quindi fare clic su **Aggiungi**. 

6. Fare clic su **Chiudi**.

Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location. 

> [!IMPORTANT]
> Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.

## <a name="setting-users-preferred-data-location"></a>Impostare la posizione dati preferita dell'utente
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.

> [!IMPORTANT]
> Se il percorso dei dati preferito dell'utente è impostato su una posizione che non sia stata configurata come posizione satellitare o posizione centrale, il sistema imposterà la posizione centrale come predefinita durante il provisioning dei siti di OneDrive, SharePoint e delle cassette postali di gruppo.

> [!TIP]
> Si consiglia di iniziare le convalide con un utente di test o con un gruppo limitato di utenti prima di distribuire le funzionalità multi-geografiche in tutta l'organizzazione.

Sono disponibili due tipi di oggetti utente in Azure Active Directory (Azure AD): solo utenti cloud e utenti sincronizzati. Seguire le istruzioni appropriate in base al tipo di utente.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Sincronizzare la posizione preferita dei dati dell'utente utilizzando Azure AD Connect 

Se gli utenti dell'organizzazione sono sincronizzati da un sistema di Active Directory locale con Azure AD, il PreferredDataLocation deve essere popolato in Active Directory e sincronizzato con Azure AD.

Seguire la procedura in [Sincronizzazione di Azure Active Directory Connect: configurare la posizione preferita dei dati per le risorse di Microsoft 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) per configurare la sincronizzazione della posizione preferita dei dati da Active Directory Domain Services (AD DS) locale a Azure AD.

È consigliabile includere l'impostazione della posizione dati preferita dell'utente nel processo standard di creazione degli utenti.

> [!IMPORTANT]
> Per i nuovi utenti senza il provisioning di OneDrive, attendere almeno 24 ore dopo che il PDL di un utente viene sincronizzato con Azure AD perché le modifiche si propaghino, prima che l'utente acceda a OneDrive for Business. (Impostare la posizione dati preferita prima che l'utente si connetta per effettuare il provisioning di OneDrive for Business consente al nuovo OneDrive dell'utentedi effettuareil provisioning nella posizione corretta.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Impostazione della posizione dati preferita per utenti solo cloud 

Se gli utenti dell'azienda non vengono sincronizzati da un sistema Active Directory locale ad Azure AD, significa che sono stati creati in Microsoft 365 o Azure AD e quindi la posizione preferita dei dati deve essere impostata tramite il modulo Azure Active Directory per Windows PowerShell.

La procedura contenuta in questa sezione richiede il [modulo di Microsoft Azure Active Directory per Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se il modulo è già installato, assicurarsi di eseguire l'aggiornamento alla versione più recente.

1.  [Connettersi e accedere](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con le credenziali di amministratore globale del tenant.

2.  Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:

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

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Convalida della configurazione di Microsoft 365 Multi-Geo

Ecco alcuni casi di utilizzo di base che è opportuno includere nel piano di convalida prima della distribuzione di Microsoft 365 Multi-Geo su vasta scala all'interno dell'azienda. Dopo aver completato i test e i casi di utilizzo aggiuntivi di interesse per l'azienda, è possibile procedere con l'aggiunta di utenti nel gruppo pilota iniziale.

**OneDrive for Business**

Selezionare OneDrive dall'icona di avvio delle app di Microsoft 365 e verificare che si venga indirizzati automaticamente alla posizione geografica appropriata per l'utente, in base alla sua posizione dati preferita. OneDrive for Business dovrebbe ora iniziare il provisioning in quella posizione. Una volta effettuato il provisioning, provare a caricare e scaricare alcuni documenti.

**App OneDrive per dispositivi mobili**

Accedere all'app OneDrive per dispositivi mobili con le credenziali dell'account di test. Verificare che sia possibile visualizzare i file di OneDrive for Business e di poterli usare dal dispositivo mobile.

**Client di sincronizzazione di OneDrive**

Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.

**Applicazioni di Office**

Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.

**Condivisione**

Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.
