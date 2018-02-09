---
title: "Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Riepilogo: Configurare e illustrare come Information Rights Management di Office 365 consente di proteggere i file riservati, anche quando vengono registrate per la raccolta siti di SharePoint Online non corretto.'
ms.openlocfilehash: 388eb2a6288fc72771b6a554d1c9de78febe8a4e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="5a1ef-103">Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="5a1ef-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="5a1ef-104">**Riepilogo:** Configurare e illustrare come Information Rights Management di Office 365 consente di proteggere i file riservati, anche quando vengono registrate per la raccolta siti di SharePoint Online non corretto.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="5a1ef-p101">Information Rights Management (IRM) in Office 365 è un set di funzionalità per proteggere i documenti che vengono scaricati dalle raccolte e dagli elenchi di SharePoint Online. I file scaricati vengono crittografati e includono le autorizzazioni per aprire, copiare, salvare e stampare che riflettono la raccolta di SharePoint Online in cui sono stati salvati.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="5a1ef-107">Con le istruzioni disponibili in questo articolo, è possibile abilitare e testare Information Rights Management in Office 365 per i file contenenti possibili informazioni riservate nella sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="5a1ef-108">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="5a1ef-109">Fase 1: creare l'ambiente di sviluppo/testing di Office 365</span><span class="sxs-lookup"><span data-stu-id="5a1ef-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="5a1ef-110">Se si desidera testare protezione file riservati in un modo semplice con i requisiti minimi, seguire le istruzioni in fasi 2 e 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="5a1ef-111">Se si desidera testare protezione file riservati in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="5a1ef-p102">Il test della protezione dei file sensibili non richiede l'ambiente di sviluppo/testing aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione directory per una foresta di Windows Server AD. Questo test viene fornito qui come opzione in modo per consentire di testare la protezione dei file sensibili e sperimentarla in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="5a1ef-114">Fase 2: dimostrare in che modo i documenti dei siti protetti possono andare persi</span><span class="sxs-lookup"><span data-stu-id="5a1ef-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="5a1ef-115">In questa fase si dimostra che un utente può scaricare un documento da un sito protetto da autorizzazioni e quindi caricarlo in un sito con autorizzazioni aperte.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="5a1ef-116">È innanzitutto necessario aggiungere tre nuovi account utente che rappresentano i dirigenti e assegnare loro le licenze di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="5a1ef-117">Utilizzare le istruzioni riportate in [connessione a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) per installare i moduli di PowerShell (se necessario) e connettersi a tua nuova sottoscrizione di Office 365 da:</span><span class="sxs-lookup"><span data-stu-id="5a1ef-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="5a1ef-118">Dal computer (per l'ambiente di sviluppo/test di Office 365 leggero).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="5a1ef-119">Dalla macchina virtuale CLIENT1 (per l'ambiente di sviluppo/test di Office 365 aziendale simulato).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="5a1ef-120">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il nome di amministratore globale di Office 365 (esempio: jdoe@contosotoycompany.onmicrosoft.com) e la password dell'abbonamento prova Office 365.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="5a1ef-121">Immettere il nome dell'organizzazione (ad esempio: contosotoycompany) e il prefisso internazionale a due caratteri, quindi eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5a1ef-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="5a1ef-122">La visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account di amministratore delegato e registrarlo in un percorso sicuro.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="5a1ef-123">Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5a1ef-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="5a1ef-124">Dalla visualizzazione del comando **New-MsolUser** , tenere presente la password generata per l'account di amministratore e registrarlo in un percorso sicuro.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="5a1ef-125">Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5a1ef-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="5a1ef-126">Dalla visualizzazione del comando **New-MsolUser** , tenere presente la password generata per l'account COO e registrarlo in un percorso sicuro.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="5a1ef-127">Successivamente, si crea un gruppo di dirigenti privato e vi si aggiungono i nuovi account dirigente.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="5a1ef-128">Nel browser, accedere al portale di Office in [http://portal.office.com](http://portal.office.com) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="5a1ef-129">Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, aprire una sessione privata di Internet Explorer o del proprio browser e accedere dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="5a1ef-130">Se è in uso l'ambiente di sviluppo/test di Office 365 aziendale simulato, utilizzare il Portale di Azure per connettersi alla macchina virtuale CLIENT1, quindi accedere da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="5a1ef-131">Nella scheda **Home page di Microsoft Office** , fare clic su **Amministrazione > gruppi > gruppi**e quindi fare clic su **Aggiungi gruppo**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="5a1ef-132">Nella finestra **Aggiungi gruppo**, selezionare **il gruppo di Office 365** per il tipo di gruppo, digitare **dirigenti** in **nome** e l' **Id di gruppo**, selezionare **privata** di **Privacy**e quindi fare clic su **Seleziona proprietario**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="5a1ef-133">Nell'elenco, fare clic sul nome dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="5a1ef-134">Fare clic su **Aggiungi**e quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="5a1ef-135">Nell'elenco gruppi fare clic su **dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="5a1ef-136">Fare clic su **Modifica per i membri**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="5a1ef-p103">Fare clic su **Aggiungi membri**. Nell'elenco dei membri, selezionare l'account utente seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a1ef-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="5a1ef-139">Amministratore delegato</span><span class="sxs-lookup"><span data-stu-id="5a1ef-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="5a1ef-140">Direttore finanziario</span><span class="sxs-lookup"><span data-stu-id="5a1ef-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="5a1ef-141">Responsabile produzione</span><span class="sxs-lookup"><span data-stu-id="5a1ef-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="5a1ef-142">Fare clic su **Salva**e quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="5a1ef-143">Chiudere la scheda di **interfaccia di amministrazione di Office** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="5a1ef-144">Successivamente, creare una raccolta siti dirigenti e consentire solo ai membri del gruppo Dirigenti di accedervi.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="5a1ef-145">Nella scheda **Microsoft Office Home**, fare clic sulla sezione **Amministrazione**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="5a1ef-146">Nella scheda di **interfaccia di amministrazione di Office** , fare clic su **Admin Center > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="5a1ef-147">Nella scheda di **interfaccia di amministrazione di SharePoint** , fare clic su **Nuovo > raccolta siti privata**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="5a1ef-148">Nel nuovo riquadro di raccolta siti, digitare **dirigenti** **titolo**, dirigenti nella casella URL specificare il nome dell'account di amministratore globale di **amministratore**e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="5a1ef-p104">Attendere che la nuova raccolta siti è stata creata. Al termine, copiare l'URL della nuova raccolta di siti dirigenti e incollarlo in una nuova scheda del browser.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="5a1ef-151">In alto a destra della raccolta siti **dirigenti** , fare clic sull'icona impostazioni e quindi fare clic su **condiviso con**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="5a1ef-152">In **condivisione "Executives"**fare clic su **Avanzate**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="5a1ef-153">Nell'elenco dei gruppi di SharePoint fare clic su **Dirigenti membri**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="5a1ef-154">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="5a1ef-155">In **condivisione "Executives"**, digitare **dirigenti**, fare clic sul gruppo **dirigenti** e fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="5a1ef-156">Chiudere la scheda **utenti e gruppi** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="5a1ef-157">Successivamente, consentire a tutti gli utenti di accedere alla raccolta siti vendite.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="5a1ef-158">Dalla scheda di **interfaccia di amministrazione di SharePoint** , copiare l'URL della raccolta siti di vendita e incollarlo in una nuova scheda del browser..</span><span class="sxs-lookup"><span data-stu-id="5a1ef-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="5a1ef-159">In alto a destra, fare clic sull'icona impostazioni e quindi fare clic su **condiviso con**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="5a1ef-160">In **condivisione "Collection sito vendite"**, fare clic su **Avanzate**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="5a1ef-161">Nell'elenco dei gruppi di SharePoint, fare clic su **raccolta membri siti Sales**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="5a1ef-162">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="5a1ef-163">In **condivisione "Collection sito vendite"**, digitare **tutti**, fare clic su **tutti tranne agli utenti esterni**e quindi fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="5a1ef-164">Chiudere le schede **SharePoint** e **raccolta siti di Sales** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="5a1ef-165">Successivamente, accedere con un account dirigente e creare un documento nella raccolta siti dirigenti.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="5a1ef-166">Nella scheda **Home page di Microsoft Office** , fare clic sull'icona utente in alto a destra e fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="5a1ef-167">Visitare [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="5a1ef-168">Nella pagina **Office 365 accedere** , fare clic su **utilizza un altro account**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="5a1ef-169">Digitare il nome dell'account **amministratore delegato** e la relativa password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="5a1ef-170">In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti ( **https://**\<nome organizzazione >**.sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="5a1ef-171">Fare clic su **documenti**, fare clic su **Nuovo** e quindi fare clic su **Documenti di Word**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="5a1ef-172">Fare clic sulla barra del titolo e digitare **SensitiveData BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="5a1ef-173">Fare clic su nel corpo del documento e digitare **minuti dalla riunione più recente di area**e quindi fare clic su **dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="5a1ef-174">Dovrebbe essere visibile **SensitiveData BeforeIRM.docx** nella cartella **documenti** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="5a1ef-175">Quindi scaricare una copia locale del documento SensitiveData-BeforeIRM.docx e quindi pubblicarla accidentalmente nella raccolta siti vendite.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="5a1ef-176">Creare una nuova cartella nel computer locale (ad esempio, c\\laboratori\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="5a1ef-177">Nella scheda **documenti** del browser, selezionare il documento **SensitiveData BeforeIRM.docx** , fare clic sui puntini di sospensione e quindi fare clic su **Download**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="5a1ef-178">Archiviare i documenti **SensitiveData BeforeIRM.docx** nella cartella creata nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="5a1ef-179">In una nuova scheda del browser, digitare l'URL della raccolta siti di vendite ( **https://**\<nome organizzazione >**.sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="5a1ef-180">Fare clic sulla cartella **documenti** della **raccolta siti di Sales**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="5a1ef-181">Fare clic su **Carica**e quindi specificare **SensitiveData BeforeIRM.docx** documento nella cartella creata nel passaggio 1 e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="5a1ef-182">Verificare che il documento **SensitiveData BeforeIRM.docx** sia nella cartella **documenti** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="5a1ef-183">Chiudere le schede **vendite** e **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="5a1ef-184">Successivamente, accedere come User5 e provare ad aprire il documento SensitiveData-BeforeIRM.docx nella raccolta siti vendite.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="5a1ef-185">Nella scheda **Home page di Microsoft Office** , fare clic sull'icona utente in alto a destra e fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="5a1ef-186">Visitare [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="5a1ef-187">Nella pagina **Office 365 accedere** , fare clic su **utilizza un altro account**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="5a1ef-188">Digitare il nome dell'account User5 e la relativa password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="5a1ef-189">In una nuova scheda del browser, digitare l'URL della raccolta siti di Sales.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="5a1ef-190">Nella cartella **documenti** di **vendita raccolta siti**, fare clic sul documento **SensitiveData BeforeIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="5a1ef-191">Dovrebbero essere visualizzati i relativi contenuti.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="5a1ef-192">Chiudere le schede di **documenti** e **raccolta siti di Sales** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="5a1ef-193">Registrando accidentalmente il documento SensitiveData-BeforeIRM.docx nella raccolta siti vendite, il CEO ha ignorato la sicurezza delle autorizzazioni della raccolta siti dirigenti.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="5a1ef-194">Per preparare Office 365 per le fasi 3 e 4, abilitare IRM per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="5a1ef-195">Nella scheda **Home page di Microsoft Office** , fare clic sull'icona utente in alto a destra e fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="5a1ef-196">Visitare [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="5a1ef-197">Nella pagina **Office 365 accedere** fare clic sul nome di account amministratore globale, digitare la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="5a1ef-198">Nella scheda **Home page di Microsoft Office** , fare clic su **Amministrazione > Admin Center > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="5a1ef-199">Nella scheda di **interfaccia di amministrazione di SharePoint** fare clic su **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="5a1ef-200">Nella sezione **Information Rights Management (IRM)** della pagina **Impostazioni** selezionare **utilizza il servizio IRM specificato nella configurazione**e quindi selezionare **Aggiorna le impostazioni di IRM**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="5a1ef-201">Chiudere la scheda di **interfaccia di amministrazione di SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="5a1ef-202">Fase 3: usare Information Rights Management di SharePoint con un gruppo privato di Office 365</span><span class="sxs-lookup"><span data-stu-id="5a1ef-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="5a1ef-203">In questa fase, si utilizza SharePoint Information Rights Management con un gruppo privato di Office 365 per proteggere l'accesso a un documento con informazioni riservate, anche quando viene pubblicato in un sito con autorizzazioni aperte.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="5a1ef-204">Innanzitutto, abilitare e configurare IRM per la raccolta documenti della raccolta siti dirigenti. </span><span class="sxs-lookup"><span data-stu-id="5a1ef-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="5a1ef-205">In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="5a1ef-206">Fare clic su **documenti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="5a1ef-207">In alto a destra, fare clic sull'icona impostazioni e quindi fare clic su **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="5a1ef-208">Nella pagina **Impostazioni** in **autorizzazioni e gestione**fare clic su **Information Rights Management**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="5a1ef-209">Nella pagina **Impostazioni di Information Rights Management** :</span><span class="sxs-lookup"><span data-stu-id="5a1ef-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="5a1ef-210">Selezionare **Limita le autorizzazioni per i documenti al momento del download della raccolta**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="5a1ef-211">Per **creare un titolo di criteri di autorizzazione**digitare **dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="5a1ef-212">Per **una descrizione dei criteri di autorizzazione Aggiungi**, digitare **IRM per i dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="5a1ef-213">Fare clic su **Mostra opzioni**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="5a1ef-214">In **impostazioni aggiuntive IRM raccolta**, selezionare **non consentire agli utenti di caricare documenti che non supportano IRM**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="5a1ef-215">In **Configura diritti di accesso di documento**, selezionare **Consenti visualizzatori di stampa** e **Consenti visualizzatori di scrittura su una copia del documento scaricato**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="5a1ef-216">In **impostare la protezione di gruppo e l'intervallo delle credenziali**, selezionare **Consenti la protezione di gruppo** e nel **gruppo predefinito**, digitare **dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="5a1ef-217">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-217">Click **OK**.</span></span>
    
<span data-ttu-id="5a1ef-218">Successivamente, agendo da CEO, si carica un nuovo documento nella cartella documenti Dirigenti, lo si scarica, quindi lo si carica accidentalmente nella cartella documenti Vendite.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="5a1ef-219">Aprire la cartella locale in cui sono memorizzati i documenti **SensitiveData BeforeIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="5a1ef-220">Pulsante destro del mouse **SensitiveData BeforeIRM.docx**e quindi fare clic su **Copia**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="5a1ef-221">Pulsante destro del mouse all'interno della cartella e quindi scegliere **Incolla**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="5a1ef-222">Rinominare il nuovo file **SensitiveData-BeforeIRM - Copy.docx** a **SensitiveData AfterIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="5a1ef-223">Nella scheda **Home page di Microsoft Office** nel browser, fare clic sull'icona utente in alto a destra e quindi fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="5a1ef-224">Visitare [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="5a1ef-225">Nella pagina **Office 365 accedere** fare clic sul nome di account di amministratore delegato, digitare la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="5a1ef-226">In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="5a1ef-227">Nella pagina **documenti** fare clic su **Carica**, specificare il documento **SensitiveData AfterIRM.docx** nella cartella locale e quindi fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="5a1ef-228">Selezionare il nuovo documento **SensitiveData AfterIRM.docx** nella pagina **documenti** , fare clic sui puntini di sospensione (...) nella barra dei menu e quindi fare clic su **Download**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="5a1ef-229">Quando richiesto, salvare il documento **SensitiveData AfterIRM.docx** nella cartella locale, sovrascrivendo la versione originale.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="5a1ef-230">Chiudere la scheda per la pagina **documenti** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="5a1ef-231">In una nuova scheda del browser, digitare l'URL della raccolta siti di Sales.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="5a1ef-232">Fare clic su **documenti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="5a1ef-233">Nella pagina **documenti** fare clic su **Carica**, specificare il documento **SensitiveData AfterIRM.docx** nella cartella locale e quindi fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="5a1ef-234">Chiudere le schede **SharePoint** e **raccolta siti di Sales** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="5a1ef-235">Successivamente, opera come utente normale, si tenta di accedere al documento **SensitiveData AfterIRM.docx** nella cartella del documento Sales.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="5a1ef-236">Nella scheda **Home page di Microsoft Office** nel browser, fare clic sull'icona utente in alto a destra e quindi fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="5a1ef-237">Visitare [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="5a1ef-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="5a1ef-238">Nella pagina **Office 365 accedere** fare clic sul nome di account User5, digitare la password e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="5a1ef-239">In una nuova scheda del browser, digitare l'URL della raccolta siti di Sales.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="5a1ef-240">Fare clic su **documenti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="5a1ef-241">Nella pagina **documenti** , aprire il documento **SensitiveData AfterIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="5a1ef-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="5a1ef-242">Verrà visualizzato un messaggio di errore "Impossibile aprire il documento in Word Online perché è protetto con Information Rights Management (IRM)". </span><span class="sxs-lookup"><span data-stu-id="5a1ef-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="5a1ef-p105">Fare clic su **Modifica in Word**. Viene chiesto se si desidera aprire il file. Fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="5a1ef-p106">Viene richiesto di accesso. digitare il nome dell'account User5 e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="5a1ef-p107">Viene chiesto di immettere la password. Digitare la password per l'account User5 e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="5a1ef-250">Verrà visualizzato un messaggio di errore che informa: "L'utente non dispone delle credenziali per aprire il documento".</span><span class="sxs-lookup"><span data-stu-id="5a1ef-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="5a1ef-251">Fare clic su **No**.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-251">Click **No**.</span></span>
    
<span data-ttu-id="5a1ef-p108">Per vedere la protezione IRM, è necessario esaminare i file nella cartella locale. **SensitiveData AfterIRM.docx** deve essere maggiore del file **SensitiveData BeforeIRM.docx** . Il file **SensitiveData AfterIRM.docx** è crittografato e aggiunte le informazioni di protezione IRM a tale.</span><span class="sxs-lookup"><span data-stu-id="5a1ef-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5a1ef-255">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5a1ef-255">See Also</span></span>

[<span data-ttu-id="5a1ef-256">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="5a1ef-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="5a1ef-257">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="5a1ef-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="5a1ef-258">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="5a1ef-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="5a1ef-259">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="5a1ef-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


