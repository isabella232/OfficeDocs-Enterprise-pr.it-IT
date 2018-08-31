---
title: Cenni preliminari sull'autenticazione moderno ibrida e prerequisiti per l'utilizzo con Skype locale per Business ed Exchange Server
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 8/27/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: Autenticazione moderno è un metodo di gestione delle identità che offre maggiore protezione l'autenticazione degli utenti e autorizzazioni. È disponibile per le distribuzioni ibride di Skype per Business server locali e di Exchange server in locale, nonché Skype dominio diviso per ibridi Business. In questo articolo include collegamenti a relativi documenti sui prerequisiti, il programma di installazione/disabilitazione dell'autenticazione moderno e di alcune delle informazioni correlate client (ad esempio Outlook e Skype i client).
ms.openlocfilehash: 3d510c6d3e9f8ff885279dc008eeefb5d1014639
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240591"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Cenni preliminari sull'autenticazione moderno ibrida e prerequisiti per l'utilizzo con Skype locale per Business ed Exchange Server

Autenticazione moderno è un metodo di gestione delle identità che offre maggiore protezione l'autenticazione degli utenti e autorizzazioni. È disponibile per le distribuzioni ibride di Office 365 di Skype per Business server locali e di Exchange server in locale, nonché, Skype dominio diviso per ibridi Business. In questo articolo include collegamenti a relativi documenti sui prerequisiti, il programma di installazione/disabilitazione dell'autenticazione moderno e di alcune delle informazioni correlate client (ad esempio Outlook e Skype i client). 
  
- [Che cos'è l'autenticazione moderno?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [Quali modifiche quando utilizza l'autenticazione moderno?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Controllare lo stato di autenticazione moderno dell'ambiente locale](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [Siano soddisfatti i prerequisiti di autenticazione moderno?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [Altre informazioni necessarie iniziare?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Elenco degli URL autenticazione moderno](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>Che cos'è l'autenticazione moderno?
<a name="BKMK_WhatisModAuth"> </a>

Quando si parla la comunicazione tra un client (ad esempio laptop o telefono) e un server, Microsoft utilizza la frase "Authentication moderno".
  
L'autenticazione moderno è un termine generico per una combinazione di autenticazione e metodi di autorizzazione, nonché alcune misure di sicurezza che si basano su criteri di accesso che è possibile avere familiarità con. Include:
  
- **Metodi di autenticazione**: autenticazione a più fattori. Autenticazione basata su certificati client e la libreria di autenticazione di Active Directory ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Metodi di autorizzazione**: implementazione Microsoft di Open Authorization (OAuth). 
    
- **Criteri di accesso condizionale**: Gestione applicazione Mobile (MAM) e Azure Active Directory condizionale l'accesso. 
    
Gestione delle identità utente con autenticazione moderno offre agli amministratori di numerosi strumenti da utilizzare quando riguarda la protezione delle risorse e offre maggiore protezione metodi di gestione delle identità per sia in locale (Exchange e Skype per le aziende), ibrida di Exchange e Skype per scenari aziendali ibrida/split-domain.
  
Tenere presente che, poiché Skype per le aziende collabora con Exchange, il comportamento di accesso Skype per client Business verrà visualizzato dagli utenti sarà interessato dallo stato di autenticazione moderno di Exchange. Verranno applicate anche nel caso di Skype per l'ambiente ibrido dominio diviso Business. Inoltre, il tipo di Skype per l'ambiente ibrido di Business che supporta l'utilizzo dell'autenticazione moderno spesso viene chiamato 'split-dominio' (in un dominio diviso, sono disponibili sia Skype Business online e Skype per Business nel-% beni e gli utenti sono ospitati in entrambe le posizioni).
  
 **Importante** Non tutti sanno che, a partire da agosto 2017 tutti i nuovi tenant di Office 365 che includono Skype per le aziende online ed Exchange online avrà moderno attivata per impostazione predefinita l'autenticazione. Tenant esistente non sarà necessario modifiche allo stato di agente di gestione predefinito, ma tutti i nuovi tenant supporta automaticamente il set di caratteristiche identità che viene visualizzato sopra elencate espanso. Per verificare lo stato dell'agente di gestione Skype for Business in linea, è possibile utilizzare Skype per PowerShell online Business con le credenziali di amministratore globale. Eseguire 'Get-CsOAuthConfiguration' per controllare l'output di - ClientADALAuthOverride. Se ClientADALAuthOverride-'ha' l'autenticazione moderno è attivato. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>Quali modifiche quando utilizza l'autenticazione moderno?
<a name="BKMK_WhatChanges"> </a>

Quando si utilizza l'autenticazione moderno con Skype locale per Business o Exchange server, si è ancora *l'autenticazione* degli utenti locali, ma il brano *dell'autorizzazione per* l'accesso alle modifiche di risorse (ad esempio, file o messaggi di posta elettronica). Questo è il motivo, anche se l'autenticazione moderno è sulla comunicazione tra client e server, le operazioni eseguite durante la configurazione di risultati di agente di gestione in evoSTS (un servizio Token di sicurezza utilizzato dal Azure Active Directory) viene impostato come Server di autenticazione per Skype per Business ed Exchange server locale. 
  
La modifica apportata all'evoSTS consente di sfruttare OAuth (emissione di token) per autorizzare i client server locale e consente inoltre il locale utilizzare metodi di protezione comuni nel cloud (ad esempio, l'autenticazione a più fattori). Inoltre, il evoSTS rilascia token che consentono agli utenti di richiedere l'accesso alle risorse senza fornire la password come parte della richiesta. Indipendentemente da dove gli utenti sono ospitati (di online o locale), e indipendentemente dalla località ospita la risorsa richiesta, EvoSTS diventerà la base di autorizzazione di utenti e i client dopo aver configurato l'autenticazione moderno.
  
Di seguito è riportato un esempio di cosa intende. Se Skype per client Business deve accedere al server di Exchange per ottenere le informazioni del calendario per conto di un utente, la raccolta di autenticazione Active Directory (ADAL) viene utilizzato per eseguire questa operazione. ADAL una libreria di codice progettata per rendere disponibile alle applicazioni client con i token di sicurezza OAuth risorse protette nella directory. ADAL funziona con OAuth per verificare basata sulle attestazioni e di scambiare token (anziché le password), per concedere l'accesso un utente a una risorsa. In passato, l'autorità in una transazione ad esempio, il server in grado di convalidare le attestazioni utente e inviare i token necessari - fosse un servizio Token di sicurezza locale o persino Active Directory Federation Services. Tuttavia, l'autenticazione moderno centralizza le quest'ultima con Azure Active Directory (Azure Active Directory) nel Cloud.
  
Significa che anche se il server di Exchange e Skype per gli ambienti aziendali possono essere completamente in locale, il server per l'autorizzazione è online e l'ambiente locale deve avere la possibilità di creare e gestire una connessione al proprio ufficio sottoscrizione 365 nel Cloud (e l'istanza di Azure Active Directory che utilizza la sottoscrizione come directory).
  
Cosa non modifica? Se si è in una dominio diviso ibrida o con Skype per Business ed Exchange server in locale, tutti gli utenti devono prima autenticarsi *locale* . In un'implementazione ibrida di autenticazione moderno, Lyncdiscovery e il rilevamento automatico selezionare il server locale. 
  
 **Importante** Se è necessario conoscere specifico Skype per le topologie aziendali supportate con agente di gestione, che è [descritte di seguito a destra](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Controllare lo stato di autenticazione moderno dell'ambiente locale
<a name="BKMK_CheckStatus"> </a>

Dal momento che l'autenticazione moderno cambia il server di autorizzazione utilizzato quando i servizi di sfruttano OAuth/S2S, è necessario sapere se l'autenticazione moderno è attivato o disattivato per il Skype per ambiente aziendale ed Exchange. È possibile controllare lo stato all'Exchange o Skype per i server aziendali, in locale, eseguendo il comando Get-CSOAuthConfiguration in PowerShell. Se il comando restituisce una proprietà 'OAuthServers' vuota, autenticazione moderno è disattivata.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Siano soddisfatti i prerequisiti di autenticazione moderno?

Verificare e verificare tali elementi disattivato nell'elenco prima di continuare:
  
- **Skype per specifiche Business**
    
  - Tutti i server devono essere SFB Server 2015 CU5 o versione successiva
    
  - **Eccezione** - funzionamento Branch Appliance (SBA) può essere alla versione corrente (basato su Lync 2013) 
    
  - Il dominio SIP viene aggiunto come un dominio federato in Office 365
    
  - Tutti i SFB Front end server deve disporre di connessioni in uscita a internet, per l'autenticazione degli URL (TCP 443) di Office 365 e noto certificato radice CRL (TCP 80) elencate nelle righe 1 e 2 della sezione "Office 365 autenticazione e identità" di [Office 365 URL e IP intervalli di indirizzi](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E).
    
 **Nota** Se il Skype per i server front-end Business utilizza un server proxy per l'accesso a Internet, il proxy server IP e numero di porta utilizzato deve essere immesso nella sezione Configurazione del file Web. config per ogni front-end. 
  
- c:\Programmi\Microsoft files\Skype per Business Server 2015\Web Components\Web ticket\int\web.config
    
- c:\Programmi\Microsoft files\Skype per Business Server 2015\Web Components\Web ticket\ext\web.config
    
- \</System.identityModel.Services\>
    
     \<System.NET\> 
    
     \<defaultProxy\> 
    
     \<proxy 
    
     ProxyAddress = "http://192.168.100.60:8080" 
    
     BypassOnLocal = "true" 
    
     /\> 
    
     \</defaultProxy\> 
    
     \</ System.NET\> 
    
    \</ Configuration\>
    
 **Importante** Assicurarsi di sottoscrivere i feed RSS per [Office 365 URL e intervalli di indirizzi IP](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) essere sempre aggiornati con gli elenchi di URL necessari più recenti. 
  
- **Specifica di Exchange Server**
    
  - Si utilizza un server di Exchange 2013 CU19 e verso l'alto o Exchange server 2016 CU8 e verso l'alto.
    
  - Non esiste alcun server Exchange 2010 nell'ambiente.
    
  - Offload SSL non è configurato. La riesecuzione della crittografia e la terminazione SSL è supportato.
    
  - Nel caso in cui l'ambiente utilizza un'infrastruttura di server proxy per consentire ai server per la connessione a Internet, assicurarsi che tutti i server Exchange che il server proxy definito nella proprietà [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) .
    
- **Requisiti dei client e il protocollo di Exchange**
  
  - I clienti seguenti supportano l'autenticazione moderno:

  |**Client**|**Protocollo principale**|**Note**|
  |:-----|:-----|:-----|
  |Outlook 2013 e Outlook 2016  <br/> |MAPI su HTTP  <br/> |MAPI su HTTP deve essere abilitato all'interno di Exchange per poter utilizzare l'autenticazione moderno con tali client (in genere attivate o True per le nuove installazioni di Exchange 2013 Service Pack 1 e versioni successive); Per ulteriori informazioni vedere [moderno come funziona l'autenticazione per le applicazioni client di Office 2013 e Office 2016](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Verificare che si esegue la compilazione necessaria minima di Outlook. vedere [gli aggiornamenti più recenti per le versioni di Outlook che utilizzano Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 per Mac  <br/> |Servizi Web Exchange  <br/> |  <br/> |
  |Outlook per iOS e Android  <br/> |  <br/> |Per ulteriori informazioni, vedere [Using ibrida moderno Authentication with Outlook per iOS e Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) .  <br/> |
  |Client Exchange ActiveSync (ad esempio, iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |Per i client Exchange ActiveSync che supportano l'autenticazione moderno, è necessario ricreare il profilo per passare dall'autenticazione di base all'autenticazione moderno.  <br/> |

- **Prerequisiti generali**
    
  - Se si utilizza ADFS, è necessario che Windows 2012 R2 ADFS 3.0 e versioni superiori per la federazione
    
  - Le configurazioni di identità sono uno dei tipi supportati da connettere AAD (ad esempio sincronizzazione delle password hash, l'autenticazione pass-through, servizio token di sicurezza supportate da Office 365 in locale, et cetera.)
    
  - È necessario AAD connettersi configurata e funzioni per la sincronizzazione e replica degli utenti.
    
  - Dopo aver verificato che ibrida funzioni tra locali e Office 365:
    
  - Istruzione di supporto ufficiale per la distribuzione ibrida di Exchange che informa che è necessario disporre di aggiornamento Cumulativo corrente o aggiornamento Cumulativo corrente - 1.
    
  - Assicurarsi che sia un utente di test in locale, nonché un utente di test ibrida ospitati in Office 365 possano accedere alla Skype per Business desktop client (se si desidera utilizzare l'autenticazione moderno con Skype) e Microsoft Outlook (se si desidera pertanto utilizza l'autenticazione moderno con Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Altre informazioni necessarie iniziare?
<a name="BKMK_Whatelse"> </a>

1. Tutti gli scenari per i server locali implicano l'utilizzo di impostazione autenticazione moderno locale (in realtà, per Skype per le aziende non esiste un elenco di Supported topologies) in modo che sia il server responsabile dell'autenticazione e autorizzazione in (Cloud Microsoft Servizio token di sicurezza del AAD, denominato 'evoSTS') e l'aggiornamento di Azure Active Directory (AAD) sull'URL o spazi dei nomi utilizzati per l'installazione locale di entrambi Skype per Business o di Exchange. Di conseguenza, i server locali assumono una dipendenza Microsoft Cloud. Effettuare questa operazione può essere considerata configurazione 'autenticazione ibrida'.
    
2. In questo articolo collegamenti fuori ad altri utenti che consentono di scegliere supportate topologie di autenticazione moderno (necessarie solo per Skype per le aziende) e procedure articles tale struttura la procedura di installazione o i passaggi per disabilitare l'autenticazione moderno per Exchange locale e Skype for Business in locale. Preferito in questa pagina nel browser se prevede di necessario base principale per l'utilizzo di autenticazione moderno nell'ambiente server.
    
## <a name="list-of-modern-authentication-urls"></a>Elenco degli URL autenticazione moderno
<a name="BKMK_URLListforMA"> </a>

- [Come configurare Exchange Server locali all'autenticazione moderno](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Skype per le topologie di Business è supportato con l'autenticazione moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Come configurare Skype aziendali locali per utilizzare l'autenticazione moderno](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

