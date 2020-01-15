---
title: Come configurare Exchange Server locale per utilizzare l'autenticazione moderna ibrida
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: L'autenticazione moderna ibrida (HMA), è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure ed è disponibile per le distribuzioni ibride locali di Exchange Server.
ms.openlocfilehash: 1a8bed186acd8da9c5f223120c5e58e8bfd445b4
ms.sourcegitcommit: ef5447665d6ebbc79399b560c9725d74e1479f7d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "41122565"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="05361-103">Come configurare Exchange Server locale per utilizzare l'autenticazione moderna ibrida</span><span class="sxs-lookup"><span data-stu-id="05361-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="05361-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="05361-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="05361-105">L'autenticazione moderna ibrida (HMA), è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure ed è disponibile per le distribuzioni ibride locali di Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="05361-105">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="05361-106">FYI</span><span class="sxs-lookup"><span data-stu-id="05361-106">FYI</span></span>

<span data-ttu-id="05361-107">Prima di iniziare, chiamo:</span><span class="sxs-lookup"><span data-stu-id="05361-107">Before we begin, I call:</span></span>
  
- <span data-ttu-id="05361-108">HMA di autenticazione \> moderna ibrida</span><span class="sxs-lookup"><span data-stu-id="05361-108">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="05361-109">Exch locale \> di Exchange</span><span class="sxs-lookup"><span data-stu-id="05361-109">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="05361-110">ESO di \> Exchange Online</span><span class="sxs-lookup"><span data-stu-id="05361-110">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="05361-111">Inoltre, *se un elemento grafico di questo articolo contiene un oggetto che è' grigio ' o ' oscurato ' che indica che il componente visualizzato in grigio non è incluso nella configurazione specifica di HMA* .</span><span class="sxs-lookup"><span data-stu-id="05361-111">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="05361-112">Abilitazione dell'autenticazione moderna ibrida</span><span class="sxs-lookup"><span data-stu-id="05361-112">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="05361-113">Se si attiva HMA, significa:</span><span class="sxs-lookup"><span data-stu-id="05361-113">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="05361-114">Assicurarsi di conoscere le prerequisiti prima di iniziare.</span><span class="sxs-lookup"><span data-stu-id="05361-114">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="05361-115">Poiché molti **prerequisiti** sono comuni sia per Skype for business che per Exchange, [Panoramica dell'autenticazione moderna ibrida e prerequisiti per l'utilizzo con i server Skype for business e Exchange locali](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="05361-115">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="05361-116">Eseguire questa operazione prima di iniziare una delle procedure descritte in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="05361-116">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="05361-117">Aggiunta di URL di servizi Web locali come nomi dell'entità servizio (SPN, Service Principal Name) in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="05361-117">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="05361-118">Garantire che tutte le directory virtuali siano abilitate per HMA</span><span class="sxs-lookup"><span data-stu-id="05361-118">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="05361-119">Verifica dell'oggetto EvoSTS Auth server</span><span class="sxs-lookup"><span data-stu-id="05361-119">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="05361-120">Abilitazione di HMA in EXCH.</span><span class="sxs-lookup"><span data-stu-id="05361-120">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="05361-121">**Note** La versione di MA di supporto di Office?</span><span class="sxs-lookup"><span data-stu-id="05361-121">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="05361-122">Vedere [come funziona l'autenticazione moderna per le app client di office 2013 e office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="05361-122">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="05361-123">Assicurarsi di conoscere tutte le Rich</span><span class="sxs-lookup"><span data-stu-id="05361-123">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="05361-124">Poiché molti prerequisiti sono comuni sia per Skype for business che per Exchange, esaminare la [Panoramica dell'autenticazione moderna ibrida e i prerequisiti per l'utilizzo con i server Skype for business e Exchange locali](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="05361-124">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="05361-125">Eseguire questa operazione *prima* di iniziare una delle procedure descritte in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="05361-125">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="05361-126">Aggiungere URL dei servizi Web locali come nomi SPN in Azure AD</span><span class="sxs-lookup"><span data-stu-id="05361-126">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="05361-127">Eseguire i comandi che assegnano gli URL dei servizi Web locali come SPN AD Azure AD.</span><span class="sxs-lookup"><span data-stu-id="05361-127">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="05361-128">Gli SPN vengono utilizzati dai computer e dai dispositivi client durante l'autenticazione e l'autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="05361-128">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="05361-129">Tutti gli URL che possono essere utilizzati per la connessione da locale ad Azure Active Directory (AAD) devono essere registrati in AAD (inclusi gli spazi dei nomi interni ed esterni).</span><span class="sxs-lookup"><span data-stu-id="05361-129">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="05361-130">In primo luogo, raccogliere tutti gli URL che è necessario aggiungere in AAD.</span><span class="sxs-lookup"><span data-stu-id="05361-130">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="05361-131">Eseguire questi comandi in locale:</span><span class="sxs-lookup"><span data-stu-id="05361-131">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="05361-132">Verificare che i client URL a cui possono connettersi siano elencati come nomi dell'entità servizio HTTPS in AAD.</span><span class="sxs-lookup"><span data-stu-id="05361-132">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="05361-133">Per prima cosa, connettersi a AAD con [queste istruzioni](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="05361-133">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="05361-134">**Note** È necessario utilizzare l'opzione Connect-MsolService di questa pagina per poter utilizzare il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="05361-134">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="05361-135">Per gli URL correlati a Exchange, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="05361-135">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="05361-136">Prendere nota di (e screenshot per il confronto successivo) l'output di questo comando, che dovrebbe includere un URL di *mail.yourdomain.com* di https:// *autodiscover.yourdomain.com* e https://, ma principalmente costituito da nomi SPN che iniziano con 00000002-0000-0FF1-CE00-000000000000/.</span><span class="sxs-lookup"><span data-stu-id="05361-136">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="05361-137">Se sono presenti URL di https://da quelli locali mancanti, sarà necessario aggiungere tali record specifici a questo elenco.</span><span class="sxs-lookup"><span data-stu-id="05361-137">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="05361-138">Se non si visualizzano i record MAPI/HTTP, EWS, ActiveSync, OAB e autodiscover interni ed esterni in questo elenco, è necessario aggiungerli utilizzando il comando riportato di seguito (gli URL`mail.corp.contoso.com`di esempio sono`owa.contoso.com`'' è ', ma si **sostituiscono gli URL di esempio con il proprio** ):</span><span class="sxs-lookup"><span data-stu-id="05361-138">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="05361-139">Verificare che i nuovi record siano stati aggiunti eseguendo di nuovo il comando Get-MsolServicePrincipal viene del passaggio 2 e analizzando l'output.</span><span class="sxs-lookup"><span data-stu-id="05361-139">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="05361-140">Confrontare l'elenco/screenshot da prima al nuovo elenco di nomi SPN (è anche possibile schermare il nuovo elenco per i record).</span><span class="sxs-lookup"><span data-stu-id="05361-140">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="05361-141">In caso di esito positivo, verranno visualizzati i due nuovi URL presenti nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="05361-141">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="05361-142">In questo esempio, l'elenco dei nomi SPN includerà ora gli URL `https://mail.corp.contoso.com` specifici e `https://owa.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="05361-142">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="05361-143">Verificare che le directory virtuali siano configurate correttamente</span><span class="sxs-lookup"><span data-stu-id="05361-143">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="05361-144">A questo punto, verificare che OAuth sia abilitato correttamente in Exchange su tutte le directory virtuali che potrebbe essere utilizzato da Outlook eseguendo i seguenti comandi:</span><span class="sxs-lookup"><span data-stu-id="05361-144">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="05361-145">Controllare l'output per assicurarsi che **OAuth** sia abilitato su ognuna di queste VDirs, avrà un aspetto simile a questo (e la cosa fondamentale da guardare è "OAuth");</span><span class="sxs-lookup"><span data-stu-id="05361-145">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="05361-146">Se OAuth non è presente in un server e in una delle quattro directory virtuali, è necessario aggiungerlo usando i comandi rilevanti prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="05361-146">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="05361-147">Confermare che l'oggetto server EvoSTS auth sia presente</span><span class="sxs-lookup"><span data-stu-id="05361-147">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="05361-148">Tornare alla shell di gestione di Exchange locale per questo ultimo comando.</span><span class="sxs-lookup"><span data-stu-id="05361-148">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="05361-149">A questo punto è possibile verificare che il provider di autenticazione di evoSTS sia presente in locale:</span><span class="sxs-lookup"><span data-stu-id="05361-149">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="05361-150">L'output deve mostrare un AuthServer del nome EvoSts e lo stato ' Enabled ' dovrebbe essere vero.</span><span class="sxs-lookup"><span data-stu-id="05361-150">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="05361-151">Se questa operazione non viene visualizzata, è consigliabile scaricare ed eseguire la versione più recente della procedura guidata di configurazione ibrida.</span><span class="sxs-lookup"><span data-stu-id="05361-151">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="05361-152">**Importante** Se si esegue Exchange 2010 nell'ambiente in uso, il provider di autenticazione di EvoSTS non verrà creato.</span><span class="sxs-lookup"><span data-stu-id="05361-152">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="05361-153">Abilitare HMA</span><span class="sxs-lookup"><span data-stu-id="05361-153">Enable HMA</span></span>

<span data-ttu-id="05361-154">Eseguire il seguente comando in Exchange Management Shell, in locale:</span><span class="sxs-lookup"><span data-stu-id="05361-154">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="05361-155">Verificare</span><span class="sxs-lookup"><span data-stu-id="05361-155">Verify</span></span>

<span data-ttu-id="05361-156">Dopo aver abilitato HMA, l'account di accesso successivo di un client utilizzerà il nuovo flusso di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="05361-156">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="05361-157">Si noti che l'attivazione di HMA non attiverà una nuova autenticazione per un client.</span><span class="sxs-lookup"><span data-stu-id="05361-157">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="05361-158">I client eseguono di nuovo l'autenticazione in base alla durata dei token di autenticazione e/o ai cert che dispongono.</span><span class="sxs-lookup"><span data-stu-id="05361-158">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="05361-159">È inoltre necessario tenere premuto il tasto CTRL contemporaneamente facendo clic con il pulsante destro del mouse sull'icona per il client di Outlook (anche nel vassoio notifiche di Windows) e facendo clic su' stato connessione '.</span><span class="sxs-lookup"><span data-stu-id="05361-159">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="05361-160">Cercare l'indirizzo SMTP del client rispetto a un tipo ' AuthN ' di ' latore\*', che rappresenta il token del portatore utilizzato in OAuth.</span><span class="sxs-lookup"><span data-stu-id="05361-160">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="05361-161">**Note** È necessario configurare Skype for business con HMA?</span><span class="sxs-lookup"><span data-stu-id="05361-161">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="05361-162">Sono necessari due articoli: uno che elenca le [topologie supportate](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)e uno che illustra [come eseguire la configurazione](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="05361-162">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
 
## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a><span data-ttu-id="05361-163">Utilizzo dell'autenticazione moderna ibrida con Outlook per iOS e Android</span><span class="sxs-lookup"><span data-stu-id="05361-163">Using hybrid Modern Authentication with Outlook for iOS and Android</span></span>

<span data-ttu-id="05361-164">Se si è un cliente locale che utilizza Exchange Server su TCP 443, è necessario selezionare gli intervalli IP seguenti: </span><span class="sxs-lookup"><span data-stu-id="05361-164">If you are an on-premises customer using Exchange server on TCP 443, please whitelist the following IP ranges:  </span></span><BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> 
  

## <a name="related-topics"></a><span data-ttu-id="05361-165">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="05361-165">Related topics</span></span>

[<span data-ttu-id="05361-166">Panoramica dell'autenticazione moderna ibrida e prerequisiti per l'utilizzo con i server Skype for business e Exchange locali</span><span class="sxs-lookup"><span data-stu-id="05361-166">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  
<span data-ttu-id="05361-167">Forzare gli utenti di Outlook all'autenticazione moderna</span><span class="sxs-lookup"><span data-stu-id="05361-167">Force Outlook users to Modern Authentication</span></span>  
[<span data-ttu-id="05361-168">Requisiti di configurazione dell'autenticazione moderna per la transizione da Office 365 dedicato/ITAR a vNext</span><span class="sxs-lookup"><span data-stu-id="05361-168">Modern Authentication configuration requirements for transition from Office 365 dedicated/ITAR to vNext</span></span>](modern-authentication-configuration.md)
