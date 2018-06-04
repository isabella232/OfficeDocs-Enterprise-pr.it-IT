---
title: Proteggere i siti di SharePoint Online in un ambiente di sviluppo/test
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/17/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Riepilogo: creare siti del team di SharePoint Online pubblici, privati, riservati ed estremamente riservati in un ambiente di sviluppo/test.'
ms.openlocfilehash: fecb725999c7958dca1278c1236fcf251adc33cd
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193726"
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="28ab7-103">Proteggere i siti di SharePoint Online in un ambiente di sviluppo/test</span><span class="sxs-lookup"><span data-stu-id="28ab7-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="28ab7-104">**Riepilogo:** creare siti del team di SharePoint Online pubblici, privati, riservati ed estremamente riservati in un ambiente di sviluppo/test.</span><span class="sxs-lookup"><span data-stu-id="28ab7-104">Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="28ab7-105">Questo articolo contiene istruzioni dettagliate per la creazione di un ambiente di sviluppo e test che includa i quattro tipi diversi di sito del team di SharePoint Online per la [soluzione di protezione di siti e file di SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="28ab7-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files solution](secure-sharepoint-online-sites-and-files.md).</span></span>
  
![Tutti i quattro siti del team nell’ambiente di sviluppo/test protetto di SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="28ab7-107">Usare questo ambiente di sviluppo e test per sperimentare i comportamenti della protezione delle informazioni e ottimizzare le impostazioni in base alle esigenze specifiche prima di distribuire siti del team di SharePoint Online nell'ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="28ab7-108">Fase 1: Creare l'ambiente di sviluppo/test</span><span class="sxs-lookup"><span data-stu-id="28ab7-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="28ab7-109">In questa fase si ottengono le sottoscrizioni di valutazione per Office 365 ed Enterprise Mobility + Security per un'organizzazione fittizia.</span><span class="sxs-lookup"><span data-stu-id="28ab7-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="28ab7-110">Per prima cosa, seguire le istruzioni della **fase 2** nell'articolo relativo all'[ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="28ab7-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="28ab7-111">Iscriversi quindi per la sottoscrizione di valutazione di EMS e aggiungerla alla stessa organizzazione della sottoscrizione di prova di Office 365.</span><span class="sxs-lookup"><span data-stu-id="28ab7-111">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="28ab7-p101">Se necessario, accedere al portale di Office 365 con le credenziali dell'account amministratore globale della sottoscrizione di valutazione. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28ab7-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28ab7-114">Fare clic sul riquadro **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="28ab7-115">Nella scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Fatturazione > Servizi di acquisto** nel riquadro di spostamento di sinistra.</span><span class="sxs-lookup"><span data-stu-id="28ab7-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="28ab7-p102">Nella pagina **Acquisto di servizi**, individuare la voce **Enterprise Mobility + Security E5**. Posizionare il puntatore del mouse su di essa e fare clic su **Avvia la versione di valutazione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="28ab7-118">Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="28ab7-119">Nella pagina **Ricevuta ordine** fare clic su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="28ab7-120">Abilitare quindi la licenza Enterprise Mobility + Security E5 per l'account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="28ab7-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="28ab7-121">Nella scheda **Interfaccia di amministrazione di Office 365** del browser fare clic su **Utenti > Utenti attivi** nel riquadro di spostamento di sinistra.</span><span class="sxs-lookup"><span data-stu-id="28ab7-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="28ab7-122">Fare clic sull'account amministratore globale e quindi su **Modifica** per le **licenze del prodotto**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="28ab7-123">Nel riquadro **Licenze per i prodotti**, impostare la licenza per i prodotti di **Enterprise Mobility + Security E5** su **Attiva**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="28ab7-124">Fase 2: Creare e configurare i gruppi e gli utenti di Azure Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="28ab7-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="28ab7-125">In questa fase vengono creati e configurati i gruppi e gli utenti di Azure AD per l'organizzazione fittizia.</span><span class="sxs-lookup"><span data-stu-id="28ab7-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="28ab7-126">Innanzitutto, creare un set di gruppi per un'organizzazione tipica con il portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="28ab7-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="28ab7-127">Creare una scheda separata nel browser, quindi passare al portale di Azure all'indirizzo [https://portal.azure.com](https://portal.azure.com). Se necessario, accedere con le credenziali dell'account amministratore globale della sottoscrizione di valutazione di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="28ab7-127">Create a separate tab in your browser, and then go to the Azure portal at https://portal.azure.com. If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="28ab7-128">Nel portale di Azure fare clic su **Azure Active Directory > Gruppi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-128">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
3. <span data-ttu-id="28ab7-129">Nel pannello **Gruppi - Tutti i gruppi** fare clic su **+ Nuovo gruppo**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="28ab7-130">Nel pannello **Gruppo**:</span><span class="sxs-lookup"><span data-stu-id="28ab7-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="28ab7-131">Selezionare **Office 365** in **Tipo di gruppo**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-131">Select **Office 365** in **Group type**.</span></span>
    
  - <span data-ttu-id="28ab7-132">Digitare **C-Suite** in **Nome**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-132">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="28ab7-133">Selezionare **Assegnato** in **Tipo di appartenenza**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-133">Select **Assigned** in **Membership**.</span></span>
      
5. <span data-ttu-id="28ab7-134">Fare clic su **Crea** e quindi chiudere il pannello **Gruppo**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="28ab7-135">Ripetere i passaggi da 3 a 5 per i nomi dei gruppi seguenti:</span><span class="sxs-lookup"><span data-stu-id="28ab7-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="28ab7-136">IT staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-136">IT staff</span></span>
    
  - <span data-ttu-id="28ab7-137">Research staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-137">Research staff</span></span>
    
  - <span data-ttu-id="28ab7-138">Regular staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-138">Regular staff</span></span>
    
  - <span data-ttu-id="28ab7-139">Marketing staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-139">Marketing staff</span></span>
    
  - <span data-ttu-id="28ab7-140">Sales staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-140">Sales staff</span></span>
    
7. <span data-ttu-id="28ab7-141">Tenere aperta la scheda del portale di Azure nel browser.</span><span class="sxs-lookup"><span data-stu-id="28ab7-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="28ab7-142">Successivamente, si configurano le licenze automatiche in modo che ai membri dei gruppi vengano automaticamente assegnate le licenze per le sottoscrizioni di Office 365 ed EMS.</span><span class="sxs-lookup"><span data-stu-id="28ab7-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="28ab7-143">Nel portale di Azure fare clic su **Azure Active Directory > Licenze > Tutti i prodotti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="28ab7-144">Nell'elenco, selezionare **Enterprise Mobility + Security E5** e **Office 365 Enterprise E5**, quindi fare clic su **Assegna**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="28ab7-145">Nel pannello **Assegnare licenza** fare clic su **Utenti e gruppi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="28ab7-146">Nell'elenco dei gruppi selezionare gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="28ab7-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="28ab7-147">C-Suite</span><span class="sxs-lookup"><span data-stu-id="28ab7-147">C-Suite</span></span>
    
  - <span data-ttu-id="28ab7-148">IT staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-148">IT staff</span></span>
    
  - <span data-ttu-id="28ab7-149">Research staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-149">Research staff</span></span>
    
  - <span data-ttu-id="28ab7-150">Regular staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-150">Regular staff</span></span>
    
  - <span data-ttu-id="28ab7-151">Marketing staff</span><span class="sxs-lookup"><span data-stu-id="28ab7-151">Marketing staff</span></span>
    
  - <span data-ttu-id="28ab7-152">Personale addetto alle vendite</span><span class="sxs-lookup"><span data-stu-id="28ab7-152">Sales staff</span></span>
    
5. <span data-ttu-id="28ab7-153">Fare clic su **Seleziona**, quindi su **Assegna**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="28ab7-154">Chiudere la scheda del portale di Azure nel browser.</span><span class="sxs-lookup"><span data-stu-id="28ab7-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="28ab7-155">È quindi necessario [connettersi al modulo PowerShell di Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="28ab7-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="28ab7-156">Inserire il nome dell'organizzazione, la posizione e una password comune; eseguire quindi questi comandi dal prompt dei comandi di PowerShell o Integrated Script Environment (ISE) per creare account utente e aggiungerli ai rispettivi gruppi:</span><span class="sxs-lookup"><span data-stu-id="28ab7-156">Fill in your organization name, your location, and a common password. Run the following commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their corresponding groups.</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> <span data-ttu-id="28ab7-p103">L'utilizzo di una password comune in questo caso è per rendere automatica e facile la configurazione per un ambiente di sviluppo/test. Non è una scelta consigliata per sottoscrizioni di produzione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="28ab7-159">Seguire questi passaggi per verificare che le licenze basate su gruppo funzionino correttamente.</span><span class="sxs-lookup"><span data-stu-id="28ab7-159">Next, follow these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="28ab7-160">Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="28ab7-161">Dalla nuova scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Utenti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="28ab7-162">Fare clic su **CEO** nell'elenco degli utenti.</span><span class="sxs-lookup"><span data-stu-id="28ab7-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="28ab7-163">Nel riquadro in cui sono elencate le proprietà dell'account utente **CEO** verificare che all'account siano state assegnate le licenze **Enterprise Mobility + Security E5** e **Office 365 Enterprise E5** (nell'elenco delle **licenze del prodotto**).</span><span class="sxs-lookup"><span data-stu-id="28ab7-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="28ab7-164">Fase 3: Creare le etichette di Office 365</span><span class="sxs-lookup"><span data-stu-id="28ab7-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="28ab7-165">In questa fase vengono create le etichette per i diversi livelli di sicurezza per cartelle di documenti dei siti del team di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="28ab7-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="28ab7-p104">Se necessario, usare un'istanza privata del browser Internet e accedere al portale di Office 365 con l'account amministratore globale della sottoscrizione di valutazione di Office 365 E5. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28ab7-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28ab7-168">Dalla scheda **Microsoft Office Home** fare clic sul riquadro **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="28ab7-169">Dalla nuova scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Interfacce di amministrazione > Sicurezza e conformità**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="28ab7-170">Dalla nuova scheda **Home: Sicurezza e conformità** del browser fare clic su Classificazioni > Etichette.</span><span class="sxs-lookup"><span data-stu-id="28ab7-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="28ab7-171">Dal riquadro **Home > Etichette** fare clic su **Crea un'etichetta**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="28ab7-172">Nel riquadro **Name your label** (Denomina l'etichetta) digitare **Internal Public**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-172">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="28ab7-173">Nel riquadro **Label settings** (Importazioni etichetta) fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="28ab7-174">Nel riquadro **Verifica le impostazioni** fare clic su **Crea questa etichetta** e fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="28ab7-175">Ripetere i passaggi 5-8 per queste etichette aggiuntive:</span><span class="sxs-lookup"><span data-stu-id="28ab7-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="28ab7-176">Private</span><span class="sxs-lookup"><span data-stu-id="28ab7-176">Private</span></span>
    
  - <span data-ttu-id="28ab7-177">Dati sensibili</span><span class="sxs-lookup"><span data-stu-id="28ab7-177">Sensitive</span></span>
    
  - <span data-ttu-id="28ab7-178">Highly Confidential (Riservatezza elevata)</span><span class="sxs-lookup"><span data-stu-id="28ab7-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="28ab7-179">Dal riquadro **Home > Etichette** fare clic su **Publish labels** (Pubblica etichette).</span><span class="sxs-lookup"><span data-stu-id="28ab7-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="28ab7-180">Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Choose labels to publish** (Scegli etichette da pubblicare).</span><span class="sxs-lookup"><span data-stu-id="28ab7-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="28ab7-181">Nel riquadro **Choose labels** (Scegli etichette) fare clic su **Aggiungi** e selezionare le quattro etichette.</span><span class="sxs-lookup"><span data-stu-id="28ab7-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="28ab7-182">Fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="28ab7-183">Nel riquadro **Choose labels to publish** (Scegli etichette da pubblicare) fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="28ab7-184">Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="28ab7-185">Nel riquadro **Denomina il criterio** digitare **Example organization** in **Nome**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-185">On the **Name your policy** pane, type **Example organization** in **Name**, and click **Next**.</span></span>
    
17. <span data-ttu-id="28ab7-186">Nel riquadro **Verifica le impostazioni** fare clic su **Publish labels** (Pubblica etichette), quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="28ab7-187">Fase 4: creare i siti del team di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="28ab7-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="28ab7-188">In questa fase vengono creati e configurati i quattro tipi di siti del team di SharePoint Online per l'organizzazione di esempio.</span><span class="sxs-lookup"><span data-stu-id="28ab7-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="28ab7-189">Sito del team per l'intera organizzazione</span><span class="sxs-lookup"><span data-stu-id="28ab7-189">Organization wide team site</span></span>

<span data-ttu-id="28ab7-190">Per creare un sito pubblico iniziale per il team di SharePoint Online, eseguire queste operazioni:</span><span class="sxs-lookup"><span data-stu-id="28ab7-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="28ab7-p105">Se necessario, usare un browser sul computer locale e accedere al portale di Office 365 con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28ab7-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28ab7-193">Nell'elenco dei riquadri fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28ab7-194">Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="28ab7-195">Nella pagina **Crea un sito** fare clic su **Sito del team**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="28ab7-196">In **Nome sito** digitare **Organization wide**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="28ab7-197">Come **descrizione del sito del team** digitare **Sito SharePoint per l'intera organizzazione**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="28ab7-198">In **Impostazioni privacy** selezionare **Public – anyone in the organization can access this site** (Pubblico: qualsiasi persona dell'organizzazione può accedere a questo sito) e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28ab7-199">Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="28ab7-200">Configurare quindi la cartella dei documenti del sito del team dell'intera organizzazione per l'etichetta Internal Public.</span><span class="sxs-lookup"><span data-stu-id="28ab7-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="28ab7-201">Nella scheda **Organization wide - Home** (A livello di organizzazione - Home) del browser fare clic su **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-201">In the **Organization wide–Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="28ab7-202">Fare clic sull'icona delle impostazioni e selezionare **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="28ab7-203">In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).</span><span class="sxs-lookup"><span data-stu-id="28ab7-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="28ab7-204">In **Impostazioni: Applica etichetta** selezionare **Internal Public**, quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-204">In **Settings-Apply Label**, select **Internal Public**, and click **Save**.</span></span>
    
<span data-ttu-id="28ab7-205">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="28ab7-205">Here is your resulting configuration.</span></span>
  
![Protezione di livello di base per il sito del team di SharePoint Online pubblico a livello dell’organizzazione.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="28ab7-207">Sito del team Project 1</span><span class="sxs-lookup"><span data-stu-id="28ab7-207">Project 1 team site</span></span>

<span data-ttu-id="28ab7-208">Per creare un sito del team SharePoint Online privato iniziale per un progetto all'interno dell'organizzazione, eseguire queste operazioni:</span><span class="sxs-lookup"><span data-stu-id="28ab7-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="28ab7-p106">Se necessario, usare un browser sul computer locale e accedere al portale di Office 365 con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28ab7-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28ab7-211">Nell'elenco dei riquadri fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28ab7-212">Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="28ab7-213">Nella pagina **Crea un sito** fare clic su **Sito del team**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="28ab7-214">In **Nome del sito** digitare **Project 1**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="28ab7-215">Come **descrizione del sito del team** digitare **Sito SharePoint per Project 1**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-215">In **Team site description**, type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="28ab7-216">In **Impostazioni privacy** selezionare **Private - only members can access this site** (Privato: solo i membri possono accedere a questo sito) e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28ab7-217">Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="28ab7-218">Configurare quindi la cartella dei documenti del sito del team Project 1 per l'etichetta Private.</span><span class="sxs-lookup"><span data-stu-id="28ab7-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="28ab7-219">Nella scheda **Project 1: Home** del browser fare clic su **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="28ab7-220">Fare clic sull'icona delle impostazioni e selezionare **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="28ab7-221">In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).</span><span class="sxs-lookup"><span data-stu-id="28ab7-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="28ab7-222">In **Impostazioni - Applica etichetta**, selezionare **Privato** e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="28ab7-223">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="28ab7-223">Here is your resulting configuration.</span></span>
  
![Protezione di livello di base per il sito del team di SharePoint Online privato Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="28ab7-225">Sito del team delle campagne di marketing</span><span class="sxs-lookup"><span data-stu-id="28ab7-225">Marketing campaigns team site</span></span>

<span data-ttu-id="28ab7-226">Per creare un sito del team di SharePoint Online isolato per i dati sensibili delle risorse della campagna di marketing, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="28ab7-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="28ab7-p107">Usando un browser sul computer locale, accedere al portale di Office 365 con il proprio account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28ab7-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28ab7-229">Nell'elenco dei riquadri fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28ab7-230">Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="28ab7-231">Nella pagina **Crea un sito** fare clic su **Sito del team**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="28ab7-232">Come **nome del sito del team** digitare **Marketing campaigns**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="28ab7-233">Come **descrizione del sito del team** digitare **SharePoint site for marketing campaign resources (sensitive)** (Sito SharePoint per le risorse delle campagne marketing - dati sensibili).</span><span class="sxs-lookup"><span data-stu-id="28ab7-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="28ab7-234">In **Impostazioni privacy** selezionare **Private - only members can access this site** (Privato: solo i membri possono accedere a questo sito) e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28ab7-235">Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="28ab7-236">Nella nuova scheda **Campagne marketing** visualizzata nel browser, nella barra degli strumenti fare clic sull'icona delle impostazioni, quindi su **Autorizzazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-236">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="28ab7-237">Nel riquadro **Autorizzazioni sito** fare clic su **Advanced permissions settings** (Impostazioni autorizzazioni avanzate).</span><span class="sxs-lookup"><span data-stu-id="28ab7-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="28ab7-238">Nella nuova scheda **Autorizzazioni** del browser fare clic su **Impostazioni richieste di accesso**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="28ab7-239">Nella finestra di dialogo **Impostazioni richieste di accesso** deselezionare le caselle di controllo **Consenti ai membri di condividere il sito e singoli file e cartelle** e **Consenti ai membri di invitare altre persone nel gruppo di membri del sito**; digitare **ITAdmin1@**\<nome dell'organizzazione>**.onmicrosoft.com** in **Invia tutte le richieste di accesso**, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-239">In the Access Request Settings dialog box, clear the Allow members to share the site and individual files and folders and Allow members to invite others to the site members group check boxes, type ITAdmin1@<your organization name>.onmicrosoft.com in Send all requests for access, and then click OK.</span></span>
    
13. <span data-ttu-id="28ab7-240">Fare clic su **Marketing campaigns - Members** (Campagne di marketing - Membri) nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="28ab7-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="28ab7-241">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="28ab7-242">Nella finestra di dialogo **Condividi** digitare **Personale addetto al marketing**, selezionarlo e quindi fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-242">In the **Share** dialog box, type **Marketing staff**, select it, and click **Share**.</span></span>
    
16. <span data-ttu-id="28ab7-243">Ripetere i passaggi 14 e 15 per l'account utente **Researcher1**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-243">Repeat steps 14 and 15 for the **Analytics staff** group and the Regular1 user account.</span></span>
    
17. <span data-ttu-id="28ab7-244">Fare clic sul pulsante Indietro del browser.</span><span class="sxs-lookup"><span data-stu-id="28ab7-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="28ab7-245">Fare clic su **Marketing campaigns - Owners** (Campagne di marketing - Proprietari) nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="28ab7-245">Click **Marketing campaigns Members** in the list.</span></span>
    
19. <span data-ttu-id="28ab7-246">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="28ab7-247">Nella finestra di dialogo **Condividi**, digitare **Staff IT**, selezionarlo e quindi fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="28ab7-248">Fare clic sul pulsante Indietro del browser.</span><span class="sxs-lookup"><span data-stu-id="28ab7-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="28ab7-249">Chiudere la scheda **Utenti e gruppi** visualizzata nel browser, fare clic sulla scheda **Marketing campaigns-Home** (Campagne di marketing - Home), quindi chiudere il riquadro **Autorizzazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-249">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="28ab7-250">Ecco i risultati della configurazione delle autorizzazioni:</span><span class="sxs-lookup"><span data-stu-id="28ab7-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="28ab7-251">Il gruppo **Marketing campaigns - Members** (Campagne di marketing - Membri) di SharePoint contiene solo il gruppo **Marketing campaigns**, che contiene l'account utente amministratore globale, il gruppo **Marketing staff**, che contiene gli account utente Marketing1 e Marketing2, e l'account utente **Researcher1**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="28ab7-252">Il gruppo **Marketing campaigns - Owners** (Campagne di marketing - Proprietari) di SharePoint contiene solo il gruppo **IT staff**, che a sua volta contiene solo gli account utente ITAdmin1 e ITAdmin2.</span><span class="sxs-lookup"><span data-stu-id="28ab7-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="28ab7-253">Il gruppo **Marketing campaigns - Visitors** (Campagne di marketing - Visitatori) di SharePoint non contiene gruppi né account utente.</span><span class="sxs-lookup"><span data-stu-id="28ab7-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="28ab7-254">I membri non possono modificare le autorizzazioni a livello di sito, operazione che può essere eseguita solo dai membri del gruppo **Marketing campaigns - Owners**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="28ab7-255">Altri account utente non possono accedere al sito o alle sue risorse, ma possono richiedere l'accesso al sito, che invierà un'e-mail alla cassetta postale dell'account utente ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="28ab7-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="28ab7-256">Successivamente, configurare la cartella dei documenti del sito del team Campagne marketing per l'etichetta Riservato.</span><span class="sxs-lookup"><span data-stu-id="28ab7-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="28ab7-257">Nella scheda **Marketing campaigns - Home** (Campagne di marketing - Home) del browser fare clic su **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="28ab7-258">Fare clic sull'icona delle impostazioni e selezionare **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="28ab7-259">In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).</span><span class="sxs-lookup"><span data-stu-id="28ab7-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="28ab7-260">In **Impostazioni - Applica etichetta** selezionare **Riservato** e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="28ab7-261">Configurare quindi un criterio di prevenzione della perdita di dati che informa gli utenti quando condividono un documento presente su un sito del team di SharePoint Online con etichetta Sensitive, incluso il sito Marketing campaigns, all'esterno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="28ab7-262">Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Sicurezza &amp; Conformità**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="28ab7-263">Nella nuova scheda **Sicurezza e conformità** del browser fare clic su **Prevenzione perdita dati > Criterio**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="28ab7-264">Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="28ab7-265">Nel riquadro **Inizia con un modello o crea un criterio personalizzato**, fare clic su **Personalizza**, quindi su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="28ab7-266">Nel riquadro **Denomina il criterio**, digitare **Siti del team di SharePoint Online con etichetta Riservato** in **Nome**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="28ab7-267">Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="28ab7-268">Nell'elenco di località, disabilitare le località **Posta elettronica di Exchange** e **Account di OneDrive**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28ab7-269">Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="28ab7-270">Nel riquadro per **scegliere i tipi di contenuto da proteggere**, fare clic su **Aggiungi** nella casella di riepilogo a discesa, quindi fare clic su **Etichette**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="28ab7-271">Nel riquadro **Etichette**, fare clic su **+ Aggiungi**, selezionare l’etichetta **Riservato** fare clic su **Aggiungi**, quindi fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="28ab7-272">Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="28ab7-273">Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="28ab7-274">Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) fare clic su **Customize the tip and email** (Personalizza suggerimento e messaggio di posta elettronica).</span><span class="sxs-lookup"><span data-stu-id="28ab7-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="28ab7-275">Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).</span><span class="sxs-lookup"><span data-stu-id="28ab7-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="28ab7-276">Nella casella di testo digitare o incollare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="28ab7-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="28ab7-p108">Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="28ab7-280">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="28ab7-281">Nel riquadro **Quale operazione eseguire se vengono rilevate informazioni riservate?**, deselezionare la casella di testo per **bloccare la condivisione e limitare l'accesso al contenuto condiviso**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="28ab7-282">Nel riquadro **Abilitare il criterio o eseguire prima un test?**, fare clic su **Sì, abilitarlo immediatamente**, quindi su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="28ab7-283">Nel riquadro **Verifica le impostazioni** fare clic su **Crea** e quindi su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="28ab7-284">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="28ab7-284">Here is your resulting configuration.</span></span>
  
![Protezione di livello sensibile per il sito del team di SharePoint Online isolato delle campagne di marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="28ab7-286">Sito del team di strategia aziendale</span><span class="sxs-lookup"><span data-stu-id="28ab7-286">Company strategy team site</span></span>

<span data-ttu-id="28ab7-287">Per creare un sito del team di SharePoint Online isolato per i dati altamente riservati delle risorse aziendali strategiche dei dirigenti dell'organizzazione, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="28ab7-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="28ab7-p109">Se necessario, usare un browser sul computer locale e accedere al portale di Office 365 con l'account amministratore globale. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28ab7-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28ab7-290">Nell'elenco dei riquadri fare clic su **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28ab7-291">Nella nuova scheda **SharePoint** del browser fare clic su + **Crea sito**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="28ab7-292">Nella pagina **Crea sito** fare clic su **Sito del team**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="28ab7-293">Come **nome del sito del team** digitare **Company strategy** (Strategia aziendale).</span><span class="sxs-lookup"><span data-stu-id="28ab7-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="28ab7-294">Come **descrizione del sito del team** digitare **Sito di SharePoint per la strategia aziendale - Informazioni altamente riservate**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="28ab7-295">In **Impostazioni privacy** selezionare **Private - only members can access this site** (Privato: solo i membri possono accedere a questo sito) e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28ab7-296">Nel riquadro **Who do you want to add?** (Chi si desidera aggiungere?) fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="28ab7-297">Nella nuova scheda **Strategia aziendale** visualizzata nel browser fare clic sull'icona delle impostazioni nella barra degli strumenti, quindi su **Autorizzazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-297">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="28ab7-298">Nel riquadro **Autorizzazioni sito** fare clic su **Advanced permissions settings** (Impostazioni autorizzazioni avanzate).</span><span class="sxs-lookup"><span data-stu-id="28ab7-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="28ab7-299">Nella nuova scheda **Autorizzazioni** del browser fare clic su **Impostazioni richieste di accesso**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="28ab7-300">Nella finestra di dialogo **Impostazioni richieste di accesso**, deselezionare **Consenti ai membri di condividere il sito e singoli file e cartelle** e **Consenti ai membri di invitare altre persone nel gruppo di membri del sito** (le tre caselle di controllo devono essere deselezionate), quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="28ab7-301">Fare clic su **Membri strategia aziendale** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="28ab7-301">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="28ab7-302">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="28ab7-303">Nella finestra di dialogo **Condividi** digitare **C-Suite**, selezionarlo e quindi fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-303">In the **Share** dialog box, type **C-Suite**, select it, and click **Share**.</span></span>
    
16. <span data-ttu-id="28ab7-304">Fare clic su **Proprietari strategia aziendale** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="28ab7-304">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="28ab7-305">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="28ab7-306">Nella finestra di dialogo **Condividi**, digitare **Staff IT**, selezionarlo e quindi fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="28ab7-307">Fare clic sul pulsante Indietro del browser.</span><span class="sxs-lookup"><span data-stu-id="28ab7-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="28ab7-308">Chiudere la scheda **Utenti e gruppi** visualizzata nel browser, fare clic sulla scheda **Strategia aziendale-Home**, quindi chiudere il riquadro **Autorizzazioni sito**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-308">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="28ab7-309">Ecco i risultati della configurazione delle autorizzazioni:</span><span class="sxs-lookup"><span data-stu-id="28ab7-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="28ab7-310">Il gruppo **Company strategy - Members** (Strategia aziendale - Membri) di SharePoint contiene solo il gruppo **C-Suite**, che contiene solo gli account utente CEO, CFO e CIO, e il gruppo **Company strategy**, che contiene solo l'account utente amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="28ab7-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="28ab7-311">Il gruppo **Strategia aziendale - Proprietari** di SharePoint contiene solo il gruppo **IT staff**, che a sua volta contiene solo gli account utente ITAdmin1 e ITAdmin2.</span><span class="sxs-lookup"><span data-stu-id="28ab7-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="28ab7-312">Il gruppo **Strategia aziendale - Visitatori** di SharePoint non contiene gruppi né account utente.</span><span class="sxs-lookup"><span data-stu-id="28ab7-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="28ab7-313">I membri non possono modificare le autorizzazioni a livello di sito, operazione che può essere eseguita solo dai membri del gruppo **Company strategy - Owners**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="28ab7-p110">Gli altri account utente non possono accedere al sito o alle relative risorse né richiedere l'accesso al sito. Le autorizzazioni aggiuntive per il sito devono essere eseguite dall'amministratore globale o da un membro del gruppo **Company strategy - Owners**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="28ab7-316">Successivamente, configurare la cartella dei documenti del sito del team Strategia aziendale per l'etichetta Estremamente riservato.</span><span class="sxs-lookup"><span data-stu-id="28ab7-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="28ab7-317">Nella scheda **Strategia aziendale - Home** del browser fare clic su **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="28ab7-318">Fare clic sull'icona delle impostazioni e selezionare **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="28ab7-319">In **Autorizzazioni e gestione** fare clic su **Apply label to items in this library** (Applica etichetta agli elementi in questa libreria).</span><span class="sxs-lookup"><span data-stu-id="28ab7-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="28ab7-320">In **Impostazioni - Applica etichetta**, selezionare **Estremamente riservato** e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="28ab7-321">Configurare un criterio di prevenzione della perdita di dati che blocchi gli utenti quando condividono un documento presente su un sito del team di SharePoint Online con etichetta Highly Confidential, incluso il sito Company strategy, all'esterno dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="28ab7-p111">Se necessario, usare un browser nel computer locale e accedere al portale di Office 365 con un account con il ruolo Amministratore della sicurezza o Amministratore società. Per informazioni, vedere [Dove accedere a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28ab7-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28ab7-324">Dalla scheda **Microsoft Office Home** del browser fare clic sul riquadro **Sicurezza &amp; Conformità**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="28ab7-325">Nella nuova scheda **Sicurezza e conformità** del browser fare clic su **Prevenzione perdita dati > Criterio**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="28ab7-326">Nel riquadro **Prevenzione perdita dati** fare clic su **+ Crea un criterio**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="28ab7-327">Nel riquadro **Inizia con un modello o crea un criterio personalizzato**, fare clic su **Personalizza**, quindi su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="28ab7-328">Nel riquadro **Denomina il criterio**, digitare **Siti del team di SharePoint Online con etichetta Estremamente riservato** in **Nome**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="28ab7-329">Nel riquadro **Choose locations** (Scegli posizioni) fare clic su **Let me choose specific locations** (Consenti di scegliere posizioni specifiche) e fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="28ab7-330">Nell'elenco di località, disabilitare le località **Posta elettronica di Exchange** e **Account di OneDrive**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="28ab7-331">Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="28ab7-332">Nel riquadro per **scegliere i tipi di contenuto da proteggere**, fare clic su **Aggiungi** nella casella di riepilogo a discesa, quindi fare clic su **Etichette**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="28ab7-333">Nel riquadro **Etichette**, fare clic su **+ Aggiungi**, selezionare l’etichetta **Estremamente riservato**, fare clic su **Aggiungi**, quindi fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="28ab7-334">Nel riquadro **Choose the types of content to protect** (Scegli i tipi di contenuto da proteggere) fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="28ab7-335">Nel riquadro **Customize the types of sensitive info you want to protect** (Personalizza i tipi di informazioni sensibili da proteggere) fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="28ab7-336">Nel riquadro **What do you want to do if we detect sensitive info?** (Selezionare come procedere in caso di informazioni sensibili rilevate) fare clic su **Customize the tip and email** (Personalizza suggerimento e messaggio di posta elettronica).</span><span class="sxs-lookup"><span data-stu-id="28ab7-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="28ab7-337">Nel riquadro **Customize policy tips and email notifications** (Personalizza i suggerimenti per i criteri e le notifiche tramite posta elettronica) fare clic su **Customize the policy tip text** (Personalizza testo suggerimento per criterio).</span><span class="sxs-lookup"><span data-stu-id="28ab7-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="28ab7-338">Nella casella di testo digitare o incollare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="28ab7-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="28ab7-p112">Per condividere con un utente esterno all'organizzazione, scaricare il file e quindi aprirlo. Fare clic su File, Proteggi documento, Crittografa con password, quindi specificare una password complessa. Inviare la password in un'e-mail separata o con altri mezzi di comunicazione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="28ab7-342">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="28ab7-343">Nel riquadro **Quale operazione eseguire se vengono rilevate informazioni riservate?**, selezionare l’opzione per **richiedere motivazioni aziendali per eseguire l'override**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="28ab7-344">Nel riquadro **Abilitare il criterio o eseguire prima un test?**, fare clic su **Sì, abilitarlo immediatamente**, quindi su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="28ab7-345">Nel riquadro **Verifica le impostazioni** fare clic su **Crea** e quindi su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="28ab7-346">Seguire quindi le istruzioni in [Attivare Azure RMS dall'interfaccia di amministrazione di Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="28ab7-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="28ab7-347">Successivamente, configurare Azure Information Protection con nuovi criteri e un'etichetta secondaria con ambito per il gruppo C-Suite per la protezione e le autorizzazioni con la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="28ab7-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="28ab7-p113">Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="28ab7-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="28ab7-350">In un'altra scheda del browser, accedere al portale di Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="28ab7-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="28ab7-351">Se è la prima volta che viene configurato Azure Information Protection, consultare queste [istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="28ab7-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="28ab7-352">Nel riquadro dell'elenco, fare clic su **Ulteriori servizi**, digitare **Informazioni**, quindi fare clic su **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>

5. <span data-ttu-id="28ab7-353">Fare clic su **Etichette**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-353">Click **Labels**.</span></span>
    
6. <span data-ttu-id="28ab7-354">Fare clic con il pulsante destro del mouse sull'etichetta **Estremamente riservato**, quindi su **Aggiungi un'etichetta secondaria**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-354">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
7. <span data-ttu-id="28ab7-355">Digitare **Membri C-Suite** in **Nome** e **Descrizione**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-355">Type **C-Suite members** in **Name** and **Description**.</span></span>
    
8. <span data-ttu-id="28ab7-356">In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-356">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
9. <span data-ttu-id="28ab7-357">Nella sezione **Protezione** fare clic su **Azure (chiave cloud)**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-357">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
10. <span data-ttu-id="28ab7-358">Nel pannello **Protezione** fare clic su **+ Aggiungi autorizzazioni** in **Impostazioni di protezione**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-358">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
11. <span data-ttu-id="28ab7-359">Nel pannello **Aggiungi autorizzazioni**, in **Specifica utenti e gruppi** fare clic su **+ Sfoglia la directory**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-359">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
12. <span data-ttu-id="28ab7-360">Nel riquadro **Utenti e gruppi di AAD** selezionare **C-Suite** e quindi fare clic su **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-360">On the **AAD Users and Groups** pane, select **C-Suite**, and click **Select**.</span></span>
    
13. <span data-ttu-id="28ab7-361">In **Scegliere le autorizzazioni dal set di impostazioni o imposta personalizzato** fare clic su **Personalizza**, quindi sulla casella **Visualizza diritti**, **Modifica contenuto**, ** Salva**, **Rispondi** e **Rispondi a tutti**</span><span class="sxs-lookup"><span data-stu-id="28ab7-361">Under **Choose permissions from the preset or set custom**, click **Custom**, and then click the **View Rights**, **Edit Content**, **Save**, **Reply**, and **Reply all** check boxes.</span></span>
    
14. <span data-ttu-id="28ab7-362">Fare due volte clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-362">Click **OK** twice.</span></span>
    
15. <span data-ttu-id="28ab7-363">Nel pannello **Etichetta secondaria** fare clic su **Salva**, quindi su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-363">On the **Sub-label** blade, click **Save**, and then click **OK**.</span></span>

16. <span data-ttu-id="28ab7-364">Nel pannello **Azure Information Protection** fare clic su **Criteri > + Aggiungi un nuovo criterio**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-364">On the **Azure Information protection** blade, click **Scoped policies > + Add a new policy**.</span></span>
    
17. <span data-ttu-id="28ab7-365">Digitare **CompanyStrategy** in **Nome criterio** ed **Etichetta per i documenti nel sito del team di strategia aziendale** in **Descrizione**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-365">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
18. <span data-ttu-id="28ab7-366">Fare clic su **Selezionare gli utenti o i gruppi a cui viene applicato il criterio > Utenti/Gruppi**, quindi selezionare **C-Suite**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-366">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
19. <span data-ttu-id="28ab7-367">Fare clic su **Seleziona > OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-367">Click **Select > OK**.</span></span>

20. <span data-ttu-id="28ab7-p114">Fare clic su **Aggiungi o rimuovi etichette**. Nel riquadro **Criteri: Aggiungere o rimuovere etichette** fare clic su **C-Suite**, quindi su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-p114">Click **Add or remove labels**. In the **Policy: Add or remove labels** pane, click **C-Suite**, and then click **OK**.</span></span>   

21. <span data-ttu-id="28ab7-370">Fare clic su **Salva**, quindi su **OK**.</span><span class="sxs-lookup"><span data-stu-id="28ab7-370">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="28ab7-371">Per proteggere un documento con Azure Information Protection e la nuova etichetta, è necessario [installare il client di Azure Information Protection in un computer di test](https://docs.microsoft.com/information-protection/rms-client/install-client-app), installare Office dal portale di Office 365 e quindi accedere da Microsoft Word con un account del gruppo **C-Suite** della sottoscrizione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-371">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
<span data-ttu-id="28ab7-372">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="28ab7-372">Here is your resulting configuration.</span></span>
  
![Protezione di livello estremamente riservato per un sito del team di SharePoint Online isolato di strategia aziendale.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="28ab7-374">A questo punto si è pronti a creare documenti in questi quattro siti e a testare l'accesso ai siti usando diversi account utente della sottoscrizione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-374">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="28ab7-375">Di seguito è riportata la configurazione completa per tutti i quattro siti del team di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="28ab7-375">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Tutti i quattro siti del team nell’ambiente di sviluppo/test protetto di SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="28ab7-377">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="28ab7-377">Next step</span></span>

<span data-ttu-id="28ab7-378">Quando si è pronti per la distribuzione di produzione dei siti di SharePoint Online protetti, vedere [Proteggere siti e file di SharePoint Online](secure-sharepoint-online-sites-and-files.md) per informazioni dettagliate e collegamenti ad articoli relativi alle procedure di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="28ab7-378">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="28ab7-379">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="28ab7-379">See Also</span></span>

[<span data-ttu-id="28ab7-380">Protezione di file e siti di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="28ab7-380">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="28ab7-381">Soluzioni di sicurezza</span><span class="sxs-lookup"><span data-stu-id="28ab7-381">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="28ab7-382">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="28ab7-382">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="28ab7-383">Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili</span><span class="sxs-lookup"><span data-stu-id="28ab7-383">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




