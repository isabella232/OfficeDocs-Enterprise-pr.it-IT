---
title: Perché è necessario usare PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Riepilogo: comprendere il motivo per cui è necessario utilizzare PowerShell di Office 365 per gestire Office 365, in alcuni casi in modo più efficiente e in altri casi per necessità.'
ms.openlocfilehash: be117dd2e4eaa7f3e2e95cd0d2444bd5b813bccb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071152"
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="949a6-103">Perché è necessario usare PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="949a6-103">Why you need to use Office 365 PowerShell</span></span>

 <span data-ttu-id="949a6-104">**Sintesi:** comprendere il motivo per cui è necessario utilizzare PowerShell di Office 365 per gestire Office 365, in alcuni casi in modo più efficiente e in altri casi per necessità.</span><span class="sxs-lookup"><span data-stu-id="949a6-104">**Summary:** Understand why you must use Office 365 PowerShell to manage Office 365, in some cases more efficiently and in other cases by necessity.</span></span>
  
<span data-ttu-id="949a6-105">Con l'interfaccia di amministrazione di Microsoft 365, è possibile non solo gestire gli account utente e le licenze di Office 365, ma è anche possibile gestire i prodotti di Office 365 server: Exchange, Skype for business online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="949a6-105">With the Microsoft 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 server products: Exchange, Skype for Business Online, and SharePoint Online.</span></span> <span data-ttu-id="949a6-106">Tuttavia, questi elementi possono essere gestiti anche con i comandi PowerShell di PowerShell di Office 365, sfruttando un ambiente con riga di comando e linguaggio di scripting per velocità, automazione e funzionalità aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="949a6-106">However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="949a6-107">In questo articolo verranno illustrati i modi in cui è possibile utilizzare PowerShell di Office 365 per gestire Office 365.</span><span class="sxs-lookup"><span data-stu-id="949a6-107">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365.</span></span>
  
- <span data-ttu-id="949a6-108">Office 365 PowerShell è in grado di rivelare informazioni aggiuntive che non sono visibili con l'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="949a6-108">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="949a6-109">Office 365 presenta funzionalità che è possibile configurare solo mediante PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="949a6-109">Office 365 has features that you can only configure by using Office 365 PowerShell</span></span>
    
- <span data-ttu-id="949a6-110">PowerShell di Office 365 è ideale per l'esecuzione di operazioni di massa</span><span class="sxs-lookup"><span data-stu-id="949a6-110">Office 365 PowerShell is great at performing bulk operations</span></span>
    
- <span data-ttu-id="949a6-111">PowerShell di Office 365 è ottimo per filtrare i dati</span><span class="sxs-lookup"><span data-stu-id="949a6-111">Office 365 PowerShell is great at filtering data</span></span>
    
- <span data-ttu-id="949a6-112">PowerShell di Office 365 facilita la stampa e il salvataggio dei dati</span><span class="sxs-lookup"><span data-stu-id="949a6-112">Office 365 PowerShell makes it easy to print or save data</span></span>
    
- <span data-ttu-id="949a6-113">PowerShell di Office 365 consente di gestire diversi prodotti server</span><span class="sxs-lookup"><span data-stu-id="949a6-113">Office 365 PowerShell lets you manage across server products</span></span>
    
<span data-ttu-id="949a6-p102">Prima di iniziare, comprendere che PowerShell di Office 365 è un insieme di moduli per Windows PowerShell, un ambiente con riga di comando per i servizi e le piattaforme basati su Windows. Questo ambiente crea un linguaggio della shell dei comandi che è possibile estendere con moduli aggiuntivi e offre un modo per eseguire comandi o script semplici o complessi. Ad esempio, dopo l'installazione dei moduli di PowerShell di Office 365 e la connessione alla sottoscrizione di Office 365, è possibile eseguire questo comando per visualizzare l'elenco di tutte le cassette postali utente per Microsoft Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="949a6-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts. For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```
Get-Mailbox
```

<span data-ttu-id="949a6-117">La possibilità di ottenere l'elenco delle cassette postali può essere completata facilmente utilizzando l'interfaccia di amministrazione di Microsoft 365, ma il conteggio del numero di elementi in tutti gli elenchi di tutti i siti per tutte le app Web non può essere effettuato facilmente.</span><span class="sxs-lookup"><span data-stu-id="949a6-117">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="949a6-118">Tenere presente che Office 365 PowerShell è stato creato per aumentare e migliorare la possibilità di gestire Office 365, non per sostituire l'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="949a6-118">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="949a6-119">In qualità di amministratore di Office 365, è necessario almeno acquisire familiarità con PowerShell di Office 365 poiché esistono alcune procedure di configurazione che possono essere eseguite solo con i comandi di PowerShell di Office 365.</span><span class="sxs-lookup"><span data-stu-id="949a6-119">As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands.</span></span> <span data-ttu-id="949a6-120">In questi casi, verrà richiesto di conoscere le procedure per effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="949a6-120">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="949a6-121">Installare i moduli di PowerShell di Office 365 (operazione eseguita solo una volta per ogni computer di amministratore).</span><span class="sxs-lookup"><span data-stu-id="949a6-121">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="949a6-122">Connettersi alla sottoscrizione di Office 365 (operazione eseguita una sola volta per ogni sessione di PowerShell).</span><span class="sxs-lookup"><span data-stu-id="949a6-122">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="949a6-123">Raccogliere le informazioni necessarie per eseguire i comandi di PowerShell di Office 365 necessari.</span><span class="sxs-lookup"><span data-stu-id="949a6-123">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="949a6-124">Eseguire correttamente i comandi di PowerShell di Office 365.</span><span class="sxs-lookup"><span data-stu-id="949a6-124">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="949a6-p104">Dopo aver appreso le competenze di base, non è necessario elencare gli utenti delle cassette postali con il comando **Get-Mailbox**, né saper creare un nuovo comando simile a quello precedente per contare tutti gli elementi in tutti gli elenchi di tutti i siti per tutte le app Web. Microsoft e la community degli amministratori di Office 365 possono offrire supporto per questa operazione.</span><span class="sxs-lookup"><span data-stu-id="949a6-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="949a6-127">Office 365 PowerShell è in grado di rivelare informazioni aggiuntive che non sono visibili con l'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="949a6-127">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="949a6-128">L'interfaccia di amministrazione di Microsoft 365 Visualizza molte informazioni utili, ma ciò non significa che Visualizza tutte le informazioni possibili che Office 365 archivia su utenti, licenze, cassette postali e siti.</span><span class="sxs-lookup"><span data-stu-id="949a6-128">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="949a6-129">Di seguito è riportato un esempio per **gli utenti e i gruppi** nell'interfaccia di amministrazione di Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="949a6-129">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Esempio di visualizzazione di utenti e gruppi nell'interfaccia di amministrazione di Microsoft 365.](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="949a6-131">Per diversi scopi, verranno visualizzate le informazioni necessarie.</span><span class="sxs-lookup"><span data-stu-id="949a6-131">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="949a6-132">Tuttavia, in alcuni casi sono necessarie informazioni aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="949a6-132">However, there are times when you need more.</span></span> <span data-ttu-id="949a6-133">Ad esempio, le licenze di Office 365 (e le funzionalità di Office 365 disponibili per un utente) dipendono in parte dalla posizione geografica dell'utente.</span><span class="sxs-lookup"><span data-stu-id="949a6-133">For example, Office 365 licensing (and the Office 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="949a6-134">I criteri e le funzionalità che è possibile estendere a un utente che vive negli Stati Uniti potrebbero non essere gli stessi per un utente che risiede in India o Belgio.</span><span class="sxs-lookup"><span data-stu-id="949a6-134">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="949a6-135">È possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per determinare la posizione geografica di un utente con questa procedura:</span><span class="sxs-lookup"><span data-stu-id="949a6-135">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="949a6-136">Fare doppio clic sul **Nome visualizzato** dell'utente.</span><span class="sxs-lookup"><span data-stu-id="949a6-136">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="949a6-137">Nelle proprietà del riquadro di visualizzazione dell'utente, fare clic su **Dettagli**.</span><span class="sxs-lookup"><span data-stu-id="949a6-137">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="949a6-138">Nella visualizzazione dettagli, fare clic su **ulteriori dettagli**.</span><span class="sxs-lookup"><span data-stu-id="949a6-138">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="949a6-139">Scorrere verso il basso fino a quando non viene visualizzata l'intestazione **Paese o regione**:</span><span class="sxs-lookup"><span data-stu-id="949a6-139">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Esempio di informazioni sull'area geografica per un utente nell'interfaccia di amministrazione di Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="949a6-141">Prendere nota del nome visualizzato e della posizione dell'utente su un pezzo di carta o copiarlo e incollarlo nel Blocco note.</span><span class="sxs-lookup"><span data-stu-id="949a6-141">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="949a6-p107">È necessario ripetere questa procedura per ogni utente. Per molti utenti, potrebbe trattarsi di un'attività noiosa. Con PowerShell di Office 365, è possibile visualizzare queste informazioni per tutti gli utenti con il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="949a6-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> <span data-ttu-id="949a6-145">Questo comando richiede l'installazione del [modulo di Windows Azure Active Directory](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="949a6-145">This command requires you to install the [Windows Azure Active Directory module](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).</span></span> 
  
<span data-ttu-id="949a6-146">Ecco un esempio di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="949a6-146">Here is an example of the display:</span></span>
  
```
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="949a6-147">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente ( **Get-MsolUser** ), ma visualizzare solo il nome e la posizione di ogni utente ( **Select DisplayName, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-147">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="949a6-p108">Poiché PowerShell di Office 365 supporta un linguaggio della shell dei comandi, è possibile modificare ulteriormente le informazioni ottenute dal comando **Get-MSolUser**. Ad esempio, se si desidera ordinare tali utenti per posizione, è possibile raggruppare tutti gli utenti brasiliani, tutti gli utenti degli Stati Uniti e così via. Ecco il comando:</span><span class="sxs-lookup"><span data-stu-id="949a6-p108">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="949a6-150">Ecco un esempio di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="949a6-150">Here is an example of the display:</span></span>
  
```
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  <span data-ttu-id="949a6-151">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente, ma visualizzare solo il nome e il percorso per ciascun utente, e ordinarli prima in base alla posizione, quindi in base ai nomi ( **Sort UsageLocation, DisplayName** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-151">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="949a6-p109">È inoltre possibile utilizzare altre opzioni di filtro. Ad esempio, se si desidera visualizzare tali informazioni sugli utenti residenti in Brasile, utilizzare questo comando:</span><span class="sxs-lookup"><span data-stu-id="949a6-p109">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="949a6-154">Ecco un esempio di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="949a6-154">Here is an example of the display:</span></span>
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="949a6-155">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente la cui posizione è il Brasile ( **Where {$\_.UsageLocation -eq "BR"}** ), quindi visualizzare posizione e nome di ogni utente.</span><span class="sxs-lookup"><span data-stu-id="949a6-155">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="949a6-156">**Nota rapida riguardo i domini più grandi**</span><span class="sxs-lookup"><span data-stu-id="949a6-156">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="949a6-p110">Se si dispone di un dominio di grandi dimensioni, con decine di migliaia di utenti, alcuni degli esempi mostrati in questo articolo potrebbero causare una "limitazione". Ciò significa che, in base a dati come la potenza di elaborazione e lunghezza di banda disponibile, si sta cercando di effettuare troppe operazioni contemporaneamente. Per questo, le organizzazioni più grandi potrebbero desiderare di dividere alcuni comandi di PowerShell di Office 365 in due. Ad esempio, questo comando restituisce tutti gli account utente e mostra il nome e la posizione di ciascun utente:</span><span class="sxs-lookup"><span data-stu-id="949a6-p110">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="949a6-p111">Questa operazione funziona perfettamente per i domini più piccoli. Nelle organizzazioni di grandi dimensioni, tuttavia, potrebbe essere necessario dividerlo in due comandi: un comando per archiviare le informazioni sugli account utente in una variabile, l'altro per visualizzare le informazioni necessarie. Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="949a6-p111">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


<span data-ttu-id="949a6-164">L'interpretazione di questo set di comandi PowerShell di Office 365 è:</span><span class="sxs-lookup"><span data-stu-id="949a6-164">The interpretation of this set of Office 365 PowerShell commands is:</span></span>
- <span data-ttu-id="949a6-165">Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente e archiviare le informazioni in una variabile denominata $x ( **$x = Get-MsolUser** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-165">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="949a6-166">Visualizzare il contenuto della variabile $x, ma includere solo il nome e la posizione di ciascun utente ( **$x | Select DisplayName, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-166">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="949a6-167">Office 365 presenta funzionalità che è possibile configurare solo con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="949a6-167">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>

<span data-ttu-id="949a6-168">L'interfaccia di amministrazione di Microsoft 365 ha lo scopo di consentire l'accesso alle attività amministrative più comuni o significative che si applicano alla maggior parte delle persone.</span><span class="sxs-lookup"><span data-stu-id="949a6-168">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="949a6-169">In altre parole, l'interfaccia di amministrazione di Microsoft 365 è stata progettata in modo che l'amministratore comune potesse utilizzare lo strumento per eseguire le attività di gestione più comuni.</span><span class="sxs-lookup"><span data-stu-id="949a6-169">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="949a6-170">In base a questa definizione, significa che sono presenti alcune attività che non possono essere completate tramite l'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="949a6-170">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="949a6-171">Ad esempio, l'interfaccia di amministrazione di Skype for Business online offre alcune opzioni per la creazione di convocazioni di riunioni personalizzate:</span><span class="sxs-lookup"><span data-stu-id="949a6-171">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Esempio di visualizzazione di inviti personalizzati a riunioni nell’interfaccia di amministrazione di Skype for Business online.](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="949a6-p113">Con queste impostazioni, è possibile aggiungere un tocco di personalizzazione e professionalità alle convocazioni di riunioni. Tuttavia, esistono più impostazioni di configurazione di una riunione rispetto alla semplice creazione di convocazioni personalizzate. Ad esempio, per impostazione predefinita le riunioni consentono:</span><span class="sxs-lookup"><span data-stu-id="949a6-p113">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="949a6-176">A utenti anonimi di ottenere l'ingresso automatico a ogni riunione.</span><span class="sxs-lookup"><span data-stu-id="949a6-176">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="949a6-177">Ai partecipanti di registrare una riunione.</span><span class="sxs-lookup"><span data-stu-id="949a6-177">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="949a6-178">A tutti gli utenti dell'organizzazione di essere designati come relatori quando partecipano a riunione.</span><span class="sxs-lookup"><span data-stu-id="949a6-178">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="949a6-p114">Queste impostazioni non sono disponibili dall'interfaccia di amministrazione di Skype for Business online. Tuttavia, è possibile controllarle da PowerShell di Office 365. Ecco un comando che consente di disabilitare queste tre impostazioni:</span><span class="sxs-lookup"><span data-stu-id="949a6-p114">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="949a6-182">Questo comando richiede l'installazione del [modulo di PowerShell per Skype for Business Online ](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="949a6-182">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="949a6-183">L'interpretazione di questo comando di PowerShell di Office 365 è: Per le impostazioni per le nuove riunioni di Skype for Business online ( **Set-CsMeetingConfiguration** ), disabilitare l'autorizzazione per gli utenti anonimi a ottenere l'accesso automatico alle riunioni ( **- AdmitAnonymousUsersByDefault $False** ), disattivare la possibilità per i partecipanti di registrare le riunioni ( **- AllowConferenceRecording $False** ) e non designare tutti gli utenti dell'organizzazione come relatori ( **-DesignateAsPresenter "None"** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-183">The interpretation of this Office 365 PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="949a6-184">Se si cambia idea e si desidera ripristinare le impostazioni predefinite (tutte abilitate), sarà sufficiente eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="949a6-184">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="949a6-p115">Questo è solo un esempio. Ne esistono altri, per questo motivo l'amministratore di Office 365 deve avere una certa familiarità con l'esecuzione dei comandi di PowerShell di Office 365.</span><span class="sxs-lookup"><span data-stu-id="949a6-p115">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="949a6-187">PowerShell di Office 365 è ottimale per eseguire operazioni in massa</span><span class="sxs-lookup"><span data-stu-id="949a6-187">Office 365 PowerShell is great at carrying out bulk operations</span></span>

<span data-ttu-id="949a6-188">Storicamente, le interfacce visive come l'interfaccia di amministrazione di Microsoft 365 sono più importanti quando si ha un'unica operazione da eseguire.</span><span class="sxs-lookup"><span data-stu-id="949a6-188">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="949a6-189">Ad esempio, se è necessario disabilitare un account utente, è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per individuare e cancellare rapidamente una casella di controllo.</span><span class="sxs-lookup"><span data-stu-id="949a6-189">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="949a6-190">Questa operazione può risultare più semplice rispetto all'esecuzione di un'operazione simile in PowerShell di Office 365.</span><span class="sxs-lookup"><span data-stu-id="949a6-190">This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="949a6-191">Tuttavia, se è necessario modificare molte cose o alcuni elementi selezionati all'interno di un insieme di grandi dimensioni, è possibile che l'interfaccia di amministrazione di Microsoft 365 non sia il miglior utilizzo del proprio tempo.</span><span class="sxs-lookup"><span data-stu-id="949a6-191">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="949a6-192">Ad esempio, se è stato necessario cambiare il prefisso su migliaia di numeri di telefono o se è necessario rimuovere un utente specifico, Ken remario, da tutti i siti di SharePoint Online, come è possibile eseguire tale operazione nell'interfaccia di amministrazione di Microsoft 365?</span><span class="sxs-lookup"><span data-stu-id="949a6-192">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="949a6-193">Per quanto riguarda l'ultimo esempio, sono presenti diverse centinaia di siti di SharePoint Online e non si sa nemmeno di quali di questi siti è membro Ken Meyer.</span><span class="sxs-lookup"><span data-stu-id="949a6-193">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="949a6-194">Questo significa che sarà necessario iniziare dall'interfaccia di amministrazione di Microsoft 365 e quindi eseguire questa procedura per ogni sito:</span><span class="sxs-lookup"><span data-stu-id="949a6-194">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="949a6-195">Fare clic sull' **URL** del sito.</span><span class="sxs-lookup"><span data-stu-id="949a6-195">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="949a6-196">Nella casella **proprietà della raccolta del sito**, fare clic sul link **Indirizzo sito Web** per aprire il sito.</span><span class="sxs-lookup"><span data-stu-id="949a6-196">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="949a6-197">Nel sito, fare clic su **Condividi**.</span><span class="sxs-lookup"><span data-stu-id="949a6-197">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="949a6-198">Nella finestra di dialogo **Condividi** fare clic sul link che mostra tutti gli utenti che dispongono delle autorizzazioni per il sito:</span><span class="sxs-lookup"><span data-stu-id="949a6-198">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![Esempio di visualizzazione di membri del sito SharePoint Online nell'interfaccia di amministrazione di SharePoint Online.](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="949a6-200">Nella finestra di dialogo **Condiviso con** fare clic su **Avanzate**.</span><span class="sxs-lookup"><span data-stu-id="949a6-200">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="949a6-201">Scorrere l'elenco degli utenti, trovare e selezionare Ken Myer (presumendo che disponga delle autorizzazioni per il sito), quindi fare clic su **Rimuovi autorizzazioni utente**.</span><span class="sxs-lookup"><span data-stu-id="949a6-201">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="949a6-202">La procedura può richiedere molto tempo per diverse centinaia di siti.</span><span class="sxs-lookup"><span data-stu-id="949a6-202">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="949a6-203">L'alternativa consiste nell'usare PowerShell di Office 365 e il seguente comando per rimuovere Ken Myer da tutti i siti:</span><span class="sxs-lookup"><span data-stu-id="949a6-203">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="949a6-204">Questo comando richiede l'installazione di [ Connect per PowerShell di SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="949a6-204">This command requires that you install the [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="949a6-205">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti i siti di SharePoint nella sottoscrizione di Office 365 corrente ( **Get-SPOSite** ) e per ogni sito, rimuovere Ken Meyer dall'elenco di utenti che possono accedervi ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-205">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="949a6-206">Perché stiamo indicando a Office 365 di rimuovere Ken Meyer da tutti i siti, inclusi quelli a cui non può accedere, la visualizzazione di questo comando mostrerà degli errori per i siti per i quali al momento non dispone dell'accesso.</span><span class="sxs-lookup"><span data-stu-id="949a6-206">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="949a6-207">È possibile utilizzare una condizione aggiuntiva su questo comando, per rimuovere Ken Meyer solo dai siti in cui compare nell'elenco degli accessi, ma gli errori elencati non danneggiano i siti.</span><span class="sxs-lookup"><span data-stu-id="949a6-207">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="949a6-208">Questo comando potrebbe richiedere alcuni minuti per l'esecuzione in centinaia di siti anziché ore di utilizzo dell'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="949a6-208">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="949a6-p120">Ecco un altro esempio di operazione di massa. Utilizzare questo comando per aggiungere Bonnie Kearney, un nuovo amministratore di SharePoint, a tutti i siti dell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="949a6-p120">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="949a6-211">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti i siti di SharePoint nella sottoscrizione di Office 365 corrente e, per ogni sito, consentire l'accesso a Bonnie Kearney aggiungendo il suo nome di accesso al gruppo Membri del sito ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-211">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="949a6-212">PowerShell di Office 365 è molto utile per il filtro dei dati</span><span class="sxs-lookup"><span data-stu-id="949a6-212">Office 365 PowerShell is great at filtering data</span></span>

<span data-ttu-id="949a6-213">L'interfaccia di amministrazione di Microsoft 365 offre diversi modi per filtrare i dati in modo da individuare rapidamente e facilmente un sottoinsieme di informazioni mirato.</span><span class="sxs-lookup"><span data-stu-id="949a6-213">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="949a6-214">Ad esempio, Exchange facilita il filtro di qualsiasi proprietà relativa alla cassetta postale di un utente.</span><span class="sxs-lookup"><span data-stu-id="949a6-214">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="949a6-215">Ad esempio, questo è un elenco delle cassette postali degli utenti che vivono nella città di Bloomington:</span><span class="sxs-lookup"><span data-stu-id="949a6-215">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![Esempio di ricerca avanzata nell'interfaccia di amministrazione di Microsoft 365 per l'elenco delle cassette postali per tutti gli utenti che vivono nella città di Bloomington.](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="949a6-p122">L'interfaccia di amministrazione di Exchange consente di combinare i criteri di filtro. Ad esempio, è possibile trovare le cassette postali di tutti i residenti di Bloomington e di coloro che lavorano nel reparto finanziario.</span><span class="sxs-lookup"><span data-stu-id="949a6-p122">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="949a6-p123">Tuttavia, esistono limitazioni per le operazioni che è possibile eseguire nell'interfaccia di amministrazione di Exchange. Ad esempio, si potrebbe desiderare di individuare le cassette postali di persone che vivono a Bloomington o San Diego oppure le cassette postali di tutte le persone non residenti a Bloomington.</span><span class="sxs-lookup"><span data-stu-id="949a6-p123">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="949a6-221">Con PowerShell di Office 365 è possibile ottenere un elenco delle cassette postali di tutte le persone che vivono nelle città di Bloomington o San Diego grazie a questo comando:</span><span class="sxs-lookup"><span data-stu-id="949a6-221">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="949a6-222">Ecco un esempio di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="949a6-222">Here is an example of the display:</span></span>
  
```
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="949a6-223">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente che dispongono di una cassetta postale nelle città di San Diego o Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), quindi visualizzare il nome e la città di ognuno ( **Select DisplayName, City** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-223">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="949a6-224">Il comando di seguito consente di elencare tutte le cassette postali delle persone che vivono in qualsiasi altro posto a eccezione di Bloomington:</span><span class="sxs-lookup"><span data-stu-id="949a6-224">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="949a6-225">Ecco un esempio di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="949a6-225">Here is an example of the display:</span></span>
  
```
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  <span data-ttu-id="949a6-226">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente che dispongono di una cassetta postale non ubicata a Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), quindi visualizzare il nome e la città di ognuno.</span><span class="sxs-lookup"><span data-stu-id="949a6-226">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="949a6-p124">È inoltre possibile utilizzare caratteri jolly nei filtri PowerShell di Office 365 per trovare una corrispondenza con parte di un nome. Ad esempio, si supponga di effettuare la ricerca di un account utente e di ricordare solo che il cognome potrebbe corrispondere ad Anderson o forse a Henderson oppure Jorgenson.</span><span class="sxs-lookup"><span data-stu-id="949a6-p124">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="949a6-229">È possibile rintracciare l'utente nell'interfaccia di amministrazione di Microsoft 365 utilizzando lo strumento di ricerca ed effettuando tre ricerche diverse:</span><span class="sxs-lookup"><span data-stu-id="949a6-229">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="949a6-230">Una per  *Anderson*</span><span class="sxs-lookup"><span data-stu-id="949a6-230">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="949a6-231">Una per  *Henderson*</span><span class="sxs-lookup"><span data-stu-id="949a6-231">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="949a6-232">Una per  *Jorgenson*</span><span class="sxs-lookup"><span data-stu-id="949a6-232">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="949a6-p125">Poiché tutti e tre questi nomi terminano in "son", è possibile indicare a PowerShell di Office 365 di visualizzare tutti gli utenti il cui nome termina con "son". Ecco il comando:</span><span class="sxs-lookup"><span data-stu-id="949a6-p125">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="949a6-p126">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione a Office 365 corrente, ma utilizzare un filtro che elenca solo gli utenti il cui cognome termina in "son"( **-Filter '{LastName -like "\*son"}'** ). \* rappresenta qualsiasi set di caratteri, vale a dire lettere, nel caso del cognome di un utente.</span><span class="sxs-lookup"><span data-stu-id="949a6-p126">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ). The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="949a6-237">PowerShell di Office 365 facilita la stampa e il salvataggio dei dati</span><span class="sxs-lookup"><span data-stu-id="949a6-237">Office 365 PowerShell makes it easy to print or save data</span></span>

<span data-ttu-id="949a6-238">L'interfaccia di amministrazione di Microsoft 365 consente di visualizzare gli elenchi di dati.</span><span class="sxs-lookup"><span data-stu-id="949a6-238">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="949a6-239">Ecco un esempio dell'interfaccia di amministrazione di Skype for Business online che mostra un elenco di utenti che sono stati abilitati per Skype for Business online:</span><span class="sxs-lookup"><span data-stu-id="949a6-239">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Esempio di interfaccia di amministrazione di Skype for Business online che mostra un elenco di utenti abilitati a Skype for Business online.](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="949a6-241">Per salvare queste informazioni in un file, è necessario copiarle e incollarle in un documento o in Excel.</span><span class="sxs-lookup"><span data-stu-id="949a6-241">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="949a6-242">In entrambi i casi, la copia potrebbe richiedere ulteriore formattazione.</span><span class="sxs-lookup"><span data-stu-id="949a6-242">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="949a6-243">Inoltre, l'interfaccia di amministrazione di Microsoft 365 non consente di stampare direttamente l'elenco visualizzato.</span><span class="sxs-lookup"><span data-stu-id="949a6-243">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="949a6-p129">Fortunatamente, è possibile utilizzare PowerShell di Office 365 non solo per visualizzare l'elenco, ma anche per salvarlo in un file che può essere facilmente importato in Excel. Ecco un comando di esempio per salvare i dati utente di Skype for Business online in un file con valori delimitati da virgole (CSV), che può essere facilmente importato come tabella in un foglio di lavoro di Excel:</span><span class="sxs-lookup"><span data-stu-id="949a6-p129">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="949a6-246">Ecco un esempio di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="949a6-246">Here is an example of the display:</span></span>
  
![Esempio di tabella importata in un foglio Excel di dati di utenti di Skype for Business online, salvati in un file con valori delimitati da virgole (CSV).](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="949a6-248">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti di Skype for Business online nella sottoscrizione di Office 365 corrente ( **Get-CsOnlineUser** ), ottenere solo il nome utente, l'UPN e la posizione ( **Select DisplayName, UserPrincipalName, UsageLocation** ), quindi salvare le informazioni nel file CSV denominato C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-248">The interpretation of this Office 365 PowerShell command is: Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="949a6-p130">È anche possibile utilizzare le opzioni per salvare questo elenco come file XML o pagina HTML. Infatti, con altri comandi di PowerShell, è possibile salvarlo direttamente come file di Excel, con qualsiasi formattazione personalizzata che si desidera.</span><span class="sxs-lookup"><span data-stu-id="949a6-p130">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="949a6-p131">È anche possibile inviare l'output di un comando PowerShell di Office 365 che visualizza un elenco direttamente alla stampante predefinita in Windows. Ecco un esempio di comando:</span><span class="sxs-lookup"><span data-stu-id="949a6-p131">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="949a6-253">Di seguito, è riportato l'aspetto del documento stampato:</span><span class="sxs-lookup"><span data-stu-id="949a6-253">Here's what your printed document will look like:</span></span>
  
![Esempio di documento stampato, output di un comando Office 365 PowerShell elencato direttamente alla stampante predefinita in Windows.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="949a6-255">L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti di Skype for Business online nella sottoscrizione di Office 365 corrente, ottenere solo il nome utente, l'UPN e la posizione, e quindi inviare queste informazioni alla stampante predefinita di Windows ( **Out-Printer** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-255">The interpretation of this Office 365 PowerShell command is:  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="949a6-256">Il documento stampato presenta la stessa formattazione semplice visualizzata all'interno della finestra del comando PowerShell di Office 365, ma dopo aver creato un comando PowerShell di Office 365 per elencare gli elementi necessari, è sufficiente aggiungere **| Out-Printer** alla fine del comando per ottenere una copia stampata su cui lavorare.</span><span class="sxs-lookup"><span data-stu-id="949a6-256">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="949a6-257">PowerShell di Office 365 consente di gestire diversi prodotti server</span><span class="sxs-lookup"><span data-stu-id="949a6-257">Office 365 PowerShell lets you manage across server products</span></span>

<span data-ttu-id="949a6-p132">I diversi componenti che costituiscono Office 365 sono progettati per collaborare. Si supponga, ad esempio, di aggiungere un nuovo utente a Office 365 e, dopo aver eseguito l'operazione, di specificare informazioni come il reparto e il numero di telefono dell'utente. Queste informazioni saranno quindi disponibili se si accede alle informazioni dell'utente usando uno dei prodotti server di Office 365: Skype for Business online, Exchange o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="949a6-p132">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="949a6-p133">Si tratta di informazioni generali che interessano la famiglia di prodotti. Le informazioni specifiche di un prodotto, ad esempio quelle relative alla cassetta postale di Exchange di un utente, non sono generalmente disponibili tra le famiglie di prodotti. Ad esempio, se si desidera sapere se la cassetta postale di un utente è abilitata o meno, tale informazione è disponibile solo nell'interfaccia di amministrazione di Exchange.</span><span class="sxs-lookup"><span data-stu-id="949a6-p133">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="949a6-264">Si supponga di voler creare un report che mostra le seguenti informazioni per tutti gli utenti:</span><span class="sxs-lookup"><span data-stu-id="949a6-264">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="949a6-265">Nome visualizzato dell'utente</span><span class="sxs-lookup"><span data-stu-id="949a6-265">The user's display name</span></span>
    
- <span data-ttu-id="949a6-266">La disponibilità della licenza per Office 365 dell'utente</span><span class="sxs-lookup"><span data-stu-id="949a6-266">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="949a6-267">L'abilitazione della cassetta postale di Exchange dell'utente.</span><span class="sxs-lookup"><span data-stu-id="949a6-267">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="949a6-268">L'abilitazione per Skype for Business online dell'utente</span><span class="sxs-lookup"><span data-stu-id="949a6-268">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="949a6-269">Al momento non è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per produrre facilmente un rapporto di questo tipo.</span><span class="sxs-lookup"><span data-stu-id="949a6-269">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="949a6-270">Al contrario, è necessario creare un documento separato per archiviare le informazioni, ad esempio un foglio di lavoro di Excel, e ottenere tutti i nomi utente e le informazioni di licenza dall'interfaccia di amministrazione di Microsoft 365, ottenere le informazioni della cassetta postale dall'interfaccia di amministrazione di Exchange, ottenere Skype for Informazioni business online dall'interfaccia di amministrazione di Skype for business online e quindi raccogliere e combinare tali informazioni.</span><span class="sxs-lookup"><span data-stu-id="949a6-270">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="949a6-271">L'alternativa consiste nell'usare uno script di PowerShell di Office 365 che compili automaticamente questo report.</span><span class="sxs-lookup"><span data-stu-id="949a6-271">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="949a6-p135">Il seguente script di esempio è più complesso dei comandi che finora sono stati illustrati in questo articolo. Tuttavia, mostra la possibilità di utilizzare PowerShell di Office 365 per creare visualizzazioni delle informazioni che sono molto difficili da creare in altri modi. Ecco lo script in grado di compilare e visualizzare l'elenco necessario:</span><span class="sxs-lookup"><span data-stu-id="949a6-p135">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
```
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="949a6-275">Ecco un esempio di visualizzazione:</span><span class="sxs-lookup"><span data-stu-id="949a6-275">Here is an example of the display:</span></span>
  
```
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="949a6-276">L'interpretazione di questo script di PowerShell di Office 365 è:</span><span class="sxs-lookup"><span data-stu-id="949a6-276">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="949a6-277">Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente e archiviare le informazioni in una variabile denominata $x ( **$x = Get-MsolUser** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-277">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="949a6-278">Avviare un ciclo che viene eseguito su tutti gli utenti nella variabile denominata $x ( **foreach ($i in $x)** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-278">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="949a6-279">Definire una variabile denominata $y e archiviarvi all'interno le informazioni sulla cassetta postale dell'utente ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-279">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="949a6-280">Aggiungere una nuova proprietà alle informazioni sull'utente denominata IsMailBoxEnabled e impostarla sul valore della proprietà IsMailBoxEnabled della cassetta postale dell'utente ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-280">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="949a6-281">Definire una variabile denominata $y e archiviarvi all'interno le informazioni su Skype for Business Online relative all'utente ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-281">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="949a6-282">Aggiungere una nuova proprietà alle informazioni sull'utente denominata EnabledForSfB e impostarla sul valore della proprietà EnabledForSfB della cassetta postale dell'utente di Skype for Business Online ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-282">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="949a6-283">Visualizzare l'elenco di utenti, ma includere solo il nome, se dispongono di una licenza e le due nuove proprietà che indicano se la loro cassetta postale è abilitata e se loro sono abilitati per Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span><span class="sxs-lookup"><span data-stu-id="949a6-283">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="949a6-284">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="949a6-284">See also</span></span>

[<span data-ttu-id="949a6-285">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="949a6-285">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="949a6-286">Gestire gli account utente e le licenze con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="949a6-286">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="949a6-287">Utilizzo di Windows PowerShell per creare rapporti in Office 365</span><span class="sxs-lookup"><span data-stu-id="949a6-287">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

