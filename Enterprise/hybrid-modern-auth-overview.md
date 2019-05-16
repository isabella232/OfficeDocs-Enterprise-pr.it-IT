---
title: Panoramica dell'autenticazione moderna ibrida e prerequisiti per l'utilizzo con i server Skype for business e Exchange locali
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: L'autenticazione moderna è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure. È disponibile per le distribuzioni ibride di Skype for Business Server locale ed Exchange Server locale, nonché per gli ibridi di Skype for business suddivisi in domini. In questo articolo vengono forniti collegamenti a documenti correlati relativi ai prerequisiti, all'installazione e alla disabilitazione dell'autenticazione moderna e ad alcuni client correlati (es. Informazioni su Outlook e client Skype).
ms.openlocfilehash: 17c61b028aacd5abaf72450e197475fa2c0a2589
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067202"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Panoramica dell'autenticazione moderna ibrida e prerequisiti per l'utilizzo con i server Skype for business e Exchange locali

L'autenticazione moderna è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure. È disponibile per le distribuzioni ibride di Office 365 di Skype for Business Server in locale ed Exchange Server locale, nonché per gli ibridi di Skype for business suddivisi in più domini. In questo articolo vengono forniti collegamenti a documenti correlati relativi ai prerequisiti, all'installazione e alla disabilitazione dell'autenticazione moderna e ad alcuni client correlati (es. Informazioni su Outlook e client Skype). 
  
- [Che cos'è l'autenticazione moderna?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [Modifiche apportate quando si utilizza l'autenticazione moderna](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Controllare lo stato di autenticazione moderna dell'ambiente locale](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [Vengono soddisfatti i prerequisiti di autenticazione moderni?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [Cos'altro è necessario sapere prima di iniziare?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Elenco degli URL di autenticazione moderni](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>Che cos'è l'autenticazione moderna?
<a name="BKMK_WhatisModAuth"> </a>

Quando si parla di comunicazione tra un client (ad esempio, il laptop o il telefono) e un server, Microsoft utilizza la frase "autenticazione moderna".
  
L'autenticazione moderna è un termine ombrello per una combinazione di metodi di autenticazione e autorizzazione, nonché alcune misure di sicurezza che si basano su criteri di accesso che potrebbero essere già familiari. Include:
  
- **Metodi di autenticazione**: autenticazione a più fattori; Autenticazione basata su certificato client; e la libreria di autenticazione di Active Directory ( [adal](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Metodi di autorizzazione**: implementazione di Microsoft di autorizzazione aperta (OAuth). 
    
- **Criteri di accesso condizionale**: la gestione delle applicazioni mobili (MAM) e l'accesso condizionale di Azure Active Directory. 
    
La gestione delle identità degli utenti con l'autenticazione moderna fornisce agli amministratori numerosi strumenti diversi da utilizzare per la protezione delle risorse e offre metodi più sicuri di gestione delle identità sia in locale (Exchange e Skype for business), Exchange Hybrid e scenari ibridi/Split-Domain di Skype for business.
  
Tenere presente che, poiché Skype for business è compatibile con Exchange, il comportamento di login che gli utenti di client Skype for business vedranno verranno effettuati tramite lo stato di autenticazione moderna di Exchange. Questo si applica anche se si dispone di un ibrido Split-Domain di Skype for business. Inoltre, il tipo di ibrido di Skype for business che supporta l'utilizzo dell'autenticazione moderna è spesso definito ' Split-Domain ' (in un dominio diviso, si hanno sia Skype for business online sia Skype for business on-Prem e gli utenti sono ospitati in entrambi i percorsi).
  
> [!IMPORTANT]
> Lo sapevate che, dall'agosto del 2017, tutti i nuovi tenant di Office 365 che includono Skype for business online ed Exchange Online avranno l'autenticazione moderna abilitata per impostazione predefinita? I tenant preesistenti non avranno una modifica nello stato di MA di default, ma tutti i nuovi tenant supportano automaticamente il set esteso di funzionalità di identità visualizzate sopra elencate. Per controllare lo stato di MA per Skype for business online, è possibile utilizzare PowerShell di Skype for business online con le credenziali di amministratore globale. Eseguire `Get-CsOAuthConfiguration` per controllare l'output di-ClientADALAuthOverride. Se-ClientADALAuthOverride è' consentito ', l'autenticazione moderna è attiva. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>Modifiche apportate quando si utilizza l'autenticazione moderna
<a name="BKMK_WhatChanges"> </a>

Quando si utilizza l'autenticazione moderna con Skype for business o Exchange Server locale, si sta ancora *eseguendo* l'autenticazione degli utenti in locale, ma la storia ** di autorizzare l'accesso alle risorse (come i file o i messaggi di posta elettronica) cambia. Per questo motivo, anche se l'autenticazione moderna riguarda la comunicazione tra client e server, i passaggi durante la configurazione di MA risultano in evoSTS (un servizio token di sicurezza utilizzato da Azure AD) impostato come server di autenticazione per Skype for business ed Exchange Server locale. 
  
La modifica apportata a evoSTS consente ai server locali di usufruire di OAuth (emissione di token) per l'autorizzazione dei client e consente inoltre ai metodi di sicurezza di utilizzo locale comuni nel cloud (come l'autenticazione a più fattori). Inoltre, il evoSTS rilascia token che consentono agli utenti di richiedere l'accesso alle risorse senza fornire la propria password come parte della richiesta. Indipendentemente dal luogo in cui gli utenti sono ospitati (di online o in locale) e indipendentemente dalla posizione in cui si trova la risorsa necessaria, EvoSTS diventerà il fulcro dell'autorizzazione degli utenti e dei client dopo che è stata configurata l'autenticazione moderna.
  
Di seguito è riportato un esempio di cosa intendo. Se il client Skype for business ha bisogno di accedere a Exchange Server per ottenere informazioni di calendario per conto di un utente, utilizza la libreria di autenticazione di Active Directory (ADAL) per eseguire tale operazione. ADAL è una libreria di codice progettata per rendere disponibili le risorse protette nella directory per le applicazioni client utilizzando i token di sicurezza OAuth. ADAL utilizza OAuth per verificare le attestazioni e i token di Exchange (anziché le password) per concedere a un utente l'accesso a una risorsa. In passato, l'autorità in una transazione come questa, ovvero il server che sa come convalidare le attestazioni degli utenti e il rilascio dei token necessari, potrebbe essere stato un servizio token di sicurezza locale o anche Active Directory Federation Services. Tuttavia, l'autenticazione moderna centralizza tale autorità con Azure Active Directory (Azure AD) nel cloud.
  
Questo significa anche che, anche se gli ambienti Exchange Server e Skype for business possono essere interamente in locale, il server di autorizzazione sarà online e l'ambiente locale deve avere la possibilità di creare e gestire una connessione a Office 365 sottoscrizione nel cloud (e nell'istanza di Azure Active Directory utilizzata dall'abbonamento come directory).
  
Cosa non cambia? Se si è in un ambiente ibrido suddiviso in domini o si utilizza Skype for business ed Exchange Server locale, tutti gli utenti devono prima eseguire l'autenticazione *locale* . In un'implementazione ibrida di autenticazione moderna, Lyncdiscovery e individuazione automatica puntano al server locale. 
  
> [!IMPORTANT]
> Se è necessario conoscere le topologie di Skype for business specifiche supportate con MA, questo è [documentato proprio qui](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Controllare lo stato di autenticazione moderna dell'ambiente locale
<a name="BKMK_CheckStatus"> </a>

Poiché l'autenticazione moderna cambia il server di autorizzazione utilizzato quando i servizi utilizzano OAuth/S2S, è necessario sapere se l'autenticazione moderna è inserita o disattivata per l'ambiente Skype for business e Exchange. È possibile controllare lo stato nei server Exchange o Skype for business, in locale, eseguendo il `Get-CSOAuthConfiguration` comando in PowerShell. Se il comando restituisce una proprietà' OAuthServers ' vuota, l'autenticazione moderna è disattivata.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Vengono soddisfatti i prerequisiti di autenticazione moderni?

Verificare e controllare questi elementi dall'elenco prima di continuare:
  
- **Specifiche di Skype for business**
    
  - Tutti i server devono disporre di questo server 2015 CU5 o versione successiva
    
  - **Eccezione** : Survivable Branch Appliance (SBA) può essere nella versione corrente (basata su Lync 2013) 
    
  - Il dominio SIP viene aggiunto come dominio federato in Office 365
    
  - Tutti i front-end di questo devono disporre di connessioni in uscita su Internet, per gli URL di autenticazione di Office 365 (TCP 443) e per i CRL radice del certificato (TCP 80) elencati nelle righe 56 e 125 della sezione ' Microsoft 365 Common and Office Online ' di [office 365 URLs and IP intervalli di indirizzi](urls-and-ip-address-ranges.md).
  
- **Skype for business locale in un ambiente ibrido di Office 365**
  - Una distribuzione di Skype for Business Server 2019 con tutti i server che eseguono Skype for Business Server 2019.
  
  - Una distribuzione di Skype for Business Server 2015 con tutti i server che eseguono Skype for Business Server 2015.
  
  - Una distribuzione con un massimo di due versioni server diverse, come elencato di seguito:
  
     - Skype for Business Server 2015 e Skype for Business Server 2019
     
  - Tutti i server Skype for business devono avere gli aggiornamenti di cummulative più recenti installati, vedere [aggiornamenti di Skype for Business Server](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) per trovare e gestire tutti gli aggiornamenti disponibili.
  - Non esiste alcun Lync Server 2010 o 2013 nell'ambiente ibrido.
    
 **Note** Se i server front-end Skype for business utilizzano un server proxy per l'accesso a Internet, l'indirizzo IP del server proxy e il numero di porta utilizzati devono essere immessi nella sezione configurazione del file Web. config per ogni front-end. 
  
- C:\Program Skype for Business Server 2015 \ Web Components\Web ticket\int\web.config
    
- C:\Program Skype for Business Server 2015 \ Web Components\Web ticket\ext\web.config
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> Assicurarsi di sottoscrivere il feed RSS per gli [URL di Office 365 e gli intervalli di indirizzi IP](urls-and-ip-address-ranges.md) per rimanere aggiornati con le ultime inserzioni degli URL necessari. 
  
- **Specifici di Exchange Server**
    
  - Si sta utilizzando Exchange Server 2013 CU19 e up o Exchange Server 2016 CU8 e versioni rialzate.
    
  - Nell'ambiente non è presente alcun server Exchange 2010.
    
  - La ripartizione del carico di SSL non è configurata. La terminazione SSL e la ricrittografia sono supportate.
    
  - Nel caso in cui l'ambiente utilizzi un'infrastruttura del server proxy per consentire ai server di connettersi a Internet, assicurarsi che tutti i server di Exchange dispongano del server proxy definito nella proprietà [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) .
  
- **Exchange Server locale in un ambiente ibrido di Office 365**

  - Se si utilizza Exchange Server 2013, è necessario che almeno un server disponga dei ruoli del server Accesso client e cassette postali installati. Anche se è possibile installare i ruoli cassette postali e accesso client su server distinti, è consigliabile installare entrambi i ruoli in ogni server per offrire maggiore affidabilità e prestazioni migliorate.
  
  - Se si utilizza Exchange Server 2016 o versione successiva, almeno un server deve disporre del ruolo del server cassette postali installato.
  
  - Non è presente alcun server Exchange 2007 o 2010 nell'ambiente ibrido.
  
  - Per tutti i server di Exchange devono essere installati gli aggiornamenti più recenti di cummulative, vedere [Upgrade Exchange to the più recenti cumulative updates](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) to find and manage all available updates.
    
- **Requisiti del protocollo e del client di Exchange**
  
  - I client seguenti supportano l'autenticazione moderna:

  |**Client**|**Protocollo primario**|**Note**|
  |:-----|:-----|:-----|
  |Outlook 2013 e Outlook 2016  <br/> |MAPI su HTTP  <br/> |MAPI su HTTP deve essere abilitato all'interno di Exchange per sfruttare l'autenticazione moderna con questi client (in genere abilitato o vero per le nuove installazioni di Exchange 2013 Service Pack 1 e superiori); Per ulteriori informazioni [, vedere come funziona l'autenticazione moderna per le app client di office 2013 e office 2016](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Assicurarsi di eseguire la build minima richiesta di Outlook; vedere [gli aggiornamenti più recenti per le versioni di Outlook che utilizzano Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 per Mac  <br/> |Servizi Web Exchange  <br/> |  <br/> |
  |Outlook per iOS e Android  <br/> |  <br/> |Per ulteriori informazioni, vedere [utilizzo dell'autenticazione moderna ibrida con Outlook per iOS e Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) .  <br/> |
  |Client Exchange ActiveSync (ad esempio, iOS11 mail)  <br/> |Exchange ActiveSync  <br/> |Per i client Exchange ActiveSync che supportano l'autenticazione moderna, è necessario ricreare il profilo per passare dall'autenticazione di base all'autenticazione moderna.  <br/> |

- **Prerequisiti generali**
    
  - Se si utilizza ADFS, è necessario disporre di Windows 2012 R2 ADFS 3,0 e superiori per la Federazione
    
  - Le configurazioni di identità sono uno dei tipi supportati da AAD Connect (ad esempio sincronizzazione hash delle password, autenticazione pass-through, STS locali supportati da Office 365 e così via).
    
  - Si dispone di AAD Connect configurato e funzionante per la replica e la sincronizzazione degli utenti.
    
  - È stato verificato che Hybrid è configurato utilizzando la modalità topologia ibrida classica di Exchange tra l'ambiente locale e quello di Office 365. Dichiarazione di supporto ufficiale per Exchange Hybrid indica che è necessario disporre di un cu-1 corrente o di un cu.
    
    > [!Note]
    > L'autenticazione moderna ibrida non è supportata con l' [agente ibrido](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).
    
  - Assicurarsi che sia un utente di test locale, sia un utente di test ibrido ospitato in Office 365, possano accedere al client desktop di Skype for business (se si desidera utilizzare l'autenticazione moderna con Skype) e Microsoft Outlook (se lo si desidera, utilizzare l'autenticazione moderna con Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Cos'altro è necessario sapere prima di iniziare?
<a name="BKMK_Whatelse"> </a>

1. Tutti gli scenari per i server locali implicano la configurazione dell'autenticazione moderna locale (infatti, per Skype for business è presente un elenco di topologie supportate), in modo che il server responsabile dell'autenticazione e dell'autorizzazione si trovi nel cloud Microsoft ( Il servizio token di sicurezza di AAD, denominato "evoSTS", e l'aggiornamento di Azure Active Directory (AAD) sugli URL o gli spazi dei nomi utilizzati dall'installazione locale di Skype for business o di Exchange. Di conseguenza, i server locali assumono una dipendenza cloud Microsoft. L'esecuzione di questa azione può essere considerata configurata come ' Hybrid auth '.
    
2. In questo articolo vengono forniti collegamenti ad altri utenti che consentono di scegliere le topologie di autenticazione moderna supportate (necessarie solo per Skype for business) e gli articoli che illustrano i passaggi di installazione oppure i passaggi per disabilitare l'autenticazione moderna per Exchange locale e Skype for business locale. Questa pagina è preferita nel browser se si ha bisogno di una Home-base per l'utilizzo dell'autenticazione moderna nell'ambiente server.
    
## <a name="list-of-modern-authentication-urls"></a>Elenco degli URL di autenticazione moderni
<a name="BKMK_URLListforMA"> </a>

- [Informazioni su come configurare Exchange Server locale per l'utilizzo dell'autenticazione moderna](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Topologie di Skype for business supportate con l'autenticazione moderna](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Come configurare Skype for business in locale per l'utilizzo dell'autenticazione moderna](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Rimozione o disabilitazione dell'autenticazione moderna ibrida da Skype for Business ed Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

