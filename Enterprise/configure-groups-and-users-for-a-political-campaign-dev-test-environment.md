---
title: Configurare gruppi e utenti per un ambiente di sviluppo/test per la campagna politica
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Riepilogo: Creare Office 365 e mobilità aziendale + sottoscrizioni di valutazione di sicurezza (EMS) con gli utenti e gruppi per un ambiente di sviluppo e di testing politici campagne."
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="443d3-103">Configurare gruppi e utenti per un ambiente di sviluppo/test per la campagna politica</span><span class="sxs-lookup"><span data-stu-id="443d3-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="443d3-104">**Riepilogo:** Creazione di Office 365 e mobilità aziendale + sottoscrizioni di valutazione di sicurezza (EMS) con gli utenti e gruppi per un ambiente di sviluppo e di testing politici campagne.</span><span class="sxs-lookup"><span data-stu-id="443d3-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="443d3-105">Utilizzare le istruzioni riportate in questo articolo per creare un ambiente di sviluppo e di testing che include gli account utente semplificata e gruppi per la soluzione [Microsoft Security Guidance for campagne politici, ricchi e altre organizzazioni Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) .</span><span class="sxs-lookup"><span data-stu-id="443d3-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="443d3-106">Fase 1: creare l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="443d3-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="443d3-107">In questa fase per ottenere le sottoscrizioni di valutazione di Office 365 E5 e mobilità aziendale + E5 di sicurezza (EMS) per le organizzazioni che rappresenta una campagna politica fittizia.</span><span class="sxs-lookup"><span data-stu-id="443d3-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="443d3-108">Per prima cosa, seguire le istruzioni nella **fase 2** dell' [ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="443d3-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="443d3-109">Successivamente, Esegui l'iscrizione per la sottoscrizione di prova EMS E5 e come aggiungerla alla stessa organizzazione la sottoscrizione di prova di Office 365.</span><span class="sxs-lookup"><span data-stu-id="443d3-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="443d3-p101">Se necessario, accedere al portale di Office 365 con le credenziali dell'account amministratore globale della sottoscrizione di prova. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="443d3-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="443d3-112">Fare clic sul riquadro **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="443d3-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="443d3-113">Scheda di **interfaccia di amministrazione di Office** nel browser, nel riquadro di spostamento sinistra fare clic su **fatturazione > servizi di acquisto**.</span><span class="sxs-lookup"><span data-stu-id="443d3-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="443d3-p102">Nella pagina **servizi di acquisto** individuare l'elemento di **sicurezza E5 + mobilità aziendale** . Posizionare il puntatore del mouse su di esso e fare clic su **Start versione di valutazione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="443d3-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="443d3-116">Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.</span><span class="sxs-lookup"><span data-stu-id="443d3-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="443d3-117">Nella pagina **Ricevuta ordine**, fare clic su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="443d3-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="443d3-118">Successivamente, abilitare la licenza E5 EMS per l'account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="443d3-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="443d3-119">Nella scheda **Centro di amministrazione di Office 365** nel browser, nel riquadro di spostamento sinistra fare clic su **utenti > utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="443d3-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="443d3-120">Fare clic sull'account di amministratore globale e quindi fare clic su **Modifica** per **le licenze del prodotto**.</span><span class="sxs-lookup"><span data-stu-id="443d3-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="443d3-121">Nel riquadro di **licenze per i prodotti** , attivare la licenza del prodotto per la **mobilità aziendale + E5 di sicurezza** per **in**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="443d3-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="443d3-122">Fase 2: Creare e configurare i gruppi di Azure Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="443d3-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="443d3-123">In questa fase, vengono creati e configurati i gruppi di Azure AD per la campagna.</span><span class="sxs-lookup"><span data-stu-id="443d3-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="443d3-124">Creare innanzitutto un insieme di gruppi per una campagna politico tipica con il portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="443d3-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="443d3-125">In una scheda distinta nel browser, accedere al portale di Azure in [https://portal.azure.com](https://portal.azure.com). Se necessario, accedere con le credenziali dell'account amministratore globale per la sottoscrizione di valutazione di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="443d3-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="443d3-126">Nel portale di Azure, fare clic su **Azure Active Directory > utenti e gruppi > tutti i gruppi di**.</span><span class="sxs-lookup"><span data-stu-id="443d3-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="443d3-127">Eseguire la procedura seguente per ogni nome di gruppo in questo elenco:</span><span class="sxs-lookup"><span data-stu-id="443d3-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="443d3-128">Personale senior e strategico</span><span class="sxs-lookup"><span data-stu-id="443d3-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="443d3-129">Personale IT</span><span class="sxs-lookup"><span data-stu-id="443d3-129">IT staff</span></span>
    
  - <span data-ttu-id="443d3-130">Personale di analisi</span><span class="sxs-lookup"><span data-stu-id="443d3-130">Analytics staff</span></span>
    
  - <span data-ttu-id="443d3-131">Personale di base regolare</span><span class="sxs-lookup"><span data-stu-id="443d3-131">Regular core staff</span></span>
    
  - <span data-ttu-id="443d3-132">Personale delle operazioni</span><span class="sxs-lookup"><span data-stu-id="443d3-132">Operations staff</span></span>
    
  - <span data-ttu-id="443d3-133">Personale di campo</span><span class="sxs-lookup"><span data-stu-id="443d3-133">Field staff</span></span>
    
1. <span data-ttu-id="443d3-134">Su blade **tutti i gruppi** , fare clic su **+ nuovo gruppo**.</span><span class="sxs-lookup"><span data-stu-id="443d3-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="443d3-135">Digitare il nome del gruppo dall'elenco **nome**.</span><span class="sxs-lookup"><span data-stu-id="443d3-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="443d3-136">Selezionare **utente dinamica** di **appartenenza**.</span><span class="sxs-lookup"><span data-stu-id="443d3-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="443d3-137">Fare clic su **Sì** per **caratteristiche di attivare Office**.</span><span class="sxs-lookup"><span data-stu-id="443d3-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="443d3-138">Fare clic su **Add query dinamica**.</span><span class="sxs-lookup"><span data-stu-id="443d3-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="443d3-139">In **aggiungere gli utenti cui**, selezionare **reparto**.</span><span class="sxs-lookup"><span data-stu-id="443d3-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="443d3-140">Nel campo successivo, selezionare **è uguale a**.</span><span class="sxs-lookup"><span data-stu-id="443d3-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="443d3-141">Nel campo successivo, digitare il nome del gruppo dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="443d3-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="443d3-142">Fare clic su **Add query**e quindi fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="443d3-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="443d3-143">Fare clic su **utenti e gruppi: tutti i gruppi**.</span><span class="sxs-lookup"><span data-stu-id="443d3-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="443d3-144">Punto, configurare i gruppi in modo che i membri vengono assegnati automaticamente le licenze di Office 365 E5 ed EMS E5.</span><span class="sxs-lookup"><span data-stu-id="443d3-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="443d3-145">Nel portale di Azure, fare clic su **Azure Active Directory > licenze > tutti i prodotti**.</span><span class="sxs-lookup"><span data-stu-id="443d3-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="443d3-146">Nell'elenco, selezionare **mobilità aziendale + sicurezza E5** e **Office 365 Enterprise E5**e quindi fare clic su **+ assegnare**.</span><span class="sxs-lookup"><span data-stu-id="443d3-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="443d3-147">In blade **assegnare licenze** , fare clic su **utenti e gruppi**.</span><span class="sxs-lookup"><span data-stu-id="443d3-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="443d3-148">Nell'elenco dei gruppi, selezionare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="443d3-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="443d3-149">Personale di analisi</span><span class="sxs-lookup"><span data-stu-id="443d3-149">Analytics staff</span></span>
    
  - <span data-ttu-id="443d3-150">Personale di campo</span><span class="sxs-lookup"><span data-stu-id="443d3-150">Field staff</span></span>
    
  - <span data-ttu-id="443d3-151">Personale IT</span><span class="sxs-lookup"><span data-stu-id="443d3-151">IT staff</span></span>
    
  - <span data-ttu-id="443d3-152">Personale delle operazioni</span><span class="sxs-lookup"><span data-stu-id="443d3-152">Operations staff</span></span>
    
  - <span data-ttu-id="443d3-153">Personale di base regolare</span><span class="sxs-lookup"><span data-stu-id="443d3-153">Regular core staff</span></span>
    
  - <span data-ttu-id="443d3-154">Personale senior e strategico</span><span class="sxs-lookup"><span data-stu-id="443d3-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="443d3-155">Fare clic su **Seleziona**e quindi fare clic su **Assegna**.</span><span class="sxs-lookup"><span data-stu-id="443d3-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="443d3-156">Chiudere la scheda del portale di Azure nel browser.</span><span class="sxs-lookup"><span data-stu-id="443d3-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="443d3-157">Fase 3: Aggiungere gli account utente</span><span class="sxs-lookup"><span data-stu-id="443d3-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="443d3-158">In questa fase, si aggiungono gli account utente di esempio per la campagna politica.</span><span class="sxs-lookup"><span data-stu-id="443d3-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="443d3-159">Innanzitutto, si [Connetti con il modulo di Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="443d3-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="443d3-160">Successivamente, inserire il nome dell'organizzazione, la posizione e una password comune; eseguire quindi questi comandi dal prompt dei comandi di PowerShell o Integrated Script Environment (ISE):</span><span class="sxs-lookup"><span data-stu-id="443d3-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="443d3-p103">L'utilizzo di una password di comune è per l'automazione e semplicità di configurazione per un ambiente di sviluppo e di testing. Ciò non è consigliata per le sottoscrizioni di produzione. Come si accede con ognuno di questi nuovi account utente, verrà richiesto di modificare la password.</span><span class="sxs-lookup"><span data-stu-id="443d3-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="443d3-164">Seguire questi passaggi per verificare che l'appartenenza ai gruppi dinamici e le licenze basate su gruppi funzionino correttamente.</span><span class="sxs-lookup"><span data-stu-id="443d3-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="443d3-165">Nella scheda **Home page di Microsoft Office** del browser, fare clic su tessera di **amministrazione** .</span><span class="sxs-lookup"><span data-stu-id="443d3-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="443d3-166">Dalla nuova scheda di **interfaccia di amministrazione di Office** del browser, fare clic su **utenti**.</span><span class="sxs-lookup"><span data-stu-id="443d3-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="443d3-167">Nell'elenco di utenti, fare clic su **candidato**.</span><span class="sxs-lookup"><span data-stu-id="443d3-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="443d3-168">Nel riquadro in cui sono elencati le proprietà dell'account utente **Candidate** , verificare che:</span><span class="sxs-lookup"><span data-stu-id="443d3-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="443d3-169">È un membro del gruppo **Senior e personale strategico** (in **appartenenza a gruppi**).</span><span class="sxs-lookup"><span data-stu-id="443d3-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="443d3-170">È stata assegnata la **mobilità aziendale + sicurezza E5** e **Office 365 Enterprise E5** licenze ( **licenze per i prodotti**).</span><span class="sxs-lookup"><span data-stu-id="443d3-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="443d3-171">Chiudere il riquadro di account utente **candidato** .</span><span class="sxs-lookup"><span data-stu-id="443d3-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="443d3-172">Registrare i valori per consultarli in futuro</span><span class="sxs-lookup"><span data-stu-id="443d3-172">Record values for future reference</span></span>

<span data-ttu-id="443d3-173">Registrare questi valori per utilizzarli con le sottoscrizioni di valutazione di Office 365 ed EMS per questo ambiente di sviluppo/test:</span><span class="sxs-lookup"><span data-stu-id="443d3-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="443d3-174">Nome dell'organizzazione della sottoscrizione di valutazione: _______________________________________________ </span><span class="sxs-lookup"><span data-stu-id="443d3-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="443d3-175">Ad esempio, per il nome di dominio della sottoscrizione di valutazione di contoso.onmicrosoft.com, il nome dell'azienda è "contoso".</span><span class="sxs-lookup"><span data-stu-id="443d3-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="443d3-176">Il nome di amministratore globale di Office 365: ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="443d3-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="443d3-177">Registrare la password per questo account e la password iniziale comune per gli altri account utente in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="443d3-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="443d3-178">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="443d3-178">Next step</span></span>

<span data-ttu-id="443d3-179">Creare quattro diversi tipi di siti del team SharePoint Online in questo ambiente di sviluppo e di testing e [creare siti del team in un ambiente di sviluppo e di testing politici campagne](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="443d3-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="443d3-180">See Also</span><span class="sxs-lookup"><span data-stu-id="443d3-180">See Also</span></span>

[<span data-ttu-id="443d3-181">Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili</span><span class="sxs-lookup"><span data-stu-id="443d3-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="443d3-182">Creare siti del team in un ambiente di sviluppo e di testing campagne politici</span><span class="sxs-lookup"><span data-stu-id="443d3-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="443d3-183">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="443d3-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="443d3-184">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="443d3-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




