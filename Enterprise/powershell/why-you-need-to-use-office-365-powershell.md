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
# <a name="why-you-need-to-use-office-365-powershell"></a>Perché è necessario usare PowerShell di Office 365

 **Sintesi:** comprendere il motivo per cui è necessario utilizzare PowerShell di Office 365 per gestire Office 365, in alcuni casi in modo più efficiente e in altri casi per necessità.
  
Con l'interfaccia di amministrazione di Microsoft 365, è possibile non solo gestire gli account utente e le licenze di Office 365, ma è anche possibile gestire i prodotti di Office 365 server: Exchange, Skype for business online e SharePoint Online. Tuttavia, questi elementi possono essere gestiti anche con i comandi PowerShell di PowerShell di Office 365, sfruttando un ambiente con riga di comando e linguaggio di scripting per velocità, automazione e funzionalità aggiuntive.
  
In questo articolo verranno illustrati i modi in cui è possibile utilizzare PowerShell di Office 365 per gestire Office 365.
  
- Office 365 PowerShell è in grado di rivelare informazioni aggiuntive che non sono visibili con l'interfaccia di amministrazione di Microsoft 365
    
- Office 365 presenta funzionalità che è possibile configurare solo mediante PowerShell di Office 365
    
- PowerShell di Office 365 è ideale per l'esecuzione di operazioni di massa
    
- PowerShell di Office 365 è ottimo per filtrare i dati
    
- PowerShell di Office 365 facilita la stampa e il salvataggio dei dati
    
- PowerShell di Office 365 consente di gestire diversi prodotti server
    
Prima di iniziare, comprendere che PowerShell di Office 365 è un insieme di moduli per Windows PowerShell, un ambiente con riga di comando per i servizi e le piattaforme basati su Windows. Questo ambiente crea un linguaggio della shell dei comandi che è possibile estendere con moduli aggiuntivi e offre un modo per eseguire comandi o script semplici o complessi. Ad esempio, dopo l'installazione dei moduli di PowerShell di Office 365 e la connessione alla sottoscrizione di Office 365, è possibile eseguire questo comando per visualizzare l'elenco di tutte le cassette postali utente per Microsoft Exchange Online:
  
```
Get-Mailbox
```

La possibilità di ottenere l'elenco delle cassette postali può essere completata facilmente utilizzando l'interfaccia di amministrazione di Microsoft 365, ma il conteggio del numero di elementi in tutti gli elenchi di tutti i siti per tutte le app Web non può essere effettuato facilmente.
  
Tenere presente che Office 365 PowerShell è stato creato per aumentare e migliorare la possibilità di gestire Office 365, non per sostituire l'interfaccia di amministrazione di Microsoft 365. In qualità di amministratore di Office 365, è necessario almeno acquisire familiarità con PowerShell di Office 365 poiché esistono alcune procedure di configurazione che possono essere eseguite solo con i comandi di PowerShell di Office 365. In questi casi, verrà richiesto di conoscere le procedure per effettuare le seguenti operazioni:
  
- Installare i moduli di PowerShell di Office 365 (operazione eseguita solo una volta per ogni computer di amministratore).
    
- Connettersi alla sottoscrizione di Office 365 (operazione eseguita una sola volta per ogni sessione di PowerShell).
    
- Raccogliere le informazioni necessarie per eseguire i comandi di PowerShell di Office 365 necessari.
    
- Eseguire correttamente i comandi di PowerShell di Office 365.
    
Dopo aver appreso le competenze di base, non è necessario elencare gli utenti delle cassette postali con il comando **Get-Mailbox**, né saper creare un nuovo comando simile a quello precedente per contare tutti gli elementi in tutti gli elenchi di tutti i siti per tutte le app Web. Microsoft e la community degli amministratori di Office 365 possono offrire supporto per questa operazione.
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>Office 365 PowerShell è in grado di rivelare informazioni aggiuntive che non sono visibili con l'interfaccia di amministrazione di Microsoft 365

L'interfaccia di amministrazione di Microsoft 365 Visualizza molte informazioni utili, ma ciò non significa che Visualizza tutte le informazioni possibili che Office 365 archivia su utenti, licenze, cassette postali e siti. Di seguito è riportato un esempio per **gli utenti e i gruppi** nell'interfaccia di amministrazione di Microsoft 365:
  
![Esempio di visualizzazione di utenti e gruppi nell'interfaccia di amministrazione di Microsoft 365.](media/o365-powershell-users-and-groups.png)
  
Per diversi scopi, verranno visualizzate le informazioni necessarie. Tuttavia, in alcuni casi sono necessarie informazioni aggiuntive. Ad esempio, le licenze di Office 365 (e le funzionalità di Office 365 disponibili per un utente) dipendono in parte dalla posizione geografica dell'utente. I criteri e le funzionalità che è possibile estendere a un utente che vive negli Stati Uniti potrebbero non essere gli stessi per un utente che risiede in India o Belgio. È possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per determinare la posizione geografica di un utente con questa procedura:
  
1. Fare doppio clic sul **Nome visualizzato** dell'utente.
    
2. Nelle proprietà del riquadro di visualizzazione dell'utente, fare clic su **Dettagli**.
    
3. Nella visualizzazione dettagli, fare clic su **ulteriori dettagli**.
    
4. Scorrere verso il basso fino a quando non viene visualizzata l'intestazione **Paese o regione**:
    
     ![Esempio di informazioni sull'area geografica per un utente nell'interfaccia di amministrazione di Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. Prendere nota del nome visualizzato e della posizione dell'utente su un pezzo di carta o copiarlo e incollarlo nel Blocco note. 
    
È necessario ripetere questa procedura per ogni utente. Per molti utenti, potrebbe trattarsi di un'attività noiosa. Con PowerShell di Office 365, è possibile visualizzare queste informazioni per tutti gli utenti con il seguente comando:
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> Questo comando richiede l'installazione del [modulo di Windows Azure Active Directory](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0). 
  
Ecco un esempio di visualizzazione:
  
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
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente ( **Get-MsolUser** ), ma visualizzare solo il nome e la posizione di ogni utente ( **Select DisplayName, UsageLocation** ).
  
Poiché PowerShell di Office 365 supporta un linguaggio della shell dei comandi, è possibile modificare ulteriormente le informazioni ottenute dal comando **Get-MSolUser**. Ad esempio, se si desidera ordinare tali utenti per posizione, è possibile raggruppare tutti gli utenti brasiliani, tutti gli utenti degli Stati Uniti e così via. Ecco il comando:
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Ecco un esempio di visualizzazione:
  
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
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente, ma visualizzare solo il nome e il percorso per ciascun utente, e ordinarli prima in base alla posizione, quindi in base ai nomi ( **Sort UsageLocation, DisplayName** ).
  
È inoltre possibile utilizzare altre opzioni di filtro. Ad esempio, se si desidera visualizzare tali informazioni sugli utenti residenti in Brasile, utilizzare questo comando:
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

Ecco un esempio di visualizzazione:
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente la cui posizione è il Brasile ( **Where {$\_.UsageLocation -eq "BR"}** ), quindi visualizzare posizione e nome di ogni utente.
  
 **Nota rapida riguardo i domini più grandi**
  
Se si dispone di un dominio di grandi dimensioni, con decine di migliaia di utenti, alcuni degli esempi mostrati in questo articolo potrebbero causare una "limitazione". Ciò significa che, in base a dati come la potenza di elaborazione e lunghezza di banda disponibile, si sta cercando di effettuare troppe operazioni contemporaneamente. Per questo, le organizzazioni più grandi potrebbero desiderare di dividere alcuni comandi di PowerShell di Office 365 in due. Ad esempio, questo comando restituisce tutti gli account utente e mostra il nome e la posizione di ciascun utente:
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

Questa operazione funziona perfettamente per i domini più piccoli. Nelle organizzazioni di grandi dimensioni, tuttavia, potrebbe essere necessario dividerlo in due comandi: un comando per archiviare le informazioni sugli account utente in una variabile, l'altro per visualizzare le informazioni necessarie. Ecco un esempio:
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


L'interpretazione di questo set di comandi PowerShell di Office 365 è:
- Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente e archiviare le informazioni in una variabile denominata $x ( **$x = Get-MsolUser** ).
- Visualizzare il contenuto della variabile $x, ma includere solo il nome e la posizione di ciascun utente ( **$x | Select DisplayName, UsageLocation** ).
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a>Office 365 presenta funzionalità che è possibile configurare solo con PowerShell di Office 365

L'interfaccia di amministrazione di Microsoft 365 ha lo scopo di consentire l'accesso alle attività amministrative più comuni o significative che si applicano alla maggior parte delle persone. In altre parole, l'interfaccia di amministrazione di Microsoft 365 è stata progettata in modo che l'amministratore comune potesse utilizzare lo strumento per eseguire le attività di gestione più comuni. In base a questa definizione, significa che sono presenti alcune attività che non possono essere completate tramite l'interfaccia di amministrazione di Microsoft 365.
  
Ad esempio, l'interfaccia di amministrazione di Skype for Business online offre alcune opzioni per la creazione di convocazioni di riunioni personalizzate:
  
![Esempio di visualizzazione di inviti personalizzati a riunioni nell’interfaccia di amministrazione di Skype for Business online.](media/o365-powershell-meeting-invitation.png)
  
Con queste impostazioni, è possibile aggiungere un tocco di personalizzazione e professionalità alle convocazioni di riunioni. Tuttavia, esistono più impostazioni di configurazione di una riunione rispetto alla semplice creazione di convocazioni personalizzate. Ad esempio, per impostazione predefinita le riunioni consentono:
  
- A utenti anonimi di ottenere l'ingresso automatico a ogni riunione.
    
- Ai partecipanti di registrare una riunione.
    
- A tutti gli utenti dell'organizzazione di essere designati come relatori quando partecipano a riunione.
    
Queste impostazioni non sono disponibili dall'interfaccia di amministrazione di Skype for Business online. Tuttavia, è possibile controllarle da PowerShell di Office 365. Ecco un comando che consente di disabilitare queste tre impostazioni:
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Questo comando richiede l'installazione del [modulo di PowerShell per Skype for Business Online ](https://www.microsoft.com/download/details.aspx?id=39366). 
  
> [!TIP]
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Per le impostazioni per le nuove riunioni di Skype for Business online ( **Set-CsMeetingConfiguration** ), disabilitare l'autorizzazione per gli utenti anonimi a ottenere l'accesso automatico alle riunioni ( **- AdmitAnonymousUsersByDefault $False** ), disattivare la possibilità per i partecipanti di registrare le riunioni ( **- AllowConferenceRecording $False** ) e non designare tutti gli utenti dell'organizzazione come relatori ( **-DesignateAsPresenter "None"** ).
  
Se si cambia idea e si desidera ripristinare le impostazioni predefinite (tutte abilitate), sarà sufficiente eseguire questo comando:
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Questo è solo un esempio. Ne esistono altri, per questo motivo l'amministratore di Office 365 deve avere una certa familiarità con l'esecuzione dei comandi di PowerShell di Office 365.
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a>PowerShell di Office 365 è ottimale per eseguire operazioni in massa

Storicamente, le interfacce visive come l'interfaccia di amministrazione di Microsoft 365 sono più importanti quando si ha un'unica operazione da eseguire. Ad esempio, se è necessario disabilitare un account utente, è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per individuare e cancellare rapidamente una casella di controllo. Questa operazione può risultare più semplice rispetto all'esecuzione di un'operazione simile in PowerShell di Office 365.
  
Tuttavia, se è necessario modificare molte cose o alcuni elementi selezionati all'interno di un insieme di grandi dimensioni, è possibile che l'interfaccia di amministrazione di Microsoft 365 non sia il miglior utilizzo del proprio tempo. Ad esempio, se è stato necessario cambiare il prefisso su migliaia di numeri di telefono o se è necessario rimuovere un utente specifico, Ken remario, da tutti i siti di SharePoint Online, come è possibile eseguire tale operazione nell'interfaccia di amministrazione di Microsoft 365?
  
Per quanto riguarda l'ultimo esempio, sono presenti diverse centinaia di siti di SharePoint Online e non si sa nemmeno di quali di questi siti è membro Ken Meyer. Questo significa che sarà necessario iniziare dall'interfaccia di amministrazione di Microsoft 365 e quindi eseguire questa procedura per ogni sito:
  
1. Fare clic sull' **URL** del sito.
    
2. Nella casella **proprietà della raccolta del sito**, fare clic sul link **Indirizzo sito Web** per aprire il sito.
    
3. Nel sito, fare clic su **Condividi**.
    
4. Nella finestra di dialogo **Condividi** fare clic sul link che mostra tutti gli utenti che dispongono delle autorizzazioni per il sito:
    
     ![Esempio di visualizzazione di membri del sito SharePoint Online nell'interfaccia di amministrazione di SharePoint Online.](media/o365-powershell-view-permissions.png)
  
5. Nella finestra di dialogo **Condiviso con** fare clic su **Avanzate**.
    
6. Scorrere l'elenco degli utenti, trovare e selezionare Ken Myer (presumendo che disponga delle autorizzazioni per il sito), quindi fare clic su **Rimuovi autorizzazioni utente**.
    
La procedura può richiedere molto tempo per diverse centinaia di siti.
  
L'alternativa consiste nell'usare PowerShell di Office 365 e il seguente comando per rimuovere Ken Myer da tutti i siti:
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Questo comando richiede l'installazione di [ Connect per PowerShell di SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps). 
  
> [!TIP]
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti i siti di SharePoint nella sottoscrizione di Office 365 corrente ( **Get-SPOSite** ) e per ogni sito, rimuovere Ken Meyer dall'elenco di utenti che possono accedervi ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).
  
Perché stiamo indicando a Office 365 di rimuovere Ken Meyer da tutti i siti, inclusi quelli a cui non può accedere, la visualizzazione di questo comando mostrerà degli errori per i siti per i quali al momento non dispone dell'accesso. È possibile utilizzare una condizione aggiuntiva su questo comando, per rimuovere Ken Meyer solo dai siti in cui compare nell'elenco degli accessi, ma gli errori elencati non danneggiano i siti. Questo comando potrebbe richiedere alcuni minuti per l'esecuzione in centinaia di siti anziché ore di utilizzo dell'interfaccia di amministrazione di Microsoft 365.
  
Ecco un altro esempio di operazione di massa. Utilizzare questo comando per aggiungere Bonnie Kearney, un nuovo amministratore di SharePoint, a tutti i siti dell'organizzazione:
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti i siti di SharePoint nella sottoscrizione di Office 365 corrente e, per ogni sito, consentire l'accesso a Bonnie Kearney aggiungendo il suo nome di accesso al gruppo Membri del sito ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a>PowerShell di Office 365 è molto utile per il filtro dei dati

L'interfaccia di amministrazione di Microsoft 365 offre diversi modi per filtrare i dati in modo da individuare rapidamente e facilmente un sottoinsieme di informazioni mirato. Ad esempio, Exchange facilita il filtro di qualsiasi proprietà relativa alla cassetta postale di un utente. Ad esempio, questo è un elenco delle cassette postali degli utenti che vivono nella città di Bloomington:
  
![Esempio di ricerca avanzata nell'interfaccia di amministrazione di Microsoft 365 per l'elenco delle cassette postali per tutti gli utenti che vivono nella città di Bloomington.](media/o365-powershell-advanced-search.png)
  
L'interfaccia di amministrazione di Exchange consente di combinare i criteri di filtro. Ad esempio, è possibile trovare le cassette postali di tutti i residenti di Bloomington e di coloro che lavorano nel reparto finanziario. 
  
Tuttavia, esistono limitazioni per le operazioni che è possibile eseguire nell'interfaccia di amministrazione di Exchange. Ad esempio, si potrebbe desiderare di individuare le cassette postali di persone che vivono a Bloomington o San Diego oppure le cassette postali di tutte le persone non residenti a Bloomington. 
  
Con PowerShell di Office 365 è possibile ottenere un elenco delle cassette postali di tutte le persone che vivono nelle città di Bloomington o San Diego grazie a questo comando:
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

Ecco un esempio di visualizzazione:
  
```
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente che dispongono di una cassetta postale nelle città di San Diego o Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), quindi visualizzare il nome e la città di ognuno ( **Select DisplayName, City** ).
  
Il comando di seguito consente di elencare tutte le cassette postali delle persone che vivono in qualsiasi altro posto a eccezione di Bloomington:
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Ecco un esempio di visualizzazione:
  
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
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente che dispongono di una cassetta postale non ubicata a Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), quindi visualizzare il nome e la città di ognuno.
  
È inoltre possibile utilizzare caratteri jolly nei filtri PowerShell di Office 365 per trovare una corrispondenza con parte di un nome. Ad esempio, si supponga di effettuare la ricerca di un account utente e di ricordare solo che il cognome potrebbe corrispondere ad Anderson o forse a Henderson oppure Jorgenson.
  
È possibile rintracciare l'utente nell'interfaccia di amministrazione di Microsoft 365 utilizzando lo strumento di ricerca ed effettuando tre ricerche diverse:
  
- Una per  *Anderson* 
    
- Una per  *Henderson* 
    
- Una per  *Jorgenson* 
    
Poiché tutti e tre questi nomi terminano in "son", è possibile indicare a PowerShell di Office 365 di visualizzare tutti gli utenti il cui nome termina con "son". Ecco il comando:
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti nella sottoscrizione a Office 365 corrente, ma utilizzare un filtro che elenca solo gli utenti il cui cognome termina in "son"( **-Filter '{LastName -like "\*son"}'** ). \* rappresenta qualsiasi set di caratteri, vale a dire lettere, nel caso del cognome di un utente.
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a>PowerShell di Office 365 facilita la stampa e il salvataggio dei dati

L'interfaccia di amministrazione di Microsoft 365 consente di visualizzare gli elenchi di dati. Ecco un esempio dell'interfaccia di amministrazione di Skype for Business online che mostra un elenco di utenti che sono stati abilitati per Skype for Business online:
  
![Esempio di interfaccia di amministrazione di Skype for Business online che mostra un elenco di utenti abilitati a Skype for Business online.](media/o365-powershell-lync-users.png)
  
Per salvare queste informazioni in un file, è necessario copiarle e incollarle in un documento o in Excel. In entrambi i casi, la copia potrebbe richiedere ulteriore formattazione. Inoltre, l'interfaccia di amministrazione di Microsoft 365 non consente di stampare direttamente l'elenco visualizzato.
  
Fortunatamente, è possibile utilizzare PowerShell di Office 365 non solo per visualizzare l'elenco, ma anche per salvarlo in un file che può essere facilmente importato in Excel. Ecco un comando di esempio per salvare i dati utente di Skype for Business online in un file con valori delimitati da virgole (CSV), che può essere facilmente importato come tabella in un foglio di lavoro di Excel:
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Ecco un esempio di visualizzazione:
  
![Esempio di tabella importata in un foglio Excel di dati di utenti di Skype for Business online, salvati in un file con valori delimitati da virgole (CSV).](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti di Skype for Business online nella sottoscrizione di Office 365 corrente ( **Get-CsOnlineUser** ), ottenere solo il nome utente, l'UPN e la posizione ( **Select DisplayName, UserPrincipalName, UsageLocation** ), quindi salvare le informazioni nel file CSV denominato C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).
  
È anche possibile utilizzare le opzioni per salvare questo elenco come file XML o pagina HTML. Infatti, con altri comandi di PowerShell, è possibile salvarlo direttamente come file di Excel, con qualsiasi formattazione personalizzata che si desidera. 
  
È anche possibile inviare l'output di un comando PowerShell di Office 365 che visualizza un elenco direttamente alla stampante predefinita in Windows. Ecco un esempio di comando:
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Di seguito, è riportato l'aspetto del documento stampato:
  
![Esempio di documento stampato, output di un comando Office 365 PowerShell elencato direttamente alla stampante predefinita in Windows.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  L'interpretazione di questo comando di PowerShell di Office 365 è: Recuperare tutti gli utenti di Skype for Business online nella sottoscrizione di Office 365 corrente, ottenere solo il nome utente, l'UPN e la posizione, e quindi inviare queste informazioni alla stampante predefinita di Windows ( **Out-Printer** ).
  
Il documento stampato presenta la stessa formattazione semplice visualizzata all'interno della finestra del comando PowerShell di Office 365, ma dopo aver creato un comando PowerShell di Office 365 per elencare gli elementi necessari, è sufficiente aggiungere **| Out-Printer** alla fine del comando per ottenere una copia stampata su cui lavorare.
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a>PowerShell di Office 365 consente di gestire diversi prodotti server

I diversi componenti che costituiscono Office 365 sono progettati per collaborare. Si supponga, ad esempio, di aggiungere un nuovo utente a Office 365 e, dopo aver eseguito l'operazione, di specificare informazioni come il reparto e il numero di telefono dell'utente. Queste informazioni saranno quindi disponibili se si accede alle informazioni dell'utente usando uno dei prodotti server di Office 365: Skype for Business online, Exchange o SharePoint Online.
  
Si tratta di informazioni generali che interessano la famiglia di prodotti. Le informazioni specifiche di un prodotto, ad esempio quelle relative alla cassetta postale di Exchange di un utente, non sono generalmente disponibili tra le famiglie di prodotti. Ad esempio, se si desidera sapere se la cassetta postale di un utente è abilitata o meno, tale informazione è disponibile solo nell'interfaccia di amministrazione di Exchange. 
  
Si supponga di voler creare un report che mostra le seguenti informazioni per tutti gli utenti:
  
- Nome visualizzato dell'utente
    
- La disponibilità della licenza per Office 365 dell'utente
    
- L'abilitazione della cassetta postale di Exchange dell'utente.
    
- L'abilitazione per Skype for Business online dell'utente
    
Al momento non è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 per produrre facilmente un rapporto di questo tipo. Al contrario, è necessario creare un documento separato per archiviare le informazioni, ad esempio un foglio di lavoro di Excel, e ottenere tutti i nomi utente e le informazioni di licenza dall'interfaccia di amministrazione di Microsoft 365, ottenere le informazioni della cassetta postale dall'interfaccia di amministrazione di Exchange, ottenere Skype for Informazioni business online dall'interfaccia di amministrazione di Skype for business online e quindi raccogliere e combinare tali informazioni.
  
L'alternativa consiste nell'usare uno script di PowerShell di Office 365 che compili automaticamente questo report.
  
Il seguente script di esempio è più complesso dei comandi che finora sono stati illustrati in questo articolo. Tuttavia, mostra la possibilità di utilizzare PowerShell di Office 365 per creare visualizzazioni delle informazioni che sono molto difficili da creare in altri modi. Ecco lo script in grado di compilare e visualizzare l'elenco necessario:
  
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

Ecco un esempio di visualizzazione:
  
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

L'interpretazione di questo script di PowerShell di Office 365 è:  
- Recuperare tutti gli utenti nella sottoscrizione di Office 365 corrente e archiviare le informazioni in una variabile denominata $x ( **$x = Get-MsolUser** ).
- Avviare un ciclo che viene eseguito su tutti gli utenti nella variabile denominata $x ( **foreach ($i in $x)** ).  
- Definire una variabile denominata $y e archiviarvi all'interno le informazioni sulla cassetta postale dell'utente ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).
- Aggiungere una nuova proprietà alle informazioni sull'utente denominata IsMailBoxEnabled e impostarla sul valore della proprietà IsMailBoxEnabled della cassetta postale dell'utente ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).
- Definire una variabile denominata $y e archiviarvi all'interno le informazioni su Skype for Business Online relative all'utente ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).
- Aggiungere una nuova proprietà alle informazioni sull'utente denominata EnabledForSfB e impostarla sul valore della proprietà EnabledForSfB della cassetta postale dell'utente di Skype for Business Online ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).
- Visualizzare l'elenco di utenti, ma includere solo il nome, se dispongono di una licenza e le due nuove proprietà che indicano se la loro cassetta postale è abilitata e se loro sono abilitati per Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).
  
## <a name="see-also"></a>Vedere anche

[Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
  
[Gestire gli account utente e le licenze con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Utilizzo di Windows PowerShell per creare rapporti in Office 365](use-windows-powershell-to-create-reports-in-office-365.md)

