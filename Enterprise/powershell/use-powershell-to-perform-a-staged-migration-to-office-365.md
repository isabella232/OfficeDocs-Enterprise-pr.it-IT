---
title: Utilizzare PowerShell per eseguire una migrazione a fasi a Office 365
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 'Riepilogo: informazioni sull''utilizzo di Windows PowerShell per eseguire una migrazione a fasi a Office 365.'
ms.openlocfilehash: 6c3ed6c0e37f7b99d3f26056dfe1b9d989388ff3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="f9912-103">Utilizzare PowerShell per eseguire una migrazione a fasi a Office 365</span><span class="sxs-lookup"><span data-stu-id="f9912-103">Use PowerShell to perform a staged migration to Office 365</span></span>

 <span data-ttu-id="f9912-104">**Sintesi:** Informazioni sull'utilizzo di Windows PowerShell per eseguire una migrazione a fasi a Office 365.</span><span class="sxs-lookup"><span data-stu-id="f9912-104">Summary: Learn how to use Windows PowerShell to perform a staged migration to Office 365.</span></span>
  
<span data-ttu-id="f9912-105">È possibile migrare i contenuti delle cassette postali degli utenti da un sistema di posta elettronica di origine a Office 365 nel tempo utilizzando una migrazione a fasi.</span><span class="sxs-lookup"><span data-stu-id="f9912-105">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="f9912-p101">In questo articolo vengono illustrate le attività necessarie per una migrazione della posta elettronica a fasi tramite PowerShell di Exchange Online. Nell'argomento [Informazioni utili su una migrazione a fasi della posta elettronica a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487) viene fornita una panoramica della procedura di migrazione. Una volta appresi i contenuti di questo articolo, utilizzare quest'ultimo per iniziare la migrazione delle cassette postali da un sistema di posta elettronica a un altro.</span><span class="sxs-lookup"><span data-stu-id="f9912-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f9912-p102">È anche possibile utilizzare l'interfaccia di amministrazione di Exchange per eseguire la migrazione a fasi. Vedere [Eseguire una migrazione a fasi della posta elettronica a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="f9912-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="f9912-111">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="f9912-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="f9912-p103">Tempo stimato per il completamento di questa attività: tra i 2 e i 5 minuti per creare un batch di migrazione. Dopo l'avvio del batch di migrazione, la durata della migrazione varia in base al numero di cassette postali nel batch, alla dimensione di ogni cassetta postale e alla capacità di rete disponibile. Per informazioni su altri fattori che influenzano il tempo necessario per eseguire la migrazione delle cassette postali su Office 365, vedere l'articolo relativo alle [prestazioni della migrazione](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="f9912-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="f9912-p104">È necessario disporre delle autorizzazioni per poter eseguire queste procedure. Per verificare le autorizzazioni necessarie, vedere la voce "Migrazione" nell'argomento [Autorizzazioni di destinatari](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="f9912-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="f9912-p105">Per utilizzare i cmdlet di PowerShell di Exchange Online, è necessario eseguire l'accesso e importare i cmdlet nella sessione di Windows PowerShell locale. Per le istruzioni, vedere [Connettersi a Exchange Online tramite Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="f9912-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="f9912-119">Per un elenco completo dei comandi di migrazione, vedere [Cmdlet di spostamento e migrazione](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="f9912-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="f9912-120">Procedura della migrazione</span><span class="sxs-lookup"><span data-stu-id="f9912-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="f9912-121">Passaggio 1: predisporre la migrazione a fasi</span><span class="sxs-lookup"><span data-stu-id="f9912-121">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="f9912-122">Prima di eseguire la migrazione delle cassette postali a Office 365 utilizzando una migrazione a fasi, esistono alcune modifiche che è necessario apportare al proprio ambiente di Exchange.</span><span class="sxs-lookup"><span data-stu-id="f9912-122">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="f9912-p106">**Configurare Outlook via Internet su Exchange Server locale** Il servizio di migrazione della posta elettronica utilizza Outlook via Internet (noto come RPC su HTTP) per connettersi a Exchange Server locale. Per informazioni su come impostare Outlook via Internet per Exchange Server 2007 e Exchange 2003, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="f9912-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="f9912-125">Exchange 2007: Come abilitare Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="f9912-125">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="f9912-126">Configurazione di Outlook via Internet con Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="f9912-126">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="f9912-p107">È necessario utilizzare un certificato rilasciato da un'autorità di certificazione attendibile (CA) con la configurazione di Outlook via Internet. Non è possibile configurare Outlook via Internet con un certificato autofirmato. Per ulteriori informazioni, vedere [Come configurare SSL per Outlook via Internet](https://go.microsoft.com/fwlink/?LinkID=80875)</span><span class="sxs-lookup"><span data-stu-id="f9912-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="f9912-130">**Facoltativo: verificare che sia possibile connettersi all'organizzazione di Exchange utilizzando Outlook via Internet** Utilizzare uno dei seguenti metodi per verificare le impostazioni di connessione.</span><span class="sxs-lookup"><span data-stu-id="f9912-130">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="f9912-131">Utilizzare Outlook all'esterno della rete aziendale per connettersi alla cassetta postale di Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="f9912-131">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="f9912-p108">Utilizzare [Microsoft Exchange Remote Connectivity Analyzer]((https://www.testexchangeconnectivity.com/)) per testare le impostazioni della connessione. Utilizzare i test di individuazione automatica di Outlook o Outlook via Internet (RPC su HTTP).</span><span class="sxs-lookup"><span data-stu-id="f9912-p108">Use the [Microsoft Exchange Remote Connectivity Analyzer]((https://www.testexchangeconnectivity.com/)) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="f9912-134">In PowerShell di Exchange Online, eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f9912-134">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="f9912-p109">**Impostare le autorizzazioni** L'account utente locale usato per connettersi all'organizzazione di Exchange locale (denominato anche amministratore della migrazione) deve disporre delle autorizzazioni necessarie per accedere alle cassette postali locali di cui si vuole eseguire la migrazione a Office 365. Questo account utente verrà usato per eseguire la connessione al sistema di posta elettronica creando un endpoint di migrazione più avanti in questa procedura ([Passaggio 3: creare un endpoint di migrazione](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="f9912-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="f9912-137">Per eseguire la migrazione delle cassette postali, l'amministratore deve disporre di uno dei seguenti set di autorizzazioni:</span><span class="sxs-lookup"><span data-stu-id="f9912-137">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="f9912-138">Essere un membro del gruppo **Domain Admins** di Active Directory nell'organizzazione locale.</span><span class="sxs-lookup"><span data-stu-id="f9912-138">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="f9912-139">oppure</span><span class="sxs-lookup"><span data-stu-id="f9912-139">or</span></span>
    
- <span data-ttu-id="f9912-140">Disporre dell'autorizzazione **FullAccess** per ogni cassetta postale locale e dell'autorizzazione **WriteProperty** per modificare la proprietà **TargetAddress** negli account utente locali.</span><span class="sxs-lookup"><span data-stu-id="f9912-140">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="f9912-141">oppure</span><span class="sxs-lookup"><span data-stu-id="f9912-141">or</span></span>
    
- <span data-ttu-id="f9912-142">Disporre dell'autorizzazione **Receive As** sul database delle cassette postali locale in cui sono memorizzate le cassette postali degli utenti e dell'autorizzazione **WriteProperty** per modificare la proprietà **TargetAddress** negli account utente locali.</span><span class="sxs-lookup"><span data-stu-id="f9912-142">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="f9912-143">Per istruzioni su come impostare queste autorizzazioni, vedere [Assegnazione delle autorizzazioni per la migrazione dalle cassette postali a Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span><span class="sxs-lookup"><span data-stu-id="f9912-143">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="f9912-p110">**Disabilitare la messaggistica unificata** Se la messaggistica unificata è attivata per le cassette postali locali, disattivarla prima di eseguirne le migrazione. Una volta completata la migrazione, attivare la messaggistica unificata per le cassette postali. Per le procedure da eseguire, vedere l'argomento relativo alla[disabilitazione della messaggistica unificata](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="f9912-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="f9912-p111">**Utilizzare la sincronizzazione delle directory per creare nuovi utenti in Office 365.** La sincronizzazione della directory consente di creare tutti gli utenti locali nell'organizzazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="f9912-p111">**Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="f9912-p112">Dopo avere creato gli utenti, è necessario assegnare loro le licenze. Il tempo disponibile per aggiungere le licenze dopo la creazione degli utenti è di 30 giorni. Per la procedura per aggiungere licenze, vedere [Passaggio 8: completare le attività successive alla migrazione](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="f9912-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="f9912-p113">È possibile usare lo Strumento di sincronizzazione di Microsoft Azure Active Directory o i Servizi di sincronizzazione di Microsoft Azure Active Directory per sincronizzare e creare gli utenti locali in Office 365. Dopo la migrazione delle cassette postali in Office 365, gli account utente verranno gestiti nell'organizzazione locale e saranno sincronizzati con l'organizzazione di Office 365. Per ulteriori informazioni, vedere [Integrazione di directory](https://go.microsoft.com/fwlink/?LinkId=521788) .</span><span class="sxs-lookup"><span data-stu-id="f9912-p113">You can use either the Microsoft Azure Active Directory Synchronization Tool or the Microsoft Azure Active Directory Sync Services (AAD Sync) to synchronize and create your on-premises users in Office 365. After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="f9912-155">Passaggio 2: creazione di un file CSV per un batch di migrazione a fasi</span><span class="sxs-lookup"><span data-stu-id="f9912-155">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="f9912-p114">Dopo aver individuato gli utenti per cui eseguire la migrazione delle cassette postali locali in Office 365, si userà un file con valori delimitati da virgole (CSV) per creare un batch di migrazione. Ogni riga nel file CSV, che viene usato da Office 365 per eseguire la migrazione, contiene informazioni relative a una cassetta postale locale.</span><span class="sxs-lookup"><span data-stu-id="f9912-p114">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="f9912-p115">Il numero di cassette postali che è possibile migrare in Office 365 utilizzando una migrazione a fasi è illimitato. Il file CSV per un batch di migrazione può contenere al massimo 2.000 righe. Per eseguire la migrazione di oltre 2.000 cassette postali, creare altri file CSV e usare ogni file per creare un nuovo batch di migrazione.</span><span class="sxs-lookup"><span data-stu-id="f9912-p115">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="f9912-161">**Attributi supportati**</span><span class="sxs-lookup"><span data-stu-id="f9912-161">**Supported attributes**</span></span>
  
<span data-ttu-id="f9912-p116">Il file CSV per una migrazione a fasi supporta i tre attributi seguenti. Ogni riga nel file CSV corrisponde a una cassetta postale e deve contenere un valore per ognuno di questi attributi.</span><span class="sxs-lookup"><span data-stu-id="f9912-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="f9912-164">**Attributo**</span><span class="sxs-lookup"><span data-stu-id="f9912-164">**Attribute**</span></span>|<span data-ttu-id="f9912-165">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="f9912-165">**Description**</span></span>|<span data-ttu-id="f9912-166">**Obbligatorio?**</span><span class="sxs-lookup"><span data-stu-id="f9912-166">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f9912-167">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="f9912-167">EmailAddress</span></span>  <br/> |<span data-ttu-id="f9912-168">Specifica l'indirizzo di posta elettronica SMTP principale, ad esempio pilarp@contoso.com, per le cassette postali locali.</span><span class="sxs-lookup"><span data-stu-id="f9912-168">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="f9912-p117">Usare l'indirizzo SMTP principale per le cassette postali locali e non gli ID utente di Office 365. Ad esempio, se il dominio locale è denominato contoso.com, ma il nome del dominio di posta elettronica di Office 365 è service.contoso.com, si dovrà utilizzare il nome di dominio contoso.com per gli indirizzi di posta elettronica nel file CSV.</span><span class="sxs-lookup"><span data-stu-id="f9912-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="f9912-171">Obbligatorio</span><span class="sxs-lookup"><span data-stu-id="f9912-171">Required</span></span>  <br/> |
|<span data-ttu-id="f9912-172">Password</span><span class="sxs-lookup"><span data-stu-id="f9912-172">Password</span></span>  <br/> |<span data-ttu-id="f9912-p118">La password da impostare per la nuova cassetta postale di Office 365. Eventuali restrizioni relative alle password applicate all'organizzazione di Office 365 si applicano alle password incluse nel file CSV.</span><span class="sxs-lookup"><span data-stu-id="f9912-p118">The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="f9912-175">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="f9912-175">Optional</span></span>  <br/> |
|<span data-ttu-id="f9912-176">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="f9912-176">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="f9912-p119">Specifica se un utente deve cambiare la password al primo accesso alla nuova cassetta postale di Office 365. Usare **True** o **False** per il valore di questo parametro. </span><span class="sxs-lookup"><span data-stu-id="f9912-p119">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="f9912-179">> [!NOTE]> Se è stata implementata una soluzione Single Sign-On (SSO) distribuendo Active Directory Federation Services (ADFS) o versioni successive nell'organizzazione locale, è necessario usare **False** come valore dell'attributo **ForceChangePassword**.</span><span class="sxs-lookup"><span data-stu-id="f9912-179">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="f9912-180">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="f9912-180">Optional</span></span>  <br/> |
   
 <span data-ttu-id="f9912-181">**Formato del file CSV**</span><span class="sxs-lookup"><span data-stu-id="f9912-181">**CSV file format**</span></span>
  
<span data-ttu-id="f9912-p120">Di seguito viene illustrato un esempio di formato per il file CSV. In questo esempio viene eseguita la migrazione di tre cassette postali locali in Office 365.</span><span class="sxs-lookup"><span data-stu-id="f9912-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="f9912-p121">Nella prima riga, o riga di intestazione, del file CSV sono elencati i nomi degli attributi, o campi, specificati nelle righe successive. Il nome di ciascun attributo è separato da una virgola.</span><span class="sxs-lookup"><span data-stu-id="f9912-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="f9912-p122">Ogni riga che segue l'intestazione rappresenta un utente e fornisce le informazioni che verranno utilizzate per la migrazione della cassetta postale di tale utente. I valori degli attributi di ciascuna riga devono trovarsi nello stesso ordine in cui sono elencati i nomi degli attributi nella riga di intestazione.</span><span class="sxs-lookup"><span data-stu-id="f9912-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="f9912-p123">Per creare il file CSV, è possibile utilizzare un editor di testo o un'applicazione come Excel. Salvare il file con estensione .csv o .txt.</span><span class="sxs-lookup"><span data-stu-id="f9912-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f9912-p124">Se il file CSV contiene caratteri speciali o non ASCII, salvarlo con la codifica UTF-8 o Unicode. A seconda dell'applicazione, il salvataggio del file CSV con codifica UTF-8 o Unicode può risultare più semplice quando le impostazioni locali del sistema del computer corrispondono alla lingua usata nel file CSV.</span><span class="sxs-lookup"><span data-stu-id="f9912-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="f9912-192">Passaggio 3: creare un endpoint di migrazione</span><span class="sxs-lookup"><span data-stu-id="f9912-192">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="f9912-193"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="f9912-193"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="f9912-p125">Per eseguire la migrazione della posta elettronica correttamente, Office 365 deve essere in grado di connettersi e comunicare con il sistema di posta elettronica di origine. A tal fine, in Office 365 viene utilizzato un endpoint di migrazione. Per creare un endpoint di migrazione di Outlook via Internet usando PowerShell per una migrazione a fasi, è necessario innanzitutto [connettersi a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="f9912-p125">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="f9912-197">Per un elenco completo dei comandi di migrazione, vedere [Cmdlet di spostamento e migrazione](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="f9912-197">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="f9912-198">Per creare un endpoint di migrazione di Outlook via Internet denominato "StagedEndpoint" in PowerShell di Exchange Online, eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f9912-198">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="f9912-199">Per ulteriori informazioni sul cmdlet **New-MigrationEndpoint**, vedere[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span><span class="sxs-lookup"><span data-stu-id="f9912-199">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f9912-p126">Il cmdlet **New-MigrationEndpoint** può essere utilizzato per specificare un database per il servizio da utilizzare tramite l'opzione **-TargetDatabase**. In caso contrario, un database viene assegnato in modo casuale dal sito di Active Directory Federation Services (ADFS) 2.0 in cui si trova la cassetta postale di gestione.</span><span class="sxs-lookup"><span data-stu-id="f9912-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="f9912-202">Verificare che il passaggio di migrazione sia avvenuto correttamente</span><span class="sxs-lookup"><span data-stu-id="f9912-202">Verify it worked</span></span>

<span data-ttu-id="f9912-203">In PowerShell di Exchange Online eseguire il comando riportato di seguito per visualizzare le informazioni sull'endpoint di migrazione "StagedEndpoint":</span><span class="sxs-lookup"><span data-stu-id="f9912-203">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="f9912-204">Passaggio 4: creare e avviare un batch di migrazione a fasi</span><span class="sxs-lookup"><span data-stu-id="f9912-204">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="f9912-205"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="f9912-205"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="f9912-p127">È possibile utilizzare il cmdlet **New-MigrationBatch** in PowerShell di Exchange Online per creare un batch di migrazione per una migrazione completa. È possibile creare un batch di migrazione e avviarlo automaticamente includendo il parametro _AutoStart_. In alternativa, è possibile creare il batch di migrazione, per poi avviarlo utilizzando il cmdlet **Start-MigrationBatch**. In questo esempio viene creato un batch di migrazione denominato "StagedBatch1" e viene utilizzato l'endpoint di migrazione creato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="f9912-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="f9912-p128">In questo esempio viene inoltre creato un batch di migrazione denominato "StagedBatch1" e viene utilizzato l'endpoint di migrazione creato nel passaggio precedente. Poiché il parametro  _AutoStart_ non è incluso, il batch di migrazione deve essere avviato manualmente nel dashboard di migrazione oppure utilizzando il cmdlet **Start-MigrationBatch**. Come illustrato in precedenza, può esistere solo un batch di migrazione completa alla volta.</span><span class="sxs-lookup"><span data-stu-id="f9912-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="f9912-213">Verificare che il passaggio di migrazione sia avvenuto correttamente</span><span class="sxs-lookup"><span data-stu-id="f9912-213">Verify it worked</span></span>

<span data-ttu-id="f9912-214">Eseguire il seguente comando in PowerShell di Exchange Online per visualizzare informazioni su "StagedBatch1":</span><span class="sxs-lookup"><span data-stu-id="f9912-214">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="f9912-215">È inoltre possibile verificare che il batch sia stato avviato eseguendo il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f9912-215">You can also verify that the batch has started by running the following command:</span></span>
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="f9912-216">Per ulteriori informazioni sul cmdlet **Get-MigrationBatch**, vedere[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="f9912-216">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="f9912-217">Passaggio 5: convertire le cassette postali locali in utenti abilitati alla posta</span><span class="sxs-lookup"><span data-stu-id="f9912-217">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="f9912-218"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="f9912-218"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="f9912-p129">Dopo la migrazione di un batch di cassette postali, è necessario fare in modo che gli utenti possano accedere alla propria posta. Dopo la migrazione, un utente avrà una cassetta postale locale e una in Office 365. Gli utenti che dispongono di una cassetta postale in Office 365 non riceveranno più messaggi nella cassetta postale locale.</span><span class="sxs-lookup"><span data-stu-id="f9912-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="f9912-p130">Dato che le attività di migrazione non sono ancora terminate, non è ancora possibile indirizzare gli utenti a Office 365 per la posta elettronica. Pertanto, per gli utenti che dispongono di entrambe, è possibile convertire le cassette postali locali di cui è già stata eseguita la migrazione in utenti abilitati alla posta. Quando si converte una cassetta postale in un utente abilitato alla posta elettronica, è possibile indirizzare l'utente a Office 365 per la posta elettronica invece di accedere alla cassetta postale locale.</span><span class="sxs-lookup"><span data-stu-id="f9912-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="f9912-p131">Un altro motivo importante per convertire le cassette postali locali in utenti abilitati alla posta è rappresentato dalla possibilità di conservare gli indirizzi proxy dalle cassette postali di Office 365 semplicemente copiando questi indirizzi negli utenti abilitati alla posta. In questo modo è possibile gestire gli utenti basati su cloud dall'organizzazione locale utilizzando Active Directory. Inoltre, se si sceglie di rimuovere l'organizzazione Exchange Server locale dopo aver eseguito la migrazione di tutte le cassette postali in Office 365, gli indirizzi proxy copiati negli utenti abilitati alla posta elettronica resteranno nella distribuzione locale di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f9912-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
  
<span data-ttu-id="f9912-229">Per ulteriori informazioni e per scaricare gli script che consentono di convertire le cassette postali in utenti abilitati alla posta, vedere:</span><span class="sxs-lookup"><span data-stu-id="f9912-229">For more information, and to download scripts that you can run to convert mailboxes to mail-enabled users, see the following:</span></span>
  
- [<span data-ttu-id="f9912-230">Convertire le cassette postali di Exchange 2007 in utenti abilitati alla posta</span><span class="sxs-lookup"><span data-stu-id="f9912-230">Convert Exchange 2007 mailboxes to mail-enabled users</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [<span data-ttu-id="f9912-231">Convertire le cassette postali di Exchange 2003 in utenti abilitati alla posta</span><span class="sxs-lookup"><span data-stu-id="f9912-231">Convert Exchange 2003 mailboxes to mail-enabled users</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="f9912-232">Passaggio 6: eliminare un batch di migrazione a fasi</span><span class="sxs-lookup"><span data-stu-id="f9912-232">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="f9912-233"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="f9912-233"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="f9912-p132">Dopo che tutte le cassette postali incluse in un batch di migrazione sono state migrate correttamente, e una volta convertite tutte le cassette postali locali del batch in utenti abilitati alla posta, si può procedere all'eliminazione del batch di migrazione a fasi. Assicurarsi di verificare che la posta venga inoltrata alle cassette postali Office 365 nel batch di migrazione. Quando si elimina un batch di migrazione in fasi, il servizio di migrazione cancella tutti i record relativi al batch di migrazione ed elimina il batch di migrazione.</span><span class="sxs-lookup"><span data-stu-id="f9912-p132">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="f9912-237">Per eliminare il batch di migrazione "StagedBatch1" in PowerShell di Exchange Online, eseguire il comando riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="f9912-237">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="f9912-238">Per ulteriori informazioni sul cmdlet **Remove-MigrationBatch**, vedere[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="f9912-238">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="f9912-239">Verificare che il passaggio di migrazione sia avvenuto correttamente</span><span class="sxs-lookup"><span data-stu-id="f9912-239">Verify it worked</span></span>

<span data-ttu-id="f9912-240">Eseguire il seguente comando in PowerShell di Exchange Online per visualizzare informazioni su "IMAPBatch1":</span><span class="sxs-lookup"><span data-stu-id="f9912-240">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="f9912-241">Il comando restituirà il batch di migrazione con uno stato di **Rimozione in corso** o restituirà un errore che informa che non è possibile trovare il batch di migrazione, confermandone l'eliminazione.</span><span class="sxs-lookup"><span data-stu-id="f9912-241">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="f9912-242">Per ulteriori informazioni sul cmdlet **Get-MigrationBatch**, vedere[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="f9912-242">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="f9912-243">Passaggio 7: assegnare le licenze agli utenti di Office 365</span><span class="sxs-lookup"><span data-stu-id="f9912-243">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="f9912-244"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="f9912-244"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="f9912-p133">Attivare gli account utente di Office 365 per gli account migrati tramite l'assegnazione delle licenze. Se non si assegna una licenza, la cassetta postale viene disabilitata al termine del periodo di prova (30 giorni). Per assegnare una licenza nell'interfaccia di amministrazione di Office 365, vedere [Assegnare licenze per Office 365 per le aziende o annullarne l'assegnazione](https://go.microsoft.com/fwlink/?LinkId=536681).</span><span class="sxs-lookup"><span data-stu-id="f9912-p133">Activate Office 365 user accounts for the migrated accounts by assigning licenses. If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends. To assign a license in the Office 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="f9912-248">Passaggio 8: completare le attività successive alla migrazione</span><span class="sxs-lookup"><span data-stu-id="f9912-248">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="f9912-249"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="f9912-249"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="f9912-p134">**Creare un record DNS di individuazione automatica affinché gli utenti possano accedere facilmente alle proprie cassette postali.** Al termine della migrazione di tutte le cassette postali a Office 365, è possibile configurare un record DNS di individuazione automatica per la propria organizzazione di Office 365 per consentire agli utenti di connettersi facilmente alle loro nuove cassette postali di Office 365 con Outlook e i client mobili. Questo nuovo record DNS di individuazione automatica deve utilizzare lo stesso spazio dei nomi che si utilizza per l'organizzazione di Office 365. Ad esempio, se lo spazio dei nomi basato su cloud è cloud.contoso.com, il record DNS di individuazione automatica che deve essere creato è autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="f9912-p134">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="f9912-p135">In Office 365 viene utilizzato un record CNAME per implementare il servizio di individuazione automatica per Outlook e i client mobili. Il record CNAME di individuazione automatica deve includere le seguenti informazioni:</span><span class="sxs-lookup"><span data-stu-id="f9912-p135">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="f9912-256">**Alias:** individuazione automatica</span><span class="sxs-lookup"><span data-stu-id="f9912-256">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="f9912-257">**Destinazione:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="f9912-257">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="f9912-258">Per ulteriori informazioni, vedere [Creare record DNS per Office 365 quando si gestiscono i record DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="f9912-258">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="f9912-p136">**Rimuovere i server di Exchange locali.** Dopo aver verificato che tutta la posta elettronica venga instradata direttamente alle cassette postali di Office 365 e non è più necessario mantenere l'organizzazione di posta elettronica locale o non si prevede di implementare una soluzione Single Sign On (SSO), è possibile disinstallare Exchange dai server e rimuovere l'organizzazione di Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="f9912-p136">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="f9912-261">Per ulteriori informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="f9912-261">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="f9912-262">Modifica o eliminazione di Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="f9912-262">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="f9912-263">Come rimuovere un'organizzazione di Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="f9912-263">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="f9912-264">Disinstallazione di Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="f9912-264">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    
