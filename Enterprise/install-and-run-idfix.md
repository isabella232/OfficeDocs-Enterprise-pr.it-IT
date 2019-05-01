---
title: Installazione ed esecuzione dello strumento IDFix di Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Informazioni su come installare ed eseguire lo strumento Office 365 IdFix per la pulizia di Active Directory prima di sincronizzarlo con Office 365.
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488006"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Installazione ed esecuzione dello strumento IDFix di Office 365

IdFix identifica gli errori quali i duplicati e i problemi di formattazione nella directory prima di eseguire la sincronizzazione con Office 365. 
  
Per completare correttamente l'attività, è consigliabile utilizzare gli oggetti utente, gruppo e contatto in Active Directory.
  
[! Importante] se non è possibile completare questa attività, esistono un paio di altre operazioni da eseguire. Questi metodi sono più semplici, ma potrebbero richiedere più tempo o avere degli svantaggi. Tali metodi sono elencati di seguito:
  
- **Esecuzione della sincronizzazione della directory senza eseguire lo strumento IDFix.** È possibile sincronizzare la directory senza eseguire lo strumento IdFix, ma non è consigliabile. Correggere gli errori prima di eseguire la sincronizzazione richiede meno tempo e consente di effettuare una transizione sul cloud senza problemi. 
- **Contattare un consulente.** Richiedere l'assistenza di un esperto può consentire ai tuoi utenti di diventare operativi in modo rapido, nonché di sincronizzare la directory. 
    
## <a name="what-you-need-to-run-idfix"></a>Requisiti per eseguire IDFix

Il modo più facile per iniziare a usare IDFix è rappresentato dall'installazione su un computer associato al tuo dominio. È possibile eseguirlo nel controller di dominio, se lo si desidera, ma non è necessario.
  
### <a name="idfix-hardware-requirements"></a>Requisiti hardware di IDFix

Il computer in cui si installa IdFix deve soddisfare questi requisiti hardware minimi:
  
- 4 GB di RAM
- 2 GB di spazio su disco rigido
    
### <a name="idfix-software-requirements"></a>Requisiti software di IDFix

Il computer in cui viene installato IdFix deve essere aggiunto allo stesso dominio di Active Directory da cui si desidera sincronizzare gli utenti con Office 365. Inoltre, nel computer deve essere installato .NET Framework 4.0. 
  
Se esegui Windows Server 2008 o Windows Server 2012, è probabile che .NET Framework sia già installato. In caso contrario, è possibile [scaricare .net 4,0 dall'area download](https://go.microsoft.com/fwlink/p/?LinkId=400475) o tramite Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisiti di autorizzazione per lo strumento IDFix

L'account utente che usi per eseguire lo strumento IDFix deve disporre di accesso in lettura/scrittura alla directory.
  
Se non si è certi che l'account utente soddisfi questi requisiti e non si è sicuri di come controllare, è comunque possibile installare ed eseguire IdFix. Se l'account utente non dispone delle autorizzazioni appropriate, in IdFix verrà visualizzato un messaggio di errore quando si tenta di eseguirlo.
  
## <a name="install-idfix"></a>Installazione di IDFix

Per installare IdFix, scaricare e decomprimere **IdFix. exe**: 
  
1. Accedi al computer nel quale desideri installare lo strumento IDFix.
    
2. Accedere al sito di download Microsoft per lo [strumento di correzione degli errori di IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Scegliere **Download**.
    
4. Quando richiesto, scegliere **Esegui**.
    
5. Nella finestra di dialogo **Programma di autoestrazione WinZip**, nella casella di testo **Estrai nella cartella**, scrivi o cerca il percorso in cui installare lo strumento IDFix. Per impostazione predefinita, IdFix viene installato `C:\Deployment Tools\`in. 
    
6. Scegliere **unzip**.
    
## <a name="run-the-idfix-tool"></a>Eseguire lo strumento IDFix

Dopo aver installato lo strumento IDFix, eseguilo per rilevare i problemi presenti nella tua directory:
  
1. Usando un account che dispone di accesso in lettura/scrittura alla directory, accedi al computer in cui è installato IDFix.
    
2. In Esplora file, individua il percorso di installazione dello strumento IDFix. Se si è scelto la cartella predefinita durante l'installazione, `C:\Deployment Tools\IdFix`andare a.
    
3. Fai doppio clic su **IdFix.exe**. 
    
    ![Scegliere il file IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. Per impostazione predefinita, IdFix utilizza il set di regole multi-tenant per controllare le voci nella directory. Si tratta del set di regole appropriato per la maggior parte dei clienti di Office 365. Tuttavia, se si è un cliente di Office 365 dedicato o ITAR (International Traffic on Arms Regulations), è possibile configurare IdFix per utilizzare il set di regole dedicato. Se non si è certi del tipo di cliente, è possibile ignorare questo passaggio. Per impostare il set di regole su dedicato, fare clic sull'icona ingranaggio sulla barra dei menu e quindi scegliere **dedicato**.
    
5. Scegliere **query**.
    
    ![Scegliere query in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Per impostazione predefinita, lo strumento IDFix effettua la ricerca di errori nell'intera directory.
    
    A seconda della dimensione della directory, l'esecuzione della query può richiedere un po' di tempo. È possibile guardare lo stato di avanzamento nella parte inferiore della finestra principale dello strumento. Se si fa clic su **Annulla**, sarà necessario riavviare dall'inizio.
    
    ![Conteggio delle query e degli errori di IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Dopo che IdFix ha completato la query, è possibile procedere e sincronizzare la directory se non sono presenti errori. Se sono presenti errori nella directory, ti consigliamo di correggerli prima di eseguire la sincronizzazione. Se desideri ricevere informazioni più dettagliate sui tipi di errore e consigli sul modo migliore per correggerli, consulta i link disponibili alla fine di questo argomento. 
    
    Sebbene non sia obbligatorio correggere gli errori prima della sincronizzazione, ti consigliamo almeno di esaminare tutti quelli restituiti dallo strumenti IDFix.
    
    Ogni errore viene visualizzato in una riga separata nella finestra principale dello strumento. 
    
8. Se accetti la modifica consigliata nella colonna **UPDATE**, nella colonna **ACTION** seleziona l'operazione che desidera che lo strumento IDFix esegua per implementare la modifica, quindi fai clic su **Applica**. Quando fai clic su **Applica**, lo strumento apporta le modifiche nella directory.
    
    Non è necessario fare clic su **applica** dopo ogni aggiornamento. In alternativa, puoi correggere molti errori prima di fare clic su **Applica** in modo che lo strumento IDFix li modifichi in contemporanea. Puoi ordinare gli errori per tipo facendo clic su **ERROR** all'inizio della colonna che elenca i tipi di errore. 
    
    Una strategia consiste nel correggere tutti gli errori dello stesso tipo. ad esempio, per prima cosa correggere tutti i duplicati e applicarli. Successivamente, correggere gli errori relativi al formato dei caratteri e così via. Ogni volta che si applicano le modifiche, lo strumento IdFix crea un file di registro separato che può essere utilizzato per annullare le modifiche nel caso in cui si commette un errore. Il [registro delle transazioni](idfix-transaction-log.md) è archiviato nella cartella in cui è installato IdFix.  _C:\Deployment Tools\IdFix_ per impostazione predefinita. 
    
    ![Correzione degli errori in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Dopo aver apportato tutte le modifiche alla directory, eseguire di nuovo IdFix per assicurarsi che le correzioni apportate non introducano nuovi errori. È possibile ripetere la procedura tutte le volte che è necessario. È consigliabile passare un paio di volte al processo prima di eseguire la sincronizzazione.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Voglio ridefinire la mia ricerca o approfondire gli errori, quale altra operazione posso effettuare con lo strumento IDFix?

In questi argomenti, sono disponibili informazioni più approfondite:
  
- [Preparare gli attributi della directory per la sincronizzazione con Office 365 utilizzando lo strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Dopo aver installato lo strumento, consultare questo argomento per istruzioni dettagliate sulla sua esecuzione, sugli errori comuni che riscontrerai, sulle correzioni suggerite, sugli esempi e sulle procedura migliori da eseguire nel caso di molti errori. 
- [Riferimenti: Oggetti e attributi sclusi e supportati IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Riferimento: Registro delle transazioni IdFix di Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Video di formazione

Per ulteriori informazioni, vedere la lezione [installare e utilizzare lo strumento IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), portato all'utente da LinkedIn Learning.
  

