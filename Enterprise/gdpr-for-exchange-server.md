---
title: RGDP per Exchange Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Informazioni su come gestire i requisiti RGPD nell'ambiente Exchange Server locale.
ms.openlocfilehash: cf6d670134bd4aab60b97cd9f55e69a21ce06b19
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-exchange-server"></a><span data-ttu-id="e3e43-103">RGDP per Exchange Server</span><span class="sxs-lookup"><span data-stu-id="e3e43-103">GDPR for Exchange Server</span></span>

<span data-ttu-id="e3e43-104">Nell'ambito di protezione delle informazioni personali, si consiglia quanto segue:</span><span class="sxs-lookup"><span data-stu-id="e3e43-104">As part of safeguarding personal information, we recommend the following:</span></span>

-   <span data-ttu-id="e3e43-105">Utilizzare [tag e criteri di conservazione](https://technet.microsoft.com/library/dd297955(v=exchg.160).aspx) in Exchange Server per implementare un criterio di ciclo di vita della posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="e3e43-105">Use [Retention Tags and Policies](https://technet.microsoft.com/library/dd297955(v=exchg.160).aspx) in Exchange Server to implement an email life cycle policy.</span></span>

-   <span data-ttu-id="e3e43-106">Distribuire [Information Rights Management](https://technet.microsoft.com/library/dd638140(v=exchg.160).aspx) per limitare chi ha accesso alle informazioni archiviate in Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="e3e43-106">Deploy [Information Rights Management](https://technet.microsoft.com/library/dd638140(v=exchg.160).aspx) to limit who has access to information stored in Exchange Server.</span></span>

-   <span data-ttu-id="e3e43-107">Attivare la [crittografia BitLocker](https://blogs.technet.microsoft.com/exchange/2015/10/20/enabling-bitlocker-on-exchange-servers/) nei server.</span><span class="sxs-lookup"><span data-stu-id="e3e43-107">Enable [BitLocker encryption](https://blogs.technet.microsoft.com/exchange/2015/10/20/enabling-bitlocker-on-exchange-servers/) on your servers.</span></span>

## <a name="identifying-in-scope-content"></a><span data-ttu-id="e3e43-108">Identificare il contenuto nell'ambito</span><span class="sxs-lookup"><span data-stu-id="e3e43-108">Identifying In-scope Content</span></span>

<span data-ttu-id="e3e43-p101">Exchange utilizza due archivi principali per il contenuto generato dall'utente finale: cassette postali e cartelle pubbliche. Il contenuto archiviato nella cassetta postale di un utente individuale è associato in modo univoco a quell'utente e rappresenta il repository predefinito di Exchange. I dati archiviati in una cassetta postale utente includono il contenuto creato con client Outlook, Outlook sul web (precedentemente noto come Outlook Web App), Exchange ActiveSync, Skype for Business e altri strumenti di terze parti che si connettono ai server di Exchange tramite POP, IMAP o Servizi Web Exchange. Esempi di questi elementi sono: messaggi, elementi del calendario (riunioni e appuntamenti), contatti, note e attività. Eliminando la cassetta postale di un utente individuale si elimina il contenuto generato da o inviato direttamente all'utente nel contesto della propria cassetta postale. È possibile eliminare le cassette postali dell'utente tramite l'interfaccia di amministrazione di Exchange (EAC) o tramite il cmdlet [Remove-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/remove-mailbox?view=exchange-ps) in Exchange Management Shell.\\</span><span class="sxs-lookup"><span data-stu-id="e3e43-p101">Exchange uses two primary storage repositories for end user generated content: mailboxes and public folders. Content stored in an individual user’s mailbox is uniquely associated to that user and represents their default repository within Exchange. The data stored in a user mailbox includes content created using Outlook, Outlook on the web (formerly known as Outlook Web App), Exchange ActiveSync, Skype for Business clients and other third-party tools that connect to Exchange servers using POP, IMAP or Exchange Web Services (EWS). Examples of these items include: messages, calendar items (meetings and appointments), contacts, notes and tasks. Deleting an individual user’s mailbox removes content generated by or sent directly to the user in the context of their mailbox. You can delete user mailboxes by using the Exchange admin center (EAC) or the [Remove-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/remove-mailbox?view=exchange-ps) cmdlet in the Exchange Management Shell.\\</span></span>
<span data-ttu-id="e3e43-115">Nota: Il parametro Permanent sul cmdlet Remove-Mailbox deve essere utilizzato con cautela poiché i dati non saranno recuperabili se si utilizza questa opzione.</span><span class="sxs-lookup"><span data-stu-id="e3e43-115">Note: The Permanent parameter on the Remove-Mailbox cmdlet should be used with caution as the data will not be recoverable if this option is used.</span></span>

<span data-ttu-id="e3e43-p102">Exchange fornisce anche le cassette postali condivise che consentono a uno o più utenti di inviare e ricevere il contenuto archiviato in una cassetta postale comune. La cassetta postale condivisa è un'entità univoca non associata a un singolo account. Invece, più utenti sono autorizzati a inviare, ricevere ed esaminare i contenuti di posta elettronica nella cassetta postale condivisa. Le cassette postali condivise sono gestite tramite l'interfaccia di amministrazione di Exchange e tramite gli stessi cmdlet utilizzati per gestire le normali cassette postali utente. Se è necessario rimuovere i singoli messaggi da una cassetta postale, sono disponibili opzioni diverse a seconda della versione di Exchange. In Exchange Server 2010 e 2013, è possibile usare il cmdlet [Search-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/search-mailbox?view=exchange-ps) con il parametro DeleteContent per identificare e rimuovere i messaggi da una cassetta postale. In Exchange Server 2016 e versioni successive, è necessario usare la funzionalità [New-ComplianceSearch](https://technet.microsoft.com/library/ff459253(v=exchg.160).aspx).</span><span class="sxs-lookup"><span data-stu-id="e3e43-p102">Exchange also provides shared mailboxes that allow one or more users access to send and receive content that’s stored in a common mailbox. The shared mailbox is a unique entity that’s not associated with a single account. Instead, multiple users are granted access to send, receive and review email content in the shared mailbox. Shared mailboxes are administered using the Exchange admin center and the same cmdlets used to manage regular user mailboxes. If you need to remove individual messages from a mailbox, there are different options available depending upon the version of Exchange. In Exchange Server 2010 and 2013, you can use the [Search-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/search-mailbox?view=exchange-ps) cmdlet with the DeleteContent parameter to identify and remove messages from a mailbox. In Exchange Server 2016 and later, you need to use the [New-ComplianceSearch](https://technet.microsoft.com/library/ff459253(v=exchg.160).aspx) functionality.</span></span>

<span data-ttu-id="e3e43-p103">Le cartelle pubbliche sono un'implementazione di archiviazione condivisa che non è associata a un utente specifico. Invece gli utenti possono accedere alle cartelle pubbliche per generare contenuto. L'implementazione delle cartelle pubbliche effettiva varia a seconda della versione di Exchange (Exchange Server 2010 utilizza un'implementazione diversa rispetto a Exchange Server 2013 e versioni successive). Per gestire il contenuto delle cartelle pubbliche sono disponibili strumenti limitati. Gli strumenti client (ad esempio Outlook) sono il meccanismo principale per la gestione dei contenuti nelle cartelle pubbliche. Sono disponibili i cmdlet per la gestione degli oggetti della cartella pubblica, ma non per la gestione dei singoli elementi contenuti nella cartella pubblica. Sarà probabilmente necessario uno script personalizzato che utilizza i Servizi Web Exchange o altri strumenti di terze parti per gestire gli elementi delle cartelle pubbliche.</span><span class="sxs-lookup"><span data-stu-id="e3e43-p103">Public folders are a shared storage implementation that’s not associated with a specific user. Instead, users are granted access to public folders to generate content. The actual implementation of public folders varies depending upon the version of Exchange (Exchange Server 2010 uses a different implementation than Exchange Server 2013 and later). Limited tools exist to manage the content in public folders. Client tools (for example, Outlook) are the primary mechanism for managing content in public folders. There are cmdlets for managing public folder objects, but not for managing individual content items within the public folder. A custom script that leverages Exchange Web Services (EWS) or other third-party tools will likely be needed to manage individual public folder items.</span></span>

<span data-ttu-id="e3e43-p104">Il requisito principale probabilmente gestirà il contenuto della cassetta postale dell'utente individuale. Questo requisito verrà risolto facilmente utilizzando gli strumenti di grafica o basati su cmdlet usati regolarmente per gestire le cassette postali. Se è necessario elaborare il contenuto su più cassette postali o i tipi di risorse [eDiscovery](https://technet.microsoft.com/library/dd298021(v=exchg.160).aspx) è la soluzione migliore in Exchange per identificare il contenuto nell'ambito.</span><span class="sxs-lookup"><span data-stu-id="e3e43-p104">The primary requirement will likely be managing individual user mailbox content. This requirement will be easily addressed through the graphical or cmdlet-based tools that you regularly use to manage mailboxes. If you need to process content across multiple mailboxes or types of resources, [eDiscovery](https://technet.microsoft.com/library/dd298021(v=exchg.160).aspx) is the preferred mechanism within Exchange to identify in-scope content.</span></span>

## <a name="deleted-item-retention"></a><span data-ttu-id="e3e43-133">Mantenimento elementi eliminati</span><span class="sxs-lookup"><span data-stu-id="e3e43-133">Deleted Item Retention</span></span>

<span data-ttu-id="e3e43-p105">Quando si eliminano messaggi individuali o elementi da una cassetta postale (non l'intera cassetta postale o una risorsa cartella pubblica) il contenuto viene mantenuto in un modulo ripristinabile in base al valore del parametro DeletedItemRetention per il database della cassetta postale o database della cartella pubblica. Il valore predefinito è pari a 14 giorni, ma questo valore può essere configurato dall'amministratore di Exchange.</span><span class="sxs-lookup"><span data-stu-id="e3e43-p105">When you delete individual messages or items from a mailbox (not the entire mailbox or public folder resource itself) the content is retained in a recoverable form based on the value of the DeletedItemRetention parameter for the mailbox database or public folder database. The default value is 14 days, but this value is configurable by an Exchange administrator.</span></span>

## <a name="removing-soft-deleted-and-disconnected-mailboxes"></a><span data-ttu-id="e3e43-136">Rimozione di cassette postali disconnesse ed eliminate temporaneamente</span><span class="sxs-lookup"><span data-stu-id="e3e43-136">Removing Soft-Deleted and Disconnected Mailboxes</span></span>

<span data-ttu-id="e3e43-p106">Quando una cassetta postale di Exchange viene disattivata, eliminata o spostata tra database (ad esempio, durante il bilanciamento del carico), la cassetta postale viene posizionata nello stato disabilitato, eliminato temporaneamente o disconnesso a seconda dell'operazione. Con la cassetta postale in uno di questi stati, Exchange mantiene la cassetta postale, che include il contenuto, in base al valore corrente del parametro MailboxRetention specificato per il database delle cassette postali. Il valore predefinito è di 30 giorni, ma questo valore può essere configurato dall'amministratore di Exchange. È possibile usare il cmdlet [Remove-StoreMailbox](https://docs.microsoft.com/powershell/module/exchange/mailbox-databases-and-servers/remove-storemailbox?view=exchange-ps) per forzare Exchange a rimuovere definitivamente (eliminare) tutti i dati associati a una cassetta postale prima della scadenza naturale del periodo di mantenimento.</span><span class="sxs-lookup"><span data-stu-id="e3e43-p106">When an Exchange mailbox is disabled, deleted or moved between databases (for example, as a part of load balancing), the mailbox is placed into a disabled, soft-deleted or disconnected state depending on the operation. While the mailbox is in any of these states, Exchange maintains the mailbox (which includes its contents) based on the current value of the MailboxRetention parameter that’s specified on the mailbox database. The default value is 30 days, but this value is configurable by an Exchange administrator. You can use the [Remove-StoreMailbox](https://docs.microsoft.com/powershell/module/exchange/mailbox-databases-and-servers/remove-storemailbox?view=exchange-ps) cmdlet to force Exchange to permanently remove (purge) all data associated with a mailbox prior to the retention period expiring naturally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3e43-141">Utilizzare il cmdlet Remove-StoreMailbox con cautela poiché genera una perdita di dati irreversibile per la cassetta postale di destinazione.</span><span class="sxs-lookup"><span data-stu-id="e3e43-141">Use the Remove-StoreMailbox cmdlet with caution as it results in an unrecoverable loss of data for the target mailbox.</span></span> 

## <a name="on-prem-to-cloud-migrations"></a><span data-ttu-id="e3e43-142">Migrazioni da locale al cloud</span><span class="sxs-lookup"><span data-stu-id="e3e43-142">On-Prem to Cloud Migrations</span></span>

<span data-ttu-id="e3e43-p107">Durante la migrazione dei dati da Exchange Server a Exchange Online, i dati migrati possono continuare a trovarsi su Exchange Server locale di origine in un modulo recuperato da un amministratore di Exchange. Per impostazione predefinita, questi dati vengono automaticamente rimossi dal database entro 30 giorni (vedere la sezione precedente Rimozione di cassette postali disconnesse ed eliminate temporaneamente).</span><span class="sxs-lookup"><span data-stu-id="e3e43-p107">While migrating data from Exchange Server to Exchange Online, migrated data may continue to reside on the source on-premises Exchange Server in a form that’s recoverable by an Exchange administrator. By default, this data will be automatically removed from the database within 30 days (see the Removing Soft-Deleted and Disconnected Mailboxes section above).</span></span>

## <a name="automatic-data-collection-reported-to-microsoft-by-exchange-server"></a><span data-ttu-id="e3e43-145">Raccolta automatica dei dati segnalata a Microsoft da Exchange Server</span><span class="sxs-lookup"><span data-stu-id="e3e43-145">Automatic Data Collection Reported to Microsoft by Exchange Server</span></span>

<span data-ttu-id="e3e43-p108">Exchange Server distribuiti in ambienti locali non forniscono alcun tipo di segnalazione automatica o di acquisizione dati dell'utente finale a Microsoft. Exchange Server con abilitata la segnalazione di dump di arresto anomalo del sistema di Dr Watson nel sistema operativo Windows possono ricevere contenuto di memoria limitato al momento in cui viene visualizzato il report di arresto anomalo.</span><span class="sxs-lookup"><span data-stu-id="e3e43-p108">Exchange Servers deployed in on-premises environments do not provide any type of automated reporting or end user data capture to Microsoft. Exchange Servers that have Watson crash dump reporting enabled in the Windows Operating System may receive limited contents of memory at the time the crash report is produced.</span></span>