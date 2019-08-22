---
title: Come configurare Skype for Business locale per utilizzare l'autenticazione moderna ibrida
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: L'autenticazione moderna, è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure, è disponibile per Skype for Business Server locale e Exchange Server locale, nonché per gli ibridi di Skype for business suddivisi in domini.
ms.openlocfilehash: 5db33a39ff58ae2aa21968c2f092c8ac29af5681
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493333"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Come configurare Skype for Business locale per utilizzare l'autenticazione moderna ibrida

L'autenticazione moderna, è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure, è disponibile per Skype for Business Server locale e Exchange Server locale, nonché per gli ibridi di Skype for business suddivisi in domini.
  
 **Importante** Per ulteriori informazioni sull'autenticazione moderna (MA) e sul perché potrebbe essere preferibile utilizzarla nella propria azienda o nell'organizzazione? Per una panoramica, vedere [questo documento](hybrid-modern-auth-overview.md) . Se hai bisogno di sapere quali topologie Skype for business sono supportate con MA, questo è documentato qui! 
  
 **Prima di iniziare**, chiamo: 
  
- Autenticazione \> moderna ma
    
- HMA di autenticazione \> moderna ibrida
    
- Exch locale \> di Exchange
    
- ESO di \> Exchange Online
    
- Questo in locale \> di Skype for business
    
- e Skype for business online \> SFBO
    
Inoltre, * se un elemento grafico di questo articolo contiene un oggetto che è "grigio" o "oscurato" che indica che il componente visualizzato in grigio **non è** incluso nella configurazione specifica di ma. * 
  
## <a name="read-the-summary"></a>Leggere il riepilogo

Questo riepilogo riduce il processo in passaggi che potrebbero altrimenti perdersi durante l'esecuzione ed è utile per una check-list generale per tenere conto del percorso in cui ci si trova.
  
1. Prima di tutto, assicurarsi di rispettare tutti i prerequisiti.
    
1. Poiché molti **prerequisiti** sono comuni sia per Skype for business che per Exchange, [vedere l'articolo introduttivo relativo all'elenco di controllo di prereq](hybrid-modern-auth-overview.md). Eseguire questa operazione *prima* di iniziare una delle procedure descritte in questo articolo. 
    
2. Raccogliere le informazioni specifiche di HMA necessarie in un file o in OneNote.
    
3. Attiva l'autenticazione moderna per EXO (se non è già attivata).
    
4. Abilitare l'autenticazione moderna per SFBO (se non è già attivata).
    
5. Abilitare l'autenticazione moderna ibrida per Exchange locale.
    
6. Attiva l'autenticazione moderna ibrida per Skype for business in locale.
    
Nota questi passaggi attivano MA per questo, SFBO, EXCH e EXO, ovvero tutti i prodotti che possono partecipare a una configurazione di HMA di questo e SFBO (incluse le dipendenze su EXCH/EXO). In altre parole, se gli utenti sono ospitati in/dispongono di cassette postali create in qualsiasi parte dell'ambiente ibrido (EXO + SFBO, EXO + questo, EXCH + SFBO o EXCH + questo), il prodotto finale sarà simile al seguente:
  
![Una topologia di HMA di Skype for business mista ha un Master in tutte e quattro le posizioni possibili.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Come si può notare, ci sono quattro luoghi diversi per accendere MA! Per una migliore esperienza utente, si consiglia di abilitare MA in tutte e quattro le posizioni. Se non è possibile abilitare MA in tutti questi percorsi, regolare i passaggi in modo che si accenda solo nelle posizioni che sono necessarie per l'ambiente.
  
Per informazioni sulle topologie supportate, vedere l' [argomento relativo alla supportabilità per Skype for business con ma](https://technet.microsoft.com/en-us/library/mt803262.aspx) . 
  
 **Importante** Verificare che siano stati soddisfatti tutti i prerequisiti prima di iniziare. Queste informazioni sono disponibili [qui](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Raccogliere tutte le informazioni specifiche di HMA necessarie

Dopo aver verificato che vengano soddisfatti i [prerequisiti](hybrid-modern-auth-overview.md) per l'utilizzo dell'autenticazione moderna (vedere la nota precedente), è necessario creare un file per contenere le informazioni necessarie per la configurazione di HMA nei passaggi successivi. Esempi utilizzati in questo articolo: 
  
- **Dominio SIP/SMTP**
    
  - Ex. contoso.com (è federato con Office 365)
    
- **ID tenant**
    
  - GUID che rappresenta il tenant di Office 365 (nell'account di accesso di contoso.onmicrosoft.com).
    
- **URL del servizio Web di questo 2015 CU5**
    
Sarà necessario l'URL del servizio Web interno ed esterno per tutti i pool di questo 2015 distribuiti. Per ottenere queste operazioni, eseguire la seguente procedura da Skype for Business Management Shell:
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Ex. Internohttps://lyncwebint01.contoso.com
    
- Ex. Esternohttps://lyncwebext01.contoso.com
    
Se si utilizza un server Standard Edition, l'URL interno sarà vuoto. In questo caso, utilizzare il nome di dominio completo del pool per l'URL interno.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Abilitare l'autenticazione moderna per EXO

Seguire le istruzioni riportate di seguito: [Exchange Online: informazioni su come abilitare il tenant per l'autenticazione moderna.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Abilitare l'autenticazione moderna per SFBO

Seguire le istruzioni riportate di seguito: [Skype for business online: abilitare il tenant per l'autenticazione moderna](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Abilitare l'autenticazione moderna ibrida per Exchange locale

Seguire le istruzioni riportate di seguito: informazioni [su come configurare Exchange Server locale per l'utilizzo dell'autenticazione moderna ibrida](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Abilitare l'autenticazione moderna ibrida per Skype for business in locale

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Aggiungere URL dei servizi Web locali come nomi SPN in Azure AD

A questo punto è necessario eseguire comandi per aggiungere gli URL (raccolti in precedenza) come entità di servizio in SFBO.
  
 **Note** I nomi dell'entità servizio (SPN) identificano i servizi Web e li associano a un'entità di sicurezza, ad esempio un nome account o un gruppo, in modo che il servizio possa agire per conto di un utente autorizzato. I client che eseguono l'autenticazione in un server utilizzano le informazioni contenute nei nomi SPN. 
  
1. Per prima cosa, connettersi a AAD con [queste istruzioni](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).
    
2. Eseguire questo comando, in locale, per ottenere un elenco di URL del servizio Web di questo.

   Si noti che AppPrincipalId inizia con `00000004`. Corrisponde a Skype for business online.
    
   Prendere nota di (e screenshot per il confronto successivo) l'output di questo comando, che includerà un URL SE e WS, ma principalmente costituito da nomi SPN `00000004-0000-0ff1-ce00-000000000000/`che iniziano con.
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. Se gli URL di questo interni **o** esterni sono mancanti (ad esempio, https://lyncwebint01.contoso.com e https://lyncwebext01.contoso.com) sarà necessario aggiungere tali record specifici all'elenco. 
    
    Assicurarsi di sostituire *gli URL di esempio* , di seguito, con gli URL effettivi nei comandi Aggiungi! 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. Verificare che i nuovi record siano stati aggiunti eseguendo di nuovo il comando Get-MsolServicePrincipal viene del passaggio 2 e analizzando l'output. Confrontare l'elenco/screenshot da prima al nuovo elenco di nomi SPN (è anche possibile schermare il nuovo elenco per i record). In caso di esito positivo, verranno visualizzati i due nuovi URL presenti nell'elenco. In questo esempio, l'elenco dei nomi SPN includerà ora gli URL https://lyncweb01.contoso.com specifici e https://lyncwebext01.contoso.com/.
    
### <a name="create-the-evosts-auth-server-object"></a>Creare l'oggetto server auth EvoSTS

Eseguire il seguente comando in Skype for Business Management Shell.
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a>Abilitare l'autenticazione moderna ibrida

Questo è il passaggio che attiva effettivamente MA. Tutti i passaggi precedenti possono essere eseguiti in anticipo senza modificare il flusso di autenticazione del client. Quando si è pronti per modificare il flusso di autenticazione, eseguire questo comando in Skype for Business Management Shell. 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a>Verificare

Dopo aver abilitato HMA, l'account di accesso successivo di un client utilizzerà il nuovo flusso di autenticazione. Si noti che l'attivazione di HMA non attiverà una nuova autenticazione per un client. I client eseguono di nuovo l'autenticazione in base alla durata dei token di autenticazione e/o ai cert che dispongono.
  
Per testare il funzionamento di HMA dopo averla abilitata, disconnettersi da un client di Windows questo di test e fare clic su' Elimina le credenziali '. Accedere di nuovo. Il client dovrebbe ora usare il flusso di autenticazione moderna e ora il tuo account di accesso includerà un prompt di **Office 365** per un account ' work or School ', visto subito prima che il client contatti il server e ti registri. 
  
È inoltre necessario controllare le ' informazioni di configurazione ' per i client Skype for business per un'autorità OAuth. Per eseguire questa operazione nel computer client, tenere premuto il tasto CTRL contemporaneamente facendo clic con il pulsante destro del mouse sull'icona Skype for business nel vassoio di notifica di Windows. Fare clic su informazioni di configurazione nel menu visualizzato. Nella finestra ' informazioni di configurazione di Skype for business ' che verrà visualizzata sul desktop, cercare gli elementi seguenti:
  
![Le informazioni di configurazione di un client Skype for business utilizzando l'autenticazione moderna mostrano un URL dell'autorità OAUTH di https://login.windows.net/common/oauth2/authorizeLync e EWS.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
È inoltre necessario tenere premuto il tasto CTRL contemporaneamente facendo clic con il pulsante destro del mouse sull'icona per il client di Outlook (anche nel vassoio notifiche di Windows) e facendo clic su' stato connessione '. Cercare l'indirizzo SMTP del client rispetto a un tipo di "portatore\*", che rappresenta il token del portatore utilizzato in OAuth.
  
## <a name="related-articles"></a>Articoli correlati

[Collegare di nuovo la panoramica dell'autenticazione moderna](hybrid-modern-auth-overview.md) . 
  
È necessario sapere come usare l'autenticazione moderna (ADAL) per i client Skype for business? Sono disponibili passaggi. [](https://technet.microsoft.com/en-us/library/mt710548.aspx)
  
Si desidera leggere questi passaggi come vengono visualizzati per Exchange Server, in locale, in esecuzione senza questo? Tali passaggi sono disponibili qui.
  

