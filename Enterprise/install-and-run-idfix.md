---
title: Installazione ed esecuzione dello strumento IDFix di Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Come installare ed eseguire lo strumento IdFix di Office 365 per pulitura di active directory prima della sincronizzazione a Office 365.
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541137"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="d03bf-103">Installazione ed esecuzione dello strumento IDFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="d03bf-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="d03bf-104">IdFix identifica gli errori, ad esempio duplicati e problemi di formattazione della directory prima della sincronizzazione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="d03bf-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="d03bf-105">Per completare correttamente questa attività, è necessario avere familiarità con l'utente, gruppo e gli oggetti contatto di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d03bf-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="d03bf-p101">Se non è possibile completare questa attività, sono disponibili due di altre operazioni da eseguire. Questi metodi potrebbero essere più facile, ma che potrebbero inoltre richiedere più tempo o presentano altri inconvenienti. Sono:</span><span class="sxs-lookup"><span data-stu-id="d03bf-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="d03bf-p102">**Eseguire la sincronizzazione delle directory senza eseguire lo strumento IdFix.** È possibile sincronizzare le directory senza eseguire lo strumento IdFix, ma non è consigliabile. Correzione degli errori prima della sincronizzazione impiegherà meno tempo e spesso fornisce una transizione più uniforme nel cloud.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="d03bf-p103">**Contattare un consulente.** Richiedere l'assistenza di un esperto può consentire ai tuoi utenti di diventare operativi in modo rapido, nonché di sincronizzare la directory.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="d03bf-114">Requisiti per eseguire IDFix</span><span class="sxs-lookup"><span data-stu-id="d03bf-114">What you need to run IdFix</span></span>

<span data-ttu-id="d03bf-p104">Più semplice tornare IdFix e in esecuzione viene installato in un computer appartenente al dominio. Se si desidera, ma non è necessario, è possibile eseguire lo nel controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want to, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="d03bf-117">Requisiti hardware di IDFix</span><span class="sxs-lookup"><span data-stu-id="d03bf-117">IdFix hardware requirements</span></span>

<span data-ttu-id="d03bf-118">Il computer nel quale viene installato lo strumento IDFix deve soddisfare i seguenti requisiti hardware:</span><span class="sxs-lookup"><span data-stu-id="d03bf-118">The computer where you install IdFix needs to meet these hardware requirements:</span></span>
  
- <span data-ttu-id="d03bf-119">4 GB di RAM (minimo)</span><span class="sxs-lookup"><span data-stu-id="d03bf-119">4 GB RAM (minimum)</span></span>
- <span data-ttu-id="d03bf-120">2 GB di spazio libero sul disco rigido (minimo)</span><span class="sxs-lookup"><span data-stu-id="d03bf-120">2 GB of hard disk space (minimum)</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="d03bf-121">Requisiti software di IDFix</span><span class="sxs-lookup"><span data-stu-id="d03bf-121">IdFix software requirements</span></span>

<span data-ttu-id="d03bf-p105">Computer in cui è installato lo strumento IdFix deve deve essere aggiunto allo stesso dominio di Active Directory da cui si desidera sincronizzare gli utenti a Office 365. Il computer deve inoltre disporre installato .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p105">The computer where you install IdFix needs to needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="d03bf-p106">Se si esegue Windows Server 2008 o Windows Server 2012, è probabile che già installato .NET Framework. Se non, è possibile [scaricare .NET 4.0 dall'area download](https://go.microsoft.com/fwlink/p/?LinkId=400475) o tramite Windows Update.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or by using Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="d03bf-126">Requisiti di autorizzazione per lo strumento IDFix</span><span class="sxs-lookup"><span data-stu-id="d03bf-126">IdFix permissions requirements</span></span>

<span data-ttu-id="d03bf-127">L'account utente che usi per eseguire lo strumento IDFix deve disporre di accesso in lettura/scrittura alla directory.</span><span class="sxs-lookup"><span data-stu-id="d03bf-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="d03bf-p107">Se non si è certi che l'account utente soddisfa questi requisiti e non si è certi come controllare, è comunque possibile installare ed eseguire IdFix comunque. Se l'account utente non dispone delle autorizzazioni appropriate, IdFix verrà semplicemente visualizzato un errore quando si tenta di eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix anyway. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="d03bf-130">Installazione di IDFix</span><span class="sxs-lookup"><span data-stu-id="d03bf-130">Install IdFix</span></span>

<span data-ttu-id="d03bf-131">Per installare lo strumento IDFix, scarica e decomprimi il file **IdFix.exe**, come descritto nella seguente procedura:</span><span class="sxs-lookup"><span data-stu-id="d03bf-131">To install IdFix, you download and unzip **IdFix.exe** as described in these steps:</span></span> 
  
1. <span data-ttu-id="d03bf-132">Accedi al computer nel quale desideri installare lo strumento IDFix.</span><span class="sxs-lookup"><span data-stu-id="d03bf-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="d03bf-133">Passare al sito di download Microsoft per lo [Strumento di risoluzione dei problemi di IdFix DirSync errore](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="d03bf-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="d03bf-134">Scegliere **Download**.</span><span class="sxs-lookup"><span data-stu-id="d03bf-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="d03bf-135">Quando richiesto, scegliere **Esegui**.</span><span class="sxs-lookup"><span data-stu-id="d03bf-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="d03bf-p108">Nella casella di testo **Unzip alla cartella** della finestra di dialogo **WinZip Self-Extractor** digitare o selezionare il percorso in cui si desidera installare lo strumento IdFix. Per impostazione predefinita è installato IdFix in strumenti C:\Deployment\.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into C:\Deployment Tools\.</span></span> 
    
6. <span data-ttu-id="d03bf-138">Scegliere **Unzip**.</span><span class="sxs-lookup"><span data-stu-id="d03bf-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="d03bf-139">Eseguire lo strumento IDFix</span><span class="sxs-lookup"><span data-stu-id="d03bf-139">Run the IdFix tool</span></span>

<span data-ttu-id="d03bf-140">Dopo aver installato lo strumento IDFix, eseguilo per rilevare i problemi presenti nella tua directory:</span><span class="sxs-lookup"><span data-stu-id="d03bf-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="d03bf-141">Usando un account che dispone di accesso in lettura/scrittura alla directory, accedi al computer in cui è installato IDFix.</span><span class="sxs-lookup"><span data-stu-id="d03bf-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="d03bf-p109">In Esplora file, individua il percorso di installazione dello strumento IDFix. Se durante l'installazione hai scelto la cartella predefinita, accedi a C:\Deployment Tools\IdFix.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to C:\Deployment Tools\IdFix.</span></span>
    
3. <span data-ttu-id="d03bf-144">Fai doppio clic su **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="d03bf-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Selezionare il file IdFix.exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="d03bf-p110">Per impostazione predefinita, lo strumento IdFix utilizza multi-Tenant set di regole per testare le voci nella directory. Si tratta della regola destra impostato per la maggior parte dei clienti di Office 365. Tuttavia, se si è un cliente ITAR che offre (traffico internazionale in rami normative) o dedicati di Office 365, è possibile configurare IdFix per l'utilizzo in realtà set di regole dedicato. Se non si è certi di che tipo di cliente è, in modo sicuro è possibile ignorare questo passaggio. Per impostare il set di regole per dedicate, fare clic sull'icona dell'ingranaggio nella barra dei menu e quindi fare clic su **dedicate**.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="d03bf-151">Scegliere **Query**.</span><span class="sxs-lookup"><span data-stu-id="d03bf-151">Choose **Query**.</span></span>
    
    ![Scegliere query in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="d03bf-153">Per impostazione predefinita, lo strumento IDFix effettua la ricerca di errori nell'intera directory.</span><span class="sxs-lookup"><span data-stu-id="d03bf-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="d03bf-p111">A seconda delle dimensioni della directory, l'esecuzione della query può richiedere un po' di tempo. È possibile controllare lo stato di avanzamento nella parte inferiore della finestra principale dello strumento. Se si sceglie **Annulla**, sarà necessario riavviare dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![Numero di query e di errore IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="d03bf-p112">Al termine dell'esecuzione della query da parte dello strumento IDFix e se non vengono segnalati errori nella directory, puoi procedere con la sincronizzazione della directory. Se sono presenti errori nella directory, ti consigliamo di correggerli prima di eseguire la sincronizzazione. Se desideri ricevere informazioni più dettagliate sui tipi di errore e consigli sul modo migliore per correggerli, consulta i link disponibili alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p112">After IdFix completes the query, and if there are no errors in your directory, you can go ahead and synchronize your directory. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="d03bf-161">Sebbene non sia obbligatorio correggere gli errori prima della sincronizzazione, ti consigliamo almeno di esaminare tutti quelli restituiti dallo strumenti IDFix.</span><span class="sxs-lookup"><span data-stu-id="d03bf-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="d03bf-162">Ogni errore viene visualizzato in una riga separata nella finestra principale dello strumento.</span><span class="sxs-lookup"><span data-stu-id="d03bf-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="d03bf-p113">Se accetti la modifica consigliata nella colonna **UPDATE**, nella colonna **ACTION** seleziona l'operazione che desidera che lo strumento IDFix esegua per implementare la modifica, quindi fai clic su **Applica**. Quando fai clic su **Applica**, lo strumento apporta le modifiche nella directory.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="d03bf-p114">Non è necessario fare clic su **Applica** dopo ogni aggiornamento. In realtà, è possibile risolvere diversi errori prima che si fa clic su **Applica** e IdFix verrà modificato tutti alla stessa ora. È possibile ordinare gli errori dal tipo di errore facendo clic su **errori** nella parte superiore della colonna in cui sono elencati i tipi di errore.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="d03bf-p115">Una strategia consiste nel correggere tutti gli errori dello stesso tipo. ad esempio, eliminare innanzitutto tutti i duplicati e applicarle. Successivamente, correggere gli errori di formato del carattere e così via. Ogni volta che si applicano le modifiche, lo strumento IdFix consente di creare un file di registro distinto che è possibile utilizzare per annullare le modifiche nel caso in cui si effettua un errore. Il [registro delle transazioni](idfix-transaction-log.md) viene archiviato nella cartella in cui è installato IdFix in.  _C:\Deployment Tools\IdFix_ per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Correzione degli errori in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="d03bf-p116">Dopo tutto delle modifiche apportate alla directory, eseguire lo strumento IdFix per verificare che le correzioni apportate non introducano nuovi errori. È possibile ripetere questi passaggi più volte è necessario. È buona norma passare attraverso il processo più volte prima della sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="d03bf-177">Voglio ridefinire la mia ricerca o approfondire gli errori, quale altra operazione posso effettuare con lo strumento IDFix?</span><span class="sxs-lookup"><span data-stu-id="d03bf-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="d03bf-178">In questi argomenti, sono disponibili informazioni più approfondite:</span><span class="sxs-lookup"><span data-stu-id="d03bf-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="d03bf-p117">[Attributi di directory di preparazione per la sincronizzazione con Office 365 tramite lo strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Dopo aver installato lo strumento ponticello a questo argomento per istruzioni dettagliate su come eseguire lo strumento, si verificheranno gli errori più comuni suggerito correzioni, esempi e procedure consigliate per operazioni da eseguire quando presente un numero elevato di errori.</span><span class="sxs-lookup"><span data-stu-id="d03bf-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="d03bf-181">Riferimenti: Oggetti e attributi sclusi e supportati IdFix</span><span class="sxs-lookup"><span data-stu-id="d03bf-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="d03bf-182">Riferimento: Registro delle transazioni IdFix di Office 365</span><span class="sxs-lookup"><span data-stu-id="d03bf-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="d03bf-183">Formazione video</span><span class="sxs-lookup"><span data-stu-id="d03bf-183">Video training</span></span>

<span data-ttu-id="d03bf-184">Per ulteriori informazioni, vedere la lezione, [installare e utilizzare lo strumento IDFix](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), per offerto da Learning LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="d03bf-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), brought to you by LinkedIn Learning.</span></span>
  

