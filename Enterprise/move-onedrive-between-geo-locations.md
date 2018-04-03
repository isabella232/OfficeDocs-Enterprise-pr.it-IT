---
title: Spostare un sito di OneDrive in un'altra posizione geografica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informazioni su come spostare un sito di OneDrive in un'altra posizione geografica.
ms.openlocfilehash: a31f683170fdb83dac90e9d09884c3020d1a47b1
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="d8ea6-103">Spostare un sito di OneDrive in un'altra posizione geografica</span><span class="sxs-lookup"><span data-stu-id="d8ea6-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="d8ea6-p101">A OneDrive geo spostamento, è possibile spostare OneDrive un utente in una posizione geografica diversi. OneDrive geo move viene eseguita dall'amministratore di SharePoint Online o amministratore globale di Office 365. Prima di avviare un OneDrive geo spostare, assicurarsi di notificare all'utente viene spostato il cui OneDrive e consigliabile che alla chiusura di tutti i file per la durata dello spostamento. (Se l'utente ha Microsoft aprire un documento utilizzando il client di Office durante lo spostamento, quindi su Sposta completamento documento necessario per essere salvato nella nuova posizione.) Lo spostamento può essere pianificato per un secondo momento, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="d8ea6-p102">Il servizio OneDrive utilizza archiviazione Blob Azure per archiviare il contenuto. Blob Storage associate a OneDrive dell'utente verranno spostate dall'origine alla posizione geografica di destinazione entro 40 giorni di destinazione OneDrive disponibile all'utente. Accesso a OneDrive dell'utente vengono ripristinata non appena la destinazione OneDrive è disponibile.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="d8ea6-p103">Durante la finestra di spostamento geo OneDrive (circa 2-6 ore) OneDrive dell'utente è impostato su sola lettura. L'utente può accedere ai file tramite il client di sincronizzazione OneDrive o sito OneDrive in SharePoint Online. Dopo aver OneDrive geo move, l'utente verrà connesso automaticamente alla loro OneDrive in corrispondenza della posizione geografica di destinazione quando si spostano per OneDrive in avvio di applicazioni di Office 365. Il client di sincronizzazione verrà avviata automaticamente la sincronizzazione dal nuovo percorso.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="d8ea6-115">Le procedure descritte in questo articolo richiedono il [Modulo di PowerShell di Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="d8ea6-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="d8ea6-116">Spostamento di un sito di OneDrive</span><span class="sxs-lookup"><span data-stu-id="d8ea6-116">Moving a OneDrive site</span></span>

<span data-ttu-id="d8ea6-p104">Per eseguire un OneDrive spostare geo, l'amministratore tenant necessario innanzitutto impostare preferito dati posizione (PDL il suo) alla posizione geografica appropriato. Dopo aver impostato le PDL, attendere almeno 24 ore per l'aggiornamento PDL per la sincronizzazione tra i percorsi geo prima di iniziare lo spostamento geo OneDrive.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="d8ea6-119">Quando con il livello geografico Sposta cmdlet, connettersi al servizio di SharePoint Online nella posizione di geo OneDrive corrente dell'utente, utilizzando la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="d8ea6-120">Ad esempio: per spostare OneDrive dell'utente 'Matt@contosoenergy.onmicrosoft.com', connettersi all'interfaccia di amministrazione di SharePoint EUR OneDrive dell'utente è in posizione geografica EUR:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="d8ea6-121">Convalida dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="d8ea6-121">Validating the environment</span></span>

<span data-ttu-id="d8ea6-122">Prima di iniziare un geo OneDrive spostamento, è consigliabile convalidare l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="d8ea6-123">Per assicurarsi che tutti i percorsi geo siano compatibili, eseguire:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="d8ea6-p105">Se non è un OneDrive in conservazione a fini giudiziari o se contiene un sito secondario, non può essere spostato. È possibile utilizzare il cmdlet Start-SPOUserAndContentMove con il parametro - ValidationOnly per verificare se il OneDrive è in grado di essere spostati:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="d8ea6-p106">Se il OneDrive è pronto per essere spostato o esito negativo se esiste una conservazione a fini giudiziari o sito secondario che potrebbe impedire lo spostamento restituirà esito positivo. Dopo aver verificato che il OneDrive è pronto a passare, è possibile avviare lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="d8ea6-128">Avviare uno spostamento geo OneDrive</span><span class="sxs-lookup"><span data-stu-id="d8ea6-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="d8ea6-129">Per avviare lo spostamento, eseguire:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="d8ea6-130">Utilizzo di questi parametri:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-130">Using these parameters:</span></span>

-   <span data-ttu-id="d8ea6-131">_UserPrincipalName_ – UPN dell'utente viene spostato il cui OneDrive.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="d8ea6-p107">_DestinationDataLocation_ -posizione geografica in cui il OneDrive deve essere spostato. Deve essere uguale al percorso dei dati Preferiti dell'utente.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="d8ea6-134">È consigliabile esecuzione `Get-SPOGeoMoveStateCompatibility` con `ValidationOnly` prima dell'avvio OneDrive geo spostare.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="d8ea6-135">Ad esempio, per spostare il OneDrive di matt@contosoenergy.onmicrosoft.com da EUR Australia, eseguire:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="d8ea6-136">Per pianificare uno spostamento geo per un secondo momento, utilizzare uno dei seguenti parametri:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="d8ea6-137">_PreferredMoveBeginDate_ – move probabile iniziare attualmente specificato.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-137">_PreferredMoveBeginDate_ – The move will likely begin at this specified time.</span></span>

-   <span data-ttu-id="d8ea6-138">_PreferredMoveEndDate_ – probabile spostamento completate manualmente questo intervallo di tempo specificato singoli impegno maggiore.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-138">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis.</span></span>

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="d8ea6-139">Annullare uno spostamento geo OneDrive</span><span class="sxs-lookup"><span data-stu-id="d8ea6-139">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="d8ea6-140">È possibile interrompere lo spostamento geo di OneDrive dell'utente, se lo spostamento non è in corso o completata utilizzando il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-140">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="d8ea6-141">Dove _UserPrincipalName_ è l'UPN dell'utente il cui OneDrive spostare che si desidera interrompere.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-141">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="d8ea6-142">Determinare lo stato corrente</span><span class="sxs-lookup"><span data-stu-id="d8ea6-142">Determining current status</span></span>

<span data-ttu-id="d8ea6-143">È possibile controllare lo stato di un OneDrive geo spostare e da geografica cui si è connessi a utilizzando il cmdlet Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-143">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="d8ea6-144">Nella tabella seguente sono descritti gli stati di spostamento.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-144">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d8ea6-145"><strong>Status</strong></span><span class="sxs-lookup"><span data-stu-id="d8ea6-145"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="d8ea6-146"><strong>Descrizione</strong></span><span class="sxs-lookup"><span data-stu-id="d8ea6-146"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d8ea6-147">Non avviato</span><span class="sxs-lookup"><span data-stu-id="d8ea6-147">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="d8ea6-148">Lo spostamento non è avviato.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-148">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8ea6-149">In corso (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="d8ea6-149">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="d8ea6-150">Lo spostamento è in corso in uno dei seguenti stati: convalida (1/4), eseguire il Backup (2/4), ripristinare 3/4, pulitura (4/4).</span><span class="sxs-lookup"><span data-stu-id="d8ea6-150">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d8ea6-151">Esito positivo</span><span class="sxs-lookup"><span data-stu-id="d8ea6-151">Success</span></span></td>
<td align="left"><span data-ttu-id="d8ea6-152">Lo spostamento è stata completata correttamente.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-152">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8ea6-153">Operazione non riuscita</span><span class="sxs-lookup"><span data-stu-id="d8ea6-153">Failed</span></span></td>
<td align="left"><span data-ttu-id="d8ea6-154">Lo spostamento non è riuscita.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-154">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="d8ea6-155">Per individuare lo stato di spostamento di un utente specifico, utilizzare il parametro UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-155">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="d8ea6-156">Per individuare lo stato di tutti gli spostamenti o ridurre la posizione geografica cui si è connessi a, utilizzare il parametro MoveState con uno dei seguenti valori: NotStarted, in corso, esito positivo, non superato, tutti.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-156">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="d8ea6-157">È inoltre possibile aggiungere il `-Verbose` parametro per una descrizione più dettagliate dello stato di spostamento.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-157">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="d8ea6-158">Prestazioni</span><span class="sxs-lookup"><span data-stu-id="d8ea6-158">User Experience</span></span>

<span data-ttu-id="d8ea6-p108">Gli utenti di OneDrive noteranno un impatto minimo se loro OneDrive viene spostato in una posizione geografica diversi. A parte di uno stato di sola lettura breve durante lo spostamento, autorizzazioni e i collegamenti esistenti continuerà a funzionare come previsto dopo lo spostamento viene completato.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p108">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="d8ea6-161">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="d8ea6-161">OneDrive for Business</span></span>

<span data-ttu-id="d8ea6-p109">Durante lo spostamento in corso OneDrive dell'utente è impostato su sola lettura. Dopo lo spostamento viene completato, l'utente viene indirizzato al loro OneDrive nella nuova posizione geografica quando si spostano per OneDrive il servizio di avvio di applicazioni di Office 365 o un web browser.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p109">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="d8ea6-164">Autorizzazioni su contenuto OneDrive</span><span class="sxs-lookup"><span data-stu-id="d8ea6-164">Permissions on OneDrive content</span></span>

<span data-ttu-id="d8ea6-165">Gli utenti che dispongono delle autorizzazioni per il contenuto OneDrive continuerà a disporre dell'accesso al contenuto durante lo spostamento e al termine dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-165">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="d8ea6-166">Client di sincronizzazione di OneDrive</span><span class="sxs-lookup"><span data-stu-id="d8ea6-166">OneDrive Sync Client</span></span> 

<span data-ttu-id="d8ea6-p110">Il client di sincronizzazione OneDrive verrà rileva automaticamente e senza problemi trasferire sincronizzazione in corso nella nuova posizione OneDrive dopo lo spostamento geo OneDrive è stato completo. L'utente non è necessario accesso nuovamente o eseguire altre azioni.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p110">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="d8ea6-169">Se un utente aggiorna un file durante lo spostamento geo OneDrive è in corso, il client di sincronizzazione verrà informarli che il caricamento di file è in sospeso durante lo spostamento in corso.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-169">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="d8ea6-170">Collegamenti di condivisione</span><span class="sxs-lookup"><span data-stu-id="d8ea6-170">Sharing links</span></span> 

<span data-ttu-id="d8ea6-171">Al livello geografico OneDrive spostare completamento, i collegamenti esistenti condivisi per i file che sono stati spostati reindirizzerà automaticamente nella nuova posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-171">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="d8ea6-172">Utilizzo di OneNote</span><span class="sxs-lookup"><span data-stu-id="d8ea6-172">OneNote Experience</span></span> 

<span data-ttu-id="d8ea6-p111">Client win32 OneNote e UWP App (universale) verrà rileva automaticamente e senza problemi di sincronizzazione blocchi appunti nella nuova posizione OneDrive dopo OneDrive geo spostamento sia stato completato. L'utente non è necessario accesso nuovamente o eseguire altre azioni. L'indicatore visibile solo all'utente è sincronizzazione blocco appunti potrebbe non riuscire se OneDrive geo move è in corso. Questa funzionalità è disponibile nelle versioni client OneNote seguenti:</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p111">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="d8ea6-177">OneNote win32 – versione 16.0.8326.2096 (e versioni successive)</span><span class="sxs-lookup"><span data-stu-id="d8ea6-177">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="d8ea6-178">OneNote UWP – versione 16.0.8431.1006 (e versioni successive)</span><span class="sxs-lookup"><span data-stu-id="d8ea6-178">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="d8ea6-179">OneNote Mobile App – versione 16.0.8431.1011 (e versioni successive)</span><span class="sxs-lookup"><span data-stu-id="d8ea6-179">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="d8ea6-180">I team app</span><span class="sxs-lookup"><span data-stu-id="d8ea6-180">Teams app</span></span>

<span data-ttu-id="d8ea6-p112">Al livello geografico OneDrive spostare completamento, gli utenti potranno accedere ai rispettivi file di OneDrive in App team, inoltre, file condivisi tramite chat team dal proprio OneDrive prima di spostare geo continuerà a funzionare dopo lo spostamento sia stato completato.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p112">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="d8ea6-183">OneDrive per Business Mobile App (iOS)</span><span class="sxs-lookup"><span data-stu-id="d8ea6-183">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="d8ea6-184">Al livello geografico OneDrive spostare completamento, l'utente dovrà disconnettersi e accedere nuovamente a iOS applicazione Mobile per la sincronizzazione con il nuovo percorso di OneDrive.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-184">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="d8ea6-185">Esistenti seguito gruppi e siti</span><span class="sxs-lookup"><span data-stu-id="d8ea6-185">Existing followed groups and sites</span></span>

<span data-ttu-id="d8ea6-p113">Gruppi e siti seguiti verranno visualizzata di OneDrive for business indipendentemente dalla posizione geografica dell'utente. Siti e i gruppi ospitati in un'altra posizione geografica verranno aperto in una scheda distinta.</span><span class="sxs-lookup"><span data-stu-id="d8ea6-p113">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
