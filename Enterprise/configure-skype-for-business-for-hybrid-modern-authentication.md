---
title: Come configurare Skype for Business locale per utilizzare l'autenticazione moderna ibrida
ms.author: tracyp
author: MSFTTracyP
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
ms.openlocfilehash: a6f1b64aade9cd7c2fa5b44e18e1075008676f90
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067992"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="622d9-103">Come configurare Skype for Business locale per utilizzare l'autenticazione moderna ibrida</span><span class="sxs-lookup"><span data-stu-id="622d9-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="622d9-104">L'autenticazione moderna, è un metodo di gestione delle identità che offre un'autenticazione e un'autorizzazione utente più sicure, è disponibile per Skype for Business Server locale e Exchange Server locale, nonché per gli ibridi di Skype for business suddivisi in domini.</span><span class="sxs-lookup"><span data-stu-id="622d9-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="622d9-105">**Importante** Per ulteriori informazioni sull'autenticazione moderna (MA) e sul perché potrebbe essere preferibile utilizzarla nella propria azienda o nell'organizzazione?</span><span class="sxs-lookup"><span data-stu-id="622d9-105">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="622d9-106">Per una panoramica, vedere [questo documento](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="622d9-106">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="622d9-107">Se hai bisogno di sapere quali topologie Skype for business sono supportate con MA, questo è documentato qui!</span><span class="sxs-lookup"><span data-stu-id="622d9-107">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="622d9-108">**Prima di iniziare**, chiamo:</span><span class="sxs-lookup"><span data-stu-id="622d9-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="622d9-109">Autenticazione \> moderna ma</span><span class="sxs-lookup"><span data-stu-id="622d9-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="622d9-110">HMA di autenticazione \> moderna ibrida</span><span class="sxs-lookup"><span data-stu-id="622d9-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="622d9-111">Exch locale \> di Exchange</span><span class="sxs-lookup"><span data-stu-id="622d9-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="622d9-112">ESO di \> Exchange Online</span><span class="sxs-lookup"><span data-stu-id="622d9-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="622d9-113">Questo in locale \> di Skype for business</span><span class="sxs-lookup"><span data-stu-id="622d9-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="622d9-114">e Skype for business online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="622d9-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="622d9-115">Inoltre, \* se un elemento grafico di questo articolo contiene un oggetto che è "grigio" o "oscurato" che indica che il componente visualizzato in grigio **non è** incluso nella configurazione specifica di ma.</span><span class="sxs-lookup"><span data-stu-id="622d9-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="622d9-116">Leggere il riepilogo</span><span class="sxs-lookup"><span data-stu-id="622d9-116">Read the summary</span></span>

<span data-ttu-id="622d9-117">Questo riepilogo riduce il processo in passaggi che potrebbero altrimenti perdersi durante l'esecuzione ed è utile per una check-list generale per tenere conto del percorso in cui ci si trova.</span><span class="sxs-lookup"><span data-stu-id="622d9-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="622d9-118">Prima di tutto, assicurarsi di rispettare tutti i prerequisiti.</span><span class="sxs-lookup"><span data-stu-id="622d9-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="622d9-119">Poiché molti **prerequisiti** sono comuni sia per Skype for business che per Exchange, [vedere l'articolo introduttivo relativo all'elenco di controllo di prereq](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="622d9-119">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="622d9-120">Eseguire questa operazione *prima* di iniziare una delle procedure descritte in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="622d9-120">Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="622d9-121">Raccogliere le informazioni specifiche di HMA necessarie in un file o in OneNote.</span><span class="sxs-lookup"><span data-stu-id="622d9-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="622d9-122">Attiva l'autenticazione moderna per EXO (se non è già attivata).</span><span class="sxs-lookup"><span data-stu-id="622d9-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="622d9-123">Abilitare l'autenticazione moderna per SFBO (se non è già attivata).</span><span class="sxs-lookup"><span data-stu-id="622d9-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="622d9-124">Abilitare l'autenticazione moderna ibrida per Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="622d9-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="622d9-125">Attiva l'autenticazione moderna ibrida per Skype for business in locale.</span><span class="sxs-lookup"><span data-stu-id="622d9-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="622d9-126">Nota questi passaggi attivano MA per questo, SFBO, EXCH e EXO, ovvero tutti i prodotti che possono partecipare a una configurazione di HMA di questo e SFBO (incluse le dipendenze su EXCH/EXO).</span><span class="sxs-lookup"><span data-stu-id="622d9-126">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="622d9-127">In altre parole, se gli utenti sono ospitati in/dispongono di cassette postali create in qualsiasi parte dell'ambiente ibrido (EXO + SFBO, EXO + questo, EXCH + SFBO o EXCH + questo), il prodotto finale sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="622d9-127">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Una topologia di HMA di Skype for business mista ha un Master in tutte e quattro le posizioni possibili.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="622d9-129">Come si può notare, ci sono quattro luoghi diversi per accendere MA!</span><span class="sxs-lookup"><span data-stu-id="622d9-129">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="622d9-130">Per una migliore esperienza utente, si consiglia di abilitare MA in tutte e quattro le posizioni.</span><span class="sxs-lookup"><span data-stu-id="622d9-130">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="622d9-131">Se non è possibile abilitare MA in tutti questi percorsi, regolare i passaggi in modo che si accenda solo nelle posizioni che sono necessarie per l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="622d9-131">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="622d9-132">Per informazioni sulle topologie supportate, vedere l' [argomento relativo alla supportabilità per Skype for business con ma](https://technet.microsoft.com/en-us/library/mt803262.aspx) .</span><span class="sxs-lookup"><span data-stu-id="622d9-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="622d9-133">**Importante** Verificare che siano stati soddisfatti tutti i prerequisiti prima di iniziare.</span><span class="sxs-lookup"><span data-stu-id="622d9-133">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="622d9-134">Queste informazioni sono disponibili [qui](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="622d9-134">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="622d9-135">Raccogliere tutte le informazioni specifiche di HMA necessarie</span><span class="sxs-lookup"><span data-stu-id="622d9-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="622d9-136">Dopo aver verificato che vengano soddisfatti i [prerequisiti](hybrid-modern-auth-overview.md) per l'utilizzo dell'autenticazione moderna (vedere la nota precedente), è necessario creare un file per contenere le informazioni necessarie per la configurazione di HMA nei passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="622d9-136">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="622d9-137">Esempi utilizzati in questo articolo:</span><span class="sxs-lookup"><span data-stu-id="622d9-137">Examples used in this article:</span></span> 
  
- <span data-ttu-id="622d9-138">**Dominio SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="622d9-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="622d9-139">Ex.</span><span class="sxs-lookup"><span data-stu-id="622d9-139">Ex.</span></span> <span data-ttu-id="622d9-140">contoso.com (è federato con Office 365)</span><span class="sxs-lookup"><span data-stu-id="622d9-140">contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="622d9-141">**ID tenant**</span><span class="sxs-lookup"><span data-stu-id="622d9-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="622d9-142">GUID che rappresenta il tenant di Office 365 (nell'account di accesso di contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="622d9-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="622d9-143">**URL del servizio Web di questo 2015 CU5**</span><span class="sxs-lookup"><span data-stu-id="622d9-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="622d9-144">Sarà necessario l'URL del servizio Web interno ed esterno per tutti i pool di questo 2015 distribuiti.</span><span class="sxs-lookup"><span data-stu-id="622d9-144">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="622d9-145">Per ottenere queste operazioni, eseguire la seguente procedura da Skype for Business Management Shell:</span><span class="sxs-lookup"><span data-stu-id="622d9-145">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="622d9-146">Ex.</span><span class="sxs-lookup"><span data-stu-id="622d9-146">Ex.</span></span> <span data-ttu-id="622d9-147">Internohttps://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="622d9-147">Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="622d9-148">Ex.</span><span class="sxs-lookup"><span data-stu-id="622d9-148">Ex.</span></span> <span data-ttu-id="622d9-149">Esternohttps://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="622d9-149">External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="622d9-150">Se si utilizza un server Standard Edition, l'URL interno sarà vuoto.</span><span class="sxs-lookup"><span data-stu-id="622d9-150">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="622d9-151">In questo caso, utilizzare il nome di dominio completo del pool per l'URL interno.</span><span class="sxs-lookup"><span data-stu-id="622d9-151">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="622d9-152">Abilitare l'autenticazione moderna per EXO</span><span class="sxs-lookup"><span data-stu-id="622d9-152">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="622d9-153">Seguire le istruzioni riportate di seguito: [Exchange Online: informazioni su come abilitare il tenant per l'autenticazione moderna.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="622d9-153">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="622d9-154">Abilitare l'autenticazione moderna per SFBO</span><span class="sxs-lookup"><span data-stu-id="622d9-154">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="622d9-155">Seguire le istruzioni riportate di seguito: [Skype for business online: abilitare il tenant per l'autenticazione moderna](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="622d9-155">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="622d9-156">Abilitare l'autenticazione moderna ibrida per Exchange locale</span><span class="sxs-lookup"><span data-stu-id="622d9-156">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="622d9-157">Seguire le istruzioni riportate di seguito: informazioni [su come configurare Exchange Server locale per l'utilizzo dell'autenticazione moderna ibrida](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="622d9-157">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="622d9-158">Abilitare l'autenticazione moderna ibrida per Skype for business in locale</span><span class="sxs-lookup"><span data-stu-id="622d9-158">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="622d9-159">Aggiungere URL dei servizi Web locali come nomi SPN in Azure AD</span><span class="sxs-lookup"><span data-stu-id="622d9-159">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="622d9-160">A questo punto è necessario eseguire comandi per aggiungere gli URL (raccolti in precedenza) come entità di servizio in SFBO.</span><span class="sxs-lookup"><span data-stu-id="622d9-160">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="622d9-161">**Note** I nomi dell'entità servizio (SPN) identificano i servizi Web e li associano a un'entità di sicurezza, ad esempio un nome account o un gruppo, in modo che il servizio possa agire per conto di un utente autorizzato.</span><span class="sxs-lookup"><span data-stu-id="622d9-161">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="622d9-162">I client che eseguono l'autenticazione in un server utilizzano le informazioni contenute nei nomi SPN.</span><span class="sxs-lookup"><span data-stu-id="622d9-162">Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="622d9-163">Per prima cosa, connettersi a AAD con [queste istruzioni](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span><span class="sxs-lookup"><span data-stu-id="622d9-163">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>
    
2. <span data-ttu-id="622d9-164">Eseguire questo comando, in locale, per ottenere un elenco di URL del servizio Web di questo.</span><span class="sxs-lookup"><span data-stu-id="622d9-164">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="622d9-165">Si noti che AppPrincipalId inizia con `00000004`.</span><span class="sxs-lookup"><span data-stu-id="622d9-165">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="622d9-166">Corrisponde a Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="622d9-166">This corresponds to Skype for Business Online.</span></span>
    
   <span data-ttu-id="622d9-167">Prendere nota di (e screenshot per il confronto successivo) l'output di questo comando, che includerà un URL SE e WS, ma principalmente costituito da nomi SPN `00000004-0000-0ff1-ce00-000000000000/`che iniziano con.</span><span class="sxs-lookup"><span data-stu-id="622d9-167">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. <span data-ttu-id="622d9-168">Se gli URL di questo interni **o** esterni sono mancanti (ad esempio, https://lyncwebint01.contoso.com e https://lyncwebext01.contoso.com) sarà necessario aggiungere tali record specifici all'elenco.</span><span class="sxs-lookup"><span data-stu-id="622d9-168">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="622d9-169">Assicurarsi di sostituire *gli URL di esempio* , di seguito, con gli URL effettivi nei comandi Aggiungi!</span><span class="sxs-lookup"><span data-stu-id="622d9-169">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="622d9-170">Verificare che i nuovi record siano stati aggiunti eseguendo di nuovo il comando Get-MsolServicePrincipal viene del passaggio 2 e analizzando l'output.</span><span class="sxs-lookup"><span data-stu-id="622d9-170">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="622d9-171">Confrontare l'elenco/screenshot da prima al nuovo elenco di nomi SPN (è anche possibile schermare il nuovo elenco per i record).</span><span class="sxs-lookup"><span data-stu-id="622d9-171">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="622d9-172">In caso di esito positivo, verranno visualizzati i due nuovi URL presenti nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="622d9-172">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="622d9-173">In questo esempio, l'elenco dei nomi SPN includerà ora gli URL https://lyncweb01.contoso.com specifici e https://lyncwebext01.contoso.com/.</span><span class="sxs-lookup"><span data-stu-id="622d9-173">Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="622d9-174">Creare l'oggetto server auth EvoSTS</span><span class="sxs-lookup"><span data-stu-id="622d9-174">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="622d9-175">Eseguire il seguente comando in Skype for Business Management Shell.</span><span class="sxs-lookup"><span data-stu-id="622d9-175">Run the following command in the Skype for Business Management Shell.</span></span>
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="622d9-176">Abilitare l'autenticazione moderna ibrida</span><span class="sxs-lookup"><span data-stu-id="622d9-176">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="622d9-177">Questo è il passaggio che attiva effettivamente MA.</span><span class="sxs-lookup"><span data-stu-id="622d9-177">This is the step that actually turns MA on.</span></span> <span data-ttu-id="622d9-178">Tutti i passaggi precedenti possono essere eseguiti in anticipo senza modificare il flusso di autenticazione del client.</span><span class="sxs-lookup"><span data-stu-id="622d9-178">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="622d9-179">Quando si è pronti per modificare il flusso di autenticazione, eseguire questo comando in Skype for Business Management Shell.</span><span class="sxs-lookup"><span data-stu-id="622d9-179">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a><span data-ttu-id="622d9-180">Verificare</span><span class="sxs-lookup"><span data-stu-id="622d9-180">Verify</span></span>

<span data-ttu-id="622d9-181">Dopo aver abilitato HMA, l'account di accesso successivo di un client utilizzerà il nuovo flusso di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="622d9-181">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="622d9-182">Si noti che l'attivazione di HMA non attiverà una nuova autenticazione per un client.</span><span class="sxs-lookup"><span data-stu-id="622d9-182">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="622d9-183">I client eseguono di nuovo l'autenticazione in base alla durata dei token di autenticazione e/o ai cert che dispongono.</span><span class="sxs-lookup"><span data-stu-id="622d9-183">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="622d9-184">Per testare il funzionamento di HMA dopo averla abilitata, disconnettersi da un client di Windows questo di test e fare clic su' Elimina le credenziali '.</span><span class="sxs-lookup"><span data-stu-id="622d9-184">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="622d9-185">Accedere di nuovo.</span><span class="sxs-lookup"><span data-stu-id="622d9-185">Sign in again.</span></span> <span data-ttu-id="622d9-186">Il client dovrebbe ora usare il flusso di autenticazione moderna e ora il tuo account di accesso includerà un prompt di **Office 365** per un account ' work or School ', visto subito prima che il client contatti il server e ti registri.</span><span class="sxs-lookup"><span data-stu-id="622d9-186">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="622d9-187">È inoltre necessario controllare le ' informazioni di configurazione ' per i client Skype for business per un'autorità OAuth.</span><span class="sxs-lookup"><span data-stu-id="622d9-187">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="622d9-188">Per eseguire questa operazione nel computer client, tenere premuto il tasto CTRL contemporaneamente facendo clic con il pulsante destro del mouse sull'icona Skype for business nel vassoio di notifica di Windows.</span><span class="sxs-lookup"><span data-stu-id="622d9-188">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="622d9-189">Fare clic su informazioni di configurazione nel menu visualizzato.</span><span class="sxs-lookup"><span data-stu-id="622d9-189">Click Configuration Information in the menu that appears.</span></span> <span data-ttu-id="622d9-190">Nella finestra ' informazioni di configurazione di Skype for business ' che verrà visualizzata sul desktop, cercare gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="622d9-190">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Le informazioni di configurazione di un client Skype for business utilizzando l'autenticazione moderna mostrano un URL dell'autorità OAUTH di https://login.windows.net/common/oauth2/authorizeLync e EWS.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="622d9-192">È inoltre necessario tenere premuto il tasto CTRL contemporaneamente facendo clic con il pulsante destro del mouse sull'icona per il client di Outlook (anche nel vassoio notifiche di Windows) e facendo clic su' stato connessione '.</span><span class="sxs-lookup"><span data-stu-id="622d9-192">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="622d9-193">Cercare l'indirizzo SMTP del client rispetto a un tipo di "portatore\*", che rappresenta il token del portatore utilizzato in OAuth.</span><span class="sxs-lookup"><span data-stu-id="622d9-193">Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="622d9-194">Articoli correlati</span><span class="sxs-lookup"><span data-stu-id="622d9-194">Related articles</span></span>

<span data-ttu-id="622d9-195">[Collegare di nuovo la panoramica dell'autenticazione moderna](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="622d9-195">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="622d9-196">È necessario sapere come usare l'autenticazione moderna (ADAL) per i client Skype for business?</span><span class="sxs-lookup"><span data-stu-id="622d9-196">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="622d9-197">Sono disponibili passaggi. [](https://technet.microsoft.com/en-us/library/mt710548.aspx)</span><span class="sxs-lookup"><span data-stu-id="622d9-197">We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="622d9-198">Si desidera leggere questi passaggi come vengono visualizzati per Exchange Server, in locale, in esecuzione senza questo?</span><span class="sxs-lookup"><span data-stu-id="622d9-198">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB?</span></span> <span data-ttu-id="622d9-199">Tali passaggi sono disponibili qui.</span><span class="sxs-lookup"><span data-stu-id="622d9-199">Those steps are available here.</span></span>
  

