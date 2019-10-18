---
title: Scaricare ed eseguire lo strumento IdFix di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Come scaricare ed eseguire lo strumento IdFix di Office 365 per eseguire la pulizia di Active Directory Domain Services (AD DS) prima della sincronizzazione con Office 365.
ms.openlocfilehash: 4a402cf245ebd20fbc5846908d521469ebfb90c1
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490754"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="c53bc-103">Scaricare ed eseguire lo strumento IdFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="c53bc-103">Install and run the Office 365 IdFix tool</span></span>


<span data-ttu-id="c53bc-104">IdFix identifica errori come la presenza di elementi duplicati e problemi di formattazione nel dominio di Active Directory Domain Services (AD DS) prima della sincronizzazione con Office 365.</span><span class="sxs-lookup"><span data-stu-id="c53bc-104">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="c53bc-105">Per completare correttamente questa attività, è importante avere familiarità con gli oggetti utente, gruppo e contatto in Active Directory Domain Services.</span><span class="sxs-lookup"><span data-stu-id="c53bc-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory Domain Services.</span></span>
  
<span data-ttu-id="c53bc-106">Se non si riesce a completare questa attività, è possibile provare un paio di metodi alternativi.</span><span class="sxs-lookup"><span data-stu-id="c53bc-106">If you can’t complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="c53bc-107">Questi metodi sono più semplici, ma potrebbero richiedere più tempo o avere degli svantaggi.</span><span class="sxs-lookup"><span data-stu-id="c53bc-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="c53bc-108">Tali limiti sono elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="c53bc-108">They are:</span></span>
  
- <span data-ttu-id="c53bc-109">**Eseguire la sincronizzazione della directory senza eseguire lo strumento IdFix**</span><span class="sxs-lookup"><span data-stu-id="c53bc-109">**Run directory synchronization without running IdFix.**</span></span> 

  <span data-ttu-id="c53bc-110">È possibile sincronizzare la directory senza eseguire lo strumento IdFix, ma questo metodo non è consigliato.</span><span class="sxs-lookup"><span data-stu-id="c53bc-110">You can synchronize your directory without running the IdFix tool, but we don’t recommend it.</span></span> <span data-ttu-id="c53bc-111">Correggere gli errori prima di eseguire la sincronizzazione richiede meno tempo e consente di effettuare la transizione nel cloud senza problemi.</span><span class="sxs-lookup"><span data-stu-id="c53bc-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="c53bc-112">**Contattare un consulente**</span><span class="sxs-lookup"><span data-stu-id="c53bc-112">**Hire a consultant.**</span></span> 

  <span data-ttu-id="c53bc-113">Richiedere l'assistenza di un esperto può consentire agli utenti aziendali di diventare subito operativi, nonché di sincronizzare la directory.</span><span class="sxs-lookup"><span data-stu-id="c53bc-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="c53bc-114">Requisiti per eseguire IDFix</span><span class="sxs-lookup"><span data-stu-id="c53bc-114">What you need to run IdFix</span></span>

<span data-ttu-id="c53bc-115">Il modo più facile per iniziare a usare IDFix è scaricarlo in un computer associato al dominio di Active Directory Domain Services aziendale.</span><span class="sxs-lookup"><span data-stu-id="c53bc-115">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain.</span></span> <span data-ttu-id="c53bc-116">È possibile eseguirlo sul controller di dominio, ma non è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="c53bc-116">You can run it on the domain controller if you want to, but it’s not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="c53bc-117">Requisiti hardware di IDFix</span><span class="sxs-lookup"><span data-stu-id="c53bc-117">IdFix hardware requirements</span></span>

<span data-ttu-id="c53bc-118">Il computer in cui si scarica lo strumento IDFix deve soddisfare i requisiti hardware minimi seguenti:</span><span class="sxs-lookup"><span data-stu-id="c53bc-118">The computer where you install IdFix needs to meet these hardware requirements:</span></span>
  
- <span data-ttu-id="c53bc-119">4 GB di RAM</span><span class="sxs-lookup"><span data-stu-id="c53bc-119">4 GB RAM</span></span>
- <span data-ttu-id="c53bc-120">2 MB di spazio libero sul disco rigido</span><span class="sxs-lookup"><span data-stu-id="c53bc-120">2 GB of hard disk space (minimum)</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="c53bc-121">Requisiti software di IDFix</span><span class="sxs-lookup"><span data-stu-id="c53bc-121">IdFix software requirements</span></span>

<span data-ttu-id="c53bc-122">Il computer nel quale si scarica IdFix deve far parte dello stesso dominio di AD DS da cui si vogliono sincronizzare gli utenti con Office 365.</span><span class="sxs-lookup"><span data-stu-id="c53bc-122">The computer where you install IdFix needs to needs to be joined to the same Active Directory domain from which you want to synchronize users to O365_W14_2nd.</span></span> 

<span data-ttu-id="c53bc-123">Inoltre, nel computer deve essere installato .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="c53bc-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="c53bc-124">Se si esegue Windows Server 2008 o versione successiva, è probabile che .NET Framework sia già installato.</span><span class="sxs-lookup"><span data-stu-id="c53bc-124">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed.</span></span> <span data-ttu-id="c53bc-125">In caso contrario, è possibile [scaricare .NET 4.0 dall'Area download](https://go.microsoft.com/fwlink/p/?LinkId=400475) o con Windows Update.</span><span class="sxs-lookup"><span data-stu-id="c53bc-125">If not, you can [download .NET 4.0 from the download centerhttp://go.microsoft.com/fwlink/p/?LinkId=400475](https://go.microsoft.com/fwlink/p/?LinkId=400475) or by using Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="c53bc-126">Requisiti di autorizzazione per IdFix</span><span class="sxs-lookup"><span data-stu-id="c53bc-126">IdFix permissions requirements</span></span>

<span data-ttu-id="c53bc-127">L'account utente usato per eseguire lo strumento IdFix deve disporre di accesso in lettura e scrittura al dominio di AD DS.</span><span class="sxs-lookup"><span data-stu-id="c53bc-127">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="c53bc-128">Se non si è certi che l'account utente soddisfi questi requisiti e non si sa come verificarlo, è comunque possibile scaricare ed eseguire IdFix.</span><span class="sxs-lookup"><span data-stu-id="c53bc-128">If you aren’t sure if your user account meets these requirements, and you’re not sure how to check, you can still install and run IdFix anyway.</span></span> <span data-ttu-id="c53bc-129">Se l'account utente non dispone delle autorizzazioni necessarie, verrà semplicemente visualizzato un errore quando si prova a eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="c53bc-129">If your user account doesn’t have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="c53bc-130">Scaricare ed estrarre IdFix</span><span class="sxs-lookup"><span data-stu-id="c53bc-130">Download and extract IdFix</span></span>

<span data-ttu-id="c53bc-131">Seguire queste istruzioni.</span><span class="sxs-lookup"><span data-stu-id="c53bc-131">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="c53bc-132">Accedere al computer in cui si vuole eseguire lo strumento IdFix.</span><span class="sxs-lookup"><span data-stu-id="c53bc-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="c53bc-133">Accedere al sito Microsoft per il download dello [strumento IdFix di correzione degli errori di DirSync](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="c53bc-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Toolhttp://go.microsoft.com/fwlink/p/?LinkId=396718](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="c53bc-134">Scaricare e aprire il file ZIP.</span><span class="sxs-lookup"><span data-stu-id="c53bc-134">Download and open the zip file.</span></span>
    
3. <span data-ttu-id="c53bc-135">Nella finestra **IdFix** scegliere **Estrai** e quindi **Estrai tutto**.</span><span class="sxs-lookup"><span data-stu-id="c53bc-135">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="c53bc-136">Per impostazione predefinita, IdFix viene estratto in `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="c53bc-136">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
6. <span data-ttu-id="c53bc-137">Scegliere **Estrai**.</span><span class="sxs-lookup"><span data-stu-id="c53bc-137">Choose **Extract**.</span></span>

<span data-ttu-id="c53bc-138">Queste istruzioni sono state eseguite con Internet Explorer in un server con Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="c53bc-138">These instructions were done with Internet Explorer on a server running Windows Server 2016.</span></span> <span data-ttu-id="c53bc-139">Se si usa una versione diversa di Windows o un browser diverso, la procedura potrebbe variare.</span><span class="sxs-lookup"><span data-stu-id="c53bc-139">If you're using a different version of Windows or a different browser, your steps might vary.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="c53bc-140">Eseguire lo strumento IdFix</span><span class="sxs-lookup"><span data-stu-id="c53bc-140">Run the IdFix tool</span></span>

<span data-ttu-id="c53bc-141">Dopo aver scaricato ed estratto IdFix, eseguirlo per cercare problemi nel dominio di AD DS.</span><span class="sxs-lookup"><span data-stu-id="c53bc-141">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="c53bc-142">Usando un account che dispone di accesso in lettura/scrittura al dominio di AD DS, accedere al computer in cui è stato scaricato IdFix.</span><span class="sxs-lookup"><span data-stu-id="c53bc-142">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="c53bc-143">In Esplora file passare al percorso di estrazione dello strumento IdFix.</span><span class="sxs-lookup"><span data-stu-id="c53bc-143">In File Explorer, go to the location where you installed IdFix.</span></span> <span data-ttu-id="c53bc-144">Se si è scelta la cartella predefinita durante l'estrazione, passare a `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="c53bc-144">If you chose the default folder during installation, go to C:\Deployment Tools\IdFix.</span></span> 
    
3. <span data-ttu-id="c53bc-145">Fare doppio clic su **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="c53bc-145">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="c53bc-146">Per impostazione predefinita, IdFix utilizza il set di regole multi-tenant per controllare le voci nella directory.</span><span class="sxs-lookup"><span data-stu-id="c53bc-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="c53bc-147">Si tratta del set di regole corretto per la maggior parte degli utenti di Office 365.</span><span class="sxs-lookup"><span data-stu-id="c53bc-147">This is the right rule set for most O365_W14_2nd customers.</span></span> <span data-ttu-id="c53bc-148">Tuttavia, i clienti di un piano di Office 365 dedicato o ITAR (International Traffic in Arms Regulations) possono configurare lo strumento per usare invece il set di regole Dedicato.</span><span class="sxs-lookup"><span data-stu-id="c53bc-148">However, if you are an O365_W14_2nd Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="c53bc-149">Se non si sa a quale tipologia di cliente si appartiene, è possibile saltare questo passaggio.</span><span class="sxs-lookup"><span data-stu-id="c53bc-149">If you aren’t sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="c53bc-150">Per impostare il set di regole su Dedicato, selezionare l'icona dell'ingranaggio nella barra dei menu e scegliere **Dedicato**.</span><span class="sxs-lookup"><span data-stu-id="c53bc-150">To set the rule set to Dedicated, click the gear icon in the menu bar and then click **Dedicated**.</span></span>
    
5. <span data-ttu-id="c53bc-151">Scegliere **Query**.</span><span class="sxs-lookup"><span data-stu-id="c53bc-151">Choose **Query**.</span></span>
    
    ![Scegliere Query in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="c53bc-153">Per impostazione predefinita, lo strumento IDFix effettua la ricerca di errori nell'intera directory.</span><span class="sxs-lookup"><span data-stu-id="c53bc-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="c53bc-154">A seconda della dimensione della directory, l'esecuzione della query può richiedere un po' di tempo.</span><span class="sxs-lookup"><span data-stu-id="c53bc-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="c53bc-155">È possibile visualizzare l'avanzamento della procedura nella parte inferiore della finestra principale dello strumento.</span><span class="sxs-lookup"><span data-stu-id="c53bc-155">You can watch the progress at the bottom of the tool’s main window.</span></span> <span data-ttu-id="c53bc-156">Se si fa clic su **Annulla**, si dovrà ripetere la procedura dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="c53bc-156">If you click **Cancel**, you’ll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="c53bc-157">Al termine dell'esecuzione della query da parte dello strumento IdFix e se non vengono segnalati errori, è possibile procedere con la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="c53bc-157">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="c53bc-158">Se sono presenti errori nella directory, è consigliabile correggerli prima di eseguire la sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="c53bc-158">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="c53bc-159">Per altre informazioni, vedere [Preparare gli attributi della directory per la sincronizzazione con Office 365](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="c53bc-159">See [prepare directory attributes for synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="c53bc-160">Sebbene non sia obbligatorio correggere gli errori prima della sincronizzazione, ti consigliamo almeno di esaminare tutti quelli restituiti dallo strumenti IDFix.</span><span class="sxs-lookup"><span data-stu-id="c53bc-160">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="c53bc-161">Ogni errore viene visualizzato in una riga separata nella finestra principale dello strumento.</span><span class="sxs-lookup"><span data-stu-id="c53bc-161">Each error is displayed in a separate row in the tool’s main window like this:</span></span> 
    
8. <span data-ttu-id="c53bc-p112">Se si accetta la modifica consigliata nella colonna **UPDATE**, nella colonna **ACTION** selezionare l'operazione che si desidera che lo strumento IdFix esegua per implementare la modifica, quindi fare clic su **Applica**. Quando si fa clic su **Applica**, lo strumento apporta le modifiche nella directory.</span><span class="sxs-lookup"><span data-stu-id="c53bc-p112">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="c53bc-164">Non è necessario fare clic su **Applica** dopo ogni aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="c53bc-164">You don’t have to click **Apply** after each update.</span></span> <span data-ttu-id="c53bc-165">È possibile correggere diversi errori prima di fare clic su **Applica** in modo che lo strumento IdFix li modifichi in contemporanea.</span><span class="sxs-lookup"><span data-stu-id="c53bc-165">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="c53bc-166">È possibile ordinare gli errori per tipo facendo clic su **ERROR** all'inizio della colonna che elenca i tipi di errore.</span><span class="sxs-lookup"><span data-stu-id="c53bc-166">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="c53bc-167">Una possibile strategia consiste nel correggere tutti gli errori dello stesso tipo. Ad esempio, correggere prima tutti i duplicati e applicarli.</span><span class="sxs-lookup"><span data-stu-id="c53bc-167">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="c53bc-168">Correggere quindi gli errori relativi al formato dei caratteri e così via.</span><span class="sxs-lookup"><span data-stu-id="c53bc-168">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="c53bc-169">Ogni volta che si applicano le modifiche, lo strumento IdFix crea un file di log separato che può essere usato per annullare le modifiche, in caso di errore.</span><span class="sxs-lookup"><span data-stu-id="c53bc-169">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="c53bc-170">Il [log delle transazioni](idfix-transaction-log.md) viene archiviato nella cartella in cui è stato estratto IdFix, che per impostazione predefinita è _C:\Utenti\<nome utente>\Documenti\IdFix_.</span><span class="sxs-lookup"><span data-stu-id="c53bc-170">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Correggere gli errori in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="c53bc-172">Dopo aver apportato tutte le modifiche alla directory, eseguire di nuovo lo strumento IdFix per assicurarsi che le correzioni non abbiano introdotto nuovi errori.</span><span class="sxs-lookup"><span data-stu-id="c53bc-172">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn’t introduce new errors.</span></span> <span data-ttu-id="c53bc-173">È possibile ripetere la procedura tutte le volte che è necessario.</span><span class="sxs-lookup"><span data-stu-id="c53bc-173">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="c53bc-174">È consigliabile ripetere il processo più volte prima di eseguire la sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="c53bc-174">It’s a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="c53bc-175">Altre risorse su IdFix</span><span class="sxs-lookup"><span data-stu-id="c53bc-175">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="c53bc-176">Oggetti e attributi esclusi e supportati da IdFix</span><span class="sxs-lookup"><span data-stu-id="c53bc-176">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="c53bc-177">Log delle transazioni IdFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="c53bc-177">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="c53bc-178">Video di formazione</span><span class="sxs-lookup"><span data-stu-id="c53bc-178">Video training</span></span>

<span data-ttu-id="c53bc-179">Per altre informazioni, vedere la lezione [Installare e usare lo strumento IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), offerta da LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="c53bc-179">For more information, see the lesson [Install and use the IdFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

