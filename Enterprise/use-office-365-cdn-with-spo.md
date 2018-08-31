---
title: Utilizzare la rete di distribuzione del contenuto di Office 365 con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Viene descritto l'utilizzo incorporati contenuto rete di Office 365 (CDN) per velocizzare il recapito delle risorse di SharePoint Online per tutti gli utenti indipendentemente dalla posizione in cui si trova o dalla modalità di accesso ai contenuti.
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541148"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>Utilizzare la rete di distribuzione del contenuto di Office 365 con SharePoint Online

È possibile ospitare statiche risorse della rete di distribuzione del contenuto di Office 365 (CDN) per garantire prestazioni migliori per le pagine di SharePoint Online. Risorse statiche sono file che non cambiano frequentemente, ad esempio immagini, video e audio, fogli di stile, tipi di carattere e i file JavaScript. La rete CDN funziona come un proxy di memorizzazione nella cache geograficamente distribuiti, la memorizzazione nella cache statiche risorse più vicino per i browser che ne fanno richiesta. 
  
Se si ha già familiarità con la modalità con cui utilizzano CDN, è sufficiente eseguire alcune operazioni per impostare le. In questo argomento viene descritto come. Continuare a leggere per informazioni sulle operazioni preliminari che ospita le risorse statiche e la rete CDN di Office 365.
  
 **Eseguire il titolo in [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).**
  
## <a name="office-365-cdn-basics"></a>Nozioni fondamentali sulla rete CDN di Office 365

La rete CDN di Office 365 è inclusa come parte dell'abbonamento a SharePoint Online. Non è necessario pagare molto. Office 365 fornisce supporto per entrambi privato e pubblico access ed è possibile alle risorse statica host in più posizioni o origini. La rete CDN di Office 365 non corrisponde al CDN Azure. Per ulteriori informazioni su come utilizzare una rete CDN o sui concetti generali CDN, vedere [reti di distribuzione del contenuto](content-delivery-networks.md).
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>Come la rete CDN concede l'accesso agli utenti finali

Privata risorse statiche nella rete CDN di Office 365 accedere dai token generati da SharePoint Online. Gli utenti che dispongono dell'autorizzazione per accedere alla cartella o raccolta designato dall'origine verranno concesse automaticamente i token. SharePoint Online non supporta le autorizzazioni a livello di elemento per la rete CDN.
  
Ad esempio, per un file al `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, assegnate le operazioni seguenti:
  
- 1 utente dispone dell'accesso alla cartella 1 e Image1
    
- L'utente 2 non dispone di accesso alla cartella 1
    
- 3 l'utente non dispone dell'accesso alla cartella 1 ma viene concessa l'autorizzazione esplicita per accedere a Image1 tramite SharePoint Online
    
- Utente 4 ha accesso alla cartella 1, ma è stato esplicitamente negato l'accesso a Image1
    
Quindi le seguenti condizioni sono vere:
  
- L'utente 1 e 4 utente sarà in grado di accedere a Image1 tramite la rete CDN.
    
- L'utente 2 e 3 utente non sarà in grado di accedere a Image1 tramite la rete CDN.
    
    Tuttavia, 3 utente può accedere Image1 risorse direttamente tramite SharePoint Online mentre 4 utente non può accedere bene tramite SharePoint Online.
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>Panoramica dell'utilizzo con la rete CDN di Office 365

Per configurare la rete CDN di Office 365, attenersi alla procedura riportata base:
  
- Pianificare la distribuzione CDN:
    
  - Determinare quali risorse statiche si desidera ospitare nella rete CDN Office 365. Per informazioni dettagliate su come effettuare queste scelte, vedere [reti di distribuzione del contenuto](content-delivery-networks.md).
    
  - [Determinare dove si desidera archiviare le risorse](use-office-365-cdn-with-spo.md#CDNStoreAssets). Questo percorso è una cartella o una raccolta di SharePoint e viene chiamato un'origine.
    
  - Determinare se le risorse devono essere effettuate pubbliche o mantenere private. Eseguire questa operazione quando è possibile [scegliere se ogni origine deve essere pubblica o privata](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Se si desidera, è possibile disporre di più origini alcuni sono pubblici e alcuni lavoratori sono private.
    
- [Impostare e configurare la rete CDN di Office 365 con SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Dopo aver completato questo passaggio, è necessario:
    
  - Abilitare la rete CDN per l'organizzazione.
    
  - Aggiungere le origini. Identificare ogni origine come pubblico o privato.
    
Una volta termine di programma di installazione per [gestire la rete CDN di Office 365](use-office-365-cdn-with-spo.md#CDNManage) nel tempo da: 
  
- Aggiunta, l'aggiornamento e rimozione delle risorse
    
- Aggiunta e rimozione di origini
    
- Configurazione dei criteri CDN
    
- Se necessario, disabilitare la rete CDN di Office 365
    
## <a name="determine-where-you-want-to-store-your-assets"></a>Determinare dove si desidera archiviare le risorse

La rete CDN recupera le risorse da una posizione denominata un'origine. Per Office 365, un'origine è una raccolta di SharePoint o una cartella in cui è possibile accedere da un URL. È necessario notevole flessibilità quando si specificano origini per l'organizzazione. Ad esempio, è possibile specificare più origini o una singola origine in cui si desidera inserire tutte le attività di rete CDN. È possibile disporre di origini pubbliche o private per l'organizzazione. La maggior parte delle organizzazioni verranno sceglie di implementare una combinazione delle due configurazioni.
  
Se si definisce centinaia di origini, probabilmente avrà un impatto negativo sul tempo che necessario per elaborare le richieste. È consigliabile che se si dispone di più di circa 100 origini è possibile rivedere l'architettura.
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>Scegliere se ogni origine deve essere pubblica o privata

Quando si identifica un'origine, si specifica se deve essere resa pubblica o privata. Indipendentemente dall'opzione scelta, Microsoft provvederà tutti automaticamente quando si tratta di amministrazione di rete CDN stesso. Inoltre, è possibile modificare il presente in seguito, dopo aver impostato la rete CDN e identificato le origini.
  
Miglioramenti delle prestazioni fornisce la possibilità di pubblici e privati, ma ognuno presenta vantaggi e gli attributi univoci.
  
 **Attributi e i vantaggi dell'hosting di risorse in un'origine pubblica**
  
- Risorse esposte in un'origine pubblica sono accessibili a tutti gli utenti in modo anonimo.
    
    > [!IMPORTANT]
    > Dopo aver identificato un'origine pubblica nella rete CDN, dovrebbero essere posizionati mai le risorse vengono considerate riservate dell'organizzazione in un'origine pubblico o una raccolta SharePoint Online. 
  
- Se si rimuove un bene da un'origine pubblica, le risorse continui a essere disponibili fino a 30 giorni dalla cache. Tuttavia, si invalida collegamenti a risorse nella rete CDN all'interno di 15 minuti.
    
- Quando si ospitano fogli di stile (file con estensione CSS) in un'origine pubblica, è possibile utilizzare percorsi relativi e gli URI all'interno del codice. Ciò significa che è possibile fare riferimento la posizione delle immagini di sfondo e altri oggetti relativi alla posizione del bene che di chiamata.
    
- Mentre è possibile modificare il codice URL dell'origine un pubblica, pertanto non è consigliato. Il motivo di ciò è che se l'accesso per la rete CDN risulta disponibile, l'URL non verrà risolto automaticamente per l'organizzazione in SharePoint Online e può causare tempi di collegamenti interrotti e altri errori.
    
- Tipi di file predefiniti inclusi per origini pubbliche sono CSS, .eot, GIF, con estensione ico, JPEG, jpg, js, Map, PNG, SVG, ttf e .woff. È possibile specificare altri tipi di file.
    
- Se si desidera, è possibile configurare un criterio per escludere risorse identificato dal classificazioni di sito specificato. Ad esempio, è possibile scegliere di escludere tutte le risorse che sono contrassegnate come "confidential" o "restricted" anche se sono un tipo di file consentiti e si trovano in un'origine pubblica.
    
 **Attributi e i vantaggi dell'hosting di risorse in un'origine privata**
  
- Gli utenti possono accedere le risorse da un'origine privata solo se è autorizzato a tale scopo. Non è consentito l'accesso anonimo a tali risorse.
    
- Se si rimuove una risorsa dall'origine privata, bene continui a essere disponibile per un massimo di un'ora dalla cache. Tuttavia, si invalida collegamenti a risorse nella rete CDN all'interno di 15 minuti.
    
- Tipi di file predefiniti inclusi per origini private sono GIF, con estensione ico, JPEG, jpg, js e PNG. È possibile specificare altri tipi di file.
    
- Proprio come origini pubbliche, è possibile configurare un criterio per escludere risorse identificato dal classificazioni di sito specificato anche se si utilizza i caratteri jolly per includere tutte le risorse all'interno di una cartella o una raccolta siti.
    
## <a name="default-office-365-cdn-origins"></a>Origini di Office 365 CDN predefinito

Se non diversamente specificato, Office 365 imposta alcune origini predefinito automaticamente quando si abilita la rete CDN di Office 365. Se si escludono inizialmente li, è possibile aggiungere tali origini al termine dell'installazione.
  
Origini private predefinito:
  
- \*/userphoto.aspx
    
- \*/siteassets
    
Origini pubbliche predefinite:
  
- \*/MasterPage
    
- \*raccolta /Style
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Impostare e configurare la rete CDN di Office 365 con SharePoint Online Management Shell

Le procedure descritte in questo argomento richiedono l'utilizzo di SharePoint Online Management Shell per la connessione a SharePoint Online. Per ulteriori informazioni, vedere [connettersi a PowerShell per SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).
  
Completare la procedura seguente per impostare e configurare la rete CDN di Office 365 per ospitare le risorse statiche in SharePoint Online.
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>Per consentire all'organizzazione di utilizzare la rete CDN di Office 365

Utilizzare il cmdlet **Set-SPOTenantCdnEnabled** per consentire all'organizzazione di utilizzare la rete CDN di Office 365. È possibile abilitare all'organizzazione di utilizzare origini pubblici, origini private o entrambi con la rete CDN. È inoltre possibile configurare la rete CDN 365 Office per ignorare l'impostazione delle origini predefinito quando si attiva. È sempre possibile aggiungere tali origini seguito come descritto in questo argomento. 
  
In Windows Powershell per SharePoint Online:
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Ad esempio, per consentire all'organizzazione di utilizzare origini pubblici e privati con la rete CDN, digitare il comando seguente:
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Per consentire all'organizzazione di utilizzare origini pubblici e privati con la rete CDN ma ignorare l'impostazione origini predefinito, digitare il comando seguente:
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Per consentire all'organizzazione di utilizzare origini pubbliche con la rete CDN, digitare il comando seguente:
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Per consentire all'organizzazione di utilizzare origini private con la rete CDN, digitare il comando seguente:
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Per ulteriori informazioni su questo cmdlet, vedere [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>(Facoltativo) Per modificare l'elenco dei tipi di file da includere nella rete CDN di Office 365
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> Quando si definiscono i tipi di file utilizzando il cmdlet **Set-SPOTenantCdnPolicy** , si sovrascrive l'elenco attualmente definito. Se si desidera aggiungere altri tipi di file all'elenco, utilizzare il cmdlet prima per scoprire quali tipi di file sono già stato abilitati e includono nell'elenco con le nuove strutture. 
  
Utilizzare il cmdlet **Set-SPOTenantCdnPolicy** per definire i tipi di file statici che possono essere ospitati da origini pubblici e privati nella rete CDN. Per impostazione predefinita, tipi di risorse comuni sono consentiti per js, GIF, jpg e CSS di esempio. 
  
In Windows PowerShell per SharePoint Online:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Per visualizzare i tipi di file attualmente consentiti per la rete CDN, utilizzare il cmdlet **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Per ulteriori informazioni su questi cmdlet, vedere [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>(Facoltativo) Per modificare l'elenco delle classificazioni dei siti che si desidera escludere dalla rete CDN Office 365
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> Quando si escludono le classificazioni di sito utilizzando il cmdlet **Set-SPOTenantCdnPolicy** , si sovrascrive l'elenco attualmente definito. Se si desidera escludere le classificazioni di altri siti, utilizzare il cmdlet prima per scoprire le classificazioni sono già esclusi e quindi aggiungerle con le nuove strutture. 
  
Utilizzare il cmdlet **Set-SPOTenantCdnPolicy** da escludere le classificazioni di siti che non si desidera rendere disponibili tramite la rete CDN. Per impostazione predefinita, le classificazioni Nessun sito vengono esclusi. 
  
In Windows PowerShell per SharePoint Online:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Per visualizzare le classificazioni dei siti sono limitate, utilizzare il cmdlet **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Per ulteriori informazioni su questi cmdlet, vedere [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="to-add-an-origin-for-your-assets"></a>Per aggiungere un'origine per le risorse
<a name="Office365CDNforSPOOrigin"> </a>

Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire un'origine. È possibile definire più origini. L'origine è un URL che punta a una raccolta SharePoint o una cartella che contiene le risorse che si desidera trovarsi la rete CDN. 
  
> [!IMPORTANT]
> Dopo aver identificato un'origine pubblica nella rete CDN, dovrebbero essere posizionati mai le risorse sono considerate riservate dell'organizzazione nell'origine pubblica o nella raccolta di SharePoint Online. 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

Dove percorso è il percorso della cartella che contiene le risorse. È possibile utilizzare i caratteri jolly oltre ai percorsi relativi. Ad esempio, per includere tutte le risorse nella cartella masterpages per tutti i siti come un'origine pubblica entro la rete CDN, digitare il comando seguente:
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

Per ulteriori informazioni sulla sintassi e questo comando, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Dopo aver eseguito il comando, il sistema Sincronizza la configurazione nel datacenter. Questa operazione richiede 15 minuti.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Esempio: Configurazione di un'origine pubblica per le pagine master e per la raccolta stili per SharePoint Online
<a name="ExamplePublicOrigin"> </a>

In genere, queste origini impostati per è per impostazione predefinita quando si abilita origini pubbliche per la rete CDN di Office 365. Tuttavia, se si desidera attivarli manualmente, eseguire la procedura seguente.
  
- Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la raccolta stili di un'origine pubblica entro la rete CDN di Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire le pagine master di un'origine pubblica entro la rete CDN di Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- Per ulteriori informazioni sulla sintassi e questo comando, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Dopo aver eseguito il comando, il sistema Sincronizza la configurazione nel datacenter. Questa operazione richiede 15 minuti.
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Esempio: Configurazione di un'origine privata per le risorse del sito, le pagine del sito e immagini di pubblicazione per SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella delle risorse del sito di un'origine privata entro la rete CDN di Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella di pagine del sito di un'origine privata entro la rete CDN di Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire la cartella di immagini pubblicazione come un'origine privata entro la rete CDN di Office 365. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    Per ulteriori informazioni sulla sintassi e questo comando, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Dopo aver eseguito il comando, il sistema Sincronizza la configurazione nel datacenter. Questa operazione richiede 15 minuti.
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Esempio: Configurazione di un'origine privata per una raccolta siti per SharePoint Online
<a name="ExamplePrivateOriginSiteCollection"> </a>

Utilizzare il cmdlet **Add-SPOTenantCdnOrigin** per definire una raccolta siti come un'origine privata entro la rete CDN di Office 365. Per esempio 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Per ulteriori informazioni sulla sintassi e questo comando, vedere [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Dopo aver eseguito il comando, il sistema Sincronizza la configurazione nel datacenter. Questa operazione richiede 15 minuti.
  
## <a name="manage-the-office-365-cdn"></a>Gestione di Office 365 CDN
<a name="CDNManage"> </a>

Dopo aver configurato la rete CDN, è possibile apportare modifiche alla configurazione quando si aggiorna il contenuto o in base alle esigenze, come descritto in questa sezione.
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>Per aggiungere, aggiornare o rimuovere risorse dalla rete CDN Office 365
<a name="Office365CDNforSPOaddremoveasset"> </a>

Dopo aver completato i passaggi di installazione, è possibile aggiungere nuove risorse e aggiornare o rimuovere le risorse esistenti, ogni volta che si desidera. Per le risorse in una raccolta SharePoint identificato come origine o solo apportare le modifiche. Se si aggiunge una nuova risorsa, è disponibile attraverso la rete CDN immediatamente. Tuttavia, se si aggiorna il bene, richiede un massimo di 15 minuti per la nuova copia la propagazione e saranno disponibili nella rete CDN.
  
Se si desidera recuperare il percorso di origine, è possibile utilizzare il cmdlet **Get-SPOTenantCdnOrigins** . Per informazioni su come utilizzare questo cmdlet, vedere [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>Per rimuovere un'origine dalla rete CDN Office 365
<a name="Office365CDNforSPORemoveOrigin"> </a>

Se si desidera, è possibile rimuovere l'accesso a una cartella o una raccolta SharePoint identificato come origine. A tale scopo, utilizzare il cmdlet **Remove-SPOTenantCdnOrigin** . Per informazioni su come utilizzare questo cmdlet, vedere [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>Per modificare un'origine di rete CDN Office 365
<a name="Office365CDNforSPORemoveOrigin"> </a>

È possibile modificare un'origine che sono stati creati. In realtà, rimuovere l'origine e quindi aggiungere uno nuovo. Per ulteriori informazioni, vedere [per rimuovere un'origine dalla rete CDN Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) e [per aggiungere un'origine per le risorse](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).
  
### <a name="to-disable-the-office-365-cdn"></a>Per disabilitare la rete CDN di Office 365
<a name="Office365CDNforSPODisable"> </a>

Utilizzare il cmdlet **Set-SPOTenantCdnEnabled** per disabilitare la rete CDN per l'organizzazione. Se si dispone di entrambe le origini pubbliche e private abilitate per la rete CDN, è necessario eseguire il cmdlet due volte come illustrato negli esempi seguenti. 
  
Per disabilitare l'uso delle origini pubbliche nella rete CDN, in Windows Powershell per SharePoint Online, immettere il comando seguente:
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Per disabilitare l'uso delle origini di rete CDN private, immettere il comando seguente:
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Per ulteriori informazioni su questo cmdlet, vedere [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>Risoluzione dei problemi relativi alla configurazione di Office 365 CDN
<a name="CDNManage"> </a>

Il punto finale non immediatamente sarà disponibile per l'utilizzo, come il tempo per la registrazione per la propagazione attraverso la rete CDN. Configurazione richiede 15 minuti.
  

