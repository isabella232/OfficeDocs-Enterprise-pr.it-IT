---
title: Assegnare le licenze agli account utente con Office 365 PowerShell
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.
ms.openlocfilehash: 688e2775e7a028cd9dbe0c8ea27a7f3a453b5279
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="cf782-103">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf782-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="cf782-104">**Riepilogo:**  Questo articolo viene illustrato come utilizzare Office 365 PowerShell assegna una licenza di Office 365 per gli utenti senza licenza.</span><span class="sxs-lookup"><span data-stu-id="cf782-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="cf782-p101">Gestione delle licenze gli account utente in Office 365 è importante in quanto gli utenti non possono utilizzare i servizi di Office 365 fino a quando non è stato concesso in licenza il proprio account. È possibile utilizzare Office 365 PowerShell in modo efficiente assegnare licenze agli account senza licenza, soprattutto più account.</span><span class="sxs-lookup"><span data-stu-id="cf782-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="cf782-107">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="cf782-107">Before you begin</span></span>
<span data-ttu-id="cf782-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="cf782-108"></span></span>

- <span data-ttu-id="cf782-p102">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="cf782-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="cf782-p103">Utilizzare il cmdlet **Get-MsolAccountSku** per visualizzare i piani di gestione delle licenze disponibili e il numero di licenze disponibili in ogni piano all'interno dell'organizzazione. Il numero di licenze disponibili in ogni piano è **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Per ulteriori informazioni sulle licenze di piani, le licenze e servizi, vedere [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="cf782-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="cf782-114">Per trovare gli account senza licenza all'interno dell'organizzazione, eseguire il comando`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="cf782-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="cf782-p104">È possibile assegnare licenze solo per gli account utente con la proprietà **UsageLocation** impostata su un valido ISO 3166-1 alpha-codice di paese 2. Ad esempio, ci per gli Stati Uniti e FR per Francia. Alcuni servizi di Office 365 non sono disponibili in alcune nazioni. Per ulteriori informazioni, vedere [About restrizioni relative alla licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="cf782-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="cf782-p105">Per trovare gli account di cui non sono un valore **UsageLocation** , eseguire il comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Per impostare il valore **UsageLocation** su un account, utilizzare la sintassi `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Ad esempio `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="cf782-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="cf782-122">Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il `-All` parametro, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="cf782-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="cf782-123">Versione breve (istruzioni senza spiegazioni)</span><span class="sxs-lookup"><span data-stu-id="cf782-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="cf782-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="cf782-124"></span></span>

<span data-ttu-id="cf782-p106">In questa sezione vengono presentate le procedure senza spiegazione dettagliata. Domande o altre informazioni, è possibile leggere resto dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="cf782-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="cf782-127">Per assegnare una licenza a un utente, utilizzare la sintassi seguente in Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="cf782-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="cf782-128">Questo esempio viene assegnata una licenza per il `litwareinc:ENTERPRISEPACK` piano di licenze (Office 365 Enterprise E3) all'utente senza licenza `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="cf782-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="cf782-129">Per assegnare una licenza a più utenti privi di licenza, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="cf782-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="cf782-130">**Note**</span><span class="sxs-lookup"><span data-stu-id="cf782-130">**Notes**</span></span>
  
- <span data-ttu-id="cf782-131">Non è possibile assegnare più licenze a un utente dallo stesso piano di gestione delle licenze.</span><span class="sxs-lookup"><span data-stu-id="cf782-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="cf782-132">Se non è sufficiente licenze disponibili, le licenze vengono assegnate agli utenti nell'ordine in cui si sta restituiti dal cmdlet **Get-MsolUser** fino ad esaurimento le licenze disponibili.</span><span class="sxs-lookup"><span data-stu-id="cf782-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="cf782-133">In questo esempio consente di assegnare licenze dal `litwareinc:ENTERPRISEPACK` piano di licenze (Office 365 Enterprise E3) a tutti gli utenti senza licenza.</span><span class="sxs-lookup"><span data-stu-id="cf782-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="cf782-134">In questo esempio vengono assegnate le stesse licenze agli utenti senza licenza del reparto vendite negli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="cf782-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="cf782-135">Versione estesa (istruzioni con spiegazioni dettagliate)</span><span class="sxs-lookup"><span data-stu-id="cf782-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="cf782-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="cf782-136"></span></span>

<span data-ttu-id="cf782-p107">Come osservato in precedenza nell'articolo [consente di visualizzare gli utenti con licenza e senza licenza con Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), è possibile lasciare che gli utenti che dispongono di account utente di Office 365 validi, ma che non sono state rilasciate una licenza Office 365. Ciò significa che, account o valido non valido, gli utenti non sarà in grado di accedere a Office 365. E, se non è possibile accedere, non possono trarne vantaggio dei servizi Office 365.</span><span class="sxs-lookup"><span data-stu-id="cf782-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="cf782-140">Il suddetto articolo fa notare anche che è possibile restituire un elenco di account utente senza licenza eseguendo il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="cf782-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="cf782-141">Il comando restituisce informazioni su tutti gli utenti che non dispongono di licenze attualmente per Office 365:</span><span class="sxs-lookup"><span data-stu-id="cf782-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="cf782-p108">Come si può notare, si dispone di un utente senza licenza: Belinda Newman. In che modo si passare sull'assegnazione di Belinda una licenza Office 365</span><span class="sxs-lookup"><span data-stu-id="cf782-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="cf782-144">Per iniziare, dobbiamo eseguire il cmdlet **Get-MsolAccountSku** descritto nell'articolo [View licenze e servizi con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span><span class="sxs-lookup"><span data-stu-id="cf782-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="cf782-145">Quel comando restituisce dati simili al seguente:</span><span class="sxs-lookup"><span data-stu-id="cf782-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="cf782-p109">Perché è eseguire **Get-MsolAccountSku** ? ("Sku", nel caso in cui si desidera sapere per, è abbreviazione di "unità SKU." Ai fini del presente che è appena business-parlare "prodotto".) Esistono due motivi per cui si esegue **Get-MsolAccountSku**. Innanzitutto è necessario assicurarsi che in realtà si dispone di una licenza per assegnare Belinda. È disponibile alcun licenze che è possibile assegnare Lei? Per determinare che, è accettare il valore della proprietà **ActiveUnits** (25) e sottrarre i valori delle proprietà **ConsumedUnits** (24) e **WarningUnits** (0):</span><span class="sxs-lookup"><span data-stu-id="cf782-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="cf782-p110">La proprietà **ActiveUnits** indica il numero di licenze è stato acquistato e il valore combinato di **WarningUnits** e **ConsumedUnits** indica quante licenze sono attualmente in uso. Sottraendo il numero di licenze di pronunciato già dal numero di licenze che abbiamo acquistato, per ottenere il numero di licenze è ancora disponibile. Come fortuna sarebbe è disponibile, si dispone di una licenza disponibile per la distribuzione:</span><span class="sxs-lookup"><span data-stu-id="cf782-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="cf782-p111">Secondo, per assegnare una nuova licenza è necessario conoscere il nome di questo piano di licenze di Belinda (vale a dire, è necessario conoscere **AccountSkuId** ). In questo caso, è facile: esiste solo un singolo piano di licenze ( `litwareinc:ENTERPRISEPACK`). Tuttavia, è possibile per organizzazioni che hanno più piani di gestione delle licenze. In tal caso, **Get-MsolAccountSku** restituirebbe due diversi **AccountSkuIds**ed è necessario selezionare il piano di licenze appropriato durante l'assegnazione delle licenze. Per il momento, tuttavia, verranno esaminati osserva il caso più semplice e si presuppone che è presente un solo piano di licenze.</span><span class="sxs-lookup"><span data-stu-id="cf782-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="cf782-p112">*Quindi modo assegniamo quindi Belinda Newman una nuova licenza?* Così:</span><span class="sxs-lookup"><span data-stu-id="cf782-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="cf782-162">È inoltre è necessario effettuare: sufficiente chiamare il cmdlet **Set-MsolUserLicense** , assicurandosi che si specifica il parametro _UserPrincipalName_ dell'utente e il piano di licenze appropriato.</span><span class="sxs-lookup"><span data-stu-id="cf782-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="cf782-163">**Set-MsolUserLicense** termina quando in esecuzione, verrà visualizzato qualcosa di simile a questo sullo schermo:</span><span class="sxs-lookup"><span data-stu-id="cf782-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\\windows\\system32>`
  
<span data-ttu-id="cf782-p113">In altre parole, non sembra lasciare viene spiegato. Per verificare che l'utente è stata assegnata una licenza, eseguire un comando simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="cf782-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="cf782-166">Se tutto funziona come previsto, è consigliabile vedere che la proprietà isLicensed di Belinda è ora impostata su True:</span><span class="sxs-lookup"><span data-stu-id="cf782-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! Ottima domanda Nota sulla sicurezza]<span data-ttu-id="cf782-p114">: che cosa accade se si tratta di un errore e ha tentato di assegnare una licenza a un utente che dispone già di una licenza? Potrà offrendo due licenze a un singolo utente? > La risposta rapida? No. Office 365 non consentono di assegnare più di una licenza per lo stesso account utente. (Più di una licenza dal piano di licenze stesso, l'operazione è.) Se si tenta di eseguire questa operazione il comando avrà esito negativo con il messaggio di errore: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Se tale messaggio di errore è apparirà fuorviante: la licenza non è in realtà non valida, è appena stato assegnato a un utente che ha già *dispone di* una licenza. Tuttavia, messaggio di errore, l'importante è che un utente non avere con licenze multiple.</span><span class="sxs-lookup"><span data-stu-id="cf782-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="cf782-p115">Come si è appena visto, è molto semplice da usare Office 365 PowerShell per assegnare una singola licenza a un singolo utente. E che favorisce una domanda ovvia: non sarebbero altrettanto semplice, potrebbe essere perfino più facile, utilizzare l'interfaccia di amministrazione di Office 365 per assegnare una singola licenza a un singolo utente? Beh, forse; che dipende in parte, se si è più comodo utilizzare Windows PowerShell o preferiscano utilizzando l'interfaccia di amministrazione di Office 365. Dove indicati Windows PowerShell, è tuttavia quando è necessario assegnare licenze più a più utenti. Ad esempio, questo comando assegna una licenza Office 365 a qualsiasi utente che dispone già di una licenza:</span><span class="sxs-lookup"><span data-stu-id="cf782-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="cf782-p116">Nel comando precedente vengono utilizzati **Get-MsolUser** e il parametro _UnlicensedUsersOnly_ per restituire una raccolta di tutti gli account utente senza licenza. La raccolta viene quindi passato al cmdlet **Set-MsolUserLicense** ; a sua volta, **Set-MsolUserLicense** consente di assegnare una licenza (derivato dal `litwareinc:ENTERPRISEPACK` piano di licenze) per ogni utente nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="cf782-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="cf782-p117">AH, ma se è necessario 5 utenti senza licenza ma solo una licenza disponibile? In questo caso **Set-MsolUserLicense** per ottenere la licenza disponibile per il primo utente restituito da **Get-MsolUser**. **Set-MsolUserLicense** quindi perdersi tenterà di assegnare una licenza a quattro utenti, ma tutte e quattro i tentativi di avrà esito negativo e il messaggio di errore seguente:</span><span class="sxs-lookup"><span data-stu-id="cf782-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="cf782-p118">In altri termini, Set-MsolUserLicense non appena esito negativo. In realtà, verrà assegnato il numero di licenze possa. Quindi non riuscirà.</span><span class="sxs-lookup"><span data-stu-id="cf782-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="cf782-p119">Punto provare un altro esempio. Se si desidera assegnare una licenza a tutti gli utenti del reparto vendite. Non c'è problema:</span><span class="sxs-lookup"><span data-stu-id="cf782-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="cf782-189">In alternativa, se vuoi rendere le cose più semplice e ridurre al minimo i messaggi di errori e l'elaborazione del computer, ti basterà assegnare una licenza agli utenti senza licenza del reparto Vendite:</span><span class="sxs-lookup"><span data-stu-id="cf782-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="cf782-p120">Dopo tutto, non esiste alcun punto tenta gli utenti con licenza che dispongono già di una licenza. Come già illustrato in precedenza, che non funzionano.</span><span class="sxs-lookup"><span data-stu-id="cf782-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="cf782-p121">Ecco un altro esempio. Si tratta di acquisizione della licenza per tutti gli utenti negli Stati Uniti che attualmente non dispongono di una licenza Office 365. In questo caso:</span><span class="sxs-lookup"><span data-stu-id="cf782-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="cf782-195">E così via.</span><span class="sxs-lookup"><span data-stu-id="cf782-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cf782-p122">Quanto tempo è necessario per eseguire un comando che, ad esempio, emette licenze per tutti gli utenti senza licenza? È difficile pronunciare: dipende da tutti gli elementi dal numero di utenti è necessario la velocità della connessione di rete. Se si dispone di due centinaia di utenti alla licenza questo verrà inoltrate ragionevolmente rapidamente (vale a dire non saranno necessarie più di uno o due minuti). Se si dispone di 10.000 utenti per la licenza ovviamente avrà più tempo. Ma lontano come dovrebbe seguire per assegnare licenze a 10.000 utenti utilizzando l'interfaccia di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="cf782-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="cf782-p123">Purché siamo sull'argomento, ecco è necessario apportare approfondire durante l'assegnazione delle licenze: se un utente non dispone di un valore configurato per la proprietà **UsageLocation** non sarà in grado di assegnare una licenza Office 365 a tale utente. Al contrario, verrà visualizzato un messaggio di errore simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="cf782-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="cf782-p124">In un po' rotonda, questo messaggio di errore indica che l'utente in questione non è stato assegnato un **UsageLocation**. Come è facile immaginare, la proprietà **UsageLocation** (che indica l'area o un paese in cui l'utente utilizza in genere Office 365) è estremamente importante. Perché? Poiché i servizi disponibili agli utenti dipendono non solo il pacchetto di licenze acquistate ma anche in residenza dell'utente: a causa di regole locali e le normative, alcuni servizi potrebbero non essere disponibile per alcuni utenti. Se un utente non dispone di un **UsageLocation**, Office 365 non avendo la possibilità di sapere quali servizi possono essere esposti regolarmente a tale utente. Pertanto, Office 365 non possono offrire eventuali servizi a tale utente almeno non fino a quando non è stato specificato **UsageLocation** .</span><span class="sxs-lookup"><span data-stu-id="cf782-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cf782-p125">Quando si configura un account utente significa immediatamente se esistono eventuali restrizioni associate alla parte specificata del mondo. Ad esempio, se si modifica l' **UsageLocation** per un utente con licenza in Iran ( `IR`), il comando non funzionerà con questo messaggio di errore: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> perché Office 365 non è attualmente disponibile per gli utenti in Iran. Per ulteriori informazioni, vedere [About restrizioni relative alla licenza](https://go.microsoft.com/fwlink/p/?LinkId=691730). Per inciso, Office 365 utilizza i codici di due lettere del paese prodotti da International Organization for Standardization (ISO). È possibile trovare i codici nel [sito web ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span><span class="sxs-lookup"><span data-stu-id="cf782-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="cf782-214">Se si desidera verificare che un utente specificato è un **UsageLocation** è possibile utilizzare un comando simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="cf782-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="cf782-215">In alternativa, è possibile restituire un elenco di tutti gli utenti che non possiedono l' **UsageLocation** mediante questo comando:</span><span class="sxs-lookup"><span data-stu-id="cf782-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="cf782-p126">Quando si assegna una licenza a un utente, l'utente, per impostazione predefinita, visualizzeranno l'accesso a tutti i servizi di Office 365 che dispone dell'accesso per l'organizzazione. Ad esempio, se è stato acquistato licenze per Office 365 Enterprise E3, l'utente con contratto multilicenza appena verrà automaticamente concessa accesso ai servizi quali Exchange Online, Skype per Business Online e SharePoint Online. Se si preferisce limitare l'accesso dell'utente a tali servizi (ad esempio, è possibile che un utente ad accedere a SharePoint Online ma *non* di Exchange Online e Skype Business online) quindi, vedere l'articolo [disattivare l'accesso ai servizi con Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="cf782-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="cf782-219">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="cf782-219">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="cf782-220">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cf782-220">See Also</span></span>
<span data-ttu-id="cf782-221"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="cf782-221"></span></span>

<span data-ttu-id="cf782-222">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="cf782-222">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="cf782-223">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf782-223">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="cf782-224">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf782-224">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="cf782-225">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf782-225">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="cf782-226">Rimuovere le licenze dagli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf782-226">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="cf782-227">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="cf782-227">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="cf782-228">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="cf782-228">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="cf782-229">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="cf782-229">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="cf782-230">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="cf782-230">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="cf782-231">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="cf782-231">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="cf782-232">Select-Object</span><span class="sxs-lookup"><span data-stu-id="cf782-232">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="cf782-233">Where-Object</span><span class="sxs-lookup"><span data-stu-id="cf782-233">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

