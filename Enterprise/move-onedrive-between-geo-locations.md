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
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Spostare un sito OneDrive in un'altra posizione geografica 

Lo spostamento geografico di Onedrive consente di spostare OneDrive di un utente in un'altra posizione geografica. Lo spostamento geografico di OneDrive viene eseguito dall'amministratore di SharePoint Online o dall'amministratore globale di Office 365. Prima di avviare lo spostamento geografico di OneDrive, assicurarsi di informare l'utente che il relativo OneDrive sarà spostato e di suggerirgli di chiudere tutti i file per la durata dello spostamento. Se l'utente ha un documento Office aperto durante lo spostamento, dopo lo spostamento dovrà salvarlo nella nuova posizione. Lo spostamento può essere pianificato nel futuro, se lo si desidera.

Il servizio OneDrive usa Archiviazione BLOB di Azure per archiviare il contenuto. L'archiviazione BLOB associata a OneDrive dell'utente verrà spostata dall'origine alla posizione geografica di destinazione entro 40 giorni, quando il OneDrive di destinazione diventerà disponibile all'utente. L'accesso al OneDrive dell'utente verrà ripristinato non appena il OneDrive di destinazione diventa disponibile. 

Durante il periodo dello spostamento geografico di OneDrive (circa 2-6 ore), OneDrive dell'utente è in sola lettura. L'utente può comunque accedere ai propri file attraverso il client di sincronizzazione di OneDrive oppure il sito OneDrive in SharePoint Online. Al termine dello spostamento geografico di OneDrive, l'utente verrà automaticamente connesso al proprio OneDrive nella posizione geografica di destinazione quando accederà a OneDrive dall'icona di avvio dell'app Office 365. Il client di sincronizzazione inizierà automaticamente la sincronizzazione dalla nuova posizione.

Le procedure descritte in questo articolo richiedono il [modulo PowerShell di Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

## <a name="moving-a-onedrive-site"></a>Spostamento di un sito OneDrive

Per eseguire uno spostamento geografico di OneDrive, l'amministratore del tenant deve innanzitutto impostare il percorso dati preferito dell'utente sulla posizione geografica appropriata. Dopo aver impostato il percorso dati preferito, attendere almeno 24 ore che l'aggiornamento del percorso dati preferito  si sincronizzi nelle posizioni geografiche prima di avviare lo spostamento geografico di OneDrive.

Quando si usano i cmdlet dello spostamento geografico, connettersi al servizio SPO nella posizione geografica corrente di OneDrive dell'utente, usando la sintassi seguente:

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Ad esempio: per spostare OneDrive dell'utente "Matt@contosoenergy.onmicrosoft.com", connettersi all'interfaccia di amministrazione di SharePoint EUR poiché OneDrive dell'utente si trova nella posizione geografica EUR:

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>Convalida dell'ambiente

Prima di iniziare uno spostamento geografico di OneDrive, consigliamo di convalidare l'ambiente.

Per assicurarsi che tutte le posizioni geografiche siano compatibili, eseguire:

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

Se OneDrive è sottoposto a blocco a fini giudiziari o se contiene un sito secondario, non può essere spostato. È possibile utilizzare il cmdlet Start-SPOUserAndContentMove con il parametro -ValidationOnly per verificare che OneDrive possa essere spostato:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Se OneDrive può essere spostato verrà restituito il valore Success, altrimenti verrà restituito il valore Fail in caso di blocco a fini giudiziari o di un sito secondario che impedisce lo spostamento. Dopo aver verificato che OneDrive può essere spostato, è possibile avviare lo spostamento.

## <a name="start-a-onedrive-geo-move"></a>Avviare lo spostamento geografica di OneDrive

Per avviare lo spostamento, eseguire:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Con questi parametri:

-   _UserPrincipalName_ – UPN dell'utente il cui OneDrive viene spostato.

-   _DestinationDataLocation_ – Posizione geografica dove verrà spostato OneDrive. Deve essere la stessa del percorso dati preferito dell'utente.

> [!NOTE]
> È consigliabile eseguire `Get-SPOGeoMoveStateCompatibility` con `ValidationOnly` prima di avviare lo spostamento geografico di OneDrive.

Ad esempio, per spostare OneDrive di matt@contosoenergy.onmicrosoft.com da EUR a AUS, eseguire:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

Per pianificare lo spostamento geografica in un secondo momento, utilizzare uno dei parametri seguenti:

-   _PreferredMoveBeginDate_ – Lo spostamento probabilmente inizierà a un orario specifico. L'ora deve essere specificata in Coordinated Universal Time (UTC).

-   _PreferredMoveEndDate_ – Lo spostamento probabilmente finirà entro un orario specifico, sulla base del best effort. L'ora deve essere specificata in Coordinated Universal Time (UTC). 

## <a name="cancel-a-onedrive-geo-move"></a>Annullare uno spostamento geografico di OneDrive 

È possibile interrompere lo spostamento geografico di OneDrive di un utente, ammesso che lo spostamento non sia in corso o non sia stato completato usando il cmdlet:

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

Dove _UserPrincipalName_ è il nome dell'entità utente (UPN) dell'utente titolare del OneDrive di cui si desidera interrompere lo spostamento.

## <a name="determining-current-status"></a>Determinare lo stato corrente

È possibile verificare lo stato dello spostamento geografico di OneDrive all'interno o all'esterno della posizione geografica a cui si è connessi utilizzando il cmdlet Get-SPOUserAndContentMoveState.

Gli stati dello spostamento sono descritti nella seguente tabella.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Stato</strong></th>
<th align="left"><strong>Descrizione</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">Lo spostamento non è stato avviato.</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">Lo spostamento è in corso in uno dei seguenti stati: Convalida (1/4), Backup (2/4), Ripristino 3/4, Pulizia (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Success</td>
<td align="left">Lo spostamento è stato completato correttamente.</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">Lo spostamento non è riuscito.</td>
</tr>
</tbody>
</table>

Per trovare lo stato dello spostamento di un utente specifico, utilizzare il parametro UserPrincipalName:

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Per trovare lo stato di tutti gli spostamenti dentro e fuori la posizione geografica alla quale si è connessi, utilizzare il parametro MoveState con uno dei seguenti valori: NotStarted, InProgress, Success, Failed, All.

`Get-SPOUserAndContentMoveState -MoveState <value>`

È anche possibile aggiungere il parametro `-Verbose` per descrizioni più dettagliate dello stato di spostamento.

## <a name="user-experience"></a>Esperienza utente

Gli utenti di OneDrive dovrebbero riscontrare un'interruzione minima del proprio OneDrive durante lo spostamento a un'altra posizione geografica. A parte un breve periodo di disponibilità in sola lettura di OneDrive, i collegamenti e le autorizzazioni esistenti continueranno a funzionare come previsto al termine dello spostamento.

### <a name="onedrive-for-business"></a>OneDrive for Business

Mentre lo spostamento è in corso, OneDrive dell'utente diventa di sola lettura. Al termine dello spostamento, l'utente viene indirizzato al suo OneDrive nella nuova posizione geografica non appena accede a OneDrive dall'icona di avvio dell'app Office 365 o da un browser Web.

### <a name="permissions-on-onedrive-content"></a>Autorizzazioni per il contenuto di OneDrive

Gli utenti con autorizzazioni per il contenuto di OneDrive continueranno ad avere accesso al contenuto durante lo spostamento e dopo il suo completamento.

### <a name="onedrive-sync-client"></a>Client di sincronizzazione di OneDrive 

Il client di sincronizzazione di OneDrive rileverà automaticamente e trasferirà facilmente la sincronizzazione alla nuova posizione di OneDrive al termine del relativo spostamento geografico. L'utente non deve accedere di nuovo o eseguire altre operazioni.

Se un utente aggiorna un file mentre lo spostamento geografico di OneDrive è in corso, il client di sincronizzazione lo informerà che i caricamenti file sono in sospeso poiché lo spostamento è in corso.

### <a name="sharing-links"></a>Condivisione dei collegamenti 

Al completamento dello spostamento geografico di OneDrive, i collegamenti condivisi esistenti dei file spostati verranno reindirizzati automaticamente alla nuova posizione geografica.

### <a name="onenote-experience"></a>Esperienza con OneNote 

Il client win32 di OneNote e l'app UWP (Universal Windows Platform) rileveranno automaticamente e sincronizzeranno facilmente i blocchi appunti nella nuova posizione di OneDrive al termine dello spostamento geografico. L'utente non deve accedere di nuovo o eseguire altre operazioni. L'unico indicatore visibile all'utente viene visualizzato in caso di sincronizzazione non riuscita del blocco appunti durante lo spostamento geografico di OneDrive. Questa esperienza è disponibile nelle seguenti versioni client di OneNote:

-   OneNote win32 – Versione 16.0.8326.2096 (e successive)

-   OneNote UWP – Versione 16.0.8431.1006 (e successive)

-   OneNote Mobile App – Versione 16.0.8431.1011 (e successive)

### <a name="teams-app"></a>App Teams

Al completamento dello spostamento geografico di OneDrive, gli utenti avranno accesso ai propri file di OneDrive nell'app Teams. Inoltre, i file condivisi tramite la chat di Teams dal proprio OneDrive, prima dello spostamento geografico, continueranno a funzionare anche al termine dello spostamento.

### <a name="onedrive-for-business-mobile-app-ios"></a>App Mobile di OneDrive for Business (iOS) 

Al termine dello spostamento geografico di OneDrive, l'utente deve uscire e accedere di nuovo all'app Mobile per iOS per eseguire la sincronizzazione con la nuova posizione di OneDrive.

### <a name="existing-followed-groups-and-sites"></a>I gruppi e siti seguiti esistenti

I gruppi e i siti  seguiti verranno mostrati in OneDrive for business dell'utente indipendentemente dalla loro posizione geografica. I siti e i gruppi ospitati in un'altra posizione geografica si apriranno in una scheda separata.
