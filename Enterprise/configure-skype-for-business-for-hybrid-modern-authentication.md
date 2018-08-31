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
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="15fdf-103">Come configurare Skype for Business locale per utilizzare l'autenticazione moderna ibrida</span><span class="sxs-lookup"><span data-stu-id="15fdf-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="15fdf-104">L'autenticazione moderno è un metodo di gestione delle identità che offre maggiore protezione utente autenticazione e autorizzazione, è disponibile per Skype per Business server locali e di Exchange server in locale, nonché Skype dominio diviso per ibridi Business.</span><span class="sxs-lookup"><span data-stu-id="15fdf-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="15fdf-p101">**Importante** Se si desidera fornire ulteriori informazioni di autenticazione (gestione moderno) e sui motivi per cui potrebbe essere preferibile utilizzare della società o dell'organizzazione? [In questo documento](hybrid-modern-auth-overview.md) per una panoramica di controllo. Se è necessario sapere quali Skype per con MA che descritte di seguito sono supportate le topologie Business!</span><span class="sxs-lookup"><span data-stu-id="15fdf-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="15fdf-108">**Prima di iniziare**, è possibile chiamare il metodo:</span><span class="sxs-lookup"><span data-stu-id="15fdf-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="15fdf-109">Autenticazione moderno \> agente di gestione</span><span class="sxs-lookup"><span data-stu-id="15fdf-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="15fdf-110">Autenticazione moderno ibrida \> alta</span><span class="sxs-lookup"><span data-stu-id="15fdf-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="15fdf-111">Exchange locale \> EXCH</span><span class="sxs-lookup"><span data-stu-id="15fdf-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="15fdf-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="15fdf-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="15fdf-113">Skype aziendali locali \> SFB</span><span class="sxs-lookup"><span data-stu-id="15fdf-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="15fdf-114">Skype per le aziende Online e \> SFBO</span><span class="sxs-lookup"><span data-stu-id="15fdf-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="15fdf-115">Inoltre, \* se un'immagine in questo articolo include un oggetto che è "inattivo" o "disattivato" che si intende l'elemento visualizzato in grigio **non è** incluso nella configurazione di gestione specifiche.</span><span class="sxs-lookup"><span data-stu-id="15fdf-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="15fdf-116">Leggere le informazioni di riepilogo</span><span class="sxs-lookup"><span data-stu-id="15fdf-116">Read the summary</span></span>

<span data-ttu-id="15fdf-117">In questo riepilogo include il processo di passi che potrebbero invece vanno persi durante l'esecuzione ed è utile per un elenco di controllo generale tenere traccia di cui è in corso il processo.</span><span class="sxs-lookup"><span data-stu-id="15fdf-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="15fdf-118">Per prima cosa, verificare che siano soddisfatti tutti i prerequisiti.</span><span class="sxs-lookup"><span data-stu-id="15fdf-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="15fdf-p102">Rispetto a molti **Prerequisiti** sono comuni per entrambi Skype per le aziende ed Exchange, [vedere l'articolo di panoramica per l'elenco di controllo pre-req](hybrid-modern-auth-overview.md). Questo *prima di* iniziare le procedure descritte in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="15fdf-121">Raccogliere le informazioni di alta specifici che necessari in un file o OneNote.</span><span class="sxs-lookup"><span data-stu-id="15fdf-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="15fdf-122">Attivare via moderno Authentication for EXO (se non già attivata).</span><span class="sxs-lookup"><span data-stu-id="15fdf-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="15fdf-123">Attivare via moderno Authentication for SFBO (se non già attivata).</span><span class="sxs-lookup"><span data-stu-id="15fdf-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="15fdf-124">Attivare l'autenticazione moderno ibrida di Exchange in locale.</span><span class="sxs-lookup"><span data-stu-id="15fdf-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="15fdf-125">Attivare l'autenticazione moderno ibrida per Skype aziendali locali.</span><span class="sxs-lookup"><span data-stu-id="15fdf-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="15fdf-p103">Si noti che la procedura seguente attiva agente di gestione per SFB, SFBO, EXCH ed EXO -, ovvero tutti i prodotti che possono partecipare a una configurazione di memoria alta di SFB e SFBO (inclusi dipendenze EXCH/EXO). In altre parole, se gli utenti sono ospitati nel / create cassette postali in qualsiasi parte dell'ambiente ibrido (EXO + SFBO, EXO + SFB, EXCH + SFBO, o EXCH + SFB), il prodotto completato sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="15fdf-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Una combinazione Skype 6 per la topologia di alta business presenta agente di gestione tutti i percorsi possibili quattro.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="15fdf-p104">Come si può notare sono disponibili quattro diverse posizioni per attivare la gestione! Per un'esperienza utente ottimale è consigliabile che attivare agente di gestione in tutte e quattro queste posizioni. Se Impossibile attivare l'agente di gestione in tutti i percorsi, regolare i passaggi descritti in modo che si accende solo nelle posizioni necessari per l'ambiente di gestione.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="15fdf-132">Vedere l' [argomento di supporto per Skype for Business con agente di gestione](https://technet.microsoft.com/en-us/library/mt803262.aspx) per le topologie supportate.</span><span class="sxs-lookup"><span data-stu-id="15fdf-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="15fdf-p105">**Importante** Verificare che vengano soddisfatti tutti i prerequisiti prima di iniziare. Sono disponibili informazioni [di seguito](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="15fdf-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="15fdf-135">Raccolta di tutte le informazioni di alta specifici che necessari</span><span class="sxs-lookup"><span data-stu-id="15fdf-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="15fdf-p106">Dopo aver ricontrollato che siano soddisfatti i [Prerequisiti](hybrid-modern-auth-overview.md) per utilizzare l'autenticazione moderno (vedere sopra), è consigliabile creare un file per conservare le informazioni necessarie per la configurazione alta in anticipo i passaggi. Esempi utilizzati in questo articolo:</span><span class="sxs-lookup"><span data-stu-id="15fdf-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="15fdf-138">**Dominio SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="15fdf-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="15fdf-p107">Ad esempio contoso.com (federata con Office 365)</span><span class="sxs-lookup"><span data-stu-id="15fdf-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="15fdf-141">**ID tenant**</span><span class="sxs-lookup"><span data-stu-id="15fdf-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="15fdf-142">GUID che rappresenta il tenant di Office 365 (al momento dell'accesso di contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="15fdf-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="15fdf-143">**URL del servizio Web CU5 SFB 2015**</span><span class="sxs-lookup"><span data-stu-id="15fdf-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="15fdf-p108">È necessario dell'URL del servizio web interne ed esterne per tutti i pool SfB 2015 distribuiti. Per ottenere tali, eseguire le operazioni seguenti da Skype per Business Management Shell:</span><span class="sxs-lookup"><span data-stu-id="15fdf-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="15fdf-146">Get-CsService - WebServer | PoolFqdn Select-Object, InternalFqdn, Fqdnesterno | FL</span><span class="sxs-lookup"><span data-stu-id="15fdf-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="15fdf-p109">Ad esempio interna:https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="15fdf-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="15fdf-p110">Ad esempio esterni:https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="15fdf-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="15fdf-p111">Se si utilizza un server Standard Edition, l'URL interno sarà vuoto. In questo caso, utilizzare il nome fqdn del pool per l'URL interno.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="15fdf-153">Attivare l'autenticazione moderno per EXO</span><span class="sxs-lookup"><span data-stu-id="15fdf-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="15fdf-154">Seguire le istruzioni riportate di seguito: [Exchange Online: come abilitare il tenant per l'autenticazione moderno.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="15fdf-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="15fdf-155">Attivare l'autenticazione moderno per SFBO</span><span class="sxs-lookup"><span data-stu-id="15fdf-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="15fdf-156">Seguire le istruzioni riportate di seguito: [Skype Business online: abilitare il tenant per l'autenticazione moderno](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="15fdf-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="15fdf-157">Attivare l'autenticazione moderno ibrida di Exchange in locale</span><span class="sxs-lookup"><span data-stu-id="15fdf-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="15fdf-158">Seguire le istruzioni riportate di seguito: [come configurare Exchange Server locale per utilizzare l'autenticazione moderno ibrida](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="15fdf-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="15fdf-159">Attivare l'autenticazione moderno ibrida per Skype aziendali locali</span><span class="sxs-lookup"><span data-stu-id="15fdf-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="15fdf-160">Aggiungere locale web service URL come nomi SPN in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="15fdf-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="15fdf-161">A questo punto è necessario eseguire i comandi per aggiungere gli URL (raccolti precedentemente) come entità servizio in SFBO.</span><span class="sxs-lookup"><span data-stu-id="15fdf-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="15fdf-p112">**Nota** Nomi delle entità servizi (SPN) identificano i servizi web e associarli a un'entità di sicurezza (ad esempio, un nome account o gruppo) in modo che il servizio può agire per conto di un utente autorizzato. Client di autenticazione in un server effettuare trattamento dei dati che nomi SPN contenuti in.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="15fdf-164">Innanzitutto, connettersi a AAD con [le relative istruzioni](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="15fdf-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="15fdf-165">Eseguire questo comando locale, per ottenere un elenco di URL del servizio web SFB.</span><span class="sxs-lookup"><span data-stu-id="15fdf-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="15fdf-166">Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Selezionare gli attributi SPN - ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="15fdf-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="15fdf-p113">Si noti che il AppPrincipalId inizia con '00000004'. Corrisponde a Skype Business online.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="15fdf-169">Prendere nota delle (e cattura di schermata per un confronto successivo) l'output di questo comando, che includono un SE e WS URL, ma sono costituiti principalmente nomi dell'entità servizio che iniziano con 00000004-0000-0ff1-ce00-000000000000 /.</span><span class="sxs-lookup"><span data-stu-id="15fdf-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="15fdf-170">Se l'interno **o** esterno sono presenti gli URL SFB in locale (ad esempio https://lyncwebint01.contoso.com e https://lyncwebext01.contoso.com) è necessario aggiungere tali record specifici a questo elenco.</span><span class="sxs-lookup"><span data-stu-id="15fdf-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="15fdf-171">Assicurarsi di sostituire *l'URL di esempio* , sotto, con l'URL effettivo nei comandi Add!</span><span class="sxs-lookup"><span data-stu-id="15fdf-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="15fdf-172">$x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="15fdf-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="15fdf-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="15fdf-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="15fdf-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="15fdf-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="15fdf-175">Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - gli attributi SPN $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="15fdf-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="15fdf-p114">Verificare che i nuovi record sono stati aggiunti eseguire nuovamente il comando Get-MsolServicePrincipal del passaggio 2 ed esaminando attraverso l'output. Confrontare l'elenco / schermata prima per il nuovo elenco di nomi SPN (può inoltre essere cattura di schermata del nuovo elenco per i record). Se hanno avuto esito positivo, verrà visualizzato due nuovi URL nell'elenco. Passando dall'esempio, l'elenco di nomi SPN ora includerà URL specifici https://lyncweb01.contoso.com e https://autodiscover.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="15fdf-180">Creare l'oggetto Server EvoSTS autenticazione</span><span class="sxs-lookup"><span data-stu-id="15fdf-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="15fdf-181">Eseguire il comando seguente nel Skype per Business Management Shell.</span><span class="sxs-lookup"><span data-stu-id="15fdf-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="15fdf-182">New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-tipo AzureAD</span><span class="sxs-lookup"><span data-stu-id="15fdf-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="15fdf-183">Abilitare l'autenticazione moderno ibrido</span><span class="sxs-lookup"><span data-stu-id="15fdf-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="15fdf-p115">Questo è il passaggio che attiva effettivamente agente di gestione. Senza modificare il flusso di autenticazione client, è possono eseguire i passaggi precedenti in anticipo rispetto alla volta. Quando si è pronti modificare il flusso di autenticazione, eseguire questo comando nel Skype per Business Management Shell.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="15fdf-187">Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="15fdf-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="15fdf-188">Verifica</span><span class="sxs-lookup"><span data-stu-id="15fdf-188">Verify</span></span>

<span data-ttu-id="15fdf-p116">Se si abilita alta, successivo account di accesso del client utilizzerà il nuovo flusso di autenticazione. Si noti che solo attivando alta non verrà attivato una nuova autenticazione per ogni client. Il client ad autenticarsi in base alla durata di token di autenticazione e/o hanno i certificati.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="15fdf-p117">Per verificare che funzioni alta dopo avere abilitato, disconnettersi da un client Windows SFB test e assicurarsi di fare clic su "Elimina le credenziali". Ripetere l'accesso. Il client è ora necessario utilizzare il flusso di autenticazione moderno e l'account di accesso includerà un prompt dei comandi di **Office 365** per una "lavoro o scuola' account visualizzato a destra prima che il client contatta il server e consente l'accesso.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="15fdf-p118">È consigliabile inoltre ricercare le informazioni di configurazione' ' Skype per i client Business per un'autorità di OAuth' '. A tale scopo nei computer client, tenere premuto il tasto CTRL contemporaneamente che facendo clic il Skype icona Business nel cassetto di notifica di Windows. Fare clic su informazioni di configurazione dal menu visualizzato. Nella finestra 'Skype per informazioni sulla configurazione di Business' che verrà visualizzata sul desktop, cercare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="15fdf-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Le informazioni di configurazione di un Skype per Business Client utilizzando l'autenticazione moderno mostrano un Lync ed EWS OAUTH autorità URL di https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="15fdf-p119">È inoltre deve tenere premuto il tasto CTRL contemporaneamente a destra fare clic sull'icona per il client di Outlook (anche nella barra delle applicazioni Windows Notifications) e fare clic su 'stato di connessione. Cercare l'indirizzo SMTP del client in base a un tipo di uso del ' portanti\*", che rappresenta il token portanti utilizzato in OAuth.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="15fdf-202">Articoli correlati</span><span class="sxs-lookup"><span data-stu-id="15fdf-202">Related articles</span></span>

<span data-ttu-id="15fdf-203">[Collegamento a ritroso alla panoramica autenticazione moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="15fdf-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="15fdf-p120">È necessario conoscere le modalità di utilizzare l'autenticazione (ADAL moderno) per il Skype per i client aziendali? Abbiamo passaggi [di seguito](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="15fdf-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="15fdf-p121">Sarebbe è simile a leggere la procedura seguente quando vengono visualizzati per Exchange Server, in locale, se si esegue senza SFB? Questi passaggi sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="15fdf-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

