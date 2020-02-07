---
title: Spostare un sito OneDrive in un'altra posizione geografica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Informazioni su come spostare un sito OneDrive in un'altra posizione geografica.
ms.openlocfilehash: 4b07e0610abdd38a760422eeca50b3cb76e51bf7
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844817"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Spostare un sito OneDrive in un'altra posizione geografica 

Lo spostamento geografico di Onedrive consente di spostare OneDrive di un utente in un'altra posizione geografica. Lo spostamento geografico di OneDrive viene eseguito dall'amministratore di SharePoint Online o dall'amministratore globale di Office 365. Prima di avviare lo spostamento geografico di OneDrive, assicurarsi di informare l'utente che il relativo OneDrive sarà spostato e di suggerirgli di chiudere tutti i file per la durata dello spostamento. Se l'utente ha un documento Office aperto durante lo spostamento, dopo lo spostamento dovrà salvarlo nella nuova posizione. Lo spostamento può essere pianificato nel futuro, se lo si desidera.

Il servizio OneDrive usa Archiviazione BLOB di Azure per archiviare il contenuto. L'archiviazione BLOB associata a OneDrive dell'utente verrà spostata dall'origine alla posizione geografica di destinazione entro 40 giorni, quando il OneDrive di destinazione diventerà disponibile all'utente. L'accesso al OneDrive dell'utente verrà ripristinato non appena il OneDrive di destinazione diventa disponibile. 

Durante il periodo dello spostamento geografico di OneDrive (circa 2-6 ore), OneDrive dell'utente è in sola lettura. L'utente può comunque accedere ai propri file attraverso il client di sincronizzazione di OneDrive oppure il sito OneDrive in SharePoint Online. Al termine dello spostamento geografico di OneDrive, l'utente verrà automaticamente connesso al proprio OneDrive nella posizione geografica di destinazione quando accederà a OneDrive dall'icona di avvio dell'app Office 365. Il client di sincronizzazione inizierà automaticamente la sincronizzazione dalla nuova posizione.

Le procedure descritte in questo articolo richiedono il [modulo PowerShell di Microsoft SharePoint Online](https://www.microsoft.com/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>Disposizioni agli utenti

Quando si effettua lo spostamento dei siti di OneDrive tra le posizioni geografiche, è importante comunicare agli utenti cosa aspettarsi. Questo può aiutare a ridurre la confusione degli utenti e le conseguenti chiamate all'help desk. Inviare una email agli utenti prima dello spostamento per fornire loro le seguenti informazioni:

- Quando si prevede di effettuare lo spostamento e la durata del processo
- Verso quale posizione geografica si sta spostando OneDrive e l'URL per accedere alla nuova posizione
- Evitare di chiudere i file e apportare modifiche durante lo spostamento
- Le autorizzazioni e la condivisione dei file non cambieranno in seguito allo spostamento
- Cosa aspettarsi dall'[esperienza utente in ambiente multi-geografico](multi-geo-user-experience.md)

È necessario inviare agli utenti un'email nel momento in cui lo spostamento è stato completato correttamente informandoli della possibilità di riprendere a lavorare in OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>Pianificazione degli spostamenti dei siti di OneDrive

È possibile pianificare gli spostamenti dei siti di OneDrive in anticipo (come descritto più avanti in questo articolo). È consigliabile iniziare con un numero limitato di utenti per convalidare i flussi di lavoro e le strategie di comunicazione. Una volta acquisita familiarità con la procedura, è possibile pianificare gli spostamenti nel modo seguente:

- È possibile pianificare fino a 4.000 spostamenti alla volta.
- Una volta iniziati gli spostamenti, è possibile pianificarne di nuovi, con un massimo di 4.000 spostamenti in sospeso in coda in qualsiasi momento.
- Le dimensioni massime di OneDrive che consentono lo spostamento sono 1 TB (1 TB).

## <a name="moving-a-onedrive-site"></a>Spostamento di un sito OneDrive

Per eseguire uno spostamento geografico di OneDrive, l'amministratore del tenant deve innanzitutto impostare il percorso dati preferito dell'utente sulla posizione geografica appropriata. Dopo aver impostato il percorso dati preferito, attendere almeno 24 ore che l'aggiornamento del percorso dati preferito  si sincronizzi nelle posizioni geografiche prima di avviare lo spostamento geografico di OneDrive.

Quando si usano i cmdlet dello spostamento geografico, connettersi al servizio SPO nella posizione geografica corrente di OneDrive dell'utente, usando la sintassi seguente:

`Connect-SPOService -url https://<tenantName>-admin.sharepoint.com`

Ad esempio: per spostare OneDrive dell'utente "Matt@contosoenergy.onmicrosoft.com", connettersi all'interfaccia di amministrazione di SharePoint EUR poiché OneDrive dell'utente si trova nella posizione geografica EUR:

`Connect-SPOSservice -url https://contosoenergyeur-admin.sharepoint.com`

![Screenshot della finestra di PowerShell con il cmdlet connect-sposervice](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Convalida dell'ambiente

Prima di iniziare uno spostamento geografico di OneDrive, consigliamo di convalidare l'ambiente.

Per assicurarsi che tutte le posizioni geografiche siano compatibili, eseguire:

`Get-SPOGeoMoveCrossCompatibilityStatus`

Verrà visualizzato un elenco delle posizioni geografiche e, se lo spostamento del contenuto tra tali posizioni è consentito, verrà visualizzata la dicitura "Compatibile". Se il comando restituisce "Incompatibile", provare a ripetere la convalida dello stato in un secondo momento.

Se ad esempio un sito OneDrive contiene un sito secondario, non può essere spostato. È possibile utilizzare il cmdlet Start-SPOUserAndContentMove con il parametro -ValidationOnly per verificare che OneDrive possa essere spostato:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Se OneDrive può essere spostato verrà restituito il valore Success, altrimenti verrà restituito il valore Fail in caso di blocco a fini giudiziari o di un sito secondario che impedisce lo spostamento. Dopo aver verificato che OneDrive può essere spostato, è possibile avviare lo spostamento.

## <a name="start-a-onedrive-geo-move"></a>Avviare lo spostamento geografica di OneDrive

Per avviare lo spostamento, eseguire:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Con questi parametri:

-   _UserPrincipalName_ – UPN dell'utente il cui OneDrive viene spostato.

-   _DestinationDataLocation_ – Posizione geografica dove verrà spostato OneDrive. Deve essere la stessa del percorso dati preferito dell'utente.

Ad esempio, per spostare OneDrive di matt@contosoenergy.onmicrosoft.com da EUR a AUS, eseguire:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![Screenshot della finestra di PowerShell con il cmdlet Start-SPOUserAndContentMove](media/move-onedrive-between-geo-locations-image2.png)

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

Il client di sincronizzazione di OneDrive rileverà automaticamente e trasferirà facilmente la sincronizzazione alla nuova posizione di OneDrive al termine del relativo spostamento geografico. L'utente non deve accedere di nuovo o eseguire altre operazioni. (È richiesta la versione 17.3.6943.0625 o successiva del client di sincronizzazione.)

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
