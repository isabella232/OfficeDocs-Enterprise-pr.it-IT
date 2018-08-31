---
title: Recuperare elementi eliminati in una cassetta postale utente - Guida per amministratore
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: "In questo articolo sia per gli amministratori. È stato un utente di eliminare definitivamente gli elementi dalla cassetta postale di Outlook? L'utente desidera li back ma possibile recuperarle. È possibile ripristinare gli elementi eliminati, se non sono stati rimossi definitivamente dalla cassetta postale dell'utente. "
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541180"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="95420-106">Recuperare elementi eliminati in una cassetta postale utente - Guida per amministratore</span><span class="sxs-lookup"><span data-stu-id="95420-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="95420-p102">**Questo articolo sia per gli amministratori. Si sta tentando di recuperare elementi eliminati della propria cassetta postale?** Provare a eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="95420-p102">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?** Try one of the following:</span></span>
- [<span data-ttu-id="95420-109">Recuperare gli elementi eliminati in Outlook per Windows</span><span class="sxs-lookup"><span data-stu-id="95420-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="95420-110">Recuperare elementi o messaggi di posta elettronica eliminati in Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="95420-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="95420-111">Ripristinare i messaggi di posta elettronica eliminati in Outlook sul web</span><span class="sxs-lookup"><span data-stu-id="95420-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="95420-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="95420-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="95420-p103">È stato un utente di eliminare definitivamente gli elementi dalla cassetta postale di Outlook? L'utente desidera li back ma possibile recuperarle. È possibile ripristinare gli elementi eliminati, se non sono stati rimossi definitivamente dalla cassetta postale dell'utente. Ottenere questo risultato mediante lo strumento di eDiscovery In locale in Exchange Online per la ricerca per la posta elettronica eliminato e altri elementi, ovvero e, ad esempio contatti, calendari e attività, nella cassetta postale dell'utente. Se gli elementi eliminati, è possibile esportare in un file PST (denominato anche un File di dati di Outlook), che l'utente può quindi utilizzare per ripristinare gli elementi delle relative cassette postali.</span><span class="sxs-lookup"><span data-stu-id="95420-p103">Did a user permanently delete items from their Outlook mailbox? The user wants them back but can't recover them. You may be able recover the purged items if they haven't been permanently removed from the user's mailbox. You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox. If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="95420-p104">Ecco la procedura per ripristinare gli elementi eliminati nella cassetta postale dell'utente. Quanto tempo richiederà l'implementazione? La prima volta può richiedere 20 o 30 minuti di eseguire tutte le procedure, in base al numero di elementi sta tentando di ripristino.</span><span class="sxs-lookup"><span data-stu-id="95420-p104">Here are the steps for recovering deleted items in a user's mailbox. How long will this take? The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="95420-p105">È necessario essere un **amministratore globale** in Office 365 o un **amministratore di Exchange** o essere un membro del gruppo di ruoli Gestione organizzazione in Exchange Online per eseguire i passaggi descritti in questo articolo. Per ulteriori informazioni, vedere [ruoli di amministratore su Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="95420-p105">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article. For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="95420-123">Passaggio 1: Assegnare manualmente le autorizzazioni di eDiscovery</span><span class="sxs-lookup"><span data-stu-id="95420-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="95420-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="95420-124"></span></span>

<span data-ttu-id="95420-p106">Il primo passaggio consiste nell'assegnare manualmente le autorizzazioni necessarie di Exchange Online in modo che è possibile utilizzare lo strumento di eDiscovery In locale per postale una cassetta di ricerca. È necessario eseguire questa operazione una sola volta. Se si dispone di un'altra cassetta postale di ricerca in futuro, è possibile ignorare questo passaggio.</span><span class="sxs-lookup"><span data-stu-id="95420-p106">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox. You only have to do this once. If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="95420-128">[Percorso di accesso a Office 365 per aziende](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="95420-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="95420-129">Selezionare l'icona di avvio per app ![l'icona di avvio di app in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in alto a sinistra e fare clic su **amministratore**.</span><span class="sxs-lookup"><span data-stu-id="95420-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="95420-130">Nel riquadro di spostamento sinistro nell'interfaccia di amministrazione di Office 365, espandere **Admin Center**e quindi fare clic su **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="95420-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![Elenco di centro di amministrazione](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="95420-132">Nell'interfaccia di amministrazione di Exchange, fare clic su **autorizzazioni**e quindi fare clic su **ruoli amministratore**.</span><span class="sxs-lookup"><span data-stu-id="95420-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="95420-133">Nella visualizzazione elenco, selezionare **Gestione individuazione**e quindi fare clic su **Modifica**![sull'icona Modifica](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span><span class="sxs-lookup"><span data-stu-id="95420-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![Aggiungersi al gruppo di ruoli gestione individuazione in EAC](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="95420-135">Nel **Gruppo di ruoli**, fare clic su **Aggiungi**in **membri**,![sull'icona Aggiungi](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="95420-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="95420-136">Nella **Selezione membri**, familiarità selezionare dall'elenco dei nomi, fare clic su **Aggiungi**e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="95420-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="95420-p107">È inoltre possibile aggiungere un gruppo di essere un membro di, ad esempio la gestione dell'organizzazione o TenantAdmins. Se si aggiunge un gruppo, gli altri membri del gruppo riceveranno le autorizzazioni necessarie per eseguire lo strumento di eDiscovery In locale.</span><span class="sxs-lookup"><span data-stu-id="95420-p107">You can also add a group that you are a member of, such as Organization Management or TenantAdmins. If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="95420-139">Nel **Gruppo di ruoli**, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="95420-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="95420-140">Disconnettersi da Office 365.</span><span class="sxs-lookup"><span data-stu-id="95420-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="95420-141">È necessario disconnettersi prima di iniziare il passaggio successivo per rendere effettive le nuove autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="95420-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="95420-p108">Membri del gruppo di ruoli gestione individuazione possono accedere al contenuto di messaggi sensibili. Sono incluse la ricerca di tutte le cassette postali nell'organizzazione, l'anteprima dei risultati della ricerca (e altri elementi delle cassette postali), copia i risultati di una cassetta postale di individuazione ed esportare i risultati di ricerca in un file PST.</span><span class="sxs-lookup"><span data-stu-id="95420-p108">Members of the Discovery Management role group can access sensitive message content. This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="95420-144">Inizio pagina</span><span class="sxs-lookup"><span data-stu-id="95420-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="95420-145">Passaggio 2: Ricerca cassetta postale dell'utente per gli elementi eliminati</span><span class="sxs-lookup"><span data-stu-id="95420-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="95420-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="95420-146"></span></span>

<span data-ttu-id="95420-p109">Quando si esegue una ricerca eDiscovery In locale, viene incluso automaticamente la cartella elementi ripristinabili nella cassetta postale una ricerca nella ricerca. La cartella elementi ripristinabili è cui gli elementi eliminati in modo permanente vengono archiviati fino a quando non si sta eliminati (rimossa definitivamente) dalla cassetta postale. Pertanto, se non è stato eliminato un elemento, dovrebbe essere in grado di trovare mediante lo strumento di eDiscovery In locale.</span><span class="sxs-lookup"><span data-stu-id="95420-p109">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search. The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox. So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="95420-150">[Percorso di accesso a Office 365 per aziende](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="95420-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="95420-151">Selezionare l'icona di avvio per app ![l'icona di avvio di app in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in alto a sinistra e fare clic su **amministratore**.</span><span class="sxs-lookup"><span data-stu-id="95420-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="95420-152">Nel riquadro di spostamento sinistro nell'interfaccia di amministrazione di Office 365, espandere **amministrazione**e quindi fare clic su **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="95420-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="95420-153">Nell'interfaccia di amministrazione di Exchange, fare clic su **gestione della conformità**, fare clic su **In-Place eDiscovery &amp; attesa**e quindi fare clic su **Nuovo**![sull'icona Aggiungi](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="95420-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![In EAC, nella pagina Gestione conformità, fare clic su In-Place eDiscovery e archiviazione](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="95420-155">Nella pagina **nome e descrizione** digitare un nome per la ricerca (ad esempio il nome dell'utente ripristino di posta elettronica per), una descrizione facoltativa e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="95420-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="95420-156">Nella pagina **cassette postali** , fare clic su **specificare le cassette postali per la ricerca**e quindi fare clic su **Aggiungi**![sull'icona Aggiungi](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="95420-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![Fare clic su specificare le cassette postali per la ricerca per cercare una cassetta postale specifico](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="95420-158">Trovare e selezionare il nome dell'utente che sta recupero posta eliminata per, fare clic su **Aggiungi**e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="95420-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="95420-159">Fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="95420-159">Click **Next**.</span></span>
    
    <span data-ttu-id="95420-p110">Verrà visualizzata la pagina di **query di ricerca** . In questo campo definire i criteri di ricerca che consentono di individuare gli elementi mancanti nella cassetta postale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="95420-p110">The **Search query** page is displayed. This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="95420-162">Nella pagina **Query di ricerca** compilare i seguenti campi:</span><span class="sxs-lookup"><span data-stu-id="95420-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="95420-p111">**Includere tutti i contenuti** Selezionare questa opzione per includere tutti i contenuti nella cassetta postale dell'utente nei risultati della ricerca. Se si seleziona questa opzione, è possibile specificare ulteriori criteri di ricerca.</span><span class="sxs-lookup"><span data-stu-id="95420-p111">**Include all content** Select this option to include all content in the user's mailbox in the search results. If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="95420-165">**Filtro in base ai criteri** Selezionare questa opzione per specificare i criteri di ricerca, inclusi parole chiave, avviare e terminare le date, mittente e gli indirizzi dei destinatari e i tipi di messaggio.</span><span class="sxs-lookup"><span data-stu-id="95420-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![Creare una ricerca in base ai criteri, ad esempio parole chiave, intervallo di date, i destinatari e i tipi di messaggi](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="95420-167">**Campo**</span><span class="sxs-lookup"><span data-stu-id="95420-167">**Field**</span></span>|<span data-ttu-id="95420-168">**Utilizzare questa opzione per...**</span><span class="sxs-lookup"><span data-stu-id="95420-168">**Use this to...**</span></span>|
|:-----|:-----|
|![Un numero in un cerchio rosa](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="95420-170">Specificare le parole chiave, intervallo di date, i destinatari e tipi di messaggio.</span><span class="sxs-lookup"><span data-stu-id="95420-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![Numero 2 in un cerchio rosa.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="95420-172">Cercare i messaggi con parole chiave o frasi e utilizzare gli operatori logici, ad esempio **AND** o **OR**.</span><span class="sxs-lookup"><span data-stu-id="95420-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![Numero 3 in un cerchio rosa.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="95420-174">Cercare i messaggi inviati o ricevuti in un intervallo di date.</span><span class="sxs-lookup"><span data-stu-id="95420-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![Numero 4 in un cerchio rosa.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="95420-176">Cercare i messaggi ricevuti o inviati a utenti specifici.</span><span class="sxs-lookup"><span data-stu-id="95420-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![Numero 5 in un cerchio rosa.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="95420-178">Cercare tutti i tipi di messaggi oppure selezionare quelle specifiche.</span><span class="sxs-lookup"><span data-stu-id="95420-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="95420-p112">Nella pagina **impostazioni di conservazione In locale** , fare clic su **Fine** per avviare la ricerca. Per ripristinare posta eliminata, c'è motivo alla cassetta postale dell'utente di mettere in attesa.</span><span class="sxs-lookup"><span data-stu-id="95420-p112">On the **In-Place Hold settings** page, click **Finish** to start the search. To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="95420-181">Dopo aver avviato la ricerca, Exchange verrà visualizzata una stima delle dimensioni totali e numero di elementi che verranno restituiti dalla ricerca in base ai criteri specificati.</span><span class="sxs-lookup"><span data-stu-id="95420-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="95420-p113">Selezionare la ricerca appena creata e fare clic su **Aggiorna**![aggiornamento](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) per aggiornare le informazioni visualizzate nel riquadro dei dettagli. Lo stato della **Stima ha avuto esito positivo** indica che la ricerca sia stata completata. Exchange consente anche di visualizzare una stima del numero totale di elementi (e le dimensioni) trovato mediante la ricerca in base ai criteri di ricerca specificata nel passaggio 9.</span><span class="sxs-lookup"><span data-stu-id="95420-p113">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane. The status of **Estimate Succeeded** indicates that the search has finished. Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="95420-p114">Nel riquadro dei dettagli fare clic su **Anteprima risultati di ricerca** per visualizzare gli elementi che sono stati trovati. Questo può essere utile identificare gli elementi che si sta cercando. Se gli elementi che si desidera ripristinare, andare al passaggio 4 per esportare i risultati della ricerca in un file PST.</span><span class="sxs-lookup"><span data-stu-id="95420-p114">In the details pane, click **Preview search results** to view the items that were found. This might help you identify the item(s) that you're looking for. If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![Fare clic su anteprima i risultati di ricerca per visualizzare l'elemento che si desidera ripristinare](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="95420-p115">Se non si trova ciò che sta cercando, è possibile modificare i criteri di ricerca, selezionare la ricerca, fare clic su **Modifica**![sull'icona Modifica](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)e quindi fare clic su **query di ricerca**. Modificare i criteri di ricerca e quindi eseguire nuovamente la ricerca.</span><span class="sxs-lookup"><span data-stu-id="95420-p115">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**. Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="95420-191">Inizio pagina</span><span class="sxs-lookup"><span data-stu-id="95420-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="95420-192">(Facoltativo) Passaggio 3: Copiare i risultati della ricerca in una cassetta postale di individuazione</span><span class="sxs-lookup"><span data-stu-id="95420-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="95420-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="95420-193"></span></span>

<span data-ttu-id="95420-p116">Se non è possibile trovare un elementi dalla visualizzazione in anteprima i risultati della ricerca o se si desidera visualizzare gli elementi che si trovano nella cartella elementi ripristinabili dell'utente, quindi è possibile copiare i risultati della ricerca in una cassetta postale speciale (noti come cassetta postale di individuazione) e quindi aprire tale cassetta postale di Outlook sul web t o visualizzare gli elementi effettivi. Il motivo principale per copiare i risultati di ricerca è pertanto è possibile visualizzare gli elementi nella cartella elementi ripristinabili dell'utente. L'elemento che si desidera recuperare più probabile che si trova nella sottocartella Elimina.</span><span class="sxs-lookup"><span data-stu-id="95420-p116">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items. The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder. More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="95420-197">Nell'interfaccia di amministrazione di Exchange, andare a **Gestione conformità** \> **In-Place eDiscovery &amp; attesa**.</span><span class="sxs-lookup"><span data-stu-id="95420-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="95420-198">Nell'elenco delle ricerche, selezionare la ricerca creata nel passaggio 2.</span><span class="sxs-lookup"><span data-stu-id="95420-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="95420-199">Fare clic su **Cerca**![ricerca](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), quindi fare clic su **copiare i risultati della ricerca** dall'elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="95420-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![Fare clic su Cerca e quindi fare clic su copiare i risultati della ricerca](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="95420-201">Nella pagina **Copiare i risultati della ricerca** fare clic su **Sfoglia**.</span><span class="sxs-lookup"><span data-stu-id="95420-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![Lasciare le caselle di controllo deselezionata durante il ripristino degli elementi eliminati](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="95420-203">In **Nome visualizzato**, fare clic su **Cassetta postale di individuazione**e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="95420-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![Copiare i risultati della ricerca per la cassetta postale di individuazione predefinita](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="95420-205">La cassetta postale di individuazione è una cassetta postale di individuazione predefinita che viene creata automaticamente nella propria organizzazione Office 365.</span><span class="sxs-lookup"><span data-stu-id="95420-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="95420-206">Torna nella pagina **Copiare i risultati della ricerca** fare clic su **Copia** per avviare il processo per copiare i risultati della ricerca per la cassetta postale di individuazione.</span><span class="sxs-lookup"><span data-stu-id="95420-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![Fare clic su copia per copiare i risultati della ricerca per la cassetta postale di individuazione](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="95420-208">Fare clic su **Aggiorna**![aggiornamento](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) per aggiornare le informazioni sullo stato copia che viene visualizzata nel riquadro dei dettagli.</span><span class="sxs-lookup"><span data-stu-id="95420-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="95420-209">La copia di un termine, fare clic su **Apri** per aprire la cassetta postale di individuazione per visualizzare i risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="95420-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![Fare clic su Apri per accedere alla cassetta postale di ricerca di individuazione per visualizzare i risultati di ricerca](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="95420-p117">I risultati della ricerca copiati la cassetta postale di individuazione è incluso in una cartella con lo stesso nome di ricerca di eDiscovery In locale. È possibile scegliere una cartella per visualizzare gli elementi presenti nella cartella.</span><span class="sxs-lookup"><span data-stu-id="95420-p117">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search. You can click a folder to display the items in that folder.</span></span>
    
    ![Risultati della ricerca nella cassetta postale di individuazione; gli elementi nella cartella Elimina solo possono essere ripristinati da un amministratore](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="95420-p118">Quando si esegue una ricerca, anche ricerca nella cartella elementi ripristinabili dell'utente. Ciò significa che se gli elementi nella cartella elementi ripristinabili soddisfano i criteri di ricerca, siano inclusi nei risultati della ricerca. Gli elementi nella cartella eliminazioni sono gli elementi che l'utente eliminato in modo permanente (eliminando un elemento dalla cartella Posta eliminata o selezionandolo e premendo **MAIUSC + CANC**. Un utente può utilizzare lo strumento Recupera elementi eliminati in Outlook o Outlook sul web per ripristinare gli elementi nella cartella eliminazioni. Gli elementi nella cartella Elimina sono gli elementi eliminati tramite lo strumento Recupera posta eliminata dell'utente o gli elementi che sono stati eliminati automaticamente mediante un criterio applicato alla cassetta postale. In entrambi i casi, è possibile solo un amministratore recuperare elementi nella cartella Elimina.</span><span class="sxs-lookup"><span data-stu-id="95420-p118">When you run a search, the user's Recoverable Items folder is also searched. That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results. Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**. A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder. Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox. In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="95420-p119">Se un utente non riesce a trovare un elemento eliminato utilizzando lo strumento degli elementi recuperabili, ma che l'elemento sia ancora recuperabile, ovvero non è stata rimossa definitivamente dalla cassetta postale, molto probabilmente si trova nella cartella Elimina. Quindi, assicurarsi di cercare nella cartella Elimina per l'elemento eliminato che si sta tentando di ripristino di un utente.</span><span class="sxs-lookup"><span data-stu-id="95420-p119">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder. So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="95420-222">Inizio pagina</span><span class="sxs-lookup"><span data-stu-id="95420-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="95420-223">Passaggio 4: Esportare i risultati della ricerca in un file PST</span><span class="sxs-lookup"><span data-stu-id="95420-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="95420-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="95420-224"></span></span>

<span data-ttu-id="95420-p120">Dopo aver individuato l'elemento che si sta tentando di ripristino di un utente, il passaggio successivo è per esportare i risultati di ricerca che è stato eseguito nel passaggio 2 in un file PST. L'utente verrà utilizzato il file PST nel passaggio successivo per ripristinare elementi eliminati alle cassette postali.</span><span class="sxs-lookup"><span data-stu-id="95420-p120">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file. The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="95420-227">Nell'interfaccia di amministrazione di Exchange, andare a **Gestione conformità** \> **In-Place eDiscovery &amp; attesa**.</span><span class="sxs-lookup"><span data-stu-id="95420-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="95420-228">Nell'elenco delle ricerche, selezionare la ricerca creata nel passaggio 2.</span><span class="sxs-lookup"><span data-stu-id="95420-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="95420-229">Fare clic su **Esporta in un file PST**.</span><span class="sxs-lookup"><span data-stu-id="95420-229">Click **Export to a PST file**.</span></span>
    
    ![Fare clic su Esporta in un file PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="95420-231">Se viene richiesto di installare strumento di esportazione di eDiscovery, fare clic su **Esegui**.</span><span class="sxs-lookup"><span data-stu-id="95420-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="95420-232">In strumento di esportazione PST di eDiscovery, fare clic su **Sfoglia** per specificare il percorso in cui si desidera scaricare il file PST.</span><span class="sxs-lookup"><span data-stu-id="95420-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![Strumento di esportazione PST di eDiscovery](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="95420-234">È possibile ignorare le opzioni per abilitare deduplication e includere gli elementi non ricercabili.</span><span class="sxs-lookup"><span data-stu-id="95420-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="95420-235">Fare clic su **Start** per scaricare il file PST nel computer.</span><span class="sxs-lookup"><span data-stu-id="95420-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="95420-p121">**EDiscovery dello strumento di esportazione PST** Visualizza le informazioni sullo stato sul processo di esportazione. Al termine dell'esportazione, è possibile accedere il file nel percorso in cui è stato scaricato.</span><span class="sxs-lookup"><span data-stu-id="95420-p121">The **eDiscovery PST Export Tool** displays status information about the export process. When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="95420-238">Inizio pagina</span><span class="sxs-lookup"><span data-stu-id="95420-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="95420-239">Passaggio 5: Ripristinare gli elementi ripristinati alla cassetta postale dell'utente</span><span class="sxs-lookup"><span data-stu-id="95420-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="95420-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="95420-240"></span></span>

<span data-ttu-id="95420-p122">Il passaggio finale deve utilizzare il file PST esportato nel passaggio 4 per ripristinare gli elementi ripristinati alla cassetta postale dell'utente. Dopo aver inviato il file PST all'utente, nella parte restante di questo passaggio viene eseguita dall'utente per aprire il file PST e quindi spostare gli elementi recuperati in un'altra cartella nella propria cassetta postale. Per istruzioni dettagliate, si può inoltre inviare all'utente un collegamento in questo argomento: [Open e chiudere il file di dati di Outlook (con estensione pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Oppure è possibile inviare all'utente un collegamento alla sezione [Ripristina posta eliminata in una cassetta postale utilizzando un file PST](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) e chiedere di eseguire la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="95420-p122">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox. After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox. For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="95420-245">**Inviare il file PST all'utente**</span><span class="sxs-lookup"><span data-stu-id="95420-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="95420-p123">Il passaggio finale che è necessario eseguire Invia il file PST esportato nel passaggio 4 per l'utente. Esistono alcuni modi per eseguire questa operazione:</span><span class="sxs-lookup"><span data-stu-id="95420-p123">The final step that you need to perform is sending the PST file that was exported in step 4 to the user. There are a few ways to do this:</span></span>
  
- <span data-ttu-id="95420-p124">Allegare il file PST a un messaggio di posta elettronica. Se Outlook è configurata per i file di blocco file PST, sarà necessario il file zip e quindi connettersi al messaggio. Ecco come:</span><span class="sxs-lookup"><span data-stu-id="95420-p124">Attach the PST file to an email message. If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message. Here's how:</span></span>
    
1. <span data-ttu-id="95420-251">In Esplora risorse o Esplora File, passare al file PST.</span><span class="sxs-lookup"><span data-stu-id="95420-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="95420-p125">Il file e quindi selezionare **Invia a** \> **Compressed cartella compressa**. Windows consente di creare un nuovo file con estensione zip e gli assegna lo stesso nome del file PST.</span><span class="sxs-lookup"><span data-stu-id="95420-p125">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**. Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="95420-254">Allegare il file PST compresso a un messaggio di posta elettronica e inviarlo all'utente, che può quindi decomprimere il file appena facendovi.</span><span class="sxs-lookup"><span data-stu-id="95420-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="95420-255">Copiare il file PST in una cartella condivisa che l'utente può accedere e recupero.</span><span class="sxs-lookup"><span data-stu-id="95420-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="95420-256">I passaggi nella sezione successiva vengono eseguiti dall'utente per ripristinare gli elementi eliminati alle cassette postali.</span><span class="sxs-lookup"><span data-stu-id="95420-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="95420-257">**Ripristino di elementi eliminati per una cassetta postale tramite un file PST**</span><span class="sxs-lookup"><span data-stu-id="95420-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="95420-p126">È necessario utilizzare l'app desktop Outlook per ripristinare un elemento eliminato tramite un file PST. È possibile utilizzare Outlook Web App o Outlook sul web per aprire un file PST.</span><span class="sxs-lookup"><span data-stu-id="95420-p126">You have to use the Outlook desktop app to restore a deleted item by using a PST file. You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="95420-260">In Outlook 2013 o 2016 Outlook, fare clic sulla scheda **File** .</span><span class="sxs-lookup"><span data-stu-id="95420-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="95420-261">Fare clic su **Open &amp; esportare**e quindi fare clic su **Apri File di dati di Outlook**.</span><span class="sxs-lookup"><span data-stu-id="95420-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="95420-262">Passare al percorso in cui è stato salvato il file PST che ha inviato all'amministratore.</span><span class="sxs-lookup"><span data-stu-id="95420-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="95420-263">Selezionare il file PST e quindi fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="95420-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="95420-264">Il file PST viene visualizzato nella barra di navigazione sinistra di Outlook.</span><span class="sxs-lookup"><span data-stu-id="95420-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![Il file PST viene visualizzato nella barra di navigazione sinistra di Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="95420-266">Fare clic sulle frecce per espandere il file PST e le relative sottocartelle per individuare l'elemento che si desidera ripristinare.</span><span class="sxs-lookup"><span data-stu-id="95420-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![Cercare nella cartella Elimina per l'elemento che si desidera ripristinare](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="95420-p127">Cercare nella cartella Elimina per l'elemento che si desidera ripristinare. Si tratta di una cartella nascosta eliminati vengono spostati gli elementi. È probabile che la voce corrispondente all'amministratore di ripristino in questa cartella.</span><span class="sxs-lookup"><span data-stu-id="95420-p127">Look in the Purges folder for the item you want to recover. This is a hidden folder that purged items are moved to. It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="95420-271">Pulsante destro del mouse l'elemento che si desidera ripristinare e quindi fare clic su **Sposta** \> **Altra cartella**.</span><span class="sxs-lookup"><span data-stu-id="95420-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![Fare clic su Sposta e quindi selezionare altre cartelle](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="95420-273">Per spostare l'elemento di posta in arrivo, fare clic su **posta in arrivo**e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="95420-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="95420-274">**Suggerimento:** Per recuperare gli altri tipi di elementi, effettuare una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="95420-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="95420-275">Per ripristinare un elemento del calendario, pulsante destro del mouse e quindi fare clic su **Sposta** \> **Altre cartelle** \> **calendario**.</span><span class="sxs-lookup"><span data-stu-id="95420-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="95420-276">Per ripristinare un contatto, pulsante destro del mouse e quindi fare clic su **Sposta** \> **Altre cartelle** \> **contatti**.</span><span class="sxs-lookup"><span data-stu-id="95420-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="95420-277">Per ripristinare un'attività, pulsante destro del mouse e quindi fare clic su **Sposta** \> **Altre cartelle** \> **attività**.</span><span class="sxs-lookup"><span data-stu-id="95420-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![Selezionare una cartella in cui spostare altri tipi di elementi](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="95420-279">Una volta terminato il ripristino degli elementi eliminati, fare clic sul file PST nella barra di navigazione sinistra e selezionare **Chiudi "nome del file PST"**.</span><span class="sxs-lookup"><span data-stu-id="95420-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="95420-280">Return to top</span><span class="sxs-lookup"><span data-stu-id="95420-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="95420-281">Ulteriori informazioni</span><span class="sxs-lookup"><span data-stu-id="95420-281">More information</span></span>
<span data-ttu-id="95420-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="95420-282"></span></span>

- <span data-ttu-id="95420-p128">Potrebbe essere possibile per un utente di recuperare un elemento eliminato definitivamente se il periodo di mantenimento elementi eliminati per l'elemento non è scaduto. L'amministratore che potrebbe essere specificati quanto tempo gli elementi nella cartella elementi recuperabili sono disponibili per il ripristino. Potrebbe, ad esempio esistere un criterio che consente di eliminare qualsiasi operazione che è stato nella cartella Posta eliminata dell'utente per 30 giorni e un altro criterio che consente agli utenti di ripristino di elementi nella cartella elementi recuperabili per fino a un altro 14 giorni. Dopo questo 14 giorni, tuttavia, può comunque essere in grado di ripristinare un elemento in postale una cassetta utilizzando le procedure descritte in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="95420-p128">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired. As an admin you may have specified how long items in the Recoverable Items folder are available for recovery. For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days. However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="95420-p129">Gli utenti possono recuperare un elemento eliminato se non è stato eliminato e se il periodo di mantenimento elementi eliminati per l'elemento non è scaduto. Per consentire agli utenti di recuperare elementi eliminati nella propria cassetta postale, puntino a uno degli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="95420-p129">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="95420-289">Recuperare gli elementi eliminati in Outlook per Windows</span><span class="sxs-lookup"><span data-stu-id="95420-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="95420-290">Recupero degli elementi eliminati in Outlook 2010</span><span class="sxs-lookup"><span data-stu-id="95420-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="95420-291">Recuperare elementi o messaggi di posta elettronica eliminati in Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="95420-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="95420-292">Ripristinare i messaggi di posta elettronica eliminati in Outlook sul web</span><span class="sxs-lookup"><span data-stu-id="95420-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="95420-293">Ripristino di un contatto eliminato in Outlook</span><span class="sxs-lookup"><span data-stu-id="95420-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="95420-294">Ripristinare i messaggi di posta elettronica eliminati in Outlook.com</span><span class="sxs-lookup"><span data-stu-id="95420-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="95420-295">Inizio pagina</span><span class="sxs-lookup"><span data-stu-id="95420-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

