---
title: Utilizzo di Azure Active Directory per l'autenticazione di SharePoint Server
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.date: 3/2/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: 'Riepilogo: Informazioni su come ignorare il servizio di controllo di accesso di Azure e utilizzo di SAML 1.1 per autenticare gli utenti di SharePoint Server con Azure Active Directory.'
ms.openlocfilehash: 1ab0bb3215531ca8b2d0fda8d70874f966438759
ms.sourcegitcommit: def3e311db9322e469753bac59ff03624349b140
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Utilizzo di Azure Active Directory per l'autenticazione di SharePoint Server

 **Riepilogo:** Informazioni su come eseguire l'autenticazione agli utenti di SharePoint Server 2016 con Azure Active Directory.
  
> [!NOTE]
> In questo articolo si basa sul lavoro di Lorenzo Evans, Microsoft Principal Program Manager. 

<blockquote>
<p>In questo articolo si riferisce a esempi di codice per l'interazione con Azure Active Directory grafico. È possibile scaricare gli esempi di codice [di seguito](https://github.com/kaevans/spsaml11/tree/master/scripts).</p>
</blockquote>

SharePoint Server 2016 offre la possibilità per autenticare gli utenti che utilizzano l'autenticazione basata sulle attestazioni, semplificando la gestione degli utenti tramite l'autenticazione di essi con i provider di identità diversi che si considera attendibile, ma un utente di gestione. Ad esempio, invece di gestire l'autenticazione degli utenti tramite servizi di dominio Active Directory (AD DS), è possibile consentire agli utenti per l'autenticazione con Azure Active Directory (Azure Active Directory). In questo modo l'autenticazione per gli utenti di cloud-only con il suffisso onmicrosoft.com il proprio nome utente, gli utenti sincronizzati con una directory locale e utenti guest da altre directory invitati. Consente inoltre di poter usufruire delle funzionalità di Azure Active Directory, ad esempio l'autenticazione a più fattori e funzionalità di reporting avanzate.

> [!IMPORTANT]
> La soluzione descritta in questo articolo può essere utilizzata anche con SharePoint Server 2013; Tuttavia, tenere presente che SharePoint Server 2013 si avvicina alla fine del supporto "Mainstream". Per ulteriori informazioni, vedere [Microsoft ciclo di vita](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) e [Aggiornato per la manutenzione dei prodotto per SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).

In questo articolo viene illustrato come utilizzare Azure Active Directory per autenticare gli utenti anziché locale di dominio Active Directory. In questa configurazione, Azure Active Directory diventa un provider di identità attendibile per SharePoint Server 2016. Questa configurazione viene aggiunto un metodo di autenticazione utente distinto dall'autenticazione di dominio Active Directory utilizzato per l'installazione di SharePoint Server 2016 stesso. Per trarre vantaggio da questo articolo, è consigliabile acquisire familiarità con WS-Federation. Per ulteriori informazioni, vedere [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).

![Utilizzo di Azure Active Directory per l'autenticazione di SharePoint](images/SAML11/fig1-architecture.png)

In precedenza, questa configurazione avrebbe richiesto un servizio federativo, ad esempio Azure Access Control Service (ACS) nel cloud o in un ambiente che ospita Active Directory Federation Services (ADFS) trasformare token da 2.0 SAML da SAML 1.1. Questa trasformazione non è più necessaria in quanto consente di Azure Active Directory ora emittente token SAML 1.1. Nel diagramma precedente viene illustrato il funzionamento dell'autenticazione per gli utenti di SharePoint 2016 in questa configurazione, dimostrare che viene a mancare un requisito per intermediario per eseguire questa trasformazione.

> [!NOTE]
> Questa configurazione può essere utilizzato se la farm di SharePoint è ospitata in macchine virtuali di Azure o locale. Non richiede l'apertura di porte del firewall aggiuntivi oltre alla conferma che gli utenti può accedere Azure Active Directory dal browser.

Per informazioni sull'accessibilità 2016 SharePoint, vedere [Linee guida sull'accessibilità in SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Panoramica della configurazione

Eseguire la procedura generale per configurare l'ambiente da utilizzare Azure Active Directory come un provider di identità di SharePoint Server 2016.

1. Creare una nuova directory Azure Active Directory oppure utilizzare la directory esistente.
2. Verificare l'area per l'applicazione web che si desidera proteggere con Azure Active Directory è configurata per l'utilizzo di SSL.
3. Creare una nuova applicazione aziendale in Azure Active Directory.
4. Configurare un nuovo provider di identità attendibile in SharePoint Server 2016.
5. Impostare le autorizzazioni per l'applicazione web.
6. Aggiungere un criterio di emissione di token SAML 1.1 in Azure Active Directory.
7. Verificare il nuovo provider.

Nelle sezioni seguenti viene descritto come eseguire queste attività.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Passaggio 1: Creare una nuova directory Azure Active Directory oppure utilizzare la directory esistente

Nel portale di Azure ([https://portal.azure.com](https://portal.azure.com)), creare una nuova directory. Fornire il nome dell'organizzazione, il nome di dominio iniziale e il paese o regione.

![Creazione di una directory](images/SAML11/fig2-createdirectory.png) 

 Se si dispone già di una directory, ad esempio quello utilizzato per la sottoscrizione di Microsoft Azure o Microsoft Office 365, è possibile utilizzare tale directory invece. È necessario disporre delle autorizzazioni per registrare le applicazioni nella directory.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Passaggio 2: Verificare che l'area per l'applicazione web che si desidera proteggere con Azure Active Directory è configurata per l'utilizzo di SSL

In questo articolo è stato scritto tramite l'architettura di riferimento di [eseguire una farm di SharePoint Server 2016 in Azure la disponibilità elevata](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). Script di accompagnamento dell'articolo utilizzati per distribuire la soluzione illustrata in [questo articolo](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) creare un sito che non utilizza SSL.  

Utilizzo di SAML, è necessario configurare l'applicazione per l'utilizzo di SSL. Se l'applicazione web di SharePoint non è configurato per l'utilizzo di SSL, utilizzare la procedura seguente per creare un nuovo certificato autofirmato per configurare l'applicazione web per SSL. Questa configurazione è solo a scopo di un ambiente di laboratorio e non è progettata per la produzione. Ambienti di produzione è consigliabile utilizzare un certificato firmato.

1. Accedere ad **Amministrazione centrale** > **Gestione applicazioni** > **Gestisci applicazioni Web**e scegliere l'applicazione web che deve essere estesa per l'utilizzo di SSL. Selezionare l'applicazione web e fare clic sul pulsante **della barra multifunzione Extend** . Estendere l'applicazione web per utilizzare lo stesso URL mentre l'utilizzo di SSL per la porta 443.</br>![Estendere l'applicazione web a un altro sito IIS](images/SAML11/fig3-extendwebapptoiis.png)</br>
2. In Gestione IIS, fare doppio clic su **Certificati del Server**.
3. Nel riquadro **Azioni** fare clic su **Crea certificato autofirmato**. Digitare un nome descrittivo del certificato nella casella specificare un nome descrittivo per la casella di certificato e quindi fare clic su **OK**.
4. Nella finestra di dialogo **Modifica Binding sito** verificare che il nome host è identico al nome descrittivo, come illustrato nella figura seguente.</br>![Modifica dei binding dei siti in IIS](images/SAML11/fig4-editsitebinding.png)</br>

Ogni server web front-end della farm di SharePoint richiederà la configurazione del certificato per l'associazione del sito in IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Passaggio 3: Creare una nuova applicazione aziendale in Azure Active Directory

1. Nel portale di Azure ([https://portal.azure.com](https://portal.azure.com)), aprire la directory di Azure Active Directory. Fare clic su **Applicazioni aziendali**e quindi fare clic su **nuova applicazione**. Scegliere **l'applicazione Non raccolta**. Specificare un nome, ad esempio *Integrazione SAML con SharePoint* e fare clic su **Aggiungi**.</br>![Aggiunta di una nuova applicazione non raccolta](images/SAML11/fig5-addnongalleryapp.png)</br>
2. Scegliere il collegamento Single sign-on nel riquadro di spostamento per configurare l'applicazione. Modificare l'elenco a discesa **modalità Single Sign-on** di **SAML-based Sign-on** per visualizzare le proprietà di configurazione di SAML per l'applicazione. Configurare le proprietà seguenti:</br>
    - Identificatore:`urn:sharepoint:portal.contoso.local`
    - URL di risposta:`https://portal.contoso.local/_trust/default.aspx`
    - URL di accesso:`https://portal.contoso.local/_trust/default.aspx`
    - Identificatore utente:`user.userprincipalname`</br>
    - Nota: È necessario modificare gli URL sostituendo *portal.contoso.local* con l'URL del sito di SharePoint che si desidera proteggere.</br>
3. Impostare una tabella (simile a 1 nella tabella riportata di seguito) che include le righe seguenti:</br> 
    - Area di autenticazione
    - Percorso completo al file del certificato di firma SAML
    - SAML Single Sign-On URL del servizio (sostituendo */saml2* con */wsfed*)
    - ID dell'oggetto Application. </br>
Copiare il valore *dell'identificatore* nella proprietà *dell'area di autenticazione* in una tabella (vedere tabella 1, sotto)
4. Salvare le modifiche.
5. Fare clic sul collegamento **Configura (nome app)** per accedere alla pagina Configura sign-on.</br>![Configurazione di un single sign-on pagina](images/SAML11/fig7-configssopage.png)</br> 
    -  Fare clic sul collegamento di **SAML certificato per la firma - non elaborati** per scaricare il certificato di firma SAML come file con estensione cer. Copiare e incollare il percorso completo per il file scaricato la tabella.
    - Copiare e incollare il collegamento SAML Single Sign-On URL del servizio nei, sostituendo parte */saml2* dell'URL con */wsfed*.</br>
6.  Passare al riquadro delle **proprietà** per l'applicazione. Copiare e incollare il valore dell'ID oggetto nella tabella che impostare nel passaggio 3.</br>![Riquadro delle proprietà per l'applicazione](images/SAML11/fig8-propertiespane.png)</br>
7. Utilizzando i valori che acquisite, verificare che la tabella che impostare nel passaggio 3 è analogo a 1 nella tabella riportata di seguito.


| Nella tabella 1: I valori acquisiti  |  |
|---------|---------|
|Area di autenticazione | `urn:sharepoint:portal.contoso.local` |
|Percorso completo al file del certificato di firma SAML | `C:/temp/SharePoint SAML Integration.cer`  |
|URL del servizio single sign-on SAML (sostituire /saml2 con /wsfed) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|ID oggetto applicazione | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Sostituire il valore */saml2* nell'URL con */wsfed*. L'endpoint */saml2* elaborerà i token SAML 2.0. L'endpoint */wsfed* Attiva elaborazione SAML 1.1 basato su token ed è necessaria per la federazione SharePoint 2016 SAML.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Passaggio 4: Configurare un nuovo provider di identità attendibile in SharePoint Server 2016

Accedere a server di SharePoint Server 2016 e aprire SharePoint 2016 Management Shell. Compilare i valori di $realm, $wsfedurl e $filepath dalla tabella 1 ed eseguire i comandi seguenti per configurare un nuovo provider di identità attendibile.

> [!TIP]
> Se si ha familiarità con l'utilizzo di PowerShell o per ulteriori informazioni sul funzionamento di PowerShell, vedere [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

Successivamente, eseguire la procedura seguente per abilitare il provider di identità attendibile per l'applicazione:
1. In Amministrazione centrale, passare a **Gestione applicazione Web** e selezionare l'applicazione web che si desidera proteggere con Azure Active Directory. 
2. Sulla barra multifunzione fare clic su **Provider di autenticazione** e selezionare l'area che si desidera utilizzare.
3. Selezionare **provider di identità attendibile** e selezionare il provider di identità che appena registrata denominato *AzureAD*.  
4. L'impostazione di URL pagina di accesso, selezionare **nella pagina di accesso personalizzata** e specificare il valore "/_trust/". 
5. Fare clic su **OK**.

![Configurazione di provider di autenticazione](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a>Passaggio 5: Impostare le autorizzazioni

Gli utenti che verranno accedere Azure Active Directory e accedere a SharePoint devono disporre dell'accesso all'applicazione. 

1. Aprire la directory di Azure Active Directory nel portale di Azure. Fare clic su **Applicazioni aziendali**e quindi fare clic su **tutte le applicazioni**. Fare clic sull'applicazione creato in precedenza (integrazione SAML con SharePoint).
2. Fare clic su **utenti e gruppi**. 
3. Fare clic su **Aggiungi utente** per aggiungere un utente o gruppo che disporrà di autorizzazioni per l'accesso a SharePoint con Azure Active Directory.
4. Selezionare l'utente o gruppo, quindi fare clic su **Assegna**.
 
L'utente dispone dell'autorizzazione in Azure Active Directory, ma anche deve essere concessa l'autorizzazione di SharePoint. Utilizzare la procedura seguente per impostare le autorizzazioni per accedere all'applicazione web.

1. In Amministrazione centrale fare clic su **Gestione applicazioni**.
2. Nella sezione **Applicazioni Web** della pagina **Gestione applicazioni** fare clic su **Gestisci applicazioni Web**.
3. Fare clic sull'applicazione Web appropriata e quindi su **Criteri utenti**.
4. In criteri per l'applicazione Web, fare clic su **Aggiungi utenti**.</br>![Cercare un utente dal proprio nome di attestazione](images/SAML11/fig11-searchbynameclaim.png)</br>
5. Nella finestra di dialogo **Aggiunta utenti** fare clic sull'area appropriata in **Aree** e quindi fare clic su **Avanti**.
6. Nella sezione **Selezione utenti** della finestra di dialogo **criteri per l'applicazione Web** fare clic sull'icona **Sfoglia** .
7. Nella casella di testo **Trova** , digitare il nome di accesso per un utente nella directory e fare clic su **Cerca**. </br>Esempio: *demouser@blueskyabove.onmicrosoft.com*.
8. Sotto l'intestazione AzureAD nella visualizzazione elenco, selezionare la proprietà name e fare clic su **Aggiungi** , quindi fare clic su **OK** per chiudere la finestra di dialogo.
9. In autorizzazioni fare clic su **Controllo completo**.</br>![Concedere il controllo completo per un utente basata sulle attestazioni](images/SAML11/fig12-grantfullcontrol.png)</br>
10. Fare clic su **Fine** e quindi su **OK**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Passaggio 6: Aggiungere un criterio di emissione di token SAML 1.1 in Azure Active Directory

Quando si crea l'applicazione di Azure Active Directory nel portale, l'impostazione predefinita all'utilizzo di SAML 2.0. SharePoint Server 2016 richiede il formato token SAML 1.1. Lo script seguente verrà rimosso il criterio di SAML 2.0 predefinito e aggiungere un nuovo criterio per i token SAML 1.1 problema. Il codice seguente è necessario scaricare gli [esempi che illustrano l'interazione con Azure Active Directory grafico](https://github.com/kaevans/spsaml11/tree/master/scripts). 


```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```
> Si noti che è importante eseguire la `Import-Module` comando come mostrato nell'esempio seguente. Verrà caricato un modulo di dipendente che contiene i comandi riportati. Potrebbe essere necessario aprire un prompt dei comandi con privilegi elevati per la corretta esecuzione di questi comandi.

Questi comandi di PowerShell di esempio sono riportati esempi di come eseguire query sull'API di grafico. Per ulteriori informazioni sui criteri di emissione di Token con Azure Active Directory, vedere [Guida di riferimento API di grafico per operazioni nei criteri](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).

## <a name="step-7-verify-the-new-provider"></a>Passaggio 7: Verificare il nuovo provider

Aprire un browser per l'URL dell'applicazione web che è stato configurato nella procedura precedente. Si verrà reindirizzati per accedere a Azure Active Directory.

![Accesso a Azure Active Directory configurato per la federazione](images/SAML11/fig13-examplesignin.png)

Viene chiesto se si desidera restare connessi.

![Restare connessi?](images/SAML11/fig14-staysignedin.png)

Infine, è possibile accedere al sito connesso con un utente dal tenant di Azure Active Directory.

![Utente effettuato l'accesso a SharePoint](images/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>Gestione dei certificati
È importante tenere presente che il certificato di firma che è stato configurato per il provider di identità attendibile nel passaggio 4 è una data di scadenza e dover essere rinnovato. Vedere l'articolo [gestire certificati federati single sign - on in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) per informazioni sul rinnovo del certificato. Dopo che il certificato è stato rinnovato in Azure Active Directory, il download in un file locale e utilizzare lo script seguente per configurare il provider di identità attendibile con il certificato di firma rinnovato. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>Configurazione di un provider di identità attendibile per più applicazioni web
La configurazione può essere utilizzato per una singola applicazione web, ma è necessario configurazione aggiuntiva se si intende utilizzare lo stesso provider di identità attendibile per più applicazioni web. Si supponga ad esempio si fosse estesa di un'applicazione web di utilizzare l'URL `https://portal.contoso.local` e si desidera eseguire l'autenticazione agli utenti di `https://sales.contoso.local` anche. A tale scopo, è necessario aggiornare il provider di identità per applicano il parametro WReply e aggiornare la registrazione dell'applicazione in Azure Active Directory per aggiungere un URL di risposta.

1. Aprire la directory di Azure Active Directory nel portale di Azure. Fare clic su **registrazioni App**e quindi fare clic su **Visualizza tutte le applicazioni**. Fare clic sull'applicazione creato in precedenza (integrazione SAML con SharePoint).
2. Fare clic su **Impostazioni**.
3. In blade impostazioni, fare clic su **Rispondi URL**. 
4. Aggiungere l'URL dell'applicazione web aggiuntivi (ad esempio `https://sales.contoso.local`) e fare clic su **Salva**. 
5. Nel server di SharePoint, aprire **SharePoint 2016 Management Shell** ed eseguire i comandi seguenti, utilizzando il nome dell'emittente di token di identità attendibile è utilizzato in precedenza.

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. In Amministrazione centrale, passare all'applicazione web e abilitare il provider di identità attendibile. Ricordare inoltre configurare l'URL della pagina di accesso come una pagina di accesso personalizzata `/_trust/`.
7. In Amministrazione centrale fare clic sull'applicazione web e scegliere **Criteri utente**. Aggiungere un utente con le autorizzazioni appropriate, come illustrato in precedenza in questo articolo.

## <a name="fixing-people-picker"></a>Correzione di selezione utenti
Gli utenti possono ora accedere 2016 SharePoint utilizzando l'identità di Azure Active Directory, ma sono ancora presenti opportunità per analisi utilizzo software per l'esperienza utente. In selezione utenti, ad esempio, la ricerca di un utente presenta più risultati della ricerca. Non esiste un risultato di ricerca per ognuno dei tipi di 3 attestazione creati nel mapping delle attestazioni. Per scegliere un account utente utilizzando la selezione utenti, è necessario digitare esattamente il proprio nome utente e scegliere il **nome** di attestazione risultati.

![I risultati di ricerca basata sulle attestazioni](images/SAML11/fig16-claimssearchresults.png)

Non esiste alcuna convalida sui valori ricerca, che possono causare errori di ortografia o all'attestazione agli utenti la scelta accidentale errato attestazione tipo da assegnare, ad esempio il **Cognome** . Ciò può impedire agli utenti di correttamente accedere alle risorse.

Per facilitare con questo scenario, non esiste un open source soluzione chiamato [AzureCP](https://yvand.github.io/AzureCP/) che fornisce un provider di attestazioni personalizzate per SharePoint 2016. Nel grafico di Azure Active Directory, viene utilizzato per risolvere quali utenti immettere ed eseguono la convalida. Ulteriori informazioni, vedere [AzureCP](https://yvand.github.io/AzureCP/). 

## <a name="additional-resources"></a>Risorse aggiuntive

[Informazioni sui WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>Partecipare alla discussione

|**Contattaci**|**Descrizione**|
|:-----|:-----|
|**Ottenere la soluzione necessaria** <br/> |Microsoft sta creando documenti contenenti soluzioni che fanno riferimento a numerosi prodotti e servizi. Fornire commenti e suggerimenti sulle soluzioni tra server proposte o richiedere una soluzione specifica inviando un'e-mail all'indirizzo [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Partecipare alla discussione sulle soluzioni** <br/> |Se si è appassionati di soluzioni basate sul cloud, prendere in considerazione l'idea di accedere al Cloud Adoption Advisory Board (CAAB) per connettersi con una community più ampia e vivace di sviluppatori di contenuti Microsoft, professionisti del settore e clienti di tutto il mondo. Per accedervi, diventare un membro dell'[area CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) della Community tecnica Microsoft e inviare una breve e-mail all'indirizzo [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Chiunque può leggere i contenuti correlati alla community nel [blog di CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Tuttavia, i membri CAAB ricevono inviti a webinar privati che descrivono le nuove soluzioni e risorse relative all'adozione del cloud.  <br/> |
|**Ottenere l'immagine visualizzata** <br/> |Se si desidera una copia modificabile dell'immagine visualizzata in questo articolo, Microsoft si occuperà di inviarla. Inviare la propria richiesta tramite e-mail, includendo l'URL e il titolo dell'immagine, all'indirizzo [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

