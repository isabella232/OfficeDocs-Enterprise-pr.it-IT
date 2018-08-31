---
title: Accesso con privilegi management in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Utilizzare questo argomento per ulteriori informazioni sulla funzionalità di gestione con privilegi di accesso in Office 365
ms.openlocfilehash: 22286d4f91ffa0bd3c49f028681d20e36d14283d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915391"
---
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="4d93e-103">Accesso con privilegi management in Office 365</span><span class="sxs-lookup"><span data-stu-id="4d93e-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d93e-104">In questo argomento vengono illustrate la distribuzione e configurazione indicazioni per la funzionalità versione beta pubblica attualmente disponibili solo in Office 365 E5 e avanzate SKU di conformità.</span><span class="sxs-lookup"><span data-stu-id="4d93e-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="4d93e-p101">Accesso privilegiato management consente di controllare l'accesso granulare attività di amministrazione con privilegi in Office 365.  È possibile proteggere dell'organizzazione da violazioni che possono utilizzare un account con privilegi di amministratore esistenti con la condizione accesso ai dati riservati o l'accesso alle impostazioni di configurazione critici. Dopo l'abilitazione della gestione dei privilegi di accesso, gli utenti dovranno richiedere l'accesso in tempo per eseguire attività con privilegi elevate e privilegiata attraverso un flusso di lavoro di approvazione altamente con ambito e specifici. In questo modo gli utenti appena sufficientemente accesso a eseguire attività in corso, senza mettere a rischio esposizione di dati riservati o le impostazioni di configurazione critico. Abilitazione della gestione dei privilegi di accesso in Office 365 all'organizzazione i mezzi operare con i privilegi zero la condizione e forniscono un livello di sistema di difesa contro le vulnerabilità derivanti a causa di questo tipo di accesso amministrativo la condizione.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="4d93e-110">In questo argomento verrà informazioni utili per la procedura abilitazione e configurazione di gestione con privilegi di accesso nella propria organizzazione Office 365 e fungere da una Guida di riferimento per la richiesta, l'approvazione e gestione della caratteristica.</span><span class="sxs-lookup"><span data-stu-id="4d93e-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="4d93e-111">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="4d93e-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="4d93e-112">Funzionalità limitate</span><span class="sxs-lookup"><span data-stu-id="4d93e-112">Limited functionality</span></span>
<span data-ttu-id="4d93e-p102">Durante la versione beta pubblica di accesso privilegiato funzionalità di gestione sono disponibili solo tramite [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Accesso con privilegi management vengono descritte le definizioni delle attività a livello di cmdlet di gestione di Exchange. In Office 365 versioni future, con privilegi di accesso funzionalità verrà reso disponibile tramite il portale di amministrazione e dovrà essere riferita altri servizi di carichi di lavoro di Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="4d93e-116">Connessione a Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d93e-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="4d93e-117">I passaggi di configurazione in questo argomento consentono di abilitare e l'utilizzo con privilegi di accesso in Office 365 con Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d93e-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="4d93e-118">Eseguire la procedura descritta in [Connect to Exchange Online PowerShell con l'autenticazione a più fattori](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) per connettersi a Exchange Online PowerShell con le credenziali di Office 365 per abilitare e configurare l'accesso con privilegiato per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="4d93e-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="4d93e-p103">Non è necessario abilitare l'autenticazione a più fattori per l'organizzazione Office 365 eseguire la procedura per abilitare l'accesso con privilegiato durante la connessione a Exchange Online PowerShell. La connessione con l'autenticazione a più fattori crea un token OAuth utilizzato per l'accesso con privilegiato per le richieste di firma.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="4d93e-121">Abilitare e configurare la gestione dei privilegi di accesso</span><span class="sxs-lookup"><span data-stu-id="4d93e-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="4d93e-122">Passaggio 1 - creare gruppo del revisore</span><span class="sxs-lookup"><span data-stu-id="4d93e-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="4d93e-p104">Dal portale di amministrazione di Office 365, selezionare **gruppi** > **Aggiungi gruppo**, quindi creare un gruppo di protezione abilitato alla posta per i responsabili di accesso predefinito con privilegiata. Al termine, scegliere **Aggiungi** per creare e salvare il gruppo responsabile approvazione.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Schermata di accesso privilegiato responsabili approvazione nel portale di amministrazione di Office 365](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="4d93e-p105">In questa fase, sono consentiti solo agli utenti l'accesso amministrativo approvare le richieste di accesso di Office 365 privilegiato. Qualsiasi utente che fa parte del gruppo dei responsabili approvazione in futuro sarà in grado di approvare le richieste di accesso.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="4d93e-128">Passaggio 2: abilitare l'accesso con privilegiato in Office 365</span><span class="sxs-lookup"><span data-stu-id="4d93e-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="4d93e-129">Accesso privilegiato deve essere attivata in modo esplicito con il gruppo responsabile approvazione predefinito, incluso un set di account di sistema che si desidera vengano esclusi dal controllo dell'accesso Gestione accesso privilegiato.</span><span class="sxs-lookup"><span data-stu-id="4d93e-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="4d93e-130">Eseguire il seguente comando in Exchange Online PowerShell per abilitare l'accesso con privilegiato e per assegnare gruppo al responsabile approvazione:</span><span class="sxs-lookup"><span data-stu-id="4d93e-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="4d93e-131">Esempio:</span><span class="sxs-lookup"><span data-stu-id="4d93e-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="4d93e-132">Gli account di sistema caratteristica viene resa disponibile per verificare che determinati automatizzazioni all'interno di organizzazioni possono lavorare senza dipendenza accesso privilegiato, tuttavia, è consigliabile che tali esclusioni eccezionali e quelle consentite deve essere approvati e controllati regolarmente.</span><span class="sxs-lookup"><span data-stu-id="4d93e-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="4d93e-133">Passaggio 3: creare un criterio di approvazione</span><span class="sxs-lookup"><span data-stu-id="4d93e-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="4d93e-p106">Un criterio di approvazione consente di definire i requisiti specifici di approvazione con ambiti a singole attività. Le opzioni di tipo approvazione sono **automatica** o **manuale**.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="4d93e-136">Eseguire il comando seguente in Exchange Online PowerShell per definire un criterio di approvazione:</span><span class="sxs-lookup"><span data-stu-id="4d93e-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="4d93e-137">Esempio:</span><span class="sxs-lookup"><span data-stu-id="4d93e-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="4d93e-138">Utilizzo di access con privilegi nella propria organizzazione Office 365</span><span class="sxs-lookup"><span data-stu-id="4d93e-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="4d93e-139">Richiesta di autorizzazione elevazione di privilegi per l'esecuzione di attività</span><span class="sxs-lookup"><span data-stu-id="4d93e-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="4d93e-p107">Dopo l'attivazione, con privilegiato di accesso richiede approvazioni per l'esecuzione di tutte le attività che dispone di un criterio di approvazione associato definito. Gli utenti che necessitano di eseguire le attività incluse nel necessario richiedere e concesso accesso approvazione per disporre delle autorizzazioni necessarie per eseguire l'attività di un criterio di approvazione.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="4d93e-142">Eseguire il comando seguente in Exchange Online PowerShell per creare e inviare una richiesta di approvazione di gruppo del revisore:</span><span class="sxs-lookup"><span data-stu-id="4d93e-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="4d93e-143">Esempio:</span><span class="sxs-lookup"><span data-stu-id="4d93e-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="4d93e-144">Visualizzare lo stato delle richieste di elevazione di privilegi</span><span class="sxs-lookup"><span data-stu-id="4d93e-144">View status of elevation requests</span></span>
<span data-ttu-id="4d93e-145">Dopo aver creata una richiesta di approvazione, è possibile rivedere stato richiesta di elevazione utilizza associato con ID richiesta.</span><span class="sxs-lookup"><span data-stu-id="4d93e-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="4d93e-146">Eseguire il comando seguente in Exchange Online PowerShell per visualizzare lo stato richiesta di approvazione per un ID richiesta specifica:</span><span class="sxs-lookup"><span data-stu-id="4d93e-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="4d93e-147">Esempio:</span><span class="sxs-lookup"><span data-stu-id="4d93e-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="4d93e-148">L'approvazione di una richiesta di autorizzazione elevazione</span><span class="sxs-lookup"><span data-stu-id="4d93e-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="4d93e-149">Quando si crea una richiesta di approvazione, i membri del gruppo responsabile approvazione pertinenti riceveranno una notifica tramite posta elettronica e autorizzati ad approvare la richiesta associata all'ID richiesta.</span><span class="sxs-lookup"><span data-stu-id="4d93e-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="4d93e-150">Eseguire il comando seguente in Exchange Online PowerShell per approvare una richiesta di autorizzazione elevazione:</span><span class="sxs-lookup"><span data-stu-id="4d93e-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="4d93e-151">Esempio:</span><span class="sxs-lookup"><span data-stu-id="4d93e-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="4d93e-152">Nega una richiesta di autorizzazione elevazione</span><span class="sxs-lookup"><span data-stu-id="4d93e-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="4d93e-153">Quando si crea una richiesta di approvazione, i membri del gruppo pertinenti responsabile approvazione possono rifiutare la richiesta associata all'ID richiesta.</span><span class="sxs-lookup"><span data-stu-id="4d93e-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="4d93e-154">Eseguire il comando seguente in Exchange Online PowerShell per rifiutare una richiesta di autorizzazione elevazione:</span><span class="sxs-lookup"><span data-stu-id="4d93e-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="4d93e-155">Esempio:</span><span class="sxs-lookup"><span data-stu-id="4d93e-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="4d93e-156">Esecuzione dell'attività</span><span class="sxs-lookup"><span data-stu-id="4d93e-156">Running the task</span></span>
<span data-ttu-id="4d93e-p108">Dopo l'approvazione, l'utente richiedente può eseguire l'operazione e accesso con privilegi verrà autorizzare ed eseguire l'attività per conto degli utenti. L'approvazione rimane valido per l'oggetto durata (durata predefinito è 4 ore), durante il quale il richiedente può eseguire l'operazione più volte. Tutti questi esecuzioni vengono registrate e resi disponibili per la protezione e il controllo della conformità.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="4d93e-160">Disabilitare l'accesso con privilegiato in Office 365</span><span class="sxs-lookup"><span data-stu-id="4d93e-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="4d93e-p109">Se necessario, è possibile disabilitare la gestione degli accessi privilegiato in Office 365. Disattivazione con privilegi accesso non vengono eliminati tutti criteri di approvazione associato o i gruppi di responsabile approvazione.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="4d93e-163">Eseguire il comando seguente in Exchange Online Powershell per disabilitare l'accesso con privilegiato:</span><span class="sxs-lookup"><span data-stu-id="4d93e-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="4d93e-164">Gestito l'accesso a Microsoft Graph in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="4d93e-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d93e-165">In questa sezione vengono illustrate ulteriori informazioni sulla caratteristica disponibile solo in anteprima.</span><span class="sxs-lookup"><span data-stu-id="4d93e-165">This section covers details about a feature currently available only in preview.</span></span>

<span data-ttu-id="4d93e-p110">Gestito l'accesso a Microsoft Graph in Microsoft Azure è un servizio che consente alle organizzazioni di esercitare un livello di granularità del controllo tramite i dati di Office 365. Questo sistema consente agli sviluppatori di applicazioni creare informativa con tali dati.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="4d93e-p111">Questo sistema utilizza l'accesso di Office 365 con privilegi di controllo dei dati tramite il flusso di lavoro approvazione, che consente l'accesso con ambito a dati di Office 365 con responsabile della supervisione admin. Le richieste di dati si quando le applicazioni vengono installate e richiedono l'accesso ai dati di Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="4d93e-170">Visualizzare i dettagli di richiesta</span><span class="sxs-lookup"><span data-stu-id="4d93e-170">View request details</span></span>
<span data-ttu-id="4d93e-171">Visualizzare i dettagli delle richieste di accesso per i dati di Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d93e-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="4d93e-172">Eseguire il comando seguente in Exchange Online Powershell per visualizzare le richieste di dati:</span><span class="sxs-lookup"><span data-stu-id="4d93e-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="4d93e-173">Output di esempio:</span><span class="sxs-lookup"><span data-stu-id="4d93e-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="4d93e-174">Approvare le richieste di accesso dei dati</span><span class="sxs-lookup"><span data-stu-id="4d93e-174">Approve data access requests</span></span>
<span data-ttu-id="4d93e-175">Tramite i cmdlet di approvazione standard accesso privilegiato è possono approvare le richieste di accesso di tutti i dati.</span><span class="sxs-lookup"><span data-stu-id="4d93e-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="4d93e-176">Eseguire il comando seguente in Exchange Online Powershell per approvare le richieste di tutti i dati per richiedente specifico:</span><span class="sxs-lookup"><span data-stu-id="4d93e-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="4d93e-177">Esempio:</span><span class="sxs-lookup"><span data-stu-id="4d93e-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="4d93e-178">Ottenere assistenza e fornire commenti e suggerimenti</span><span class="sxs-lookup"><span data-stu-id="4d93e-178">Getting help and providing feedback</span></span>
<span data-ttu-id="4d93e-p112">È importante che durante la versione beta pubblica si può implementati in un bug occasionale avere o commenti e suggerimenti su come migliorare la gestione degli accessi privilegiato. È il valore commenti e suggerimenti e incoraggiare è possibile condividere con Microsoft:</span><span class="sxs-lookup"><span data-stu-id="4d93e-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="4d93e-181">Inviare commenti e suggerimenti suggerimenti di Active Directory nel [Gruppo di Yammer Preview di Office](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span><span class="sxs-lookup"><span data-stu-id="4d93e-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="4d93e-182">I rapporti sui bug nel percorso area "Office 365 con privilegi Gestione accesso" in [Office Preview VSO](https://office-previews.visualstudio.com/previews)del file.</span><span class="sxs-lookup"><span data-stu-id="4d93e-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="4d93e-183">Domande frequenti</span><span class="sxs-lookup"><span data-stu-id="4d93e-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="4d93e-184">Quali SKU da utilizzare con privilegi di accesso in Office 365</span><span class="sxs-lookup"><span data-stu-id="4d93e-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="4d93e-185">Accesso privilegiato management in Office 365 è attualmente disponibile solo per i clienti con E5 e avanzate SKU di conformità.</span><span class="sxs-lookup"><span data-stu-id="4d93e-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="4d93e-186">Quando sarà disponibile per Office 365 dei carichi di lavoro di là Exchange con privilegi di accesso?</span><span class="sxs-lookup"><span data-stu-id="4d93e-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="4d93e-p113">Si intende offrire breve questa caratteristica in altri carichi di lavoro di Office 365. Quando si è pronti per condividere una sequenza temporale, verrà reso disponibile tramite il piano di lavoro di Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="4d93e-189">Qual è la differenza di gestione di Azure Active Directory delle identità con privilegi?</span><span class="sxs-lookup"><span data-stu-id="4d93e-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="4d93e-p114">Accesso con privilegi management in Office 365 e [Azure Active Directory privilegiato Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complemento tra loro, fornendo accesso controllano con l'accesso ad ambiti diversi nel tempo. Insieme forniscono una gamma completa di controlli per la protezione dei dati.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="4d93e-p115">Accesso privilegiato management in Office 365 possono essere definite e con ambito a livello di attività, mentre la gestione delle identità con privilegi di Azure Active Directory si applica a livello di ruolo con la possibilità di eseguire più attività.  Azure Active Directory con privilegi Identity Management principalmente consente la gestione dei tipi di accesso per gruppi di ruoli e con privilegi e ruoli AD access management in Office 365 viene applicato a livello di attività.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="4d93e-194">**Con privilegi di attivazione accedere management in Office 365 già utilizzando la gestione delle identità con privilegi di Azure Active Directory:** Aggiunta di gestione con privilegi di accesso in Office 365 consente di specificare un altro livello granulare di protezione e funzionalità per l'accesso ai dati di Office 365 con privilegiato di controllo.</span><span class="sxs-lookup"><span data-stu-id="4d93e-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="4d93e-195">**Abilitazione di Azure Active Directory privilegiato gestione delle identità durante l'utilizzo di già privilegiato gestione dell'accesso in Office 365:**  Aggiunta di gestione delle identità con privilegi di Azure Active Directory con privilegi gestione dell'accesso in Office 365 può estendere con privilegi di accesso ai dati all'esterno di Office 365 principalmente definita dal ruolo o l'identità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="4d93e-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="4d93e-196">È necessario essere un amministratore globale per gestire l'accesso con privilegiato in Office 365?</span><span class="sxs-lookup"><span data-stu-id="4d93e-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="4d93e-p116">Durante l'anteprima è necessario disporre di privilegi di amministratore globale in grado di gestire l'accesso con privilegiato in Office 365. Gli utenti che sono inclusi nel gruppo dei responsabili non è necessario essere un amministratore globale per esaminare e approvare le richieste.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="4d93e-199">Quali sono le gestione accesso privilegiato in Office 365 correlati all'archivio protetto clienti?</span><span class="sxs-lookup"><span data-stu-id="4d93e-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="4d93e-p117">[Archivio protetto cliente](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) consente a un livello di controllo di accesso per le organizzazioni per l'accesso ai dati dal provider di servizi, ad esempio Microsoft. Accesso privilegiato management in Office 365 consente il controllo di accesso granulare all'interno dell'organizzazione per tutte le attività di Office 365 con privilegi.</span><span class="sxs-lookup"><span data-stu-id="4d93e-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>