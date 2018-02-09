---
title: Utilizzare PowerShell per eseguire una migrazione completa a Office 365
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 'Riepilogo: informazioni su come utilizzare Windows PowerShell per eseguire una migrazione completa a Office 365.'
ms.openlocfilehash: 8181d59f53464034a584724dcb53956976c917dd
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="0a244-103">Utilizzare PowerShell per eseguire una migrazione completa a Office 365</span><span class="sxs-lookup"><span data-stu-id="0a244-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

 <span data-ttu-id="0a244-104">**Sintesi:** Informazioni su come utilizzare Windows PowerShell per eseguire una migrazione completa a Office 365.</span><span class="sxs-lookup"><span data-stu-id="0a244-104">**Summary:** Learn how to use Windows PowerShell to perform a cutover migration to Office 365.</span></span>
  
<span data-ttu-id="0a244-p101">È possibile migrare i contenuti delle cassette postali degli utenti da un sistema di posta elettronica di origine a Office 365 in un'unica operazione utilizzando una migrazione completa. In questo articolo vengono illustrate le attività per una migrazione completa della posta elettronica tramite PowerShell di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0a244-p101">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="0a244-p102">Consultando l'argomento [Informazioni utili su una migrazione completa della posta elettronica a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), è possibile ottenere una panoramica del processo di migrazione. Una volta appresi i contenuti di questo articolo, utilizzarlo per iniziare la migrazione delle cassette postali da un sistema di posta elettronica a un altro.</span><span class="sxs-lookup"><span data-stu-id="0a244-p102">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0a244-p103">Inoltre, è possibile utilizzare l'interfaccia di amministrazione di Exchange per eseguire una migrazione completa. Vedere [Eseguire una migrazione completa della posta elettronica a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span><span class="sxs-lookup"><span data-stu-id="0a244-p103">You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="0a244-111">Che cosa è necessario sapere prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="0a244-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="0a244-p104">Tempo stimato per il completamento di questa attività: tra i 2 e i 5 minuti per creare un batch di migrazione. Dopo l'avvio del batch di migrazione, la durata della migrazione varia in base al numero di cassette postali nel batch, alla dimensione di ogni cassetta postale e alla capacità di rete disponibile. Per informazioni su altri fattori che influenzano il tempo necessario per eseguire la migrazione delle cassette postali su Office 365, vedere l'articolo relativo alle [prestazioni della migrazione](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="0a244-p104">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="0a244-p105">È necessario disporre delle autorizzazioni per poter eseguire queste procedure. Per verificare le autorizzazioni necessarie, vedere la voce "Migrazione" in una tabella nell'argomento [Autorizzazioni di destinatari](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="0a244-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="0a244-p106">Per utilizzare i cmdlet di PowerShell di Exchange Online, è necessario eseguire l'accesso e importare i cmdlet nella sessione di Windows PowerShell locale. Per le istruzioni, vedere [Connettersi a Exchange Online tramite Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="0a244-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="0a244-119">Per un elenco completo dei comandi di migrazione, vedere [Cmdlet di spostamento e migrazione](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="0a244-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="0a244-120">Procedura della migrazione</span><span class="sxs-lookup"><span data-stu-id="0a244-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="0a244-121">Passaggio 1: predisporre una migrazione completa</span><span class="sxs-lookup"><span data-stu-id="0a244-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="0a244-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="0a244-122"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="0a244-p107">**Aggiungere l'organizzazione Exchange locale come dominio accettato dell'organizzazione di Office 365.** Il servizio di migrazione utilizza l'indirizzo SMTP delle relative cassette postali locali per creare l'ID utente Microsoft Online Services e l'indirizzo di posta elettronica per le nuove cassette postali di Office 365. La migrazione ha esito negativo se il dominio di Exchange non è un dominio accettato o il dominio primario dell'organizzazione di Office 365. Per ulteriori informazioni, vedere[Verificare il dominio in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="0a244-p107">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="0a244-p108">**Configurare Outlook via Internet nel server Exchange locale** Nel servizio di migrazione della posta elettronica viene utilizzato RPC su HTTP, anche denominato Outlook via Internet, per connettersi al server Exchange locale. Per informazioni sull'installazione di Outlook via Internet per Exchange 2010, Exchange 2007 ed Exchange 2003, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="0a244-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="0a244-130">Exchange 2010: Abilita Outlook via Internet</span><span class="sxs-lookup"><span data-stu-id="0a244-130">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="0a244-131">Exchange 2007: Come abilitare Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="0a244-131">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="0a244-132">Exchange 2003: Scenari di distribuzione per RPC su HTTP</span><span class="sxs-lookup"><span data-stu-id="0a244-132">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="0a244-133">Configurazione di Outlook via Internet con Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="0a244-133">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="0a244-p109">È necessario configurare Outlook via Internet con un certificato considerato attendibile da un'autorità di certificazione (CA, Certificate Authority). Non può essere configurato con un certificato autofirmato. Per ulteriori informazioni, vedere [Come configurare SSL per Outlook via Internet](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="0a244-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="0a244-p110">**Verificare che sia possibile connettersi all'organizzazione di Exchange tramite Outlook via Internet** Provare uno di questi metodi per testare le impostazioni di connessione:</span><span class="sxs-lookup"><span data-stu-id="0a244-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="0a244-139">Utilizzare Microsoft Outlook all'esterno della rete aziendale per connettersi alla cassetta postale di Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="0a244-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="0a244-p111">Utilizzare Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) per testare le impostazioni della connessione. Utilizzare Outlook via Internet (RPC su HTTP) o i test di individuazione automatica di Outlook.</span><span class="sxs-lookup"><span data-stu-id="0a244-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="0a244-142">In PowerShell di Exchange Online, eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="0a244-142">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="0a244-p112">**Assegnare a un account utente locale le autorizzazioni necessarie per accedere alle cassette postali nella propria organizzazione di Exchange.** È necessario che l'account utente locale, utilizzato per connettersi alla propria organizzazione Exchange locale (anche chiamatoamministratore di migrazione), possieda le corrette autorizzazioni per accedere alle cassette postali locali che si intendono migrare su Office 365. Questo account utente viene utilizzato per creare un endpoint di migrazione per la propria organizzazione locale.</span><span class="sxs-lookup"><span data-stu-id="0a244-p112">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.** The on-premises user account that you use to connect to your on-premises Exchange organization (also called themigration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="0a244-p113">Nel seguente elenco vengono mostrati i privilegi amministrativi necessari per migrare le cassette postali tramite una migrazione completa. Esistono tre opzioni possibili.</span><span class="sxs-lookup"><span data-stu-id="0a244-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="0a244-148">L'amministratore di migrazione deve essere un membro del gruppo **Domain Admins** in Active Directory nell'organizzazione locale.</span><span class="sxs-lookup"><span data-stu-id="0a244-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="0a244-149">Oppure</span><span class="sxs-lookup"><span data-stu-id="0a244-149">Or</span></span>
    
  - <span data-ttu-id="0a244-150">All'amministratore di migrazione è assegnata l'autorizzazione **FullAccess** per ogni cassetta postale locale.</span><span class="sxs-lookup"><span data-stu-id="0a244-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="0a244-151">Oppure</span><span class="sxs-lookup"><span data-stu-id="0a244-151">Or</span></span>
    
  - <span data-ttu-id="0a244-152">All'amministratore di migrazione deve essere assegnata l'autorizzazione **Receive As** nel database di cassette postali locali in cui si trovano le cassette postali dell'utente.</span><span class="sxs-lookup"><span data-stu-id="0a244-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="0a244-p114">**Disabilitare la messaggistica unificata.** Se le cassette postali locali di cui si sta eseguendo la migrazione sono abilitate per la messaggistica unificata, è necessario disabilitare la messaggistica stessa prima di eseguire la migrazione. È possibile quindi riabilitare la messaggistica unificata al termine della migrazione.</span><span class="sxs-lookup"><span data-stu-id="0a244-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="0a244-p115">**Gruppi e delegati di sicurezza** Il servizio di migrazione della posta elettronica non può rilevare se i gruppi Active Directory in locale siano o meno gruppi di sicurezza, per questo non è possibile predisporre gruppi migrati come gruppi di sicurezza in Office 365. Se si desidera disporre di gruppi di sicurezza nel tenant Office 365, è necessario predisporre prima un gruppo di sicurezza vuoto abilitato alla posta nel tenant di Office 365 prima di avviare la migrazione completa. Inoltre, questo metodo di migrazione consente di spostare solo le cassette postali, gli utenti di posta, i contatti di posta e gruppi abilitati alla posta. Se un altro oggetto di Active Directory, come l'utente non migrato a Office 365, viene assegnato come manager o delegato a un oggetto in corso di migrazione, è necessario rimuoverli dall'oggetto prima della migrazione.</span><span class="sxs-lookup"><span data-stu-id="0a244-p115">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="0a244-160">Passaggio 2: creare un endpoint di migrazione</span><span class="sxs-lookup"><span data-stu-id="0a244-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="0a244-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="0a244-161"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="0a244-p116">Per eseguire la migrazione della posta elettronica correttamente, Office 365 deve essere in grado di connettersi e comunicare con il sistema di posta elettronica di origine. A tal fine, in Office 365 viene utilizzato un endpoint di migrazione. Per creare un endpoint di migrazione di Outlook via Internet per una migrazione completa, è necessario innanzitutto [connettersi a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="0a244-p116">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="0a244-165">Per un elenco completo dei comandi di migrazione, vedere [Cmdlet di spostamento e migrazione](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="0a244-165">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="0a244-166">In PowerShell di Exchange Online, eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="0a244-166">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="0a244-167">Nell'esempio viene utilizzato il cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) per ottenere e verificare le impostazioni di connessione al server di Exchange locale. In seguito, tali impostazioni vengono utilizzate per creare l'endpoint di migrazione denominato "CutoverEndpoint".</span><span class="sxs-lookup"><span data-stu-id="0a244-167">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="0a244-p117">Il cmdlet **New-MigrationEndpoint** può essere utilizzato per specificare un database per il servizio da utilizzare tramite l'opzione **-TargetDatabase**. In caso contrario, un database viene assegnato in modo casuale dal sito di Active Directory Federation Services (ADFS) 2.0 in cui si trova la cassetta postale di gestione.</span><span class="sxs-lookup"><span data-stu-id="0a244-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="0a244-170">Verificare che il passaggio di migrazione sia avvenuto correttamente</span><span class="sxs-lookup"><span data-stu-id="0a244-170">Verify it worked</span></span>

<span data-ttu-id="0a244-171">In PowerShell di Exchange Online, eseguire il comando riportato di seguito per visualizzare le informazioni sull'endpoint di migrazione "CutoverEndpoint":</span><span class="sxs-lookup"><span data-stu-id="0a244-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="0a244-172">Passaggio 3: creare il batch di migrazione completa</span><span class="sxs-lookup"><span data-stu-id="0a244-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="0a244-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="0a244-173"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="0a244-p118">È possibile utilizzare il cmdlet **New-MigrationBatch** in PowerShell di Exchange Online per creare un batch di migrazione per una migrazione completa. È possibile creare un batch di migrazione e avviarlo automaticamente includendo il parametro _AutoStart_. In alternativa, è possibile creare il batch di migrazione, per poi avviarlo utilizzando il cmdlet **Start-MigrationBatch**. In questo esempio viene creato un batch di migrazione denominato "CutoverBatch" e viene utilizzato l'endpoint di migrazione creato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="0a244-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="0a244-p119">In questo esempio viene inoltre creato un batch di migrazione denominato "CutoverBatch" e viene utilizzato l'endpoint di migrazione creato nel passaggio precedente. Poiché il parametro  _AutoStart_ non è incluso, il batch di migrazione deve essere avviato manualmente nel dashboard di migrazione oppure utilizzando il cmdlet **Start-MigrationBatch**. Come illustrato in precedenza, può esistere solo un batch di migrazione completa alla volta.</span><span class="sxs-lookup"><span data-stu-id="0a244-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="0a244-181">Verificare che il passaggio di migrazione sia avvenuto correttamente</span><span class="sxs-lookup"><span data-stu-id="0a244-181">Verify it worked</span></span>

<span data-ttu-id="0a244-182">Per verificare che sia stato creato correttamente un batch di migrazione per una migrazione completa, eseguire il seguente comando in PowerShell di Exchange Online per visualizzare informazioni sul nuovo batch di migrazione:</span><span class="sxs-lookup"><span data-stu-id="0a244-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="0a244-183">Passaggio 4: avviare il batch di migrazione completa</span><span class="sxs-lookup"><span data-stu-id="0a244-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="0a244-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="0a244-184"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="0a244-p120">Per avviare il batch di migrazione in PowerShell di Exchange Online, eseguire il comando riportato di seguito. In tal modo verrà creato un batch di migrazione denominato "CutoverBatch".</span><span class="sxs-lookup"><span data-stu-id="0a244-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="0a244-187">Verificare che il passaggio di migrazione sia avvenuto correttamente</span><span class="sxs-lookup"><span data-stu-id="0a244-187">Verify it worked</span></span>

<span data-ttu-id="0a244-p121">Se un batch di migrazione è avviato correttamente, il relativo stato sul dashboard di migrazione viene indicato come Sincronizzazione in corso. Per verificare che sia stato avviato correttamente un batch di migrazione tramite PowerShell di Exchange Online, eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="0a244-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="0a244-190">Passaggio 5: instradare la posta elettronica a Office 365</span><span class="sxs-lookup"><span data-stu-id="0a244-190">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="0a244-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="0a244-191"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="0a244-p122">I sistemi di posta elettronica utilizzano un record DNS denominato record MX per individuare dove recapitare i messaggi di posta elettronica. Durante il processo di migrazione della posta elettronica, il record MX fa riferimento al sistema di posta elettronica di origine. Al termine della migrazione della posta elettronica a Office 365, il record MX fa riferimento a Office 365. Ciò contribuisce a garantire che la posta elettronica sia recapitata alle cassette postali di Office 365. Spostando il record MX, è inoltre possibile disattivare il sistema di posta elettronica precedente al momento più opportuno.</span><span class="sxs-lookup"><span data-stu-id="0a244-p122">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="0a244-p123">Per molti provider DNS, sono disponibili istruzioni specifiche per [modificare il record MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Se il provider DNS non è incluso oppure si desidera farsi un'idea delle direzioni generali, vengono fornite anche [istruzioni generali sul record MX](https://go.microsoft.com/fwlink/?LinkId=397449).</span><span class="sxs-lookup"><span data-stu-id="0a244-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="0a244-p124">È possibile che i sistemi di posta elettronica dei propri clienti e partner impieghino fino a 72 ore per riconoscere il record MX modificato. Attendere almeno 72 ore prima di procedere con l'attività successiva: [Passaggio 6: eliminare il batch di migrazione completa](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="0a244-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="0a244-201">Passaggio 6: eliminare il batch di migrazione completa</span><span class="sxs-lookup"><span data-stu-id="0a244-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="0a244-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="0a244-202"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="0a244-p125">Dopo aver modificato il record MX e verificato che tutta la posta elettronica venga instradata alle cassette postali di Office 365, informare gli utenti che la loro posta sarà spostata in Office 365. Dopo questa operazione, è possibile eliminare il batch di migrazione completa. Verificare le seguenti condizioni prima di eliminare il batch di migrazione.</span><span class="sxs-lookup"><span data-stu-id="0a244-p125">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="0a244-p126">Tutti gli utenti utilizzano cassette postali di Office 365. Dopo l'eliminazione del batch, la posta inviata alle cassette postali nel server di Exchange locale non viene copiata nelle cassette postali di Office 365 corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="0a244-p126">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="0a244-p127">Le cassette postali di Office 365 sono state sincronizzate almeno una volta dal momento in cui hanno cominciato a ricevere la posta elettronica direttamente. A tale scopo, assicurarsi che il valore nella casella Ultima sincronizzazione per il batch di migrazione sia più recente di quello dell'inizio dell'invio della posta direttamente alle cassette postali di Office 365.</span><span class="sxs-lookup"><span data-stu-id="0a244-p127">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="0a244-210">Per eliminare il batch di migrazione "CutoverBatch" in PowerShell di Exchange Online, eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="0a244-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="0a244-211">Sezione 7: assegnare licenze utente</span><span class="sxs-lookup"><span data-stu-id="0a244-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="0a244-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="0a244-212"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="0a244-p128">**Attivare gli account utente di Office 365 per gli account migrati tramite l'assegnazione delle licenze.** Se non si assegna una licenza, la cassetta postale viene disabilitata al termine del periodo di prova (30 giorni). Per assegnare una licenza in interfaccia di amministrazione di Office 365, vedere[Assegnare licenze per Office 365 per le aziende o annullarne l'assegnazione](https://go.microsoft.com/fwlink/?LinkId=536681).</span><span class="sxs-lookup"><span data-stu-id="0a244-p128">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.** If you don't assign a license, the mailbox is disabled when the grace period ends (30 days). To assign a license in the Office 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="0a244-216">Passaggio 8: completare le attività successive alla migrazione</span><span class="sxs-lookup"><span data-stu-id="0a244-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="0a244-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="0a244-217"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="0a244-p129">**Creare un record DNS di individuazione automatica affinché gli utenti possano accedere facilmente alle proprie cassette postali.** Al termine della migrazione di tutte le cassette postali a Office 365, è possibile configurare un record DNS di individuazione automatica per la propria organizzazione di Office 365 per consentire agli utenti di connettersi facilmente alle loro nuove cassette postali di Office 365 con Outlook e i client mobili. Questo nuovo record DNS di individuazione automatica deve utilizzare lo stesso spazio dei nomi che si utilizza per l'organizzazione di Office 365. Ad esempio, se lo spazio dei nomi basato su cloud è cloud.contoso.com, il record DNS di individuazione automatica che deve essere creato è autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="0a244-p129">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="0a244-222">Inoltre, se si conserva il server di Exchange, è necessario assicurarsi che i record CNAME DNS di individuazione automatica facciano riferimento a Office 365 in DNS interni ed esterni dopo la migrazione, in modo che il client Outlook sia in grado di connettersi alla cassetta postale corretta.</span><span class="sxs-lookup"><span data-stu-id="0a244-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="0a244-223">In Exchange 2007, Exchange 2010 e Exchange 2013 è inoltre necessario impostare  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` su `Null`.</span><span class="sxs-lookup"><span data-stu-id="0a244-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="0a244-p130">In Office 365 viene utilizzato un record CNAME per implementare il servizio di individuazione automatica per Outlook e i client mobili. Il record CNAME di individuazione automatica deve includere le seguenti informazioni:</span><span class="sxs-lookup"><span data-stu-id="0a244-p130">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="0a244-226">**Alias:** individuazione automatica</span><span class="sxs-lookup"><span data-stu-id="0a244-226">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="0a244-227">**Destinazione:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="0a244-227">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="0a244-228">Per ulteriori informazioni, vedere [Creare record DNS per Office 365 quando si gestiscono i record DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="0a244-228">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="0a244-p131">**Rimuovere i server di Exchange locali.** Dopo aver verificato che tutta la posta elettronica venga instradata direttamente alle cassette postali di Office 365 e non è più necessario mantenere l'organizzazione di posta elettronica locale o non si prevede di implementare una soluzione Single Sign On (SSO), è possibile disinstallare Exchange dai server e rimuovere l'organizzazione di Exchange locale.</span><span class="sxs-lookup"><span data-stu-id="0a244-p131">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="0a244-231">Per ulteriori informazioni, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="0a244-231">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="0a244-232">Modifica o eliminazione di Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="0a244-232">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="0a244-233">Come rimuovere un'organizzazione di Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="0a244-233">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="0a244-234">Disinstallazione di Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="0a244-234">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

