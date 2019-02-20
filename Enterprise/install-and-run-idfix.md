---
title: Installazione ed esecuzione dello strumento IDFix di Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085405"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="609e3-103">Installazione ed esecuzione dello strumento IDFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="609e3-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="609e3-104">IdFix identifica gli errori quali i duplicati e i problemi di formattazione nella directory prima di eseguire la sincronizzazione con Office 365.</span><span class="sxs-lookup"><span data-stu-id="609e3-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="609e3-105">Per completare correttamente l'attività, è consigliabile utilizzare gli oggetti utente, gruppo e contatto in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="609e3-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="609e3-p101">[! Importante] se non è possibile completare questa attività, esistono un paio di altre operazioni da eseguire. Questo metodo potrebbe essere più facile, ma potrebbe anche richiedere più tempo o altri svantaggi. Sono:</span><span class="sxs-lookup"><span data-stu-id="609e3-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="609e3-p102">**Eseguire la sincronizzazione della directory senza eseguire IdFix.** È possibile sincronizzare la directory senza eseguire lo strumento IdFix, ma non è consigliabile. La correzione degli errori prima della sincronizzazione richiede meno tempo e spesso fornisce una transizione più agevole al cloud.</span><span class="sxs-lookup"><span data-stu-id="609e3-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="609e3-p103">**Contattare un consulente.** Richiedere l'assistenza di un esperto può consentire ai tuoi utenti di diventare operativi in modo rapido, nonché di sincronizzare la directory.</span><span class="sxs-lookup"><span data-stu-id="609e3-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="609e3-114">Requisiti per eseguire IDFix</span><span class="sxs-lookup"><span data-stu-id="609e3-114">What you need to run IdFix</span></span>

<span data-ttu-id="609e3-p104">Il modo più semplice per ottenere IdFix è installarlo su un computer aggiunto al dominio. È possibile eseguirlo nel controller di dominio, se lo si desidera, ma non è necessario.</span><span class="sxs-lookup"><span data-stu-id="609e3-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="609e3-117">Requisiti hardware di IDFix</span><span class="sxs-lookup"><span data-stu-id="609e3-117">IdFix hardware requirements</span></span>

<span data-ttu-id="609e3-118">Il computer in cui si installa IdFix deve soddisfare questi requisiti hardware minimi:</span><span class="sxs-lookup"><span data-stu-id="609e3-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="609e3-119">4 GB di RAM</span><span class="sxs-lookup"><span data-stu-id="609e3-119">4 GB RAM</span></span>
- <span data-ttu-id="609e3-120">2 GB di spazio su disco rigido</span><span class="sxs-lookup"><span data-stu-id="609e3-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="609e3-121">Requisiti software di IDFix</span><span class="sxs-lookup"><span data-stu-id="609e3-121">IdFix software requirements</span></span>

<span data-ttu-id="609e3-p105">Il computer in cui viene installato IdFix deve essere aggiunto allo stesso dominio di Active Directory da cui si desidera sincronizzare gli utenti con Office 365. È inoltre necessario che nel computer sia installato .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="609e3-p105">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="609e3-p106">Se si esegue Windows Server 2008 o Windows Server 2012, è probabile che .NET Framework sia già installato. In caso contrario, è possibile [scaricare .net 4,0 dall'area download](https://go.microsoft.com/fwlink/p/?LinkId=400475) o tramite Windows Update.</span><span class="sxs-lookup"><span data-stu-id="609e3-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="609e3-126">Requisiti di autorizzazione per lo strumento IDFix</span><span class="sxs-lookup"><span data-stu-id="609e3-126">IdFix permissions requirements</span></span>

<span data-ttu-id="609e3-127">L'account utente che usi per eseguire lo strumento IDFix deve disporre di accesso in lettura/scrittura alla directory.</span><span class="sxs-lookup"><span data-stu-id="609e3-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="609e3-p107">Se non si è certi che l'account utente soddisfi questi requisiti e non si è sicuri di come controllare, è comunque possibile installare ed eseguire IdFix. Se l'account utente non dispone delle autorizzazioni appropriate, in IdFix verrà visualizzato un messaggio di errore quando si tenta di eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="609e3-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="609e3-130">Installazione di IDFix</span><span class="sxs-lookup"><span data-stu-id="609e3-130">Install IdFix</span></span>

<span data-ttu-id="609e3-131">Per installare IdFix, scaricare e decomprimere **IdFix. exe**:</span><span class="sxs-lookup"><span data-stu-id="609e3-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="609e3-132">Accedi al computer nel quale desideri installare lo strumento IDFix.</span><span class="sxs-lookup"><span data-stu-id="609e3-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="609e3-133">Accedere al sito di download Microsoft per lo [strumento di correzione degli errori di IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="609e3-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="609e3-134">Scegliere **Download**.</span><span class="sxs-lookup"><span data-stu-id="609e3-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="609e3-135">Quando richiesto, scegliere **Esegui**.</span><span class="sxs-lookup"><span data-stu-id="609e3-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="609e3-p108">Nella casella **di testo Unzip to Folder** della finestra di dialogo **WinZip Self-Extractor** Digitare o passare al percorso in cui si desidera installare lo strumento IdFix. Per impostazione predefinita, IdFix viene installato `C:\Deployment Tools\`in.</span><span class="sxs-lookup"><span data-stu-id="609e3-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="609e3-138">Scegliere **unzip**.</span><span class="sxs-lookup"><span data-stu-id="609e3-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="609e3-139">Eseguire lo strumento IDFix</span><span class="sxs-lookup"><span data-stu-id="609e3-139">Run the IdFix tool</span></span>

<span data-ttu-id="609e3-140">Dopo aver installato lo strumento IDFix, eseguilo per rilevare i problemi presenti nella tua directory:</span><span class="sxs-lookup"><span data-stu-id="609e3-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="609e3-141">Usando un account che dispone di accesso in lettura/scrittura alla directory, accedi al computer in cui è installato IDFix.</span><span class="sxs-lookup"><span data-stu-id="609e3-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="609e3-p109">In Esplora file passare al percorso in cui è stato installato IdFix. Se si è scelto la cartella predefinita durante l'installazione, `C:\Deployment Tools\IdFix`andare a.</span><span class="sxs-lookup"><span data-stu-id="609e3-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="609e3-144">Fai doppio clic su **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="609e3-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Scegliere il file IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="609e3-p110">Per impostazione predefinita, in IdFix viene utilizzato il set di regole multi-tenant per testare le voci nella directory. Si tratta del set di regole appropriato per la maggior parte dei clienti di Office 365. Tuttavia, se si è un cliente di Office 365 dedicato o ITAR (International Traffic on Arms Regulations), è possibile configurare IdFix per utilizzare il set di regole dedicato. Se non si è certi del tipo di cliente, è possibile ignorare questo passaggio. Per impostare il set di regole su dedicato, fare clic sull'icona ingranaggio sulla barra dei menu e quindi scegliere **dedicato**.</span><span class="sxs-lookup"><span data-stu-id="609e3-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="609e3-151">Scegliere **query**.</span><span class="sxs-lookup"><span data-stu-id="609e3-151">Choose **Query**.</span></span>
    
    ![Scegliere query in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="609e3-153">Per impostazione predefinita, lo strumento IDFix effettua la ricerca di errori nell'intera directory.</span><span class="sxs-lookup"><span data-stu-id="609e3-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="609e3-p111">A seconda delle dimensioni della directory, l'esecuzione della query può richiedere un po' di tempo. È possibile guardare lo stato di avanzamento nella parte inferiore della finestra principale dello strumento. Se si fa clic su **Annulla**, sarà necessario riavviare dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="609e3-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![Conteggio delle query e degli errori di IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="609e3-p112">Dopo che IdFix ha completato la query, è possibile procedere e sincronizzare la directory se non sono presenti errori. Se nella directory sono presenti errori, è consigliabile correggerli prima di eseguire la sincronizzazione. Se si desiderano informazioni più specifiche sui tipi di errori e sui suggerimenti relativi al modo migliore per risolvere ognuno di essi, vedere i collegamenti alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="609e3-p112">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="609e3-161">Sebbene non sia obbligatorio correggere gli errori prima della sincronizzazione, ti consigliamo almeno di esaminare tutti quelli restituiti dallo strumenti IDFix.</span><span class="sxs-lookup"><span data-stu-id="609e3-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="609e3-162">Ogni errore viene visualizzato in una riga separata nella finestra principale dello strumento.</span><span class="sxs-lookup"><span data-stu-id="609e3-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="609e3-p113">Se accetti la modifica consigliata nella colonna **UPDATE**, nella colonna **ACTION** seleziona l'operazione che desidera che lo strumento IDFix esegua per implementare la modifica, quindi fai clic su **Applica**. Quando fai clic su **Applica**, lo strumento apporta le modifiche nella directory.</span><span class="sxs-lookup"><span data-stu-id="609e3-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="609e3-p114">Non è necessario fare clic su **applica** dopo ogni aggiornamento. In alternativa, è possibile correggere alcuni errori prima di fare clic su **applica** e IdFix li modificherà contemporaneamente. È possibile ordinare gli errori per tipo di errore facendo clic su **errore** nella parte superiore della colonna in cui sono elencati i tipi di errore.</span><span class="sxs-lookup"><span data-stu-id="609e3-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="609e3-p115">Una strategia consiste nel correggere tutti gli errori dello stesso tipo. ad esempio, per prima cosa correggere tutti i duplicati e applicarli. Successivamente, correggere gli errori relativi al formato dei caratteri e così via. Ogni volta che si applicano le modifiche, lo strumento IdFix crea un file di registro separato che può essere utilizzato per annullare le modifiche nel caso in cui si commette un errore. Il [registro delle transazioni](idfix-transaction-log.md) è archiviato nella cartella in cui è installato IdFix.  _C:\Deployment Tools\IdFix_ per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="609e3-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Correzione degli errori in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="609e3-p116">Dopo aver apportato tutte le modifiche alla directory, eseguire di nuovo IdFix per assicurarsi che le correzioni apportate non introducano nuovi errori. È possibile ripetere questi passaggi tutte le volte che è necessario. È consigliabile passare un paio di volte al processo prima di eseguire la sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="609e3-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="609e3-177">Voglio ridefinire la mia ricerca o approfondire gli errori, quale altra operazione posso effettuare con lo strumento IDFix?</span><span class="sxs-lookup"><span data-stu-id="609e3-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="609e3-178">In questi argomenti, sono disponibili informazioni più approfondite:</span><span class="sxs-lookup"><span data-stu-id="609e3-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="609e3-p117">[Preparare gli attributi della directory per la sincronizzazione con Office 365 utilizzando lo strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Dopo aver installato lo strumento, passare a questo argomento per istruzioni più dettagliate sull'esecuzione dello strumento, errori comuni che si verificheranno, correzioni consigliate, esempi e procedure consigliate per le operazioni da eseguire quando si dispone di un numero elevato di errori.</span><span class="sxs-lookup"><span data-stu-id="609e3-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="609e3-181">Riferimenti: Oggetti e attributi sclusi e supportati IdFix</span><span class="sxs-lookup"><span data-stu-id="609e3-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="609e3-182">Riferimento: Registro delle transazioni IdFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="609e3-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="609e3-183">Video di formazione</span><span class="sxs-lookup"><span data-stu-id="609e3-183">Video training</span></span>

<span data-ttu-id="609e3-184">Per ulteriori informazioni, vedere la lezione [installare e utilizzare lo strumento IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), portato all'utente da LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="609e3-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

