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
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Spostare un sito di OneDrive in un'altra posizione geografica 

A OneDrive geo spostamento, è possibile spostare OneDrive un utente in una posizione geografica diversi. OneDrive geo move viene eseguita dall'amministratore di SharePoint Online o amministratore globale di Office 365. Prima di avviare un OneDrive geo spostare, assicurarsi di notificare all'utente viene spostato il cui OneDrive e consigliabile che alla chiusura di tutti i file per la durata dello spostamento. (Se l'utente ha Microsoft aprire un documento utilizzando il client di Office durante lo spostamento, quindi su Sposta completamento documento necessario per essere salvato nella nuova posizione.) Lo spostamento può essere pianificato per un secondo momento, se lo si desidera.

Il servizio OneDrive utilizza archiviazione Blob Azure per archiviare il contenuto. Blob Storage associate a OneDrive dell'utente verranno spostate dall'origine alla posizione geografica di destinazione entro 40 giorni di destinazione OneDrive disponibile all'utente. Accesso a OneDrive dell'utente vengono ripristinata non appena la destinazione OneDrive è disponibile.

Durante la finestra di spostamento geo OneDrive (circa 2-6 ore) OneDrive dell'utente è impostato su sola lettura. L'utente può accedere ai file tramite il client di sincronizzazione OneDrive o sito OneDrive in SharePoint Online. Dopo aver OneDrive geo move, l'utente verrà connesso automaticamente alla loro OneDrive in corrispondenza della posizione geografica di destinazione quando si spostano per OneDrive in avvio di applicazioni di Office 365. Il client di sincronizzazione verrà avviata automaticamente la sincronizzazione dal nuovo percorso.

Le procedure descritte in questo articolo richiedono il [Modulo di PowerShell di Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

## <a name="moving-a-onedrive-site"></a>Spostamento di un sito di OneDrive

Per eseguire un OneDrive spostare geo, l'amministratore tenant necessario innanzitutto impostare preferito dati posizione (PDL il suo) alla posizione geografica appropriato. Dopo aver impostato le PDL, attendere almeno 24 ore per l'aggiornamento PDL per la sincronizzazione tra i percorsi geo prima di iniziare lo spostamento geo OneDrive.

Quando con il livello geografico Sposta cmdlet, connettersi al servizio di SharePoint Online nella posizione di geo OneDrive corrente dell'utente, utilizzando la sintassi seguente:

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Ad esempio: per spostare OneDrive dell'utente 'Matt@contosoenergy.onmicrosoft.com', connettersi all'interfaccia di amministrazione di SharePoint EUR OneDrive dell'utente è in posizione geografica EUR:

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>Convalida dell'ambiente

Prima di iniziare un geo OneDrive spostamento, è consigliabile convalidare l'ambiente.

Per assicurarsi che tutti i percorsi geo siano compatibili, eseguire:

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

Se non è un OneDrive in conservazione a fini giudiziari o se contiene un sito secondario, non può essere spostato. È possibile utilizzare il cmdlet Start-SPOUserAndContentMove con il parametro - ValidationOnly per verificare se il OneDrive è in grado di essere spostati:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Se il OneDrive è pronto per essere spostato o esito negativo se esiste una conservazione a fini giudiziari o sito secondario che potrebbe impedire lo spostamento restituirà esito positivo. Dopo aver verificato che il OneDrive è pronto a passare, è possibile avviare lo spostamento.

## <a name="start-a-onedrive-geo-move"></a>Avviare uno spostamento geo OneDrive

Per avviare lo spostamento, eseguire:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Utilizzo di questi parametri:

-   _UserPrincipalName_ – UPN dell'utente viene spostato il cui OneDrive.

-   _DestinationDataLocation_ -posizione geografica in cui il OneDrive deve essere spostato. Deve essere uguale al percorso dei dati Preferiti dell'utente.

> [!NOTE]
> È consigliabile esecuzione `Get-SPOGeoMoveStateCompatibility` con `ValidationOnly` prima dell'avvio OneDrive geo spostare.

Ad esempio, per spostare il OneDrive di matt@contosoenergy.onmicrosoft.com da EUR Australia, eseguire:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

Per pianificare uno spostamento geo per un secondo momento, utilizzare uno dei seguenti parametri:

-   _PreferredMoveBeginDate_ – move probabile iniziare attualmente specificato.

-   _PreferredMoveEndDate_ – probabile spostamento completate manualmente questo intervallo di tempo specificato singoli impegno maggiore.

## <a name="cancel-a-onedrive-geo-move"></a>Annullare uno spostamento geo OneDrive 

È possibile interrompere lo spostamento geo di OneDrive dell'utente, se lo spostamento non è in corso o completata utilizzando il cmdlet:

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

Dove _UserPrincipalName_ è l'UPN dell'utente il cui OneDrive spostare che si desidera interrompere.

## <a name="determining-current-status"></a>Determinare lo stato corrente

È possibile controllare lo stato di un OneDrive geo spostare e da geografica cui si è connessi a utilizzando il cmdlet Get-SPOUserAndContentMoveState.

Nella tabella seguente sono descritti gli stati di spostamento.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Status</strong></th>
<th align="left"><strong>Descrizione</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Non avviato</td>
<td align="left">Lo spostamento non è avviato.</td>
</tr>
<tr class="even">
<td align="left">In corso (<em>n</em>/4)</td>
<td align="left">Lo spostamento è in corso in uno dei seguenti stati: convalida (1/4), eseguire il Backup (2/4), ripristinare 3/4, pulitura (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Esito positivo</td>
<td align="left">Lo spostamento è stata completata correttamente.</td>
</tr>
<tr class="even">
<td align="left">Operazione non riuscita</td>
<td align="left">Lo spostamento non è riuscita.</td>
</tr>
</tbody>
</table>

Per individuare lo stato di spostamento di un utente specifico, utilizzare il parametro UserPrincipalName:

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Per individuare lo stato di tutti gli spostamenti o ridurre la posizione geografica cui si è connessi a, utilizzare il parametro MoveState con uno dei seguenti valori: NotStarted, in corso, esito positivo, non superato, tutti.

`Get-SPOUserAndContentMoveState -MoveState <value>`

È inoltre possibile aggiungere il `-Verbose` parametro per una descrizione più dettagliate dello stato di spostamento.

## <a name="user-experience"></a>Prestazioni

Gli utenti di OneDrive noteranno un impatto minimo se loro OneDrive viene spostato in una posizione geografica diversi. A parte di uno stato di sola lettura breve durante lo spostamento, autorizzazioni e i collegamenti esistenti continuerà a funzionare come previsto dopo lo spostamento viene completato.

### <a name="onedrive-for-business"></a>OneDrive for Business

Durante lo spostamento in corso OneDrive dell'utente è impostato su sola lettura. Dopo lo spostamento viene completato, l'utente viene indirizzato al loro OneDrive nella nuova posizione geografica quando si spostano per OneDrive il servizio di avvio di applicazioni di Office 365 o un web browser.

### <a name="permissions-on-onedrive-content"></a>Autorizzazioni su contenuto OneDrive

Gli utenti che dispongono delle autorizzazioni per il contenuto OneDrive continuerà a disporre dell'accesso al contenuto durante lo spostamento e al termine dell'operazione.

### <a name="onedrive-sync-client"></a>Client di sincronizzazione di OneDrive 

Il client di sincronizzazione OneDrive verrà rileva automaticamente e senza problemi trasferire sincronizzazione in corso nella nuova posizione OneDrive dopo lo spostamento geo OneDrive è stato completo. L'utente non è necessario accesso nuovamente o eseguire altre azioni.

Se un utente aggiorna un file durante lo spostamento geo OneDrive è in corso, il client di sincronizzazione verrà informarli che il caricamento di file è in sospeso durante lo spostamento in corso.

### <a name="sharing-links"></a>Collegamenti di condivisione 

Al livello geografico OneDrive spostare completamento, i collegamenti esistenti condivisi per i file che sono stati spostati reindirizzerà automaticamente nella nuova posizione geografica.

### <a name="onenote-experience"></a>Utilizzo di OneNote 

Client win32 OneNote e UWP App (universale) verrà rileva automaticamente e senza problemi di sincronizzazione blocchi appunti nella nuova posizione OneDrive dopo OneDrive geo spostamento sia stato completato. L'utente non è necessario accesso nuovamente o eseguire altre azioni. L'indicatore visibile solo all'utente è sincronizzazione blocco appunti potrebbe non riuscire se OneDrive geo move è in corso. Questa funzionalità è disponibile nelle versioni client OneNote seguenti:

-   OneNote win32 – versione 16.0.8326.2096 (e versioni successive)

-   OneNote UWP – versione 16.0.8431.1006 (e versioni successive)

-   OneNote Mobile App – versione 16.0.8431.1011 (e versioni successive)

### <a name="teams-app"></a>I team app

Al livello geografico OneDrive spostare completamento, gli utenti potranno accedere ai rispettivi file di OneDrive in App team, inoltre, file condivisi tramite chat team dal proprio OneDrive prima di spostare geo continuerà a funzionare dopo lo spostamento sia stato completato.

### <a name="onedrive-for-business-mobile-app-ios"></a>OneDrive per Business Mobile App (iOS) 

Al livello geografico OneDrive spostare completamento, l'utente dovrà disconnettersi e accedere nuovamente a iOS applicazione Mobile per la sincronizzazione con il nuovo percorso di OneDrive.

### <a name="existing-followed-groups-and-sites"></a>Esistenti seguito gruppi e siti

Gruppi e siti seguiti verranno visualizzata di OneDrive for business indipendentemente dalla posizione geografica dell'utente. Siti e i gruppi ospitati in un'altra posizione geografica verranno aperto in una scheda distinta.
