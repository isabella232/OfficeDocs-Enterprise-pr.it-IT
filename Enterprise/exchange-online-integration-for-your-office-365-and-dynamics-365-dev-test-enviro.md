---
title: Integrazione di Exchange Online per il proprio ambiente di sviluppo/test di Office 365 e Dynamics 365
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
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "Riepilogo: Usare questa Guida del laboratorio di testing per attivare l'integrazione di Dynamics 365 per Exchange Online nella sottoscrizione di valutazione di Office 365."
ms.openlocfilehash: 320a59043ab2a8810f9bfc03fdcf896241ec6b20
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915501"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="b5fe5-103">Integrazione di Exchange Online per il proprio ambiente di sviluppo/test di Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b5fe5-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="b5fe5-104">**Riepilogo:** Usare questa Guida del laboratorio di testing per attivare l'integrazione di Dynamics 365 per Exchange Online nella sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="b5fe5-p101">Per un miglior utilizzo di Microsoft Dynamics 365 occorre memorizzare tutte le comunicazioni con il cliente in un'unica posizione, in modo che tutti gli utenti dotati delle autorizzazioni appropriate possono vedere tutti i record del cliente pertinente. Ad esempio, visualizzare tutti i messaggi associati a un particolare contatto, account, opportunità o pratica.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="b5fe5-p102">Per archiviare posta elettronica e altri record di messaggistica in Dynamics 365, è necessario sincronizzare il sistema di posta elettronica con Dynamics 365. La sincronizzazione sul lato server è il metodo di scelta per la sincronizzazione della posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="b5fe5-109">Usare questa Guida del laboratorio di testing per configurare e dimostrare come Exchange Online e il client Outlook Online possono sfruttare le informazioni archiviate in Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="b5fe5-110">Fase 1: Creare l'ambiente di sviluppo/test di Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b5fe5-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="b5fe5-111">Seguire le istruzioni riportate in [Ambiente di sviluppo/test di Office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md) per creare una versione aziendale leggera o simulata di un ambiente di sviluppo/test di Office 365 e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b5fe5-p103">La configurazione riportata in questo articolo non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server Active Directory (AD). Qui viene fornito come un'opzione in modo da poter sperimentare Office 365 e Dynamics 365 in un ambiente che rappresenta un'organizzazione tipica</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="b5fe5-114">Fase 2: Configurare e dimostrare l0integrazione di Dynamics 365 in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="b5fe5-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="b5fe5-115">Seguire questi passaggi per configurare la cassetta postale dell'amministratore globale per l'integrazione di Dynamics 365 ed Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="b5fe5-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="b5fe5-116">Mediante una sessione di private del browser, accedere a [http://portal.office.com](http://portal.office.com) e accedere utilizzando l'account amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-116">Using a private session of your browser, go to [http://portal.office.com](http://portal.office.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="b5fe5-117">Nella pagina **Microsoft Office Home**, fare clic sulla sezione **Posta di Outlook**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="b5fe5-118">Nella nuova scheda **Posta di Outlook** nel browser, fare clic su **Nuovo** e notare come l'angolo inferiore del riquadro sotto la casella per digitare un messaggio contiene un'icona per modelli personali.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message contains an icon for My Templates.</span></span>
    
     ![Un nuovo messaggio e-mail vuoto e privo d'integrazione con Dynamics 365.](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="b5fe5-120">Fare clic su **Ignora** e lasciare la scheda **Posta di Outlook** aperta.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="b5fe5-121">Fare clic sulla scheda **Microsoft Office Home** visualizzata nel browser, quindi fare clic sulla sezione **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="b5fe5-122">Nella barra di spostamento a sinistra della scheda **Interfaccia di amministrazione di Office**, fare clic su **Interfacce di amministrazione > Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="b5fe5-123">Nella nuova scheda **365 Dynamics** visualizzata nel browser, nell'elenco delle istanze di Dynamics 365 fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="b5fe5-124">Nella nuova scheda **Amministrazione** visualizzata nel browser, nella barra di spostamento, fare clic sulla freccia in giù accanto a **Impostazioni**, quindi fare clic su **Configurazione e-mail** in **Sistema**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="b5fe5-125">Nella pagina **Configurazione e-mail**, fare clic su **Impostazioni di configurazione e-mail**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="b5fe5-126">Nella scheda **E-mail** nella finestra di dialogo **Impostazioni di sistema**, modificare **Appuntamenti, contatti e attività** in **Sincronizzazione lato Server**, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="b5fe5-127">Nella pagina **Configurazione e-mail**, fare clic su **Cassette postali**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="b5fe5-128">Selezionare il nome di un amministratore globale di Office 365 nella colonna sinistra con segno di spunta, fare clic su **Applica impostazioni e-mail predefinite** nella barra degli strumenti, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="b5fe5-129">Fare clic su **Approva indirizzo e-mail** nella barra degli strumenti, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="b5fe5-130">Selezionare il nome di un amministratore globale di Office 365 nella colonna sinistra con segno di spunta, fare clic su **Verifica e abilita cassette postali** nella barra degli strumenti, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="b5fe5-131">Fare clic sulla scheda **Posta di Outlook** e verificare che l'amministratore globale abbia ricevuto un messaggio di prova.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="b5fe5-p104">Tornare alla scheda **Cassette postali Cassette postali personali attive** nel browser e aggiornare la pagina. Le colonne **Stato messaggi e-mail in arrivo** e **Stato messaggi e-mail in uscita** devono essere impostate su **Operazione riuscita** per il nome dell'account amministratore globale. Tenere presente che possono essere necessari fino a 15 minuti per completare entrambi i test.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="b5fe5-135">Seguire questi passaggi per installare l'App Dynamics 365 per Outlook e dimostrare le funzionalità di Dynamics 365 all'interno della cassetta postale dell'amministratore globale:</span><span class="sxs-lookup"><span data-stu-id="b5fe5-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="b5fe5-136">Nella scheda **Cassette postali Cassette postali personali attive** visualizzata nel browser, fare clic sulla freccia in giù accanto a **Impostazioni**, quindi fare clic su **App Dynamics 365 per Outlook** in **Sistema**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="b5fe5-p105">Nella pagina **Introduzione all'app Microsoft Dynamics 365 per Outlook** pagina, fare clic sul nome dell'amministratore globale, quindi fare clic su **Aggiungi app a Outlook**. La colonna **Stato** cambierà in **In sospeso**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="b5fe5-p106">Aggiornare la pagina finché non assume lo stato di **Aggiunto a Outlook**. Tenere presente che possono essere necessari fino a 15 minuti per completare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="b5fe5-141">Fare clic sulla scheda **Posta di Outlook** visualizzata nel browser, quindi chiuderla.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="b5fe5-142">Fare clic sulla scheda **Microsoft Office Home** visualizzata nel browser, quindi fare clic sulla sezione **Posta di Outlook**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="b5fe5-p107">Nella nuova scheda **Posta di Outlook**, fare clic su **Nuovo**. Tenere presente che l'angolo inferiore del riquadro sotto la casella per digitare un messaggio ora contiene un'icona per Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p107">On the new **Mail** tab in your browser, click **New**. Notice that the bottom corner of the pane below the box for typing a message now contains an icon for Dynamics 365.</span></span>
    
     ![Un nuovo messaggio e-mail vuoto dotato d'integrazione con Dynamics 365; visualizzazione della nuova icona.](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="b5fe5-p108">Fare clic sull'icona Dynamics 365. Verrà visualizzato un riquadro **Dynamics 365**, da cui è possibile tenere traccia della posta elettronica e accedere a modelli, documentazione di vendita o articoli.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="b5fe5-p109">Nel campo **A** del messaggio di posta elettronica, digitare **alex.y.wu@outlook.com**, quindi fare clic su **Riprova** nel riquadro **Dynamics 365**. Verrà visualizzata una sezione **Destinatari** nel riquadro **Dynamics 365** con le informazioni su Alex Wu, un contatto dall'applicazione vendita fornito con i dati di esempio per la sottoscrizione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![Riquadro informazioni di Dynamics 365 relativo a un contatto di vendita memorizzato in Dynamics 365.](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="b5fe5-151">Fare clic su **Ignora**.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="b5fe5-152">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b5fe5-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b5fe5-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b5fe5-153">See Also</span></span>

[<span data-ttu-id="b5fe5-154">Ambiente di sviluppo/test di Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b5fe5-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="b5fe5-155">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="b5fe5-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="b5fe5-156">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="b5fe5-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="b5fe5-157">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="b5fe5-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="b5fe5-158">DirSync per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="b5fe5-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="b5fe5-159">Gestione della sottoscrizione per Dynamics 365 (Online)</span><span class="sxs-lookup"><span data-stu-id="b5fe5-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="b5fe5-160">Amministrare Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b5fe5-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


