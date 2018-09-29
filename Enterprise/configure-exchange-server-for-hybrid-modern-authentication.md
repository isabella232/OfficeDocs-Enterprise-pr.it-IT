---
title: Come configurare Exchange Server locale per utilizzare l'autenticazione moderna ibrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 09/28/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Ibrida moderno autenticazione (alta), è un metodo di gestione delle identità che offre maggiore protezione l'autenticazione degli utenti e l'autorizzazione ed è disponibile per le distribuzioni ibride di Exchange server locale.
ms.openlocfilehash: 4267eaff8dfce71461f230310141a98be8a39e80
ms.sourcegitcommit: 9f921c0cae9a5dd4e66ec1a1261cb88284984a91
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2018
ms.locfileid: "25347606"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="ab646-103">Come configurare Exchange Server locale per utilizzare l'autenticazione moderna ibrida</span><span class="sxs-lookup"><span data-stu-id="ab646-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="ab646-104">Ibrida moderno autenticazione (alta), è un metodo di gestione delle identità che offre maggiore protezione l'autenticazione degli utenti e l'autorizzazione ed è disponibile per le distribuzioni ibride di Exchange server locale.</span><span class="sxs-lookup"><span data-stu-id="ab646-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="ab646-105">MONEY</span><span class="sxs-lookup"><span data-stu-id="ab646-105">FYI</span></span>

<span data-ttu-id="ab646-106">Prima di procedere, è possibile chiamare:</span><span class="sxs-lookup"><span data-stu-id="ab646-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="ab646-107">Autenticazione moderno ibrida \> alta</span><span class="sxs-lookup"><span data-stu-id="ab646-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="ab646-108">Exchange locale \> EXCH</span><span class="sxs-lookup"><span data-stu-id="ab646-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="ab646-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="ab646-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="ab646-110">Inoltre, *che se un'immagine in questo articolo include un oggetto che è "inattivo" o inattivo pertanto, l'elemento visualizzato in grigio non è incluso nella configurazione alta specifiche* .</span><span class="sxs-lookup"><span data-stu-id="ab646-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="ab646-111">Abilitazione dell'autenticazione moderno ibrido</span><span class="sxs-lookup"><span data-stu-id="ab646-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="ab646-112">Attivazione alta indica:</span><span class="sxs-lookup"><span data-stu-id="ab646-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="ab646-113">Verificando che vengano soddisfatti i prerequisiti prima di iniziare.</span><span class="sxs-lookup"><span data-stu-id="ab646-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="ab646-p101">Rispetto a molti **Prerequisiti** sono comuni per entrambi Skype per le aziende ed Exchange, [Panoramica dell'autenticazione moderno ibrida e prerequisiti per l'utilizzo con locale Skype per Business ed Exchange Server](hybrid-modern-auth-overview.md). Eseguire questa operazione prima di eseguire le procedure descritte in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ab646-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="ab646-116">Aggiunta di locale URL del servizio web come nomi delle entità servizio (SPN) in Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ab646-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="ab646-117">Verifica tutte le directory virtuali sono abilitate per alta</span><span class="sxs-lookup"><span data-stu-id="ab646-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="ab646-118">Verifica dell'oggetto Server di autenticazione EvoSTS</span><span class="sxs-lookup"><span data-stu-id="ab646-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="ab646-119">Abilitazione di alta in tassi di cambio</span><span class="sxs-lookup"><span data-stu-id="ab646-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="ab646-p102">**Nota** La versione di Office supporta agente di gestione? Vedere [come moderno funzionamento dell'autenticazione per le applicazioni client di Office 2013 e Office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="ab646-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="ab646-122">Verificare che siano soddisfatti tutti i codice prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ab646-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="ab646-p103">Poiché molti prerequisiti sono comuni per entrambi Skype per le aziende ed Exchange, leggere [Panoramica dell'autenticazione moderno ibrida e prerequisiti per l'utilizzo con Skype locale per Business ed Exchange Server](hybrid-modern-auth-overview.md). Questo *prima di* iniziare le procedure descritte in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ab646-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="ab646-125">Aggiungere locale web service URL come nomi SPN in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="ab646-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="ab646-p104">Eseguire i comandi che è necessario assegnare il web locale gli URL del servizio nomi SPN con Azure Active Directory nomi SPN. utilizzati dal computer client e dispositivi durante l'autenticazione e autorizzazione. Tutti gli URL che possono eventualmente essere utilizzati per la connessione in locale per Azure Active Directory (AAD) devono essere registrati in AAD (include spazi dei nomi interni ed esterni).</span><span class="sxs-lookup"><span data-stu-id="ab646-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="ab646-p105">Innanzitutto, raccogliere tutti gli URL che si devono aggiungere AAD. Eseguire questi comandi locale:</span><span class="sxs-lookup"><span data-stu-id="ab646-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="ab646-131">Verificare che gli URL client possono connettersi a elencato come nomi delle entità servizio HTTPS in AAD.</span><span class="sxs-lookup"><span data-stu-id="ab646-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="ab646-132">Innanzitutto, connettersi a AAD con [le relative istruzioni](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="ab646-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>
    
2. <span data-ttu-id="ab646-133">Per lo scambio correlati URL, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ab646-133">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="ab646-p106">Prendere nota delle (e cattura di schermata per un confronto successivo) l'output di questo comando, che deve includere un https:// *autodiscover.yourdomain.com* e URL https:// *mail.yourdomain.com* , ma sono costituiti principalmente nomi dell'entità servizio che iniziano con 00000002-0000-0ff1-CE00-000000000000 /. Se sono presenti gli URL https:// da locale che risultano mancanti è necessario aggiungere i record specifici a questo elenco.</span><span class="sxs-lookup"><span data-stu-id="ab646-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="ab646-136">Se i record MAPI su HTTP, servizi Web Exchange, ActiveSync, della Rubrica offline e l'individuazione automatica interni ed esterni in questo elenco non viene visualizzata, è necessario aggiungerli tramite il comando riportato di seguito (nell'esempio gli URL sono '`mail.corp.contoso.com`'e'`owa.contoso.com`', ma è possibile **sostituire l'URL di esempio con il proprio** ) :</span><span class="sxs-lookup"><span data-stu-id="ab646-136">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="ab646-p107">Verificare che i nuovi record sono stati aggiunti eseguire nuovamente il comando Get-MsolServicePrincipal del passaggio 2 ed esaminando attraverso l'output. Confrontare l'elenco / schermata prima per il nuovo elenco di nomi SPN (può inoltre essere cattura di schermata del nuovo elenco per i record). Se hanno avuto esito positivo, verrà visualizzato due nuovi URL nell'elenco. Passando dall'esempio, l'elenco di nomi SPN ora includerà URL specifici `https://mail.corp.contoso.com` e `https://owa.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="ab646-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="ab646-141">Verificare che le directory virtuali sono configurate correttamente</span><span class="sxs-lookup"><span data-stu-id="ab646-141">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="ab646-142">A questo punto verificare OAuth è abilitato correttamente in Exchange in tutti i Outlook le directory virtuali potrebbe utilizzare eseguendo i seguenti comandi:</span><span class="sxs-lookup"><span data-stu-id="ab646-142">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="ab646-143">Controllo dell'output per verificare che **OAuth** è abilitata su ciascuno di questi virtuali, sarà simile al seguente (e l'aspetto principale da esaminare 'OAuth');</span><span class="sxs-lookup"><span data-stu-id="ab646-143">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

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
  
<span data-ttu-id="ab646-144">Se non è presente alcun server e delle directory virtuali di quattro OAuth è necessario aggiungerlo utilizzando i comandi desiderati prima di procedere.</span><span class="sxs-lookup"><span data-stu-id="ab646-144">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="ab646-145">Verificare che l'oggetto Server di autenticazione EvoSTS è presente</span><span class="sxs-lookup"><span data-stu-id="ab646-145">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="ab646-p108">Tornare a locale Exchange Management Shell per questo ultimo comando eseguito. È ora possibile convalidare locale che dispone di una voce per il provider di autenticazione evoSTS:</span><span class="sxs-lookup"><span data-stu-id="ab646-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="ab646-p109">L'output dovrebbe essere visualizzato un AuthServer di EvoSts nome e lo stato 'Enabled' deve essere True. Se non è visualizzata, è necessario scaricare ed eseguire la versione più recente della procedura guidata di configurazione ibrida.</span><span class="sxs-lookup"><span data-stu-id="ab646-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="ab646-150">**Importante** Se si esegue Exchange 2010 nell'ambiente in uso, non verrà creato il provider di autenticazione EvoSTS.</span><span class="sxs-lookup"><span data-stu-id="ab646-150">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="ab646-151">Abilitare alta</span><span class="sxs-lookup"><span data-stu-id="ab646-151">Enable HMA</span></span>

<span data-ttu-id="ab646-152">Eseguire il seguente comando in Exchange Management Shell in locale:</span><span class="sxs-lookup"><span data-stu-id="ab646-152">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="ab646-153">Verifica</span><span class="sxs-lookup"><span data-stu-id="ab646-153">Verify</span></span>

<span data-ttu-id="ab646-p110">Se si abilita alta, successivo account di accesso del client utilizzerà il nuovo flusso di autenticazione. Si noti che solo attivando alta non verrà attivato una nuova autenticazione per ogni client. Il client ad autenticarsi in base alla durata di token di autenticazione e/o hanno i certificati.</span><span class="sxs-lookup"><span data-stu-id="ab646-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="ab646-p111">È inoltre deve tenere premuto il tasto CTRL contemporaneamente a destra fare clic sull'icona per il client di Outlook (anche nella barra delle applicazioni Windows Notifications) e fare clic su 'stato di connessione. Cercare l'indirizzo SMTP del client in base a un tipo di 'Uso' del ' portanti\*", che rappresenta il token portanti utilizzato in OAuth.</span><span class="sxs-lookup"><span data-stu-id="ab646-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="ab646-p112">**Nota** È necessario configurare Skype for Business con alta? È necessario due articoli: uno che elenca [topologie supportate](https://technet.microsoft.com/en-us/library/mt803262.aspx)e uno che viene illustrato [come eseguire la configurazione](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ab646-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://technet.microsoft.com/en-us/library/mt803262.aspx), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="ab646-161">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="ab646-161">Related topics</span></span>

[<span data-ttu-id="ab646-162">Cenni preliminari sull'autenticazione moderno ibrida e prerequisiti per l'utilizzo con Skype locale per Business ed Exchange Server</span><span class="sxs-lookup"><span data-stu-id="ab646-162">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

