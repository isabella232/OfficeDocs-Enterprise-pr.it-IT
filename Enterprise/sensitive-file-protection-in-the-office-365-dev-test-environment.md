---
title: Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Riepilogo: configurare e illustrare in che modo Office 365 Information Rights Management protegge i file sensibili, anche quando vengono pubblicati nella raccolta siti di SharePoint Online errata.'
ms.openlocfilehash: 59d4cf56113f8b787f0caeaefddae135ad8e6249
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574070"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="135b1-103">Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="135b1-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="135b1-104">**Riepilogo:** Configurare e illustrare in che modo Office 365 Information Rights Management protegge i file sensibili, anche quando vengono inseriti nella raccolta siti di SharePoint Online errata.</span><span class="sxs-lookup"><span data-stu-id="135b1-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="135b1-p101">Information Rights Management (IRM) in Office 365 è un set di funzionalità per proteggere i documenti che vengono scaricati dalle raccolte e dagli elenchi di SharePoint Online. I file scaricati vengono crittografati e includono le autorizzazioni per aprire, copiare, salvare e stampare che riflettono la raccolta di SharePoint Online in cui sono stati salvati.</span><span class="sxs-lookup"><span data-stu-id="135b1-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="135b1-107">Con le istruzioni disponibili in questo articolo, è possibile abilitare e testare Information Rights Management in Office 365 per i file contenenti possibili informazioni riservate nella sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="135b1-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="135b1-108">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="135b1-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="135b1-109">Fase 1: creare l'ambiente di sviluppo/testing di Office 365</span><span class="sxs-lookup"><span data-stu-id="135b1-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="135b1-110">Se si desidera semplicemente testare la protezione dei file sensibili con i requisiti minimi, seguire le istruzioni nelle fasi 2 e 3 di [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="135b1-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="135b1-111">Se si desidera testare la protezione dei file sensibili in un'azienda simulata, seguire le istruzioni in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="135b1-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="135b1-p102">Il test della protezione dei file sensibili non richiede l'ambiente di sviluppo/testing aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione directory per una foresta di Windows Server AD. Questo test viene fornito qui come opzione in modo per consentire di testare la protezione dei file sensibili e sperimentarla in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="135b1-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="135b1-114">Fase 2: dimostrare in che modo i documenti dei siti protetti possono andare persi</span><span class="sxs-lookup"><span data-stu-id="135b1-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="135b1-115">In questa fase si dimostra che un utente può scaricare un documento da un sito protetto da autorizzazioni e quindi caricarlo in un sito con autorizzazioni aperte.</span><span class="sxs-lookup"><span data-stu-id="135b1-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="135b1-116">È innanzitutto necessario aggiungere tre nuovi account utente che rappresentano i dirigenti e assegnare loro le licenze di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="135b1-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="135b1-117">Utilizzare le istruzioni in [Connect to office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) per installare i moduli di PowerShell (se necessario) e connettersi alla nuova sottoscrizione di Office 365 da:</span><span class="sxs-lookup"><span data-stu-id="135b1-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="135b1-118">Dal computer (per l'ambiente di sviluppo/test di Office 365 leggero).</span><span class="sxs-lookup"><span data-stu-id="135b1-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="135b1-119">Dalla macchina virtuale CLIENT1 (per l'ambiente di sviluppo/test di Office 365 aziendale simulato).</span><span class="sxs-lookup"><span data-stu-id="135b1-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="135b1-120">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell**, digitare il nome dell'amministratore globale Office 365 (ad esempio: jdoe@contosotoycompany.onmicrosoft.com) e la password della sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="135b1-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="135b1-121">Immettere il nome dell'organizzazione (ad esempio: contosotoycompany) e il prefisso internazionale a due caratteri, quindi eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="135b1-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="135b1-122">Dalla visualizzazione del comando **New-MsolUser**, prendere nota della password generata per l'account CEO e conservarla in una posizione sicura.</span><span class="sxs-lookup"><span data-stu-id="135b1-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="135b1-123">Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="135b1-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="135b1-124">Dalla visualizzazione del comando **New-MsolUser**, prendere nota della password generata per l'account CFO e conservarla in una posizione sicura.</span><span class="sxs-lookup"><span data-stu-id="135b1-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="135b1-125">Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="135b1-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="135b1-126">Dalla visualizzazione del comando **New-MsolUser**, prendere nota della password generata per l'account COO e conservarla in una posizione sicura.</span><span class="sxs-lookup"><span data-stu-id="135b1-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="135b1-127">Successivamente, si crea un gruppo di dirigenti privato e vi si aggiungono i nuovi account dirigente.</span><span class="sxs-lookup"><span data-stu-id="135b1-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="135b1-128">Nel browser, accedere al portale di Office [http://admin.microsoft.com](http://admin.microsoft.com) e accedere alla sottoscrizione di valutazione di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="135b1-128">In your browser, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="135b1-129">Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, aprire una sessione privata di Internet Explorer o del proprio browser e accedere dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="135b1-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="135b1-130">Se è in uso l'ambiente di sviluppo/test di Office 365 aziendale simulato, utilizzare il Portale di Azure per connettersi alla macchina virtuale CLIENT1, quindi accedere da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="135b1-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="135b1-131">Nella scheda **Microsoft Office Home**, fare clic su **Amministratore > Gruppi > Gruppi**, quindi fare clic su **Aggiungi gruppo**.</span><span class="sxs-lookup"><span data-stu-id="135b1-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="135b1-132">In **Aggiungi gruppo**, selezionare **Gruppo di Office 365** per il tipo di gruppo, digitare **Dirigenti** in **Nome** e **ID gruppo**, selezionare **Privato** per **Privacy**e quindi fare clic su **Seleziona proprietario**.</span><span class="sxs-lookup"><span data-stu-id="135b1-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="135b1-133">Nell'elenco, fare clic sul nome dell'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="135b1-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="135b1-134">Fare clic su **Aggiungi**, quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="135b1-135">Nell'elenco di gruppi, fare clic su **Dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="135b1-136">Fare clic su **Modifica per i membri**.</span><span class="sxs-lookup"><span data-stu-id="135b1-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="135b1-p103">Fare clic su **Aggiungi membri**. Nell'elenco dei membri, selezionare i seguenti account utente:</span><span class="sxs-lookup"><span data-stu-id="135b1-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="135b1-139">Amministratore delegato</span><span class="sxs-lookup"><span data-stu-id="135b1-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="135b1-140">Direttore finanziario</span><span class="sxs-lookup"><span data-stu-id="135b1-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="135b1-141">Responsabile produzione</span><span class="sxs-lookup"><span data-stu-id="135b1-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="135b1-142">Fare clic su **Salva**, quindi fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="135b1-143">Chiudere la scheda **Interfaccia di amministrazione di Office**.</span><span class="sxs-lookup"><span data-stu-id="135b1-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="135b1-144">Successivamente, creare una raccolta siti dirigenti e consentire solo ai membri del gruppo Dirigenti di accedervi.</span><span class="sxs-lookup"><span data-stu-id="135b1-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="135b1-145">Nella scheda **Microsoft Office Home**, fare clic sulla sezione **Amministrazione**.</span><span class="sxs-lookup"><span data-stu-id="135b1-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="135b1-146">Nella scheda dell'interfaccia di **amministrazione di Office** , fare clic su interfaccia di **amministrazione di > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="135b1-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="135b1-147">Nella scheda dell'interfaccia di **amministrazione di SharePoint** , fare clic su **nuova raccolta siti privati di >**.</span><span class="sxs-lookup"><span data-stu-id="135b1-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="135b1-148">Nel riquadro nuovo raccolta siti, digitare **dirigenti** in **titolo**, dirigenti nella casella URL, specificare il nome dell'account di amministratore globale in **Administrator**e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="135b1-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="135b1-149">Attendere che la nuova raccolta siti sia stata creata.</span><span class="sxs-lookup"><span data-stu-id="135b1-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="135b1-150">Al termine dell'operazione, copiare l'URL della nuova raccolta siti dirigenti e incollarlo in una nuova scheda del browser.</span><span class="sxs-lookup"><span data-stu-id="135b1-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="135b1-151">In alto a destra della raccolta siti **Dirigenti**, fare clic sull'icona Impostazioni, quindi selezionare **Condiviso con**.</span><span class="sxs-lookup"><span data-stu-id="135b1-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="135b1-152">In **Condividi "dirigenti"**, fare clic su **Avanzate**.</span><span class="sxs-lookup"><span data-stu-id="135b1-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="135b1-153">Nell'elenco dei gruppi di SharePoint, fare clic su **Membri dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="135b1-154">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="135b1-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="135b1-155">In **Condividi "dirigenti"**, digitare **dirigenti**, fare clic sul gruppo **dirigenti** , quindi fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="135b1-156">Chiudere la scheda **utenti e gruppi** .</span><span class="sxs-lookup"><span data-stu-id="135b1-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="135b1-157">Successivamente, consentire a tutti gli utenti di accedere alla raccolta siti vendite.</span><span class="sxs-lookup"><span data-stu-id="135b1-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="135b1-158">Nella scheda dell'interfaccia di **amministrazione di SharePoint** , copiare l'URL della raccolta siti di vendita e incollarlo in una nuova scheda del browser.</span><span class="sxs-lookup"><span data-stu-id="135b1-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="135b1-159">In alto a destra, fare clic sull'icona Impostazioni, quindi selezionare **Condiviso con**.</span><span class="sxs-lookup"><span data-stu-id="135b1-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="135b1-160">In **Condividi "raccolta siti vendite"**, fare clic su **Avanzate**.</span><span class="sxs-lookup"><span data-stu-id="135b1-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="135b1-161">Nell'elenco dei gruppi di SharePoint, fare clic su **Membri raccolta siti vendite**.</span><span class="sxs-lookup"><span data-stu-id="135b1-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="135b1-162">Nella pagina **Utenti e gruppi** fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="135b1-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="135b1-163">In **Condividi "raccolta siti vendite"**, digitare **tutti**, fare clic su **tutti tranne gli utenti esterni**, quindi fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="135b1-164">Chiudere le schede **Raccolta siti vendite** e **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="135b1-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="135b1-165">Successivamente, accedere con un account dirigente e creare un documento nella raccolta siti dirigenti.</span><span class="sxs-lookup"><span data-stu-id="135b1-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="135b1-166">Nella scheda **Microsoft Office Home** fare clic sull'icona dell'account utente in alto a destra, quindi fare clic su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="135b1-167">Passare a [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="135b1-167">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="135b1-168">Nella pagina di **accesso di Office 365**, fare clic su **Usa un altro account**.</span><span class="sxs-lookup"><span data-stu-id="135b1-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="135b1-169">Digitare il nome dell'account **CEO** e la relativa password, quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="135b1-170">in una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti ( **https://**\<organization name>**. sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="135b1-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="135b1-171">Fare clic su **documenti**, fare clic su **nuovo** e quindi su **documento di Word**.</span><span class="sxs-lookup"><span data-stu-id="135b1-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="135b1-172">Fare clic nella barra del titolo e digitare **SensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="135b1-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="135b1-173">Fare clic nel corpo del documento e digitare **Minuti dall'ultima riunione del consiglio di amministrazione**, quindi fare clic su **Dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="135b1-174"> Viene visualizzato *\*SensitiveData-BeforeIRM.docx** nella cartella *\*Documenti*\*.</span><span class="sxs-lookup"><span data-stu-id="135b1-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="135b1-175">Quindi scaricare una copia locale del documento SensitiveData-BeforeIRM.docx e quindi pubblicarla accidentalmente nella raccolta siti vendite.</span><span class="sxs-lookup"><span data-stu-id="135b1-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="135b1-176">Nel computer locale, creare una nuova cartella (ad esempio, C:\\TLG\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="135b1-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="135b1-177">Nella scheda **Documenti** del browser, selezionare il documento **SensitiveData-BeforeIRM.docx**, fare clic sui puntini di sospensione, quindi fare clic su **Scarica**.</span><span class="sxs-lookup"><span data-stu-id="135b1-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="135b1-178">Archiviare il documento **SensitiveData-BeforeIRM.docx** nella cartella creata nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="135b1-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="135b1-179">in una nuova scheda del browser, digitare l'URL della raccolta siti di vendita ( **https://**\<organization name>**. sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="135b1-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="135b1-180">Fare clic sulla cartella **Documenti** della **Raccolta siti vendite**.</span><span class="sxs-lookup"><span data-stu-id="135b1-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="135b1-181">Fare clic su **Carica**, quindi specificare il documento **SensitiveData-BeforeIRM.docx** nella cartella creata nel passaggio 1, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="135b1-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="135b1-182">Verificare che il documento **SensitiveData-BeforeIRM.docx** sia visualizzato nella cartella **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="135b1-183">Chiudere le schede **Vendite** e **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="135b1-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="135b1-184">Successivamente, accedere come User5 e provare ad aprire il documento SensitiveData-BeforeIRM.docx nella raccolta siti vendite.</span><span class="sxs-lookup"><span data-stu-id="135b1-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="135b1-185">Nella scheda **Microsoft Office Home** fare clic sull'icona dell'account utente in alto a destra, quindi fare clic su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="135b1-186">Passare a [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="135b1-186">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="135b1-187">Nella pagina di **accesso di Office 365**, fare clic su **Usa un altro account**.</span><span class="sxs-lookup"><span data-stu-id="135b1-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="135b1-188">Digitare il nome dell'account di User5 e la relativa password, quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="135b1-189">In una nuova scheda del browser, digitare l'URL della raccolta siti di vendita.</span><span class="sxs-lookup"><span data-stu-id="135b1-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="135b1-190">Nella cartella **Documenti** della **Raccolta siti vendite**, fare clic sul documento **SensitiveData-BeforeIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="135b1-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="135b1-191">Dovrebbero essere visualizzati i relativi contenuti.</span><span class="sxs-lookup"><span data-stu-id="135b1-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="135b1-192">Chiudere le schede **Documenti** e **Raccolta siti vendite**.</span><span class="sxs-lookup"><span data-stu-id="135b1-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="135b1-193">Registrando accidentalmente il documento SensitiveData-BeforeIRM.docx nella raccolta siti vendite, il CEO ha ignorato la sicurezza delle autorizzazioni della raccolta siti dirigenti.</span><span class="sxs-lookup"><span data-stu-id="135b1-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="135b1-194">Per preparare Office 365 per le fasi 3 e 4, abilitare IRM per SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="135b1-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="135b1-195">Nella scheda **Microsoft Office Home** fare clic sull'icona dell'account utente in alto a destra, quindi fare clic su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="135b1-196">Passare a [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="135b1-196">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="135b1-197">Nella pagina **Accesso a Office 365**, fare clic sul nome dell'account di amministratore globale, digitare la relativa password, quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="135b1-198">Nella scheda **Microsoft Office Home**, fare clic su **Amministratore > Interfacce di amministrazione > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="135b1-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="135b1-199">Nella scheda **Interfaccia di amministrazione di SharePoint**, fare clic su **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="135b1-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="135b1-200">Nella pagina **Impostazioni**, nella sezione **Information Rights Management (IRM)**, selezionare **Usa il servizio IRM specificato nella configurazione**, quindi selezionare **Aggiorna impostazioni IRM**.</span><span class="sxs-lookup"><span data-stu-id="135b1-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="135b1-201">Chiudere la scheda **Interfaccia di amministrazione di SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="135b1-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="135b1-202">Fase 3: usare Information Rights Management di SharePoint con un gruppo privato di Office 365</span><span class="sxs-lookup"><span data-stu-id="135b1-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="135b1-203">In questa fase, si utilizza SharePoint Information Rights Management con un gruppo privato di Office 365 per proteggere l'accesso a un documento con informazioni riservate, anche quando viene pubblicato in un sito con autorizzazioni aperte.</span><span class="sxs-lookup"><span data-stu-id="135b1-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="135b1-204">Innanzitutto, abilitare e configurare IRM per la raccolta documenti della raccolta siti dirigenti. </span><span class="sxs-lookup"><span data-stu-id="135b1-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="135b1-205">In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti.</span><span class="sxs-lookup"><span data-stu-id="135b1-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="135b1-206">Fare clic su **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="135b1-207">In alto a destra, fare clic sull'icona Impostazioni, quindi selezionare **Impostazioni raccolta**.</span><span class="sxs-lookup"><span data-stu-id="135b1-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="135b1-208">Nella pagina **Impostazioni**, in **Autorizzazioni e gestione**, fare clic su **Information Rights Management**.</span><span class="sxs-lookup"><span data-stu-id="135b1-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="135b1-209">Nella pagina **Information Rights Management Settings**:</span><span class="sxs-lookup"><span data-stu-id="135b1-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="135b1-210">Selezionare **Limita le autorizzazioni per i documenti di questa raccolta in fase di download**.</span><span class="sxs-lookup"><span data-stu-id="135b1-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="135b1-211">Per **Creare un titolo per i criteri di autorizzazione**, digitare **Dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="135b1-212">Per **Aggiungere una descrizione per i criteri di autorizzazione**, digitare **IRM per dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="135b1-213">Fare clic su **Mostra opzioni**.</span><span class="sxs-lookup"><span data-stu-id="135b1-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="135b1-214">In **Configurare altre impostazioni della libreria IRM**, selezionare **Non consentire il caricamento di documenti che non supportano IRM**.</span><span class="sxs-lookup"><span data-stu-id="135b1-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="135b1-215">In **Configura diritti di accesso al documento**, selezionare **Consenti ai visualizzatori di stampare** e **Consenti ai visualizzatori di scrivere in una copia del documento scaricato**.</span><span class="sxs-lookup"><span data-stu-id="135b1-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="135b1-216">In **Imposta protezione gruppo e intervallo credenziali**selezionare **Consenti protezione gruppo** e per **Gruppo predefinito**, digitare **Dirigenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="135b1-217">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="135b1-217">Click **OK**.</span></span>
    
<span data-ttu-id="135b1-218">Successivamente, agendo da CEO, si carica un nuovo documento nella cartella documenti Dirigenti, lo si scarica, quindi lo si carica accidentalmente nella cartella documenti Vendite.</span><span class="sxs-lookup"><span data-stu-id="135b1-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="135b1-219">Aprire la cartella locale in cui è stato salvato il documento **SensitiveData-BeforeIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="135b1-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="135b1-220">	Fare clic con il pulsante destro del mouse su *\*SensitiveData-BeforeIRM.docx*\*, quindi fare clic su *\*Copia*\*.</span><span class="sxs-lookup"><span data-stu-id="135b1-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="135b1-221">Fare clic con il pulsante destro del mouse sulla cartella, quindi scegliere **Incolla**.</span><span class="sxs-lookup"><span data-stu-id="135b1-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="135b1-222">Rinominare il nuovo file **SensitiveData-BeforeIRM-Copy. docx** in **SensitiveData-AfterIRM. docx**.</span><span class="sxs-lookup"><span data-stu-id="135b1-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="135b1-223">Nella scheda **Microsoft Office Home** nel browser, fare clic sull'icona utente in alto a destra, quindi fare clic su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="135b1-224">Passare a [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="135b1-224">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="135b1-225">Nella pagina **Accesso a Office 365**, fare clic sul nome dell'account CEO, digitare la relativa password, quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="135b1-226">In una nuova scheda del browser, digitare l'URL della raccolta siti dirigenti.</span><span class="sxs-lookup"><span data-stu-id="135b1-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="135b1-227">Nella pagina **Documenti**, fare clic su **Carica**, specificare il documento **SensitiveData-AfterIRM.docx** nella cartella locale, quindi fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="135b1-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="135b1-228">Selezionare il nuovo documento **SensitiveData-AfterIRM.docx** nella pagina **Documenti**, fare clic sui puntini di sospensione (…) nella barra dei menu, quindi fare clic su **Scarica**.</span><span class="sxs-lookup"><span data-stu-id="135b1-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="135b1-229">Quando richiesto, salvare il documento **SensitiveData-AfterIRM.docx** nella cartella locale, sovrascrivendo la versione originale.</span><span class="sxs-lookup"><span data-stu-id="135b1-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="135b1-230">Chiudere la scheda per la pagina **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="135b1-231">In una nuova scheda del browser, digitare l'URL della raccolta siti di vendita.</span><span class="sxs-lookup"><span data-stu-id="135b1-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="135b1-232">Fare clic su **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="135b1-233">Nella pagina **Documenti**, fare clic su **Carica**, specificare il documento **SensitiveData-AfterIRM.docx** nella cartella locale, quindi fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="135b1-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="135b1-234">Chiudere le schede **Raccolta siti vendite** e **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="135b1-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="135b1-235">Successivamente, agendo da utente normale, provare ad accedere al documento **SensitiveData-AfterIRM.docx** nella cartella documenti Vendite.</span><span class="sxs-lookup"><span data-stu-id="135b1-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="135b1-236">Nella scheda **Microsoft Office Home** nel browser, fare clic sull'icona utente in alto a destra, quindi fare clic su **Disconnetti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="135b1-237">Passare a [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="135b1-237">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="135b1-238">Nella pagina di **accesso a Office 365** fare clic sul nome dell'account User5, digitare la relativa password, quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="135b1-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="135b1-239">In una nuova scheda del browser, digitare l'URL della raccolta siti di vendita.</span><span class="sxs-lookup"><span data-stu-id="135b1-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="135b1-240">Fare clic su **Documenti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="135b1-241">Nella pagina **Documenti**, aprire il documento **SensitiveData-AfterIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="135b1-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="135b1-242">Verrà visualizzato un messaggio di errore "Impossibile aprire il documento in Word Online perché è protetto con Information Rights Management (IRM)". </span><span class="sxs-lookup"><span data-stu-id="135b1-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="135b1-p105">Selezionare **Modifica in Word**. Viene chiesto se si desidera aprire il file. Fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="135b1-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="135b1-p106">Viene richiesto di accedere. Digitare il nome dell'account utente dell'account User5, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="135b1-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="135b1-p107">Verrà chiesto di fornire la password. Digitare la password dell'account User5, quindi fare clic su **Accedi**. </span><span class="sxs-lookup"><span data-stu-id="135b1-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="135b1-250">Verrà visualizzato un messaggio di errore che informa: "L'utente non dispone delle credenziali per aprire il documento".</span><span class="sxs-lookup"><span data-stu-id="135b1-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="135b1-251">Fare clic su **No**.</span><span class="sxs-lookup"><span data-stu-id="135b1-251">Click **No**.</span></span>
    
<span data-ttu-id="135b1-p108">Un altro modo per visualizzare la protezione IRM consiste nell'esaminare i file nella cartella locale. **SensitiveData-AfterIRM.docx** deve essere molto più grande del file **SensitiveData-BeforeIRM.docx**. Il file **SensitiveData-AfterIRM.docx** è crittografato e vi sono state aggiunte le informazioni di protezione IRM.</span><span class="sxs-lookup"><span data-stu-id="135b1-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="135b1-255">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="135b1-255">See Also</span></span>

[<span data-ttu-id="135b1-256">Guida al lab test (TLG) per adozione del cloud</span><span class="sxs-lookup"><span data-stu-id="135b1-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="135b1-257">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="135b1-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="135b1-258">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="135b1-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="135b1-259">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="135b1-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


