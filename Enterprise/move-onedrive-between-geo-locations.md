---
title: Spostare un sito OneDrive in un'altra posizione geografica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informazioni su come spostare un sito OneDrive in un'altra posizione geografica
ms.openlocfilehash: 6bac98cc0707f977b7b585e8ae0a570f4b9662ee
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="f9eec-103">Spostare un sito OneDrive in un'altra posizione geografica</span><span class="sxs-lookup"><span data-stu-id="f9eec-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="f9eec-p101">Lo spostamento geografico di Onedrive consente di spostare OneDrive di un utente in un'altra posizione geografica. Lo spostamento geografico di OneDrive viene eseguito dall'amministratore di SharePoint Online o dall'amministratore globale di Office 365. Prima di avviare lo spostamento geografico di OneDrive, assicurarsi di informare l'utente che il relativo OneDrive sarà spostato e di suggerirgli di chiudere tutti i file per la durata dello spostamento. Se l'utente ha un documento Office aperto durante lo spostamento, dopo lo spostamento dovrà salvarlo nella nuova posizione. Lo spostamento può essere pianificato nel futuro, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="f9eec-p102">Il servizio OneDrive usa Archiviazione BLOB di Azure per archiviare il contenuto. L'archiviazione BLOB associata a OneDrive dell'utente verrà spostata dall'origine alla posizione geografica di destinazione entro 40 giorni, quando il OneDrive di destinazione diventerà disponibile all'utente. L'accesso al OneDrive dell'utente verrà ripristinato non appena il OneDrive di destinazione diventa disponibile. </span><span class="sxs-lookup"><span data-stu-id="f9eec-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="f9eec-p103">Durante il periodo dello spostamento geografico di OneDrive (circa 2-6 ore), OneDrive dell'utente è in sola lettura. L'utente può comunque accedere ai propri file attraverso il client di sincronizzazione di OneDrive oppure il sito OneDrive in SharePoint Online. Al termine dello spostamento geografico di OneDrive, l'utente verrà automaticamente connesso al proprio OneDrive nella posizione geografica di destinazione quando accederà a OneDrive dall'icona di avvio dell'app Office 365. Il client di sincronizzazione inizierà automaticamente la sincronizzazione dalla nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="f9eec-115">Le procedure descritte in questo articolo richiedono il [modulo PowerShell di Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="f9eec-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="f9eec-116">Spostamento di un sito OneDrive</span><span class="sxs-lookup"><span data-stu-id="f9eec-116">Moving a OneDrive site</span></span>

<span data-ttu-id="f9eec-p104">Per eseguire uno spostamento geografico di OneDrive, l'amministratore del tenant deve innanzitutto impostare il percorso dati preferito dell'utente sulla posizione geografica appropriata. Dopo aver impostato il percorso dati preferito, attendere almeno 24 ore che l'aggiornamento del percorso dati preferito  si sincronizzi nelle posizioni geografiche prima di avviare lo spostamento geografico di OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="f9eec-119">Quando si usano i cmdlet dello spostamento geografico, connettersi al servizio SPO nella posizione geografica corrente di OneDrive dell'utente, usando la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="f9eec-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="f9eec-120">Ad esempio: per spostare OneDrive dell'utente "Matt@contosoenergy.onmicrosoft.com", connettersi all'interfaccia di amministrazione di SharePoint EUR poiché OneDrive dell'utente si trova nella posizione geografica EUR:</span><span class="sxs-lookup"><span data-stu-id="f9eec-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="f9eec-121">Convalida dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="f9eec-121">Validating the environment</span></span>

<span data-ttu-id="f9eec-122">Prima di iniziare uno spostamento geografico di OneDrive, consigliamo di convalidare l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="f9eec-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="f9eec-123">Per assicurarsi che tutte le posizioni geografiche siano compatibili, eseguire:</span><span class="sxs-lookup"><span data-stu-id="f9eec-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="f9eec-p105">Se OneDrive è sottoposto a blocco a fini giudiziari o se contiene un sito secondario, non può essere spostato. È possibile utilizzare il cmdlet Start-SPOUserAndContentMove con il parametro -ValidationOnly per verificare che OneDrive possa essere spostato:</span><span class="sxs-lookup"><span data-stu-id="f9eec-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="f9eec-p106">Se OneDrive può essere spostato verrà restituito il valore Success, altrimenti verrà restituito il valore Fail in caso di blocco a fini giudiziari o di un sito secondario che impedisce lo spostamento. Dopo aver verificato che OneDrive può essere spostato, è possibile avviare lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="f9eec-128">Avviare lo spostamento geografica di OneDrive</span><span class="sxs-lookup"><span data-stu-id="f9eec-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="f9eec-129">Per avviare lo spostamento, eseguire:</span><span class="sxs-lookup"><span data-stu-id="f9eec-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="f9eec-130">Con questi parametri:</span><span class="sxs-lookup"><span data-stu-id="f9eec-130">Using these parameters:</span></span>

-   <span data-ttu-id="f9eec-131">_UserPrincipalName_ – UPN dell'utente il cui OneDrive viene spostato.</span><span class="sxs-lookup"><span data-stu-id="f9eec-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="f9eec-p107">_DestinationDataLocation_ – Posizione geografica dove verrà spostato OneDrive. Deve essere la stessa del percorso dati preferito dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="f9eec-134">È consigliabile eseguire `Get-SPOGeoMoveStateCompatibility` con `ValidationOnly` prima di avviare lo spostamento geografico di OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f9eec-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="f9eec-135">Ad esempio, per spostare OneDrive di matt@contosoenergy.onmicrosoft.com da EUR a AUS, eseguire:</span><span class="sxs-lookup"><span data-stu-id="f9eec-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="f9eec-136">Per pianificare lo spostamento geografica in un secondo momento, utilizzare uno dei parametri seguenti:</span><span class="sxs-lookup"><span data-stu-id="f9eec-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="f9eec-p108">_PreferredMoveBeginDate_ – Lo spostamento probabilmente inizierà a un orario specifico. L'ora deve essere specificata in Coordinated Universal Time (UTC).</span><span class="sxs-lookup"><span data-stu-id="f9eec-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="f9eec-p109">_PreferredMoveEndDate_ – Lo spostamento probabilmente finirà entro un orario specifico, sulla base del best effort. L'ora deve essere specificata in Coordinated Universal Time (UTC).</span><span class="sxs-lookup"><span data-stu-id="f9eec-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="f9eec-141">Annullare uno spostamento geografico di OneDrive</span><span class="sxs-lookup"><span data-stu-id="f9eec-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="f9eec-142">È possibile interrompere lo spostamento geografico di OneDrive di un utente, ammesso che lo spostamento non sia in corso o non sia stato completato usando il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="f9eec-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="f9eec-143">Dove _UserPrincipalName_ è il nome dell'entità utente (UPN) dell'utente titolare del OneDrive di cui si desidera interrompere lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="f9eec-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="f9eec-144">Determinare lo stato corrente</span><span class="sxs-lookup"><span data-stu-id="f9eec-144">Determining current status</span></span>

<span data-ttu-id="f9eec-145">È possibile verificare lo stato dello spostamento geografico di OneDrive all'interno o all'esterno della posizione geografica a cui si è connessi utilizzando il cmdlet Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="f9eec-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="f9eec-146">Gli stati dello spostamento sono descritti nella seguente tabella.</span><span class="sxs-lookup"><span data-stu-id="f9eec-146">The fields in alerts are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f9eec-147"><strong>Stato</strong></span><span class="sxs-lookup"><span data-stu-id="f9eec-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="f9eec-148"><strong>Descrizione</strong></span><span class="sxs-lookup"><span data-stu-id="f9eec-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f9eec-149">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f9eec-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="f9eec-150">Lo spostamento non è stato avviato.</span><span class="sxs-lookup"><span data-stu-id="f9eec-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f9eec-151">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="f9eec-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="f9eec-152">Lo spostamento è in corso in uno dei seguenti stati: Convalida (1/4), Backup (2/4), Ripristino 3/4, Pulizia (4/4).</span><span class="sxs-lookup"><span data-stu-id="f9eec-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f9eec-153">Success</span><span class="sxs-lookup"><span data-stu-id="f9eec-153">Success</span></span></td>
<td align="left"><span data-ttu-id="f9eec-154">Lo spostamento è stato completato correttamente.</span><span class="sxs-lookup"><span data-stu-id="f9eec-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f9eec-155">Failed</span><span class="sxs-lookup"><span data-stu-id="f9eec-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="f9eec-156">Lo spostamento non è riuscito.</span><span class="sxs-lookup"><span data-stu-id="f9eec-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f9eec-157">Per trovare lo stato dello spostamento di un utente specifico, utilizzare il parametro UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="f9eec-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="f9eec-158">Per trovare lo stato di tutti gli spostamenti dentro e fuori la posizione geografica alla quale si è connessi, utilizzare il parametro MoveState con uno dei seguenti valori: NotStarted, InProgress, Success, Failed, All.</span><span class="sxs-lookup"><span data-stu-id="f9eec-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="f9eec-159">È anche possibile aggiungere il parametro `-Verbose` per descrizioni più dettagliate dello stato di spostamento.</span><span class="sxs-lookup"><span data-stu-id="f9eec-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="f9eec-160">Esperienza utente</span><span class="sxs-lookup"><span data-stu-id="f9eec-160">User Experience</span></span>

<span data-ttu-id="f9eec-p110">Gli utenti di OneDrive dovrebbero riscontrare un'interruzione minima del proprio OneDrive durante lo spostamento a un'altra posizione geografica. A parte un breve periodo di disponibilità in sola lettura di OneDrive, i collegamenti e le autorizzazioni esistenti continueranno a funzionare come previsto al termine dello spostamento.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="f9eec-163">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="f9eec-163">OneDrive for Business</span></span>

<span data-ttu-id="f9eec-p111">Mentre lo spostamento è in corso, OneDrive dell'utente diventa di sola lettura. Al termine dello spostamento, l'utente viene indirizzato al suo OneDrive nella nuova posizione geografica non appena accede a OneDrive dall'icona di avvio dell'app Office 365 o da un browser Web.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="f9eec-166">Autorizzazioni per il contenuto di OneDrive</span><span class="sxs-lookup"><span data-stu-id="f9eec-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="f9eec-167">Gli utenti con autorizzazioni per il contenuto di OneDrive continueranno ad avere accesso al contenuto durante lo spostamento e dopo il suo completamento.</span><span class="sxs-lookup"><span data-stu-id="f9eec-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="f9eec-168">Client di sincronizzazione di OneDrive</span><span class="sxs-lookup"><span data-stu-id="f9eec-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="f9eec-p112">Il client di sincronizzazione di OneDrive rileverà automaticamente e trasferirà facilmente la sincronizzazione alla nuova posizione di OneDrive al termine del relativo spostamento geografico. L'utente non deve accedere di nuovo o eseguire altre operazioni.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="f9eec-171">Se un utente aggiorna un file mentre lo spostamento geografico di OneDrive è in corso, il client di sincronizzazione lo informerà che i caricamenti file sono in sospeso poiché lo spostamento è in corso.</span><span class="sxs-lookup"><span data-stu-id="f9eec-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="f9eec-172">Condivisione dei collegamenti</span><span class="sxs-lookup"><span data-stu-id="f9eec-172">Sharing links</span></span> 

<span data-ttu-id="f9eec-173">Al completamento dello spostamento geografico di OneDrive, i collegamenti condivisi esistenti dei file spostati verranno reindirizzati automaticamente alla nuova posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="f9eec-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="f9eec-174">Esperienza con OneNote</span><span class="sxs-lookup"><span data-stu-id="f9eec-174">OneNote Experience</span></span> 

<span data-ttu-id="f9eec-p113">Il client win32 di OneNote e l'app UWP (Universal Windows Platform) rileveranno automaticamente e sincronizzeranno facilmente i blocchi appunti nella nuova posizione di OneDrive al termine dello spostamento geografico. L'utente non deve accedere di nuovo o eseguire altre operazioni. L'unico indicatore visibile all'utente viene visualizzato in caso di sincronizzazione non riuscita del blocco appunti durante lo spostamento geografico di OneDrive. Questa esperienza è disponibile nelle seguenti versioni client di OneNote:</span><span class="sxs-lookup"><span data-stu-id="f9eec-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="f9eec-179">OneNote win32 – Versione 16.0.8326.2096 (e successive)</span><span class="sxs-lookup"><span data-stu-id="f9eec-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="f9eec-180">OneNote UWP – Versione 16.0.8431.1006 (e successive)</span><span class="sxs-lookup"><span data-stu-id="f9eec-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="f9eec-181">OneNote Mobile App – Versione 16.0.8431.1011 (e successive)</span><span class="sxs-lookup"><span data-stu-id="f9eec-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="f9eec-182">App Teams</span><span class="sxs-lookup"><span data-stu-id="f9eec-182">Teams app</span></span>

<span data-ttu-id="f9eec-p114">Al completamento dello spostamento geografico di OneDrive, gli utenti avranno accesso ai propri file di OneDrive nell'app Teams. Inoltre, i file condivisi tramite la chat di Teams dal proprio OneDrive, prima dello spostamento geografico, continueranno a funzionare anche al termine dello spostamento.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="f9eec-185">App Mobile di OneDrive for Business (iOS)</span><span class="sxs-lookup"><span data-stu-id="f9eec-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="f9eec-186">Al termine dello spostamento geografico di OneDrive, l'utente deve uscire e accedere di nuovo all'app Mobile per iOS per eseguire la sincronizzazione con la nuova posizione di OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f9eec-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="f9eec-187">I gruppi e siti seguiti esistenti</span><span class="sxs-lookup"><span data-stu-id="f9eec-187">Existing followed groups and sites</span></span>

<span data-ttu-id="f9eec-p115">I gruppi e i siti  seguiti verranno mostrati in OneDrive for business dell'utente indipendentemente dalla loro posizione geografica. I siti e i gruppi ospitati in un'altra posizione geografica si apriranno in una scheda separata.</span><span class="sxs-lookup"><span data-stu-id="f9eec-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
