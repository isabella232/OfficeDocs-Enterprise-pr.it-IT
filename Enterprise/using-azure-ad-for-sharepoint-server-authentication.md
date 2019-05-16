---
title: Utilizzare Azure AD per l'autenticazione di SharePoint Server
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: "Riepilogo: informazioni su come ignorare il servizio di controllo di accesso di Azure e l'utilizzo di SAML 1,1 per l'autenticazione degli utenti di SharePoint Server con Azure Active Directory."
ms.openlocfilehash: c2c9f33aa5e095a8b7fdde08e80cb1a61e88f3eb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070792"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Utilizzare Azure AD per l'autenticazione di SharePoint Server

 **Riepilogo:** Informazioni su come eseguire l'autenticazione degli utenti di SharePoint Server 2016 con Azure Active Directory. 

<blockquote>
<p>In questo articolo vengono riferiti esempi di codice per interagire con Azure Active Directory Graph. È possibile scaricare gli esempi di codice [qui](https://github.com/kaevans/spsaml11/tree/master/scripts).</p>
</blockquote>

SharePoint Server 2016 offre la possibilità di autenticare gli utenti utilizzando l'autenticazione basata sulle attestazioni, semplificando la gestione degli utenti mediante l'autenticazione con provider di identità diversi, attendibili, ma gestiti da un altro utente. Ad esempio, invece di gestire l'autenticazione degli utenti tramite servizi di dominio Active Directory, è possibile consentire agli utenti di eseguire l'autenticazione tramite Azure Active Directory (Azure AD). Questo consente di abilitare l'autenticazione per gli utenti solo cloud con il suffisso onmicrosoft.com nel nome utente, gli utenti sincronizzati con una directory locale e gli utenti Guest invitati da altre directory. Consente inoltre di usufruire delle funzionalità di Azure AD, come l'autenticazione a più fattori e le funzionalità di creazione di report avanzate.

> [!IMPORTANT]
> La soluzione descritta in questo articolo può essere utilizzata anche con SharePoint Server 2013; Tuttavia, tenere presente che SharePoint Server 2013 si sta avvicinando alla fine del supporto mainstream. Per ulteriori informazioni, vedere [criteri di ciclo](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) di vita di Microsoft e [criteri di manutenzione del prodotto aggiornati per SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).

In questo articolo viene illustrato come utilizzare Azure AD anziché il servizio di dominio Active Directory locale per l'autenticazione degli utenti. In questa configurazione, Azure AD diventa un provider di identità attendibile per SharePoint Server 2016. Questa configurazione aggiunge un metodo di autenticazione utente separato dall'autenticazione di servizi di dominio Active Directory utilizzata dall'installazione di SharePoint Server 2016. Per usufruire di questo articolo, è consigliabile avere familiarità con WS-Federation. Per ulteriori informazioni, vedere [understandING WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052). Per informazioni dettagliate sull'integrazione di SharePoint locale con Azure Active Directory, vedere l' [esercitazione dedicata](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial).

![Utilizzo di Azure AD per l'autenticazione di SharePoint](media/SAML11/fig1-architecture.png)

In precedenza, questa configurazione avrebbe richiesto un servizio federativo, ad esempio il servizio di controllo di accesso di Azure (ACS) nel cloud o un ambiente che ospita Active Directory Federation Services (AD FS) per trasformare i token da SAML 2,0 a SAML 1,1. Questa trasformazione non è più necessaria come Azure AD ora Abilita l'emissione di token SAML 1,1. Nel diagramma precedente viene illustrato il funzionamento dell'autenticazione per gli utenti di SharePoint 2016 in questa configurazione, in cui viene dimostrato che non è più necessario che un intermediario esegua questa trasformazione.

> [!NOTE]
> Questa configurazione funziona se la farm di SharePoint è ospitata in macchine virtuali di Azure o in locale. Non è necessario aprire ulteriori porte del firewall diverse da garantire che gli utenti possano accedere a Azure Active Directory dal browser.

Per informazioni sull'accessibilità di SharePoint 2016, vedere [linee guida per l'accessibilità in SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Panoramica della configurazione

Seguire questi passaggi generali per configurare l'ambiente per l'utilizzo di Azure AD come provider di identità di SharePoint Server 2016.

1. Creare una nuova directory di Azure AD o utilizzare la directory esistente.
2. Verificare che l'area per l'applicazione Web che si desidera proteggere con Azure AD sia configurata per l'utilizzo di SSL.
3. Creare una nuova applicazione Enterprise in Azure AD.
4. Configurare un nuovo provider di identità attendibile in SharePoint Server 2016.
5. Impostare le autorizzazioni per l'applicazione Web.
6. Aggiungere un criterio di emissione di token SAML 1,1 in Azure AD.
7. Verificare il nuovo provider.

Nelle sezioni seguenti viene descritto come eseguire queste attività.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Passaggio 1: creare una nuova directory di Azure AD o utilizzare la directory esistente

Nel portale di Azure ([https://portal.azure.com](https://portal.azure.com)), creare una nuova directory. Specificare il nome dell'organizzazione, il nome di dominio iniziale e il paese o l'area geografica.

![Creazione di una directory](media/SAML11/fig2-createdirectory.png) 

 Se si dispone già di una directory come quella utilizzata per Microsoft Office 365 o la sottoscrizione di Microsoft Azure, è possibile utilizzare tale directory. È necessario disporre delle autorizzazioni per registrare le applicazioni nella directory.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Passaggio 2: verificare che l'area per l'applicazione Web che si desidera proteggere con Azure AD sia configurata per l'utilizzo di SSL

Questo articolo è stato scritto utilizzando l'architettura di riferimento in [eseguire una farm di SharePoint Server 2016 a disponibilità elevata in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). Gli script di accompagnamento dell'articolo utilizzati per distribuire la soluzione descritta in [questo articolo](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) consentono di creare un sito che non utilizza SSL.  

L'utilizzo di SAML richiede che l'applicazione sia configurata per l'utilizzo di SSL. Se l'applicazione Web di SharePoint non è configurata per l'utilizzo di SSL, eseguire la procedura seguente per creare un nuovo certificato autofirmato per configurare l'applicazione Web per SSL. Questa configurazione è destinata solo a un ambiente lab e non è destinata alla produzione. Gli ambienti di produzione devono utilizzare un certificato firmato.

1. Accedere a**gestione** > **** applicazioni di **Amministrazione** > centrale e selezionare l'applicazione Web che deve essere estesa per l'utilizzo di SSL. Selezionare l'applicazione Web e fare clic sul pulsante **Estendi barra multifunzione** . Estendere l'applicazione Web in modo da utilizzare lo stesso URL, ma utilizzare SSL con la porta 443.<br/>![Estensione dell'applicazione Web a un altro sito IIS](media/SAML11/fig3-extendwebapptoiis.png)<br/>
2. In Gestione IIS, fare doppio clic su **certificati server**.
3. Nel riquadro **Azioni** fare clic su **Crea certificato autofirmato**. Digitare un nome descrittivo per il certificato nella casella specificare un nome descrittivo per il certificato e quindi fare clic su **OK**.
4. Nella finestra di dialogo **Modifica binding sito** verificare che il nome host corrisponda al nome descrittivo, come illustrato nell'immagine seguente.<br/>![Modifica del binding dei siti in IIS](media/SAML11/fig4-editsitebinding.png)<br/>

Ogni server front-end Web nella farm di SharePoint richiede la configurazione del certificato per l'associazione di sito in IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Passaggio 3: creare una nuova applicazione Enterprise in Azure AD

1. Nel portale di Azure ([https://portal.azure.com](https://portal.azure.com)), aprire la directory di Azure ad. Fare clic su **applicazioni Enterprise**e quindi su **nuova applicazione**. Scegliere **un'applicazione non di raccolta**. Specificare un nome, ad esempio l' *integrazione SAML di SharePoint* e fare clic su **Aggiungi**.<br/>![Aggiunta di una nuova applicazione non di raccolta](media/SAML11/fig5-addnongalleryapp.png)<br/>
2. Fare clic sul collegamento Single Sign-on nel riquadro di spostamento per configurare l'applicazione. Modificare l'elenco a discesa **modalità Single Sign-on** nell' **accesso basato su SAML** per visualizzare le proprietà di configurazione SAML per l'applicazione. Configurare le proprietà seguenti:<br/>
    - Identificatore`urn:sharepoint:portal.contoso.local`
    - URL di risposta:`https://portal.contoso.local/_trust/default.aspx`
    - URL di accesso:`https://portal.contoso.local/_trust/default.aspx`
    - Identificatore utente:`user.userprincipalname`<br/>
    - Nota: ricordarsi di modificare gli URL sostituendo *Portal. contoso. local* con l'URL del sito di SharePoint che si desidera proteggere.<br/>
3. Impostare una tabella (simile alla tabella 1 seguente) che includa le righe seguenti:<br/> 
    - Realm
    - Percorso completo del file del certificato per la firma SAML
    - URL del servizio Single Sign-On SAML (sostituzione di */Saml2* con */WSFED*)
    - ID oggetto applicazione. <br/>
Copiare il valore dell' *identificatore* nella proprietà *Realm* in una tabella (vedere la tabella 1 seguente).
4. Salvare le modifiche.
5. Fare clic sul collegamento **Configura (nome app)** per accedere alla pagina Configure Sign-on.<br/>![Configurazione di una pagina Single-Sign on](media/SAML11/fig7-configssopage.png)<br/> 
    -  Fare clic sul collegamento **certificato-RAW per la firma SAML** per scaricare il certificato per la firma SAML come file con estensione cer. Copiare e incollare il percorso completo del file scaricato nella tabella.
    - Copiare e incollare il collegamento URL del servizio Single Sign-On SAML nel proprio, sostituendo la parte */Saml2* dell'URL con */WSFED*.<br/>
6.  Passare al riquadro delle **Proprietà** dell'applicazione. Copiare e incollare il valore dell'ID oggetto nella tabella configurata nel passaggio 3.<br/>![Riquadro delle proprietà per l'applicazione](media/SAML11/fig8-propertiespane.png)<br/>
7. Utilizzando i valori acquisiti, verificare che la tabella configurata nel passaggio 3 sia simile alla tabella 1 seguente.


| Tabella 1: valori acquisiti  |  |
|---------|---------|
|Realm | `urn:sharepoint:portal.contoso.local` |
|Percorso completo del file del certificato per la firma SAML | `C:/temp/SharePoint SAML Integration.cer`  |
|URL del servizio Single Sign-On SAML (Sostituisci/Saml2 con/WSFED) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|ID oggetto applicazione | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Sostituire il valore */Saml2* nell'URL con */WSFED*. L'endpoint */Saml2* ELABORERÀ token SAML 2,0. L'endpoint */WSFED* consente di elaborare i token SAML 1,1 ed è necessario per la Federazione di SAML di SharePoint 2016.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Passaggio 4: configurare un nuovo provider di identità attendibile in SharePoint Server 2016

Accedere al server SharePoint Server 2016 e aprire SharePoint 2016 Management Shell. Inserire i valori di $realm, $wsfedurl e $filepath dalla tabella 1 ed eseguire i comandi seguenti per configurare un nuovo provider di identità attendibile.

> [!TIP]
> Se si è nuovi nell'utilizzo di PowerShell o si desiderano ulteriori informazioni sul funzionamento di PowerShell, vedere [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

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
1. In Amministrazione centrale, passare a **Gestione applicazione Web** e selezionare l'applicazione Web che si desidera proteggere con Azure ad. 
2. Sulla barra multifunzione fare clic su **provider di autenticazione** e scegliere l'area che si desidera utilizzare.
3. Selezionare **provider di identità attendibile** e selezionare il provider di identificazione appena registrato denominato *AzureAD*.  
4. Nell'impostazione relativa all'URL della pagina di accesso, selezionare **pagina di accesso personalizzata** e specificare il valore "/_trust/". 
5. Fare clic su **OK**.

![Configurazione del provider di autenticazione](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> È importante seguire tutti i passaggi, inclusa l'impostazione della pagina di accesso personalizzata su "/_trust/" come illustrato. La configurazione non funzionerà correttamente, a meno che non vengano seguiti tutti i passaggi.

## <a name="step-5-set-the-permissions"></a>Passaggio 5: impostare le autorizzazioni

Gli utenti che accedono ad Azure AD e Access SharePoint devono essere autorizzati a accedere all'applicazione. 

1. Nel portale di Azure, aprire la directory di Azure AD. Fare clic su **applicazioni Enterprise**e quindi su **tutte le applicazioni**. Fare clic sull'applicazione creata in precedenza (integrazione SAML di SharePoint).
2. Fare clic su **utenti e gruppi**. 
3. Fare clic su **Aggiungi utente** per aggiungere un utente o un gruppo che disponga delle autorizzazioni per accedere a SharePoint con Azure ad.
4. Selezionare l'utente o il gruppo, quindi fare clic su **assegna**.
 
All'utente è stata concessa l'autorizzazione in Azure Active Directory, ma deve anche essere concessa l'autorizzazione in SharePoint. Per impostare le autorizzazioni per l'accesso all'applicazione Web, attenersi alla procedura seguente.

1. In Amministrazione centrale fare clic su **Gestione applicazioni**.
2. Nella sezione **Applicazioni Web** della pagina **Gestione applicazioni** fare clic su **Gestisci applicazioni Web**.
3. Fare clic sull'applicazione Web appropriata e quindi su **Criteri utenti**.
4. In criteri per l'applicazione Web fare clic su **Aggiungi utenti**.<br/>![Ricerca di un utente in base all'attestazione del nome](media/SAML11/fig11-searchbynameclaim.png)<br/>
5. Nella finestra di dialogo **Aggiunta utenti** fare clic sull'area appropriata in **Aree** e quindi fare clic su **Avanti**.
6. Nella sezione **Selezione utenti** della finestra di dialogo **criteri per l'applicazione Web** fare clic sull'icona **Sfoglia** .
7. Nella casella di testo **trova** , digitare il nome di accesso per un utente nella directory e fare clic su **Cerca**. <br/>Esempio: *demouser@blueskyabove.onmicrosoft.com*.
8. Sotto l'intestazione AzureAD nella visualizzazione elenco, selezionare la proprietà nome e fare clic su **Aggiungi** , quindi fare clic su **OK** per chiudere la finestra di dialogo.
9. In autorizzazioni fare clic su **controllo completo**.<br/>![Concessione del controllo completo a un utente delle attestazioni](media/SAML11/fig12-grantfullcontrol.png)<br/>
10. Fare clic su **Fine** e quindi su **OK**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Passaggio 6: aggiungere un criterio di emissione di token SAML 1,1 in Azure AD

Quando si crea l'applicazione Azure AD nel portale, viene utilizzato il valore SAML 2,0. SharePoint Server 2016 richiede il formato token SAML 1,1. Lo script seguente consente di rimuovere il criterio SAML 2,0 predefinito e di aggiungere un nuovo criterio per l'emissione di token SAML 1,1. 

> Questo codice richiede il download degli esempi di accompagnamento che illustrano l' [interazione con Azure Active Directory Graph](https://github.com/kaevans/spsaml11/tree/master/scripts). Se si scaricano gli script come file ZIP da GitHub a un desktop di Windows, accertarsi di sbloccare il `MSGraphTokenLifetimePolicy.psm1` file del modulo di script e `Initialize.ps1` il file di script (fare clic con il pulsante destro del mouse su proprietà, scegliere Sblocca, fare clic su OK). 
![Sblocco dei file scaricati](media/SAML11/fig17-unblock.png)

Dopo aver scaricato lo script di esempio, creare un nuovo script PowerShell utilizzando il codice seguente, sostituendo il segnaposto con il percorso del `Initialize.ps1` file scaricato nel computer locale. Sostituire il segnaposto ID oggetto applicazione con l'ID oggetto applicazione immesso nella tabella 1. Una volta creato, eseguire lo script di PowerShell. 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> Gli script di PowerShell non sono firmati e potrebbe essere richiesto di impostare il criterio di esecuzione. Per ulteriori informazioni sui criteri di esecuzione, vedere [informazioni sui criteri di esecuzione](http://go.microsoft.com/fwlink/?LinkID=135170). Inoltre, potrebbe essere necessario aprire un prompt dei comandi con privilegi elevati per eseguire correttamente i controlli contenuti negli script di esempio.

Questo esempio di comandi di PowerShell è un esempio di come eseguire query sull'API del grafico. Per ulteriori informazioni sui criteri di rilascio dei token con Azure AD, vedere la Guida [di riferimento all'API del grafico per le operazioni sui criteri](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).

## <a name="step-7-verify-the-new-provider"></a>Passaggio 7: verificare il nuovo provider

Aprire un browser all'URL dell'applicazione Web configurata nei passaggi precedenti. Si viene reindirizzati per accedere ad Azure AD.

![Accesso a Azure AD configurata per la Federazione](media/SAML11/fig13-examplesignin.png)

Viene richiesto se si desidera rimanere connessi.

![Rimanere connesso?](media/SAML11/fig14-staysignedin.png)

Infine, è possibile accedere al sito connesso come utente dal tenant di Azure Active Directory.

![Utente che ha eseguito l'accesso a SharePoint](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>Gestione dei certificati
È importante comprendere che il certificato di firma configurato per il provider di identità attendibile nel passaggio 4 ha una data di scadenza e deve essere rinnovato. Vedere l'articolo [Manage Certificates for Federated Single Sign-on in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) per informazioni sul rinnovo del certificato. Una volta che il certificato è stato rinnovato in Azure AD, scaricare in un file locale e utilizzare lo script seguente per configurare il provider di identità attendibile con il certificato per la firma rinnovata. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>Configurazione di un provider di identità attendibile per più applicazioni Web
La configurazione funziona per una singola applicazione Web, ma richiede una configurazione aggiuntiva se si intende utilizzare lo stesso provider di identità attendibile per più applicazioni Web. Si supponga, ad esempio, di aver esteso un'applicazione Web per l' `https://portal.contoso.local` utilizzo dell'URL e di eseguire l'autenticazione anche `https://sales.contoso.local` da parte degli utenti. A tale scopo, è necessario aggiornare il provider di identità per onorare il parametro WReply e aggiornare la registrazione dell'applicazione in Azure ad per aggiungere un URL di risposta.

1. Nel portale di Azure, aprire la directory di Azure AD. Fare clic su **registrazioni app**e quindi su **Visualizza tutte le applicazioni**. Fare clic sull'applicazione creata in precedenza (integrazione SAML di SharePoint).
2. Fare clic su **Impostazioni**.
3. Nel pannello impostazioni, fare clic su **URL di risposta**. 
4. Aggiungere l'URL dell'applicazione `/_trust/default.aspx` Web aggiuntiva all'URL, ad esempio `https://sales.contoso.local/_trust/default.aspx`, e fare clic su **Salva**. 
5. In SharePoint Server, aprire **sharepoint 2016 Management Shell** ed eseguire i comandi seguenti, utilizzando il nome dell'autorità emittente di token di identità attendibile utilizzata in precedenza.

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. In Amministrazione centrale accedere all'applicazione Web e abilitare il provider di identità attendibile esistente. Ricordarsi di configurare anche l'URL della pagina di accesso come pagina `/_trust/`di accesso personalizzata.
7. In Amministrazione centrale fare clic sull'applicazione Web e scegliere **criteri utente**. Aggiungere un utente con le autorizzazioni appropriate, come illustrato in precedenza in questo articolo.

## <a name="fixing-people-picker"></a>Correzione di selezione utenti
Gli utenti possono ora accedere a SharePoint 2016 utilizzando le identità da Azure AD, ma è comunque possibile migliorare l'esperienza dell'utente. Ad esempio, la ricerca di un utente presenta più risultati di ricerca nello strumento di selezione utenti. È presente un risultato di ricerca per ognuno dei 3 tipi di attestazioni creati nel mapping di attestazioni. Per scegliere un utente tramite selezione utenti, è necessario digitare il proprio nome utente e scegliere il risultato dell'attestazione del **nome** .

![Risultati della ricerca delle attestazioni](media/SAML11/fig16-claimssearchresults.png)

Non vi sono convalide sui valori cercati, che possono causare errori ortografici o gli utenti che scelgono accidentalmente il tipo di attestazione errata **** da assegnare, ad esempio l'attestazione cognome. Ciò può impedire agli utenti di accedere correttamente alle risorse.

Per facilitare questo scenario, è disponibile una soluzione open source denominata [AzureCP](https://yvand.github.io/AzureCP/) che fornisce un provider di attestazioni personalizzato per SharePoint 2016. Utilizzerà il grafico di Azure AD per risolvere gli elementi che gli utenti immettono ed eseguono la convalida. Per ulteriori informazioni, vedere [AzureCP](https://yvand.github.io/AzureCP/). 

## <a name="additional-resources"></a>Risorse aggiuntive

[Informazioni su WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>Partecipare alla discussione

|**Contattaci**|**Descrizione**|
|:-----|:-----|
|**Ottenere la soluzione necessaria** <br/> |Microsoft sta creando documenti contenenti soluzioni che fanno riferimento a numerosi prodotti e servizi. Fornire commenti e suggerimenti sulle soluzioni tra server proposte o richiedere una soluzione specifica inviando un'e-mail all'indirizzo [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Partecipare alla discussione sulle soluzioni** <br/> |Se si è appassionati di soluzioni basate sul cloud, prendere in considerazione l'idea di accedere al Cloud Adoption Advisory Board (CAAB) per connettersi con una community più ampia e vivace di sviluppatori di contenuti Microsoft, professionisti del settore e clienti di tutto il mondo. Per accedervi, diventare un membro dell'[area CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) della Community tecnica Microsoft e inviare una breve e-mail all'indirizzo [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Chiunque può leggere i contenuti correlati alla community nel [blog di CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Tuttavia, i membri CAAB ricevono inviti a webinar privati che descrivono le nuove soluzioni e risorse relative all'adozione del cloud.  <br/> |
|**Ottenere l'immagine visualizzata** <br/> |Se si desidera una copia modificabile dell'immagine visualizzata in questo articolo, Microsoft si occuperà di inviarla. Inviare la propria richiesta tramite e-mail, includendo l'URL e il titolo dell'immagine, all'indirizzo [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

