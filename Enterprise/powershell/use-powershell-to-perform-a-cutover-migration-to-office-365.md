---
title: Utilizzare PowerShell per eseguire una migrazione completa a Office 365
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 'Riepilogo: informazioni su come utilizzare Windows PowerShell per eseguire una migrazione completa a Office 365.'
ms.openlocfilehash: db2782faac86e53ffd4d2794ee77d53605c9484e
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>Utilizzare PowerShell per eseguire una migrazione completa a Office 365

 **Sintesi:** Informazioni su come utilizzare Windows PowerShell per eseguire una migrazione completa a Office 365.
  
È possibile migrare i contenuti delle cassette postali degli utenti da un sistema di posta elettronica di origine a Office 365 in un'unica operazione utilizzando una migrazione completa. In questo articolo vengono illustrate le attività per una migrazione completa della posta elettronica tramite PowerShell di Exchange Online. 
  
Consultando l'argomento [Informazioni utili su una migrazione completa della posta elettronica a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), è possibile ottenere una panoramica del processo di migrazione. Una volta appresi i contenuti di questo articolo, utilizzarlo per iniziare la migrazione delle cassette postali da un sistema di posta elettronica a un altro.
  
> [!NOTE]
> Inoltre, è possibile utilizzare l'interfaccia di amministrazione di Exchange per eseguire una migrazione completa. Vedere [Eseguire una migrazione completa della posta elettronica a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

Tempo stimato per il completamento di questa attività: tra i 2 e i 5 minuti per creare un batch di migrazione. Dopo l'avvio del batch di migrazione, la durata della migrazione varia in base al numero di cassette postali nel batch, alla dimensione di ogni cassetta postale e alla capacità di rete disponibile. Per informazioni su altri fattori che influenzano il tempo necessario per eseguire la migrazione delle cassette postali su Office 365, vedere l'articolo relativo alle [prestazioni della migrazione](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
È necessario disporre delle autorizzazioni per poter eseguire queste procedure. Per verificare le autorizzazioni necessarie, vedere la voce "Migrazione" in una tabella nell'argomento [Autorizzazioni di destinatari](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Per utilizzare i cmdlet di PowerShell di Exchange Online, è necessario eseguire l'accesso e importare i cmdlet nella sessione di Windows PowerShell locale. Per le istruzioni, vedere [Connettersi a Exchange Online tramite Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121).
  
Per un elenco completo dei comandi di migrazione, vedere [Cmdlet di spostamento e migrazione](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Procedura della migrazione

### <a name="step-1-prepare-for-a-cutover-migration"></a>Passaggio 1: predisporre una migrazione completa
<a name="BK_Step1"> </a>

- **Aggiungere l'organizzazione Exchange locale come dominio accettato dell'organizzazione di Office 365.** Il servizio di migrazione utilizza l'indirizzo SMTP delle relative cassette postali locali per creare l'ID utente Microsoft Online Services e l'indirizzo di posta elettronica per le nuove cassette postali di Office 365. La migrazione ha esito negativo se il dominio di Exchange non è un dominio accettato o il dominio primario dell'organizzazione di Office 365. Per ulteriori informazioni, vedere[Verificare il dominio in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Configurare Outlook via Internet nel server Exchange locale** Nel servizio di migrazione della posta elettronica viene utilizzato RPC su HTTP, anche denominato Outlook via Internet, per connettersi al server Exchange locale. Per informazioni sull'installazione di Outlook via Internet per Exchange 2010, Exchange 2007 ed Exchange 2003, vedere gli argomenti seguenti:
    
  - [Exchange 2010: Abilita Outlook via Internet](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007: Come abilitare Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003: Scenari di distribuzione per RPC su HTTP](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Configurazione di Outlook via Internet con Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > È necessario configurare Outlook via Internet con un certificato considerato attendibile da un'autorità di certificazione (CA, Certificate Authority). Non può essere configurato con un certificato autofirmato. Per ulteriori informazioni, vedere [Come configurare SSL per Outlook via Internet](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
- **Verificare che sia possibile connettersi all'organizzazione di Exchange tramite Outlook via Internet** Provare uno di questi metodi per testare le impostazioni di connessione:
    
  - Utilizzare Microsoft Outlook all'esterno della rete aziendale per connettersi alla cassetta postale di Exchange locale.
    
  - Utilizzare Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) per testare le impostazioni della connessione. Utilizzare Outlook via Internet (RPC su HTTP) o i test di individuazione automatica di Outlook.
    
  - In PowerShell di Exchange Online, eseguire i comandi seguenti.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Assegnare un account utente locali le autorizzazioni necessarie per accedere alle cassette postali nell'organizzazione di Exchange.** L'account utente locale utilizzato per connettersi all'organizzazione di Exchange locale, denominato anche all'amministratore di migrazione, è necessario disporre delle autorizzazioni necessarie per accedere alle cassette postali in locale che si desiderano eseguire la migrazione a Office 365. Questo account utente viene utilizzato per creare un endpoint di migrazione per l'organizzazione locale.
    
    Nel seguente elenco vengono mostrati i privilegi amministrativi necessari per migrare le cassette postali tramite una migrazione completa. Esistono tre opzioni possibili.
    
  - L'amministratore di migrazione deve essere un membro del gruppo **Domain Admins** in Active Directory nell'organizzazione locale.
    
    Oppure
    
  - All'amministratore di migrazione è assegnata l'autorizzazione **FullAccess** per ogni cassetta postale locale.
    
    Oppure
    
  - All'amministratore di migrazione deve essere assegnata l'autorizzazione **Receive As** nel database di cassette postali locali in cui si trovano le cassette postali dell'utente.
    
- **Disabilitare la messaggistica unificata.** Se le cassette postali locali di cui si sta eseguendo la migrazione sono abilitate per la messaggistica unificata, è necessario disabilitare la messaggistica stessa prima di eseguire la migrazione. È possibile quindi riabilitare la messaggistica unificata al termine della migrazione.
    
- **Gruppi e delegati di sicurezza** Il servizio di migrazione della posta elettronica non può rilevare se i gruppi Active Directory in locale siano o meno gruppi di sicurezza, per questo non è possibile predisporre gruppi migrati come gruppi di sicurezza in Office 365. Se si desidera disporre di gruppi di sicurezza nel tenant Office 365, è necessario predisporre prima un gruppo di sicurezza vuoto abilitato alla posta nel tenant di Office 365 prima di avviare la migrazione completa. Inoltre, questo metodo di migrazione consente di spostare solo le cassette postali, gli utenti di posta, i contatti di posta e gruppi abilitati alla posta. Se un altro oggetto di Active Directory, come l'utente non migrato a Office 365, viene assegnato come manager o delegato a un oggetto in corso di migrazione, è necessario rimuoverli dall'oggetto prima della migrazione.
    
### <a name="step-2-create-a-migration-endpoint"></a>Passaggio 2: creare un endpoint di migrazione
<a name="BK_Step2"> </a>

Per eseguire la migrazione della posta elettronica correttamente, Office 365 deve essere in grado di connettersi e comunicare con il sistema di posta elettronica di origine. A tal fine, in Office 365 viene utilizzato un endpoint di migrazione. Per creare un endpoint di migrazione di Outlook via Internet per una migrazione completa, è necessario innanzitutto [connettersi a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Per un elenco completo dei comandi di migrazione, vedere [Cmdlet di spostamento e migrazione](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
In PowerShell di Exchange Online, eseguire i comandi seguenti:
  
```
$Credentials = Get-Credential
```

Nell'esempio viene utilizzato il cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) per ottenere e verificare le impostazioni di connessione al server di Exchange locale. In seguito, tali impostazioni vengono utilizzate per creare l'endpoint di migrazione denominato "CutoverEndpoint".
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> Il cmdlet **New-MigrationEndpoint** può essere utilizzato per specificare un database per il servizio da utilizzare tramite l'opzione **-TargetDatabase**. In caso contrario, un database viene assegnato in modo casuale dal sito di Active Directory Federation Services (ADFS) 2.0 in cui si trova la cassetta postale di gestione.
  
#### <a name="verify-it-worked"></a>Verificare che il passaggio di migrazione sia avvenuto correttamente

In PowerShell di Exchange Online, eseguire il comando riportato di seguito per visualizzare le informazioni sull'endpoint di migrazione "CutoverEndpoint":
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Passaggio 3: creare il batch di migrazione completa
<a name="BK_Step3"> </a>

È possibile utilizzare il cmdlet **New-MigrationBatch** in PowerShell di Exchange Online per creare un batch di migrazione per una migrazione completa. È possibile creare un batch di migrazione e avviarlo automaticamente includendo il parametro _AutoStart_. In alternativa, è possibile creare il batch di migrazione, per poi avviarlo utilizzando il cmdlet **Start-MigrationBatch**. In questo esempio viene creato un batch di migrazione denominato "CutoverBatch" e viene utilizzato l'endpoint di migrazione creato nel passaggio precedente.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

In questo esempio viene inoltre creato un batch di migrazione denominato "CutoverBatch" e viene utilizzato l'endpoint di migrazione creato nel passaggio precedente. Poiché il parametro  _AutoStart_ non è incluso, il batch di migrazione deve essere avviato manualmente nel dashboard di migrazione oppure utilizzando il cmdlet **Start-MigrationBatch**. Come illustrato in precedenza, può esistere solo un batch di migrazione completa alla volta.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Verificare che il passaggio di migrazione sia avvenuto correttamente

Per verificare che sia stato creato correttamente un batch di migrazione per una migrazione completa, eseguire il seguente comando in PowerShell di Exchange Online per visualizzare informazioni sul nuovo batch di migrazione:
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Passaggio 4: avviare il batch di migrazione completa
<a name="BK_Step4"> </a>

Per avviare il batch di migrazione in PowerShell di Exchange Online, eseguire il comando riportato di seguito. In tal modo verrà creato un batch di migrazione denominato "CutoverBatch".
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Verificare che il passaggio di migrazione sia avvenuto correttamente

Se un batch di migrazione è avviato correttamente, il relativo stato sul dashboard di migrazione viene indicato come Sincronizzazione in corso. Per verificare che sia stato avviato correttamente un batch di migrazione tramite PowerShell di Exchange Online, eseguire il comando riportato di seguito:
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>Passaggio 5: instradare la posta elettronica a Office 365
<a name="BK_Step5"> </a>

I sistemi di posta elettronica utilizzano un record DNS denominato record MX per individuare dove recapitare i messaggi di posta elettronica. Durante il processo di migrazione della posta elettronica, il record MX fa riferimento al sistema di posta elettronica di origine. Al termine della migrazione della posta elettronica a Office 365, il record MX fa riferimento a Office 365. Ciò contribuisce a garantire che la posta elettronica sia recapitata alle cassette postali di Office 365. Spostando il record MX, è inoltre possibile disattivare il sistema di posta elettronica precedente al momento più opportuno. 
  
Per molti provider DNS, sono disponibili istruzioni specifiche per [modificare il record MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Se il provider DNS non è incluso oppure si desidera farsi un'idea delle direzioni generali, vengono fornite anche [istruzioni generali sul record MX](https://go.microsoft.com/fwlink/?LinkId=397449).
  
È possibile che i sistemi di posta elettronica dei propri clienti e partner impieghino fino a 72 ore per riconoscere il record MX modificato. Attendere almeno 72 ore prima di procedere con l'attività successiva: [Passaggio 6: eliminare il batch di migrazione completa](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>Passaggio 6: eliminare il batch di migrazione completa
<a name="Bk_step6"> </a>

Dopo aver modificato il record MX e verificato che tutta la posta elettronica venga instradata alle cassette postali di Office 365, informare gli utenti che la loro posta sarà spostata in Office 365. Dopo questa operazione, è possibile eliminare il batch di migrazione completa. Verificare le seguenti condizioni prima di eliminare il batch di migrazione.
  
- Tutti gli utenti utilizzano cassette postali di Office 365. Dopo l'eliminazione del batch, la posta inviata alle cassette postali nel server di Exchange locale non viene copiata nelle cassette postali di Office 365 corrispondenti.
    
- Le cassette postali di Office 365 sono state sincronizzate almeno una volta dal momento in cui hanno cominciato a ricevere la posta elettronica direttamente. A tale scopo, assicurarsi che il valore nella casella Ultima sincronizzazione per il batch di migrazione sia più recente di quello dell'inizio dell'invio della posta direttamente alle cassette postali di Office 365.
    
Per eliminare il batch di migrazione "CutoverBatch" in PowerShell di Exchange Online, eseguire il comando riportato di seguito:
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Sezione 7: assegnare licenze utente
<a name="BK_Step7"> </a>

 **Attivare gli account utente di Office 365 per gli account migrati tramite l'assegnazione delle licenze.** Se non si assegna una licenza, la cassetta postale viene disabilitata al termine del periodo di prova (30 giorni). Per assegnare una licenza in interfaccia di amministrazione di Office 365, vedere[Assegnare licenze per Office 365 per le aziende o annullarne l'assegnazione](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Passaggio 8: completare le attività successive alla migrazione
<a name="BK_Step8"> </a>

- **Creare un record DNS di individuazione automatica affinché gli utenti possano accedere facilmente alle proprie cassette postali.** Al termine della migrazione di tutte le cassette postali a Office 365, è possibile configurare un record DNS di individuazione automatica per la propria organizzazione di Office 365 per consentire agli utenti di connettersi facilmente alle loro nuove cassette postali di Office 365 con Outlook e i client mobili. Questo nuovo record DNS di individuazione automatica deve utilizzare lo stesso spazio dei nomi che si utilizza per l'organizzazione di Office 365. Ad esempio, se lo spazio dei nomi basato su cloud è cloud.contoso.com, il record DNS di individuazione automatica che deve essere creato è autodiscover.cloud.contoso.com.
    
    Inoltre, se si conserva il server di Exchange, è necessario assicurarsi che i record CNAME DNS di individuazione automatica facciano riferimento a Office 365 in DNS interni ed esterni dopo la migrazione, in modo che il client Outlook sia in grado di connettersi alla cassetta postale corretta.
    
    > [!NOTE]
    >  In Exchange 2007, Exchange 2010 e Exchange 2013 è inoltre necessario impostare  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` su `Null`. 
  
    In Office 365 viene utilizzato un record CNAME per implementare il servizio di individuazione automatica per Outlook e i client mobili. Il record CNAME di individuazione automatica deve includere le seguenti informazioni:
    
  - **Alias:** individuazione automatica
    
  - **Destinazione:** autodiscover.outlook.com
    
    Per ulteriori informazioni, vedere [Creare record DNS per Office 365 quando si gestiscono i record DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Rimuovere i server di Exchange locali.** Dopo aver verificato che tutta la posta elettronica venga instradata direttamente alle cassette postali di Office 365 e non è più necessario mantenere l'organizzazione di posta elettronica locale o non si prevede di implementare una soluzione Single Sign On (SSO), è possibile disinstallare Exchange dai server e rimuovere l'organizzazione di Exchange locale.
    
    Per ulteriori informazioni, vedere gli argomenti seguenti:
    
  - [Modifica o eliminazione di Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Come rimuovere un'organizzazione di Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Disinstallazione di Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

