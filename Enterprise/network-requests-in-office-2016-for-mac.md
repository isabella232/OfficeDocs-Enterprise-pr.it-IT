---
title: Richieste di rete in Office 2016 per Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: 2016 di Office per le applicazioni Mac offrono un'esperienza di app nativo nella piattaforma Mac OS. Ogni app è progettato per funzionare in una vasta gamma di scenari, tra cui stati quando è disponibile alcun accesso alla rete. Quando un computer è collegato a una rete, le applicazioni di connettono automaticamente a una serie di servizi basati sul web per fornire le funzionalità avanzate. Questo white paper vengono descritti i endpoint e le applicazioni tentano di raggiungere gli URL e i servizi forniti. Queste informazioni sono utili durante la risoluzione dei problemi di rete problemi di configurazione e l'impostazione di un criterio per i server proxy di rete. I dettagli in questo articolo sono destinati a complemento l'URL in Office 365 e articolo gli intervalli di indirizzi.
ms.openlocfilehash: b94b77a0ff8cd37b0fa1c881ba590853615bfe93
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541371"
---
# <a name="network-requests-in-office-2016-for-mac"></a>Richieste di rete in Office 2016 per Mac

2016 di Office per le applicazioni Mac offrono un'esperienza di app nativo nella piattaforma Mac OS. Ogni app è progettato per funzionare in una vasta gamma di scenari, tra cui stati quando è disponibile alcun accesso alla rete. Quando un computer è collegato a una rete, le applicazioni di connettono automaticamente a una serie di servizi basati sul web per fornire le funzionalità avanzate. Questo white paper vengono descritti i endpoint e le applicazioni tentano di raggiungere gli URL e i servizi forniti. Queste informazioni sono utili per risolvere i problemi di configurazione di rete e impostazione dei criteri per i server proxy di rete. I dettagli in questo articolo sono destinati a complemento l' [URL in Office 365 e l'indirizzo articolo intervalli](urls-and-ip-address-ranges.md), che include gli endpoint per computer che eseguono Microsoft Windows.
  
La maggior parte di questo articolo è tabelle che descrive gli URL di rete, type e descrizione del servizio o la funzione forniti da tale endpoint. Ognuna delle applicazioni Office può variare in relativo utilizzo endpoint e del servizio. Le applicazioni seguenti vengono definite nelle tabelle riportate di seguito:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: outlook
- N: OneNote
   
Il tipo di URL è definito come segue:
  
- ST: Statico - l'URL è hardcoded nell'applicazione client.
    
- SS: Semi-statica-URL viene codificato come parte di una pagina web o di reindirizzamento.
    
- CS: Config Service - URL viene restituito come parte del servizio di configurazione di Office.
    
## <a name="office-2016-for-mac-default-configuration"></a>2016 di Office per la configurazione predefinita Mac

 **Installazione e aggiornamenti**
  
Gli endpoint di rete seguenti vengono utilizzati per scaricare 2016 Office Mac del programma di installazione dai contenuti rete (CDN).
  
|**URL**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Servizio di collegamento in avanti installazione portale Office 365 per pacchetti di installazione più recenti.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Posizione dei pacchetti di installazione di rete di distribuzione del contenuto.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Posizione dei pacchetti di installazione di rete di distribuzione del contenuto.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Endpoint di controllo di gestione di Microsoft AutoUpdate  <br/> |
   
 **Primo avvio di app**
  
Gli endpoint di rete seguenti vengono contattati primo avvio di un'applicazione di Office. Gli endpoint di forniscono maggiori funzionalità di Office per gli utenti e gli URL vengono contattati indipendentemente dal tipo di licenza (incluse le installazioni con contratto multilicenza).
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |Configurazione 'Flighting' - consente di funzionalità di base disponibili i backup e la sperimentazione.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test di configurazione di rete 'Flighting'  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test di configurazione di rete 'Flighting'  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Servizio di configurazione di Office - Master elenco degli endpoint del servizio.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Download di regole telemetria di Office - fornisce informazioni al client sui quali dati e gli eventi per caricare il servizio di telemetria.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |Servizio di telemetria di OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Telemetria di Office caricare Reporting - "Heartbeart" e gli eventi di errore che si verificano nel client vengono caricati nel servizio di telemetria.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Servizio di modello Office Online - fornisce agli utenti con i modelli di documento in linea.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Download di modelli di Office - archiviazione delle immagini modello PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Configurazione dell'archivio per le applicazioni di Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Home page dell'area di autenticazione rilevamento e catalogo di servizi di integrazione di Office documento (elenco di servizi e gli endpoint).  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Risorse per la home page dell'area di autenticazione individuazione v2 (15.40 e successive)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft AutoUpdate manifesti - consente di verificare se sono disponibili aggiornamenti  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Libreria Microsoft Ajax JavaScript  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |App Wikipedia per le risorse e configurazione di Office.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Applicazione della mappa di Bing per le risorse e configurazione di Office.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Persone grafico app per le risorse e configurazione di Office.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Che cos'è nuovo contenuto per OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nuovo contenuto per OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |What's New immagini per OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Servizio di supporto all'interno dell'applicazione.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Servizio di rilevamento Account di posta elettronica.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Individuazione automatica di Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Endpoint di Outlook per il servizio Office 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Icone per i componenti aggiuntivi di Outlook.  <br/> |
   
> [!NOTE]
> Il servizio di configurazione di Office funge da un servizio di individuazione automatica per tutti i client Microsoft Office, non solo per Mac. Gli endpoint restituiti nella risposta sono semi-statici nel fatto che cambia è molto poco frequenti, ma è comunque possibile. 
  
 **Accesso**
  
Gli endpoint di rete seguenti sono contattare durante l'accesso al gruppo di archiviazione basata su cloud. In base al tipo di account diversi servizi possono essere contattati. Per esempio:
  
- **MSA: Account Microsoft** : in genere utilizzato per gli scenari consumer e retail 
    
- **OrgID: organizzazione Account** : in genere utilizzato per gli scenari commerciali 
    
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Servizio di autorizzazione di Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Servizio di accesso di Office 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Servizio di accesso Account Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Account Microsoft account di accesso del servizio Helper (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Account di accesso di Office 365 personalizzazione (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Documenti e posizioni archiviazione Locator  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |La maggior parte del servizio di documenti (usati MRU Recently Used)  <br/> |
   
> [!NOTE]
> Per le licenze in abbonamento e al dettaglio, accesso sia attiva il prodotto e consente l'accesso alle risorse cloud, ad esempio OneDrive. Per le installazioni di licenza Volume License, gli utenti sono ancora richiesto di accesso in ingresso (per impostazione predefinita), ma che solo necessarie per accedere alle risorse cloud, come il prodotto è già stato attivato. 
  
 **Attivazione dei prodotti**
  
Gli endpoint di rete seguenti sono valide per le attivazioni di sottoscrizione a Office 365 e la licenza Retail. In particolare, ciò non si applica alle installazioni con contratto multilicenza.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Servizio gestione licenze Office  <br/> |
   
 **Che cos'è il nuovo contenuto**
  
Gli endpoint di rete seguenti si applicano solo a sottoscrizione a Office 365.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Che cos'è il contenuto della pagina nuova JSON.  <br/> |
   
 **Strumento ricerche**
  
Gli endpoint di rete seguenti si applicano a entrambi sottoscrizione a Office 365.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Servizio Web di Organizzatore ricerche  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Contenuto statico Organizzatore ricerche  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Provider di contenuti Organizzatore ricerche  <br/> |
   
 **Ricerca intelligente**
  
Gli endpoint di rete seguenti sono valide per le attivazioni di sottoscrizione a Office 365 sia Retail/Volume License.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Servizio Web Insights  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |Libreria JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Libreria di supporto JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Provider di contenuti Insights  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Provider di contenuti Insights  <br/> |
   
 **PowerPoint Designer**
  
Gli endpoint di rete seguenti si applicano solo a sottoscrizione a Office 365.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Servizio web Designer di PowerPoint  <br/> |
   
 **Avvio rapido di PowerPoint**
  
Gli endpoint di rete seguenti si applicano solo a sottoscrizione a Office 365.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Servizio web QuickStarter di PowerPoint  <br/> |
   
 **Inviare un Smile/cipiglio**
  
Gli endpoint di rete seguenti sono valide per le attivazioni di sottoscrizione a Office 365 sia Retail/Volume License.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Invio di un servizio Smile  <br/> |
   
 **contatta il supporto tecnico**
  
Gli endpoint di rete seguenti sono valide per le attivazioni di sottoscrizione a Office 365 sia Retail/Volume License.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Contattare il servizio di assistenza  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Servizio di supporto all'interno dell'applicazione  <br/> |
   
 **Salva come PDF**
  
Gli endpoint di rete seguenti sono valide per le attivazioni di sottoscrizione a Office 365 sia Retail/Volume License.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Servizio di conversione di documenti di Word (PDF)  <br/> |
   
 **Office Apps (ovvero componenti aggiuntivi)**
  
Gli endpoint di rete seguenti si applicano a sottoscrizione a Office 365 sia Retail/Volume License attivazioni quando i componenti aggiuntivi di applicazioni di Office sono attendibili.
  
|**URL**|**App**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Configurazione dell'archivio applicazioni Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Risorse app Wikipedia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Risorse app Bing mappe  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Risorse di persone grafico app  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Servizio di reindirizzamento di Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office JavaScript Libraries  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Telemetria e il servizio di segnalazione errori per le applicazioni di Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Libreria Microsoft Ajax JavaScript  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Libreria Microsoft Ajax JavaScript  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript Libraries  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Risorse di supporto  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Risorse di supporto  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Risorse di supporto  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |Libreria JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Segnalazione errori  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Risorse del tipo di carattere  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Servizio di telemetria  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Creazione di report di telemetria  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Raccolta di risorse di archiviazione di Microsoft  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Risorse della pagina Wikipedia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Risorse multimediali Wikipedia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Cornice sandbox Wikipedia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Mappare i modelli  <br/> |
   
 **Collegamenti sicuri**
  
Endpoint di rete seguenti valide per le applicazioni Office 2016.
  
|**URL**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Servizio di collegamento sicuro Microsoft  <br/> |
   
 **Bloccarsi reporting**
  
Endpoint di rete seguenti si applica a tutte le applicazioni Office 2016 e tipi di licenze. Quando un processo si blocca in modo imprevisto, un report viene generato e inviato al servizio Watson.
  
|**URL**|**Tipo**|**Descrizione**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Servizio di segnalazione errori Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Servizio di collaborazione sui concetti di Office  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Opzioni per la riduzione delle richieste di rete e del traffico

La configurazione predefinita di 2016 di Office per Mac offre la migliore esperienza utente, sia in termini di funzionalità e l'aggiornamento del computer. In alcuni scenari, si desidera impedire alle applicazioni di comunicazione con gli endpoint di rete. In questa sezione vengono illustrate le opzioni per farlo.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Disattivazione Cloud accesso e Office componenti aggiuntivi
  
I clienti con contratto multilicenza potrebbero essere vincolati criteri informazioni sul salvataggio di documenti in un archivio basato su cloud. Per disattivare accesso MSA/OrgID e accedere a componenti aggiuntivi di Office, è possibile impostare la preferenza per ogni applicazione.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Se gli utenti tentano di accedere alla funzione di accesso, si verrà visualizzato un errore di una connessione di rete non è presente. Poiché questa preferenza blocca anche l'attivazione del prodotto in linea, deve utilizzato solo per le installazioni di licenza Volume License. In particolare, utilizzando la preferenza impedirà alle applicazioni di Office di accedere agli endpoint per le operazioni seguenti:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Tutti gli endpoint elencati nella sezione "Sign In" sopra elencata.
    
- Tutti gli endpoint elencati nella precedente sezione 'Ricerca Smart'.
    
- Tutti gli endpoint elencati nella precedente sezione "Attivazione del prodotto".
    
- Tutti gli endpoint elencati nella precedente sezione "Office Apps (ovvero add-ins)".
    
Per ristabilire la la funzionalità per l'utente, impostare la preferenza a "2" o rimuoverlo.
  
> [!NOTE]
> Tale preferenza richiede 2016 di Office per Mac build 15.25 [160726] o versione successiva. 
  
### <a name="telemetry"></a>Telemetria
  
2016 di Office per Mac invia telemetria informazioni a Microsoft a intervalli regolari. Caricamento di dati per l'endpoint 'Del nodo'. I dati di telemetria contribuiscono il team di progettazione di valutare l'integrità e qualsiasi comportamenti imprevisti di ogni applicazione di Office. Sono disponibili due categorie di telemetria:
  
- **Heartbeat** contiene informazioni sulla versione e licenza. Questi dati viene inviati immediatamente all'avvio di app. 
    
- **Utilizzo** contiene informazioni su come vengono utilizzate applicazioni e gli errori non irreversibili. Questi dati viene inviati ogni 60 minuti. 
    
Microsoft ha molto prendere in seria la privacy dell'utente. Per ulteriori informazioni sulla raccolta di dati di Microsoft in [https://privacy.microsoft.com](https://privacy.microsoft.com). Per impedire l'invio di telemetria 'Utilizzo' delle applicazioni, la preferenza **SendAllTelemetryEnabled** può essere modificata. La preferenza è per ogni applicazione e può essere impostata tramite Mac OS profili di configurazione oppure manualmente da Terminal: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Telemetria heartbeat viene sempre inviato e non può essere disattivata.
  
### <a name="crash-reporting"></a>Bloccarsi reporting
  
Quando si verifica un errore irreversibile nell'applicazione, l'applicazione in modo imprevisto terminerà e caricare un rapporto di arresto anomalo del servizio "Watson". La segnalazione è costituita da uno stack di chiamate, ovvero l'elenco delle operazioni che l'applicazione ha elaborato causando l'arresto anomalo del sistema. Questi passaggi di identificare il team di progettazione la funzione identico non riuscito e il motivo.
  
In alcuni casi, il contenuto di un documento fa sì che l'applicazione in modo anomalo. Se l'app identifica il documento come la causa, verrà chiedere all'utente se è possibile inoltre inviare il documento e lo stack di chiamata. Gli utenti possono effettuare una scelta informata a questa domanda. Gli amministratori IT possono sono previsti requisiti strict sulla trasmissione di documenti e prendere la decisione per conto dell'utente per non inviare mai documenti. Per impedire l'invio di documenti e per sopprimere la richiesta all'utente, è possono impostare le preferenze seguenti:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Se **SendAllTelemetryEnabled** è impostato su **FALSE**, tutti bloccarsi relazioni per che processo è disabilitato. Per abilitare i report di arresto anomalo senza inviare telemetria utilizzo, è possono impostare le preferenze seguenti:```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Aggiornamenti
  
Microsoft rilascia 2016 di Office per gli aggiornamenti Mac a intervalli regolari (in genere una volta al mese). Si consiglia agli utenti e agli amministratori IT di mantenere macchine aggiornati per verificare le correzioni della protezione più recenti installati. Nei casi in cui gli amministratori IT desiderano strettamente controllo e la gestione degli aggiornamenti automatica, è possono impostare le preferenze seguenti per evitare che il processo di aggiornamento automatico da automaticamente il rilevamento e che offre gli aggiornamenti dei prodotti:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blocco delle richieste con un Firewall o Proxy
  
Se i blocchi di organizzazione richiede agli URL tramite un firewall o il server proxy è necessario configurare gli URL elencati in questo documento come consentito o bloccare nell'elenco da una risposta X 40 (ad esempio 403 o 404). Una risposta X 40 che consente le applicazioni di Office per la corretta accettare l'impossibilità di accedere alla risorsa e offrirà un'esperienza utente più veloce, più semplicemente eliminare la connessione, che a sua volta determinerà il client tentativi.
  
Se il server proxy richiede l'autenticazione, una risposta 407 verrà restituiti al client. Per risultati ottimali, assicurarsi che si sta utilizzando Office 2016 build 15.27 o versioni successive, come sono inclusi correzioni specifiche per l'utilizzo di server NTLM e Kerberos.
  
  
## <a name="see-also"></a>Vedere anche

[URL e intervalli di indirizzi IP per Office 365](urls-and-ip-address-ranges.md)

