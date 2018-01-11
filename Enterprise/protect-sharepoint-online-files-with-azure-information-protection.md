---
title: Proteggere i file di SharePoint Online con Azure Information Protection
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Sintesi: Applicare la protezione delle informazioni di Azure per proteggere i file in un sito del team di SharePoint Online di livello estremamente riservato.'
ms.openlocfilehash: 03a10c5d856c4c5518f18b9d02ffe76f2c8d2e7a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="12262-103">Proteggere i file di SharePoint Online con Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="12262-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="12262-104">**Riepilogo:** Applicare la protezione delle informazioni di Azure per proteggere i file in un sito del team di SharePoint Online di livello estremamente riservato.</span><span class="sxs-lookup"><span data-stu-id="12262-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="12262-p101">Usare i passaggi descritti in questo articolo per configurare la protezione delle informazioni di Azure per fornire la crittografia e le autorizzazioni per i file in un sito del team di SharePoint Online di livello estremamente riservato. La crittografia e la protezione delle autorizzazioni viaggia con un file anche quando questo viene scaricato dal sito. Per ulteriori informazioni sui siti del team di SharePoint Online di livello estremamente riservato, vedere [Protezione di file e siti di SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="12262-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="12262-p102">Quando la crittografia di Azure Information Protection viene applicata ai file di Office 365, il servizio non può elaborare il contenuto di tali file. Creazione condivisa, eDiscovery, ricerca, Delve e altre funzionalità di collaborazione non funzionano. I criteri di prevenzione della perdita dei dati (DLP) possono funzionare solo con i metadati (comprese le etichette di Office 365), ma non con i contenuti di tali file (ad esempio i numeri di carta di credito all'interno dei file).</span><span class="sxs-lookup"><span data-stu-id="12262-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="12262-111">Innanzitutto, attenersi alle istruzioni in [Attivare Azure RMS con l'interfaccia di amministrazione di Office 365]((https://docs.microsoft.com/information-protection/deploy-use/activate-office365)) per la sottoscrizione di Office 365 in uso.</span><span class="sxs-lookup"><span data-stu-id="12262-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center]((https://docs.microsoft.com/information-protection/deploy-use/activate-office365)) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="12262-112">Configurare quindi Azure Information Protection con un nuovo criterio con ambito e un'etichetta secondaria per la protezione e le autorizzazioni del sito del team di SharePoint Online di livello estremamente riservato.</span><span class="sxs-lookup"><span data-stu-id="12262-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="12262-p103">Accedere al portale di Office 365 con un account che dispone del ruolo Amministratore della sicurezza oppure Amministratore della società. Per informazioni, vedere [Dove accedere a Office 365 per le aziende]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).</span><span class="sxs-lookup"><span data-stu-id="12262-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).</span></span>
    
2. <span data-ttu-id="12262-115">In una scheda a parte del browser, accedere al portale di Azure ([(https://portal.azure.com)]((https://portal.azure.com))).</span><span class="sxs-lookup"><span data-stu-id="12262-115">In a separate tab of your browser, go to the Azure portal ([(https://portal.azure.com)]((https://portal.azure.com))).</span></span>
    
3. <span data-ttu-id="12262-116">Se è la prima volta che viene configurato Azure Information Protection, consultare queste [istruzioni](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="12262-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="12262-117">Nel riquadro dell'elenco, fare clic su **Ulteriori servizi**, digitare **Informazioni**, quindi fare clic su **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="12262-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="12262-118">Nel pannello **Azure Information Protection**, fare clic su **Criteri con ambiti > + Aggiungi un nuovo criterio**.</span><span class="sxs-lookup"><span data-stu-id="12262-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="12262-119">Digitare un nome per il nuovo criterio in **Nome criterio** e una descrizione in **Descrizione**.</span><span class="sxs-lookup"><span data-stu-id="12262-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="12262-120">Fare clic su **Selezionare gli utenti o i gruppi a cui viene applicato il criterio > Utenti/Gruppi**, quindi selezionare i membri del gruppo di accesso per il sito del team di SharePoint Online di livello estremamente riservato.</span><span class="sxs-lookup"><span data-stu-id="12262-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="12262-121">Fare clic su **Seleziona > OK**.</span><span class="sxs-lookup"><span data-stu-id="12262-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="12262-122">Per l'etichetta **Estremamente riservato**, fare clic sui puntini di sospensione (…), quindi su **Aggiungi un'etichetta secondaria**.</span><span class="sxs-lookup"><span data-stu-id="12262-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="12262-123">Digitare un nome per l'etichetta secondaria in **Nome** e una descrizione dell'etichetta in **Descrizione**.</span><span class="sxs-lookup"><span data-stu-id="12262-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="12262-124">In **Configurare le autorizzazioni per documenti e messaggi di posta elettronica contenenti questa etichetta** fare clic su **Proteggi**.</span><span class="sxs-lookup"><span data-stu-id="12262-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="12262-125">Nella sezione **Protezione**, fare clic su **Azure (chiave cloud)**.</span><span class="sxs-lookup"><span data-stu-id="12262-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="12262-126">Nel pannello **Protezione**, in **Impostazioni di protezione**, fare clic su **+ Aggiungi autorizzazioni**.</span><span class="sxs-lookup"><span data-stu-id="12262-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="12262-127">Nel pannello **Aggiungi autorizzazioni**, in **Specifica utenti e gruppi** fare clic su **+ Sfoglia la directory**.</span><span class="sxs-lookup"><span data-stu-id="12262-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="12262-128">Nel riquadro **Utenti e gruppi di AAD**, selezionare i membri del gruppo di accesso per il sito del team di SharePoint Online di livello estremamente riservato, quindi scegliere **Seleziona**.</span><span class="sxs-lookup"><span data-stu-id="12262-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="12262-129">In **Scegli autorizzazioni dal set di impostazioni**, deselezionare le caselle di controllo **Stampa**, **Copia ed estrai il contenuto** e **Inoltra**.</span><span class="sxs-lookup"><span data-stu-id="12262-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="12262-130">Fare due volte clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="12262-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="12262-131">Nel pannello **Etichetta secondaria** fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="12262-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="12262-132">Chiudere il pannello del nuovo criterio con ambito.</span><span class="sxs-lookup"><span data-stu-id="12262-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="12262-133">Nel pannello **Azure Information Protection - Criteri con ambito**, fare clic su **Pubblica**.</span><span class="sxs-lookup"><span data-stu-id="12262-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="12262-134">Ecco il risultato della configurazione per il sito del team di SharePoint Online di livello estremamente riservato.</span><span class="sxs-lookup"><span data-stu-id="12262-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![Etichetta Protezione delle informazioni di Azure per un sito del team di SharePoint Online isolato.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="12262-136">A questo punto si è pronti per iniziare a creare documenti e a proteggerli con la protezione delle informazioni di Azure e con la nuova etichetta.</span><span class="sxs-lookup"><span data-stu-id="12262-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="12262-p104">È necessario [installare il client Azure Information Protection]((https://docs.microsoft.com/information-protection/rms-client/install-client-app)) nel computer che esegue Windows o nel dispositivo. È possibile creare uno script e automatizzare l'installazione oppure gli utenti possono installare il client manualmente. Vedere le risorse seguenti:</span><span class="sxs-lookup"><span data-stu-id="12262-p104">You must [install the Azure Information Protection client]((https://docs.microsoft.com/information-protection/rms-client/install-client-app)) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- <span data-ttu-id="12262-140">[Lato client di Protezione delle informazioni di Azure]((https://docs.microsoft.com/information-protection/rms-client/use-client))</span><span class="sxs-lookup"><span data-stu-id="12262-140">[The client side of Azure Information Protection]((https://docs.microsoft.com/information-protection/rms-client/use-client))</span></span>
    
- <span data-ttu-id="12262-141">[Installazione del client Protezione delle informazioni di Azure]((https://docs.microsoft.com/information-protection/rms-client/client-admin-guide))</span><span class="sxs-lookup"><span data-stu-id="12262-141">[Installing the Azure Information Protection client]((https://docs.microsoft.com/information-protection/rms-client/client-admin-guide))</span></span>
    
- [<span data-ttu-id="12262-142">Pagina di download per l'installazione manuale</span><span class="sxs-lookup"><span data-stu-id="12262-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="12262-p105">Dopo aver eseguito l'installazione, gli utenti eseguono il programma, quindi accedono da un'applicazione Office (ad esempio Microsoft Word) con l'account Office 365. Una nuova barra di **Information Protection** consente agli utenti di selezionare la nuova etichetta. Assicurarsi che gli utenti conoscano il sito del team di SharePoint Online e l'etichetta da usare per proteggere i file di livello estremamente riservato.</span><span class="sxs-lookup"><span data-stu-id="12262-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="12262-146">Se si dispone di più siti del team di SharePoint Online di livello estremamente riservato, è necessario creare più criteri con ambiti di Azure Information Protection con etichette secondarie con le impostazioni precedenti, con le autorizzazioni per ogni etichetta impostata per il gruppo di accesso dei membri di un sito del team di SharePoint Online specifico.</span><span class="sxs-lookup"><span data-stu-id="12262-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="12262-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="12262-147">See Also</span></span>

[<span data-ttu-id="12262-148">Protezione di file e siti di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="12262-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="12262-149">Proteggere i siti di SharePoint Online in un ambiente di sviluppo e di testing</span><span class="sxs-lookup"><span data-stu-id="12262-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="12262-150">Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili</span><span class="sxs-lookup"><span data-stu-id="12262-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="12262-151">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="12262-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




