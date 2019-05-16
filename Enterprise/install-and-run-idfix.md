---
title: Installazione ed esecuzione dello strumento IDFix di Office 365
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
description: Informazioni su come installare ed eseguire lo strumento Office 365 IdFix per la pulizia di Active Directory prima di sincronizzarlo con Office 365.
ms.openlocfilehash: 4197694ce90ab600652aa729809ef0ddb0647e03
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067292"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="557a7-103">Installazione ed esecuzione dello strumento IDFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="557a7-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="557a7-104">IdFix identifica gli errori quali i duplicati e i problemi di formattazione nella directory prima di eseguire la sincronizzazione con Office 365.</span><span class="sxs-lookup"><span data-stu-id="557a7-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="557a7-105">Per completare correttamente l'attività, è consigliabile utilizzare gli oggetti utente, gruppo e contatto in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="557a7-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="557a7-106">[! Importante] se non è possibile completare questa attività, esistono un paio di altre operazioni da eseguire.</span><span class="sxs-lookup"><span data-stu-id="557a7-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="557a7-107">Questi metodi sono più semplici, ma potrebbero richiedere più tempo o avere degli svantaggi.</span><span class="sxs-lookup"><span data-stu-id="557a7-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="557a7-108">Tali metodi sono elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="557a7-108">They are:</span></span>
  
- <span data-ttu-id="557a7-109">**Esecuzione della sincronizzazione della directory senza eseguire lo strumento IDFix.**</span><span class="sxs-lookup"><span data-stu-id="557a7-109">**Run directory synchronization without running IdFix.**</span></span> <span data-ttu-id="557a7-110">È possibile sincronizzare la directory senza eseguire lo strumento IdFix, ma non è consigliabile.</span><span class="sxs-lookup"><span data-stu-id="557a7-110">You can synchronize your directory without running the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="557a7-111">Correggere gli errori prima di eseguire la sincronizzazione richiede meno tempo e consente di effettuare una transizione sul cloud senza problemi.</span><span class="sxs-lookup"><span data-stu-id="557a7-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="557a7-p103">**Contattare un consulente.** Richiedere l'assistenza di un esperto può consentire ai tuoi utenti di diventare operativi in modo rapido, nonché di sincronizzare la directory.</span><span class="sxs-lookup"><span data-stu-id="557a7-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="557a7-114">Requisiti per eseguire IDFix</span><span class="sxs-lookup"><span data-stu-id="557a7-114">What you need to run IdFix</span></span>

<span data-ttu-id="557a7-115">Il modo più facile per iniziare a usare IDFix è rappresentato dall'installazione su un computer associato al tuo dominio.</span><span class="sxs-lookup"><span data-stu-id="557a7-115">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain.</span></span> <span data-ttu-id="557a7-116">È possibile eseguirlo nel controller di dominio, se lo si desidera, ma non è necessario.</span><span class="sxs-lookup"><span data-stu-id="557a7-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="557a7-117">Requisiti hardware di IDFix</span><span class="sxs-lookup"><span data-stu-id="557a7-117">IdFix hardware requirements</span></span>

<span data-ttu-id="557a7-118">Il computer in cui si installa IdFix deve soddisfare questi requisiti hardware minimi:</span><span class="sxs-lookup"><span data-stu-id="557a7-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="557a7-119">4 GB di RAM</span><span class="sxs-lookup"><span data-stu-id="557a7-119">4 GB RAM</span></span>
- <span data-ttu-id="557a7-120">2 GB di spazio su disco rigido</span><span class="sxs-lookup"><span data-stu-id="557a7-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="557a7-121">Requisiti software di IDFix</span><span class="sxs-lookup"><span data-stu-id="557a7-121">IdFix software requirements</span></span>

<span data-ttu-id="557a7-122">Il computer in cui viene installato IdFix deve essere aggiunto allo stesso dominio di Active Directory da cui si desidera sincronizzare gli utenti con Office 365.</span><span class="sxs-lookup"><span data-stu-id="557a7-122">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365.</span></span> <span data-ttu-id="557a7-123">Inoltre, nel computer deve essere installato .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="557a7-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="557a7-124">Se esegui Windows Server 2008 o Windows Server 2012, è probabile che .NET Framework sia già installato.</span><span class="sxs-lookup"><span data-stu-id="557a7-124">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed.</span></span> <span data-ttu-id="557a7-125">In caso contrario, è possibile [scaricare .net 4,0 dall'area download](https://go.microsoft.com/fwlink/p/?LinkId=400475) o tramite Windows Update.</span><span class="sxs-lookup"><span data-stu-id="557a7-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="557a7-126">Requisiti di autorizzazione per lo strumento IDFix</span><span class="sxs-lookup"><span data-stu-id="557a7-126">IdFix permissions requirements</span></span>

<span data-ttu-id="557a7-127">L'account utente che usi per eseguire lo strumento IDFix deve disporre di accesso in lettura/scrittura alla directory.</span><span class="sxs-lookup"><span data-stu-id="557a7-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="557a7-128">Se non si è certi che l'account utente soddisfi questi requisiti e non si è sicuri di come controllare, è comunque possibile installare ed eseguire IdFix.</span><span class="sxs-lookup"><span data-stu-id="557a7-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix.</span></span> <span data-ttu-id="557a7-129">Se l'account utente non dispone delle autorizzazioni appropriate, in IdFix verrà visualizzato un messaggio di errore quando si tenta di eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="557a7-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="557a7-130">Installazione di IDFix</span><span class="sxs-lookup"><span data-stu-id="557a7-130">Install IdFix</span></span>

<span data-ttu-id="557a7-131">Per installare IdFix, scaricare e decomprimere **IdFix. exe**:</span><span class="sxs-lookup"><span data-stu-id="557a7-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="557a7-132">Accedi al computer nel quale desideri installare lo strumento IDFix.</span><span class="sxs-lookup"><span data-stu-id="557a7-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="557a7-133">Accedere al sito di download Microsoft per lo [strumento di correzione degli errori di IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="557a7-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="557a7-134">Scegliere **Download**.</span><span class="sxs-lookup"><span data-stu-id="557a7-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="557a7-135">Quando richiesto, scegliere **Esegui**.</span><span class="sxs-lookup"><span data-stu-id="557a7-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="557a7-136">Nella finestra di dialogo **Programma di autoestrazione WinZip**, nella casella di testo **Estrai nella cartella**, scrivi o cerca il percorso in cui installare lo strumento IDFix.</span><span class="sxs-lookup"><span data-stu-id="557a7-136">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool.</span></span> <span data-ttu-id="557a7-137">Per impostazione predefinita, IdFix viene installato `C:\Deployment Tools\`in.</span><span class="sxs-lookup"><span data-stu-id="557a7-137">By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="557a7-138">Scegliere **unzip**.</span><span class="sxs-lookup"><span data-stu-id="557a7-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="557a7-139">Eseguire lo strumento IDFix</span><span class="sxs-lookup"><span data-stu-id="557a7-139">Run the IdFix tool</span></span>

<span data-ttu-id="557a7-140">Dopo aver installato lo strumento IDFix, eseguilo per rilevare i problemi presenti nella tua directory:</span><span class="sxs-lookup"><span data-stu-id="557a7-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="557a7-141">Usando un account che dispone di accesso in lettura/scrittura alla directory, accedi al computer in cui è installato IDFix.</span><span class="sxs-lookup"><span data-stu-id="557a7-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="557a7-142">In Esplora file, individua il percorso di installazione dello strumento IDFix.</span><span class="sxs-lookup"><span data-stu-id="557a7-142">In File Explorer, go to the location where you installed IdFix.</span></span> <span data-ttu-id="557a7-143">Se si è scelto la cartella predefinita durante l'installazione, `C:\Deployment Tools\IdFix`andare a.</span><span class="sxs-lookup"><span data-stu-id="557a7-143">If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="557a7-144">Fai doppio clic su **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="557a7-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Scegliere il file IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="557a7-146">Per impostazione predefinita, IdFix utilizza il set di regole multi-tenant per controllare le voci nella directory.</span><span class="sxs-lookup"><span data-stu-id="557a7-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="557a7-147">Si tratta del set di regole appropriato per la maggior parte dei clienti di Office 365.</span><span class="sxs-lookup"><span data-stu-id="557a7-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="557a7-148">Tuttavia, se si è un cliente di Office 365 dedicato o ITAR (International Traffic on Arms Regulations), è possibile configurare IdFix per utilizzare il set di regole dedicato.</span><span class="sxs-lookup"><span data-stu-id="557a7-148">However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="557a7-149">Se non si è certi del tipo di cliente, è possibile ignorare questo passaggio.</span><span class="sxs-lookup"><span data-stu-id="557a7-149">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="557a7-150">Per impostare il set di regole su dedicato, fare clic sull'icona ingranaggio sulla barra dei menu e quindi scegliere **dedicato**.</span><span class="sxs-lookup"><span data-stu-id="557a7-150">To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="557a7-151">Scegliere **query**.</span><span class="sxs-lookup"><span data-stu-id="557a7-151">Choose **Query**.</span></span>
    
    ![Scegliere query in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="557a7-153">Per impostazione predefinita, lo strumento IDFix effettua la ricerca di errori nell'intera directory.</span><span class="sxs-lookup"><span data-stu-id="557a7-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="557a7-154">A seconda della dimensione della directory, l'esecuzione della query può richiedere un po' di tempo.</span><span class="sxs-lookup"><span data-stu-id="557a7-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="557a7-155">È possibile guardare lo stato di avanzamento nella parte inferiore della finestra principale dello strumento.</span><span class="sxs-lookup"><span data-stu-id="557a7-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="557a7-156">Se si fa clic su **Annulla**, sarà necessario riavviare dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="557a7-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![Conteggio delle query e degli errori di IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="557a7-158">Dopo che IdFix ha completato la query, è possibile procedere e sincronizzare la directory se non sono presenti errori.</span><span class="sxs-lookup"><span data-stu-id="557a7-158">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors.</span></span> <span data-ttu-id="557a7-159">Se sono presenti errori nella directory, ti consigliamo di correggerli prima di eseguire la sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="557a7-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="557a7-160">Se desideri ricevere informazioni più dettagliate sui tipi di errore e consigli sul modo migliore per correggerli, consulta i link disponibili alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="557a7-160">If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="557a7-161">Sebbene non sia obbligatorio correggere gli errori prima della sincronizzazione, ti consigliamo almeno di esaminare tutti quelli restituiti dallo strumenti IDFix.</span><span class="sxs-lookup"><span data-stu-id="557a7-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="557a7-162">Ogni errore viene visualizzato in una riga separata nella finestra principale dello strumento.</span><span class="sxs-lookup"><span data-stu-id="557a7-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="557a7-p113">Se accetti la modifica consigliata nella colonna **UPDATE**, nella colonna **ACTION** seleziona l'operazione che desidera che lo strumento IDFix esegua per implementare la modifica, quindi fai clic su **Applica**. Quando fai clic su **Applica**, lo strumento apporta le modifiche nella directory.</span><span class="sxs-lookup"><span data-stu-id="557a7-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="557a7-165">Non è necessario fare clic su **applica** dopo ogni aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="557a7-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="557a7-166">In alternativa, puoi correggere molti errori prima di fare clic su **Applica** in modo che lo strumento IDFix li modifichi in contemporanea.</span><span class="sxs-lookup"><span data-stu-id="557a7-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="557a7-167">Puoi ordinare gli errori per tipo facendo clic su **ERROR** all'inizio della colonna che elenca i tipi di errore.</span><span class="sxs-lookup"><span data-stu-id="557a7-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="557a7-168">Una strategia consiste nel correggere tutti gli errori dello stesso tipo. ad esempio, per prima cosa correggere tutti i duplicati e applicarli.</span><span class="sxs-lookup"><span data-stu-id="557a7-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="557a7-169">Successivamente, correggere gli errori relativi al formato dei caratteri e così via.</span><span class="sxs-lookup"><span data-stu-id="557a7-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="557a7-170">Ogni volta che si applicano le modifiche, lo strumento IdFix crea un file di registro separato che può essere utilizzato per annullare le modifiche nel caso in cui si commette un errore.</span><span class="sxs-lookup"><span data-stu-id="557a7-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="557a7-171">Il [registro delle transazioni](idfix-transaction-log.md) è archiviato nella cartella in cui è installato IdFix.</span><span class="sxs-lookup"><span data-stu-id="557a7-171">The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.</span></span>  <span data-ttu-id="557a7-172">_C:\Deployment Tools\IdFix_ per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="557a7-172">_C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Correzione degli errori in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="557a7-174">Dopo aver apportato tutte le modifiche alla directory, eseguire di nuovo IdFix per assicurarsi che le correzioni apportate non introducano nuovi errori.</span><span class="sxs-lookup"><span data-stu-id="557a7-174">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="557a7-175">È possibile ripetere la procedura tutte le volte che è necessario.</span><span class="sxs-lookup"><span data-stu-id="557a7-175">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="557a7-176">È consigliabile passare un paio di volte al processo prima di eseguire la sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="557a7-176">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="557a7-177">Voglio ridefinire la mia ricerca o approfondire gli errori, quale altra operazione posso effettuare con lo strumento IDFix?</span><span class="sxs-lookup"><span data-stu-id="557a7-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="557a7-178">In questi argomenti, sono disponibili informazioni più approfondite:</span><span class="sxs-lookup"><span data-stu-id="557a7-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="557a7-179">[Preparare gli attributi della directory per la sincronizzazione con Office 365 utilizzando lo strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="557a7-179">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) .</span></span> <span data-ttu-id="557a7-180">Dopo aver installato lo strumento, consultare questo argomento per istruzioni dettagliate sulla sua esecuzione, sugli errori comuni che riscontrerai, sulle correzioni suggerite, sugli esempi e sulle procedura migliori da eseguire nel caso di molti errori.</span><span class="sxs-lookup"><span data-stu-id="557a7-180">After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="557a7-181">Riferimenti: Oggetti e attributi sclusi e supportati IdFix</span><span class="sxs-lookup"><span data-stu-id="557a7-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="557a7-182">Riferimento: Registro delle transazioni IdFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="557a7-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="557a7-183">Video di formazione</span><span class="sxs-lookup"><span data-stu-id="557a7-183">Video training</span></span>

<span data-ttu-id="557a7-184">Per ulteriori informazioni, vedere la lezione [installare e utilizzare lo strumento IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), portato all'utente da LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="557a7-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

