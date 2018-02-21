---
title: Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 che sono stati assegnati agli utenti.
ms.openlocfilehash: 69784b43e6e2b24f776d07a937877e5ae0c74888
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="5a29c-103">Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a29c-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="5a29c-104">**Riepilogo:** Questo articolo viene illustrato come utilizzare Office 365 PowerShell per determinare i servizi di Office 365 che sono stati assegnati agli utenti.</span><span class="sxs-lookup"><span data-stu-id="5a29c-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="5a29c-p101">In Office 365, concede in licenza da Gestione licenze piani (anche denominato SKU o Office 365 dei piani) è possibile accedere ai servizi definiti per i piani di Office 365. Tuttavia, un utente potrebbe non avere accesso a tutti i servizi disponibili in una licenza attualmente assegnati a loro. È possibile utilizzare Office 365 PowerShell per visualizzare lo stato dei servizi per gli account utente.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="5a29c-108">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="5a29c-108">Before you begin</span></span>
<span data-ttu-id="5a29c-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="5a29c-109"></span></span>

- <span data-ttu-id="5a29c-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="5a29c-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="5a29c-112">Utilizzare i comandi `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` per trovare le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a29c-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="5a29c-113">I piani di gestione delle licenze che sono disponibili nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="5a29c-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="5a29c-114">I servizi che sono disponibili in ogni piano di gestione delle licenze e l'ordine in cui sono elencati (il numero di indice).</span><span class="sxs-lookup"><span data-stu-id="5a29c-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="5a29c-115">Per ulteriori informazioni sulle licenze di piani di licenza e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="5a29c-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="5a29c-116">Utilizzare il comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` per individuare le licenze che sono assegnate a un utente e l'ordine in cui sono elencati (numero di indice).</span><span class="sxs-lookup"><span data-stu-id="5a29c-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="5a29c-117">Se si usa il cmdlet **Get-MsolUser** senza utilizzare il parametro _All_, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="5a29c-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="5a29c-118">Versione breve (istruzioni senza spiegazioni)</span><span class="sxs-lookup"><span data-stu-id="5a29c-118">The short version (instructions without explanations)</span></span>
<span data-ttu-id="5a29c-119"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="5a29c-119"></span></span>

<span data-ttu-id="5a29c-120">Per visualizzare tutti i servizi di Office 365 PowerShell che un utente ha accesso, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="5a29c-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="5a29c-p103">In questo esempio vengono illustrati i servizi al quale BelindaN@litwareinc.com l'utente dispone dell'accesso. Mostra i servizi associati a tutte le licenze che sono assegnate al suo account.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="5a29c-123">Questo esempio mostra i servizi ai quali l'utente BelindaN@litwareinc.com ha accesso dalla prima licenza assegnata al suo account (il numero di indice è 0).</span><span class="sxs-lookup"><span data-stu-id="5a29c-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="5a29c-124">Per trovare tutti gli utenti con licenza che sono stati abilitati o disabilitati per servizi specifici, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="5a29c-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="5a29c-125">In questi esempi vengono usate le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a29c-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="5a29c-126">La licenza che consente di accedere ai servizi di Office 365 che siamo interessati è la licenza prima che viene assegnata a tutti gli utenti (numero di indice è 0).</span><span class="sxs-lookup"><span data-stu-id="5a29c-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="5a29c-p104">I servizi di Office 365 che siamo interessati sono Skype per Business Online ed Exchange Online. Per le licenze che sono associate il piano di licenze, Skype Business online è il servizio 6 elencato (5 è il numero di indice), ed Exchange Online è il servizio 9 elencati (il numero di indice è 8).</span><span class="sxs-lookup"><span data-stu-id="5a29c-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="5a29c-129">Questo esempio vengono restituite tutte con licenza gli utenti abilitati per Skype per Business Online ed Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="5a29c-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="5a29c-130">In questo esempio restituisce tutti gli utenti con licenza non abilitati per Skype Business Online o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="5a29c-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="5a29c-131">Versione estesa (istruzioni con spiegazioni dettagliate)</span><span class="sxs-lookup"><span data-stu-id="5a29c-131">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="5a29c-132"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="5a29c-132"></span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="5a29c-133">Individuare i servizi di Office 365 PowerShell che un utente ha accesso a</span><span class="sxs-lookup"><span data-stu-id="5a29c-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="5a29c-p105">È ovviamente importante sapere quali utenti sono stati rilasciati licenze di Office 365 e gli utenti che non sono. (Vedere l'articolo [consente di visualizzare gli utenti con licenza e senza licenza con Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) per ulteriori informazioni). Tuttavia, è sufficiente disporre di una licenza Office 365 non fornisce alcuna informazione lasciare sulle operazioni che all'utente è effettivamente con Office 365. Possibile potrà utilizzare Exchange Online o Skype Business online? L'utente può accedere SharePoint Online? È necessario l'accesso a Office Professional Plus? Disporre di una licenza significa semplicemente che l'utente è in grado di accedere a tali servizi. Tuttavia, le funzionalità disponibili per un utente dipendono i servizi che sono stati abilitati per il proprio licenze.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="5a29c-p106">Come possiamo quindi determinare quali funzionalità di Office 365 un utente ha accesso? Per eseguire che è necessario eseguire un comando simile a questo:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="5a29c-144">In questo comando, viene utilizzato il cmdlet **Get-MsolUser** per restituire informazioni sull'account BelindaN@litwareinc.com. Dopo la restituzione è stata tali informazioni, viene quindi inviata tramite pipe i dati di account al cmdlet **Select-Object** e chiedere a **Select-Object** per "espandere" il valore della proprietà **licenze** :</span><span class="sxs-lookup"><span data-stu-id="5a29c-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="5a29c-p107">Perché dobbiamo farlo? Allora, per impostazione predefinita le **licenze** proprietà ci dice solo il nome del pacchetto di licenze cui proviene la licenza di Belinda da:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="5a29c-147">"Espandiamo" la proprietà **Licenses** ci otteniamo altre informazioni:</span><span class="sxs-lookup"><span data-stu-id="5a29c-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="5a29c-148">E quindi, espandendo la proprietà **ServiceStatus** possiamo ottenere ancora altre informazioni:</span><span class="sxs-lookup"><span data-stu-id="5a29c-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="5a29c-149">Servizio plan \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5a29c-149">****Service plan****</span></span>|<span data-ttu-id="5a29c-150">Descrizione \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5a29c-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="5a29c-151">Sway</span><span class="sxs-lookup"><span data-stu-id="5a29c-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="5a29c-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5a29c-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="5a29c-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-154">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="5a29c-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="5a29c-155">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="5a29c-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="5a29c-156">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="5a29c-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="5a29c-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="5a29c-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="5a29c-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5a29c-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-159">Exchange Online, piano 2</span><span class="sxs-lookup"><span data-stu-id="5a29c-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="5a29c-p108">Ad esempio, che è troppo complicato? Allora, se è possibile inserire backup di una piccola non sei pratico di Windows PowerShell, è possibile eseguire versione ridotta del comando invece: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="5a29c-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="5a29c-p109">Nel caso in cui si desidera sapere per, è possibile "espandere" la proprietà **Licenses** perché **le licenze** è una proprietà multivalore: si tratta di una singola proprietà che possono essere archiviati più valori. Quando si espande un valore della proprietà a che è semplicemente eseguire il drill-down fino ottenere i valori aggiuntivi riportati che, per impostazione predefinita, non vengono visualizzati sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5a29c-p110">In che modo puoi quindi sapere se un valore è una proprietà multivalore? Allora, per scoprirlo, prova a eseguire un comando simile al seguente: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> il cmdlet **Get-member** restituisce informazioni relative all'oggetto stesso. In questo caso, informazioni sulla proprietà valori che compongono un oggetto account utente. Ecco cosa **Get-Member** deve dire in relazione la proprietà **Licenses** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> Se la definizione della proprietà dice qualcosa sulle raccolte (in questo caso, `System.Collections.Generic.List`), quindi verificare se ha a che fare con una proprietà multivalore.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="5a29c-p111">In modo che cosa significa tutto questo? Per rispondere, possiamo prima un'altra occhiata alle informazioni restituite dal cmdlet **Get-MsolUser** :</span><span class="sxs-lookup"><span data-stu-id="5a29c-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

<span data-ttu-id="5a29c-169">Ed ecco anche una breve panoramica in una tabella in cui viene spiegato cosa questi piani di servizio strani rappresentano veramente:</span><span class="sxs-lookup"><span data-stu-id="5a29c-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="5a29c-170">Servizio plan \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5a29c-170">****Service plan****</span></span>|<span data-ttu-id="5a29c-171">Descrizione \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5a29c-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="5a29c-172">Sway</span><span class="sxs-lookup"><span data-stu-id="5a29c-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="5a29c-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5a29c-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="5a29c-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-175">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="5a29c-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="5a29c-176">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="5a29c-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="5a29c-177">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="5a29c-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="5a29c-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="5a29c-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="5a29c-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5a29c-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-180">Exchange Online, piano 2</span><span class="sxs-lookup"><span data-stu-id="5a29c-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="5a29c-p112">Tutto chiaro?  `MCOSTANDARD` è solo un nome di programmazione interno per Skype per Business Online, mentre `OFFICESUSBCRIPTION` è solo il nome di programmazione interno di Office Professional Plus. Non è più intuitivo significato del mondo, ma poiché questa tabella è mantenuto utile non sarà necessario molti problemi per l'utilizzo dei servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="5a29c-p113">Ma non è: non esiste più. Come acquisito nell'articolo [View licenze e servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), se è impostato su **ProvisioningStatus** `Success` ciò significa che il servizio è stato abilitato completamente; ad esempio se `MCOSTANDARD` è impostata su `Success` ciò significa che l'utente può accedere Skype Business online. Se è impostato su **ProvisioningStatus** `PendingInput` ciò significa che Office 365 sta ancora elaborando la richiesta di servizio. Tuttavia, l'utente può in genere accedere e accedere al servizio durante la richiesta viene terminata l'elaborazione. ( `YAMMER_ENTERPRISE` verranno sempre visualizzati come `PendingInput`, tuttavia: che non si arresta un utente di accedere a Yammer).</span><span class="sxs-lookup"><span data-stu-id="5a29c-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="5a29c-188">Gli utenti possono installare e attivare una nuova installazione di Office Professional Plus mentre `OFFICESUBSCRIPTION` nel `PendingInput` informazioni sullo stato.</span><span class="sxs-lookup"><span data-stu-id="5a29c-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="5a29c-189">E inutile a dirsi, è un servizio è impostato su `Disabled` ciò significa che il servizio in questione non è disponibile per l'utente.</span><span class="sxs-lookup"><span data-stu-id="5a29c-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="5a29c-190">Trovare gli utenti che dispongono dell'accesso a servizi di Office 365 PowerShell specifici</span><span class="sxs-lookup"><span data-stu-id="5a29c-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="5a29c-p114">In un articolo separato, sono state riscontrate come è possibile utilizzare Office 365 PowerShell per disabilitare l'accesso utente ai servizi. (Se si perde suddetto articolo, vedere [disabilitare l'accesso ai servizi di Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Che favorisce una domanda ovvia: non vi è alcun modo per determinare quali *utenti* (vale a dire più di un utente) sono i servizi abilitata o disabilitata?</span><span class="sxs-lookup"><span data-stu-id="5a29c-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="5a29c-p115">Sono state speranza che un utente potrebbe richiedere che. Per rispondere a questa domanda, è opportuno esaminare la tabella dei servizi che viene per prima cosa nell'articolo [servizi con Office 365 PowerShell e le licenze di visualizzazione](view-licenses-and-services-with-office-365-powershell.md) per il piano di licenze disponibile solo `litwareinc:ENTERPRISEPACK`:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="5a29c-196">Servizio plan \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5a29c-196">****Service plan****</span></span>|<span data-ttu-id="5a29c-197">Descrizione \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5a29c-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="5a29c-198">Sway</span><span class="sxs-lookup"><span data-stu-id="5a29c-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="5a29c-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5a29c-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="5a29c-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-201">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="5a29c-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="5a29c-202">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="5a29c-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="5a29c-203">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="5a29c-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="5a29c-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="5a29c-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="5a29c-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5a29c-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="5a29c-206">Exchange Online, piano 2</span><span class="sxs-lookup"><span data-stu-id="5a29c-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="5a29c-p116">Come si ricorderà, il piano di servizio non è altro che il nome di programmazione interno di un prodotto; ad esempio `OFFICESUBSCRIPTION`, nome uno, è il nome di programmazione interno di Office Professional Plus. Se `OFFICESUBSCRIPTION` viene visualizzato come `SUCCESS` nel piano di servizio dell'utente, quindi ciò significa che l'utente possa accedere a Office Professional Plus. Se `EXCHANGE_S_ENTERPRISE` è elencato come `DISABLED` di conseguenza, l'utente non può utilizzare Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="5a29c-210">Gli utenti possono installare e attivare una nuova installazione di Office Professional Plus mentre `OFFICESUBSCRIPTION` nel `PendingInput` informazioni sullo stato.</span><span class="sxs-lookup"><span data-stu-id="5a29c-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="5a29c-p117">È il momento in cui è estremamente importante l'ordine in cui vengono visualizzati i servizi. Windows PowerShell viene assegnato un numero di indice per ogni voce nell'elenco. La prima voce è 0, la voce successiva è 1 e così via. Nella tabella seguente vengono descritti i risultati:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="5a29c-215">Numero di indice \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5a29c-215">****Index number****</span></span>|<span data-ttu-id="5a29c-216">Servizio plan \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5a29c-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="5a29c-217">0</span><span class="sxs-lookup"><span data-stu-id="5a29c-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="5a29c-218">1</span><span class="sxs-lookup"><span data-stu-id="5a29c-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="5a29c-219">2</span><span class="sxs-lookup"><span data-stu-id="5a29c-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="5a29c-220">3</span><span class="sxs-lookup"><span data-stu-id="5a29c-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="5a29c-221">4</span><span class="sxs-lookup"><span data-stu-id="5a29c-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="5a29c-222">5</span><span class="sxs-lookup"><span data-stu-id="5a29c-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="5a29c-223">6</span><span class="sxs-lookup"><span data-stu-id="5a29c-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="5a29c-224">7</span><span class="sxs-lookup"><span data-stu-id="5a29c-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="5a29c-225">8</span><span class="sxs-lookup"><span data-stu-id="5a29c-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="5a29c-226">Come si può notare, `SWAY` è il primo servizio elencato, in modo che venga assegnato il numero di indice 0.</span><span class="sxs-lookup"><span data-stu-id="5a29c-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="5a29c-p118">Perché 0 e 1 non? Questo è un aspetto programmazione. Linguaggi di programmazione indici sapere quanto un elemento "sfalsamento" l'inizio della matrice. Il primo elemento *è* l'inizio della matrice, in modo che il relativo argomento offset è 0. Il secondo elemento è 1 dall'inizio della matrice, in modo che la distanza è 1.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="5a29c-p119">Punto provare un esempio. Si supponga che si desidera un elenco di tutti gli utenti con licenza che non sono stati abilitati per Exchange Online. A tale scopo, è possibile utilizzare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="5a29c-p120">Se è un comando little strani cercando possiamo richiedere qualche minuto per descrivere le modalità di funzionamento. Questo è effettivamente un comando di due parti e la prima parte è molto semplice: viene utilizzato il cmdlet **Get-MsolUser** per restituire una raccolta di tutti gli utenti di Office 365 (concessa in licenza e senza licenza):</span><span class="sxs-lookup"><span data-stu-id="5a29c-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="5a29c-p121">Tali informazioni viene inviata tramite pipe al cmdlet **Where-Object** . **Where-Object** esamina tutti gli account utente e cerca tali account che soddisfano entrambi i criteri seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="5a29c-p122">La proprietà **isLicensed** è uguale a ( `-eq`) `True` ( `$true`). Che ci consente di eliminare gli utenti senza licenza.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="5a29c-p123">Il valore delle licenze **[0]. ServiceStatus [8]. ProvisioningStatus** proprietà è uguale a ( `-eq`) `Disabled`. Ai fini del presente immediate, la parte importante di questo nome di proprietà difficile da gestire è la seguente:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="5a29c-p124">Il `[8]` rappresenta il numero di indice per Exchange Online. (È possibile sapere che da osservando la tabella alcuni minuti). Se si desidera trovare tutti gli utenti abilitati per Skype Business online? Il numero di indice per Skype Business online è 5, pertanto è necessario utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="5a29c-247">E così via.</span><span class="sxs-lookup"><span data-stu-id="5a29c-247">Etc., etc.</span></span>
    
    <span data-ttu-id="5a29c-p125">Per inciso, `Licenses[0]` indica il piano di licenze che si desidera esaminare. Poiché il dominio di test dispone solo di un piano di licenze ciò non è rilevante. Tuttavia, si supponga un utente che è stato assegnato licenze da due diversi piani di gestione delle licenze. In tal caso, `Licenses[0]` rappresenta il primo piano di gestione delle licenze e `Licenses[1]` potrebbe rappresentare il secondo piano di licenze.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="5a29c-252">Per trovare le licenze assegnate a un utente e l'ordine in cui sono elencate, esegui il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="5a29c-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="5a29c-p126">Vuoi vedere come funziona tutto ciò? Il numero di indice per Office Professional Plus è 4. Pertanto, questo comando restituisce un elenco di tutti gli utenti che non sono stati abilitati per Office Professional Plus:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="5a29c-p127">E se si desidera un elenco di utenti che sono stati *abilitati* per Office Professional Plus? Anche se è stato attivato, quindi la **ServiceStatus** essere costituiti da `PendingInput` o `Success`; in altre parole, la **ServiceStatus** verrà *non* è uguale ( `-ne`) `Disabled`. Vale a dire è sufficiente eseguire il comando precedente e lo swapping il `-eq` operatore per la `-ne` operatore:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="5a29c-p128">Come l'indica passa, che codice probabilmente non win molti concorsi vantaggio. E verità comunicato, il codice può ottenere ancora altre provare. Si supponga, ad esempio, che si desidera cercare gli utenti che sono stati abilitati per entrambi Skype per Business Online ed Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="5a29c-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="5a29c-p129">Ma non bisogna preoccuparsi troppo su come processo che potrebbe essere: l'importante è che, in maniera relativamente, è possibile recuperare queste informazioni. Impossibile ottenere queste stesse informazioni tramite l'interfaccia di amministrazione di Office 365? In teoria, Sì ma, in termini pratici, no. Per ottenere queste stesse informazioni tramite l'interfaccia di amministrazione di Office 365 è necessario esaminare le informazioni sulla licenze per ogni utente, un utente alla volta e quindi manualmente tenere traccia degli utenti sono stati abilitati per *X* e che non era. Che potrebbe funzionare, ma possiamo essere accurato: se si dispone di più di 10 o 11 utenti, non sarà a tale scopo. È troppo lunghe e noiose.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="5a29c-267">Naturalmente, ovvero il motivo per cui si dispone di Windows PowerShell: Windows PowerShell aiuta a evitare attività lunghe e noiose come questa.</span><span class="sxs-lookup"><span data-stu-id="5a29c-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="5a29c-268">Mentre è ora essere, ecco il comando finale per visualizzare informazioni sul servizio:</span><span class="sxs-lookup"><span data-stu-id="5a29c-268">While we're at it, here's the ultimate command for viewing service information:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

<span data-ttu-id="5a29c-p130">E si un comando molto sorta. Ma viene creato un file CSV con tutti gli utenti e tutto il relativo stato servizio.</span><span class="sxs-lookup"><span data-stu-id="5a29c-p130">And yes, that's a very crazy-looking command. But it creates a CSV file showing all of your users and all of their service statuses.</span></span>

  
## <a name="see-also"></a><span data-ttu-id="5a29c-271">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5a29c-271">See also</span></span>
<span data-ttu-id="5a29c-272"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="5a29c-272"></span></span>

<span data-ttu-id="5a29c-273">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5a29c-273">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="5a29c-274">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a29c-274">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5a29c-275">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a29c-275">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5a29c-276">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a29c-276">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5a29c-277">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a29c-277">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5a29c-278">Rimuovere le licenze dagli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a29c-278">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="5a29c-279">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="5a29c-279">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="5a29c-280">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="5a29c-280">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="5a29c-281">Format-List</span><span class="sxs-lookup"><span data-stu-id="5a29c-281">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="5a29c-282">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="5a29c-282">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="5a29c-283">Select-Object</span><span class="sxs-lookup"><span data-stu-id="5a29c-283">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="5a29c-284">Where-Object</span><span class="sxs-lookup"><span data-stu-id="5a29c-284">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="5a29c-285">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="5a29c-285">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]