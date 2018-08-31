---
title: Come configurare Skype for Business locale per utilizzare l'autenticazione moderna ibrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: L'autenticazione moderno è un metodo di gestione delle identità che offre maggiore protezione utente autenticazione e autorizzazione, è disponibile per Skype per Business server locali e di Exchange server in locale, nonché Skype dominio diviso per ibridi Business.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541467"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Come configurare Skype for Business locale per utilizzare l'autenticazione moderna ibrida

L'autenticazione moderno è un metodo di gestione delle identità che offre maggiore protezione utente autenticazione e autorizzazione, è disponibile per Skype per Business server locali e di Exchange server in locale, nonché Skype dominio diviso per ibridi Business.
  
 **Importante** Se si desidera fornire ulteriori informazioni di autenticazione (gestione moderno) e sui motivi per cui potrebbe essere preferibile utilizzare della società o dell'organizzazione? [In questo documento](hybrid-modern-auth-overview.md) per una panoramica di controllo. Se è necessario sapere quali Skype per con MA che descritte di seguito sono supportate le topologie Business! 
  
 **Prima di iniziare**, è possibile chiamare il metodo: 
  
- Autenticazione moderno \> agente di gestione
    
- Autenticazione moderno ibrida \> alta
    
- Exchange locale \> EXCH
    
- Exchange Online \> EXO
    
- Skype aziendali locali \> SFB
    
- Skype per le aziende Online e \> SFBO
    
Inoltre, * se un'immagine in questo articolo include un oggetto che è "inattivo" o "disattivato" che si intende l'elemento visualizzato in grigio **non è** incluso nella configurazione di gestione specifiche. * 
  
## <a name="read-the-summary"></a>Leggere le informazioni di riepilogo

In questo riepilogo include il processo di passi che potrebbero invece vanno persi durante l'esecuzione ed è utile per un elenco di controllo generale tenere traccia di cui è in corso il processo.
  
1. Per prima cosa, verificare che siano soddisfatti tutti i prerequisiti.
    
1. Rispetto a molti **Prerequisiti** sono comuni per entrambi Skype per le aziende ed Exchange, [vedere l'articolo di panoramica per l'elenco di controllo pre-req](hybrid-modern-auth-overview.md). Questo *prima di* iniziare le procedure descritte in questo articolo. 
    
2. Raccogliere le informazioni di alta specifici che necessari in un file o OneNote.
    
3. Attivare via moderno Authentication for EXO (se non già attivata).
    
4. Attivare via moderno Authentication for SFBO (se non già attivata).
    
5. Attivare l'autenticazione moderno ibrida di Exchange in locale.
    
6. Attivare l'autenticazione moderno ibrida per Skype aziendali locali.
    
Si noti che la procedura seguente attiva agente di gestione per SFB, SFBO, EXCH ed EXO -, ovvero tutti i prodotti che possono partecipare a una configurazione di memoria alta di SFB e SFBO (inclusi dipendenze EXCH/EXO). In altre parole, se gli utenti sono ospitati nel / create cassette postali in qualsiasi parte dell'ambiente ibrido (EXO + SFBO, EXO + SFB, EXCH + SFBO, o EXCH + SFB), il prodotto completato sarà simile al seguente:
  
![Una combinazione Skype 6 per la topologia di alta business presenta agente di gestione tutti i percorsi possibili quattro.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Come si può notare sono disponibili quattro diverse posizioni per attivare la gestione! Per un'esperienza utente ottimale è consigliabile che attivare agente di gestione in tutte e quattro queste posizioni. Se Impossibile attivare l'agente di gestione in tutti i percorsi, regolare i passaggi descritti in modo che si accende solo nelle posizioni necessari per l'ambiente di gestione.
  
Vedere l' [argomento di supporto per Skype for Business con agente di gestione](https://technet.microsoft.com/en-us/library/mt803262.aspx) per le topologie supportate. 
  
 **Importante** Verificare che vengano soddisfatti tutti i prerequisiti prima di iniziare. Sono disponibili informazioni [di seguito](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Raccolta di tutte le informazioni di alta specifici che necessari

Dopo aver ricontrollato che siano soddisfatti i [Prerequisiti](hybrid-modern-auth-overview.md) per utilizzare l'autenticazione moderno (vedere sopra), è consigliabile creare un file per conservare le informazioni necessarie per la configurazione alta in anticipo i passaggi. Esempi utilizzati in questo articolo: 
  
- **Dominio SIP/SMTP**
    
  - Ad esempio contoso.com (federata con Office 365)
    
- **ID tenant**
    
  - GUID che rappresenta il tenant di Office 365 (al momento dell'accesso di contoso.onmicrosoft.com).
    
- **URL del servizio Web CU5 SFB 2015**
    
È necessario dell'URL del servizio web interne ed esterne per tutti i pool SfB 2015 distribuiti. Per ottenere tali, eseguire le operazioni seguenti da Skype per Business Management Shell:
  
Get-CsService - WebServer | PoolFqdn Select-Object, InternalFqdn, Fqdnesterno | FL
  
- Ad esempio interna:https://lyncwebint01.contoso.com
    
- Ad esempio esterni:https://lyncwebext01.contoso.com
    
Se si utilizza un server Standard Edition, l'URL interno sarà vuoto. In questo caso, utilizzare il nome fqdn del pool per l'URL interno.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Attivare l'autenticazione moderno per EXO

Seguire le istruzioni riportate di seguito: [Exchange Online: come abilitare il tenant per l'autenticazione moderno.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Attivare l'autenticazione moderno per SFBO

Seguire le istruzioni riportate di seguito: [Skype Business online: abilitare il tenant per l'autenticazione moderno](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Attivare l'autenticazione moderno ibrida di Exchange in locale

Seguire le istruzioni riportate di seguito: [come configurare Exchange Server locale per utilizzare l'autenticazione moderno ibrida](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Attivare l'autenticazione moderno ibrida per Skype aziendali locali

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Aggiungere locale web service URL come nomi SPN in Azure Active Directory

A questo punto è necessario eseguire i comandi per aggiungere gli URL (raccolti precedentemente) come entità servizio in SFBO.
  
 **Nota** Nomi delle entità servizi (SPN) identificano i servizi web e associarli a un'entità di sicurezza (ad esempio, un nome account o gruppo) in modo che il servizio può agire per conto di un utente autorizzato. Client di autenticazione in un server effettuare trattamento dei dati che nomi SPN contenuti in. 
  
1. Innanzitutto, connettersi a AAD con [le relative istruzioni](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).
    
2. Eseguire questo comando locale, per ottenere un elenco di URL del servizio web SFB.
    
  - Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Selezionare gli attributi SPN - ExpandProperty
    
    Si noti che il AppPrincipalId inizia con '00000004'. Corrisponde a Skype Business online.
    
    Prendere nota delle (e cattura di schermata per un confronto successivo) l'output di questo comando, che includono un SE e WS URL, ma sono costituiti principalmente nomi dell'entità servizio che iniziano con 00000004-0000-0ff1-ce00-000000000000 /.
    
3. Se l'interno **o** esterno sono presenti gli URL SFB in locale (ad esempio https://lyncwebint01.contoso.com e https://lyncwebext01.contoso.com) è necessario aggiungere tali record specifici a questo elenco. 
    
    Assicurarsi di sostituire *l'URL di esempio* , sotto, con l'URL effettivo nei comandi Add! 
    
  - $x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ") 
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ") 
    
  - Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - gli attributi SPN $x.ServicePrincipalNames
    
4. Verificare che i nuovi record sono stati aggiunti eseguire nuovamente il comando Get-MsolServicePrincipal del passaggio 2 ed esaminando attraverso l'output. Confrontare l'elenco / schermata prima per il nuovo elenco di nomi SPN (può inoltre essere cattura di schermata del nuovo elenco per i record). Se hanno avuto esito positivo, verrà visualizzato due nuovi URL nell'elenco. Passando dall'esempio, l'elenco di nomi SPN ora includerà URL specifici https://lyncweb01.contoso.com e https://autodiscover.contoso.com.
    
### <a name="create-the-evosts-auth-server-object"></a>Creare l'oggetto Server EvoSTS autenticazione

Eseguire il comando seguente nel Skype per Business Management Shell.
  
- New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-tipo AzureAD
    
### <a name="enable-hybrid-modern-authentication"></a>Abilitare l'autenticazione moderno ibrido

Questo è il passaggio che attiva effettivamente agente di gestione. Senza modificare il flusso di autenticazione client, è possono eseguire i passaggi precedenti in anticipo rispetto alla volta. Quando si è pronti modificare il flusso di autenticazione, eseguire questo comando nel Skype per Business Management Shell. 
  
- Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS
    
## <a name="verify"></a>Verifica

Se si abilita alta, successivo account di accesso del client utilizzerà il nuovo flusso di autenticazione. Si noti che solo attivando alta non verrà attivato una nuova autenticazione per ogni client. Il client ad autenticarsi in base alla durata di token di autenticazione e/o hanno i certificati.
  
Per verificare che funzioni alta dopo avere abilitato, disconnettersi da un client Windows SFB test e assicurarsi di fare clic su "Elimina le credenziali". Ripetere l'accesso. Il client è ora necessario utilizzare il flusso di autenticazione moderno e l'account di accesso includerà un prompt dei comandi di **Office 365** per una "lavoro o scuola' account visualizzato a destra prima che il client contatta il server e consente l'accesso. 
  
È consigliabile inoltre ricercare le informazioni di configurazione' ' Skype per i client Business per un'autorità di OAuth' '. A tale scopo nei computer client, tenere premuto il tasto CTRL contemporaneamente che facendo clic il Skype icona Business nel cassetto di notifica di Windows. Fare clic su informazioni di configurazione dal menu visualizzato. Nella finestra 'Skype per informazioni sulla configurazione di Business' che verrà visualizzata sul desktop, cercare le operazioni seguenti:
  
![Le informazioni di configurazione di un Skype per Business Client utilizzando l'autenticazione moderno mostrano un Lync ed EWS OAUTH autorità URL di https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
È inoltre deve tenere premuto il tasto CTRL contemporaneamente a destra fare clic sull'icona per il client di Outlook (anche nella barra delle applicazioni Windows Notifications) e fare clic su 'stato di connessione. Cercare l'indirizzo SMTP del client in base a un tipo di uso del ' portanti\*", che rappresenta il token portanti utilizzato in OAuth.
  
## <a name="related-articles"></a>Articoli correlati

[Collegamento a ritroso alla panoramica autenticazione moderno](hybrid-modern-auth-overview.md) . 
  
È necessario conoscere le modalità di utilizzare l'autenticazione (ADAL moderno) per il Skype per i client aziendali? Abbiamo passaggi [di seguito](https://technet.microsoft.com/en-us/library/mt710548.aspx).
  
Sarebbe è simile a leggere la procedura seguente quando vengono visualizzati per Exchange Server, in locale, se si esegue senza SFB? Questi passaggi sono disponibili.
  

