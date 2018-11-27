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
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Come installare ed eseguire lo strumento IdFix di Office 365 per pulitura di active directory prima della sincronizzazione a Office 365.
ms.openlocfilehash: c485d8397aa32005a34b77f886b9bc8f4e857f1b
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674430"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Installazione ed esecuzione dello strumento IDFix di Office 365

IdFix identifica gli errori, ad esempio duplicati e problemi di formattazione della directory prima della sincronizzazione a Office 365. 
  
Per completare correttamente questa attività, è necessario avere familiarità con l'utente, gruppo e gli oggetti contatto di Active Directory.
  
Se non è possibile completare questa attività, sono disponibili due di altre operazioni da eseguire. Questi metodi potrebbero essere più facile, ma che potrebbero inoltre richiedere più tempo o presentano altri inconvenienti. Sono:
  
- **Eseguire la sincronizzazione delle directory senza eseguire lo strumento IdFix.** È possibile sincronizzare le directory senza eseguire lo strumento IdFix, ma non è consigliabile. Correzione degli errori prima della sincronizzazione impiegherà meno tempo e spesso fornisce una transizione più uniforme nel cloud. 
- **Contattare un consulente.** Richiedere l'assistenza di un esperto può consentire ai tuoi utenti di diventare operativi in modo rapido, nonché di sincronizzare la directory. 
    
## <a name="what-you-need-to-run-idfix"></a>Requisiti per eseguire IDFix

Più semplice tornare IdFix e in esecuzione viene installato in un computer appartenente al dominio. Se si desidera, ma non è necessario, è possibile eseguire lo nel controller di dominio.
  
### <a name="idfix-hardware-requirements"></a>Requisiti hardware di IDFix

Computer in cui è installato lo strumento IdFix deve soddisfare questi requisiti hardware minimi:
  
- 4 GB di RAM
- 2 GB di spazio su disco rigido
    
### <a name="idfix-software-requirements"></a>Requisiti software di IDFix

Computer in cui è installato lo strumento IdFix deve essere aggiunto allo stesso dominio di Active Directory da cui si desidera sincronizzare gli utenti a Office 365. Il computer deve inoltre disporre installato .NET Framework 4.0. 
  
Se si esegue Windows Server 2008 o Windows Server 2012, è probabile che già installato .NET Framework. Se non, è possibile [scaricare .NET 4.0 dall'area download](https://go.microsoft.com/fwlink/p/?LinkId=400475) o tramite Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisiti di autorizzazione per lo strumento IDFix

L'account utente che usi per eseguire lo strumento IDFix deve disporre di accesso in lettura/scrittura alla directory.
  
Se non si è certi che l'account utente soddisfa questi requisiti e non si è certi come controllare, è comunque possibile installare ed eseguire IdFix. Se l'account utente non dispone delle autorizzazioni appropriate, IdFix verrà semplicemente visualizzato un errore quando si tenta di eseguirlo.
  
## <a name="install-idfix"></a>Installazione di IDFix

Per installare lo strumento IdFix, scarica e decomprimere **IdFix.exe**: 
  
1. Accedi al computer nel quale desideri installare lo strumento IDFix.
    
2. Passare al sito di download Microsoft per lo [Strumento di risoluzione dei problemi di IdFix DirSync errore](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Scegliere **Download**.
    
4. Quando richiesto, scegliere **Esegui**.
    
5. Nella casella di testo **Unzip alla cartella** della finestra di dialogo **WinZip Self-Extractor** digitare o selezionare il percorso in cui si desidera installare lo strumento IdFix. Per impostazione predefinita, lo strumento IdFix viene installato nel `C:\Deployment Tools\`. 
    
6. Scegliere **Unzip**.
    
## <a name="run-the-idfix-tool"></a>Eseguire lo strumento IDFix

Dopo aver installato lo strumento IDFix, eseguilo per rilevare i problemi presenti nella tua directory:
  
1. Usando un account che dispone di accesso in lettura/scrittura alla directory, accedi al computer in cui è installato IDFix.
    
2. In Esplora File, passare alla cartella in cui è installato IdFix. Se si sceglie la cartella predefinita durante l'installazione, vedere `C:\Deployment Tools\IdFix`.
    
3. Fai doppio clic su **IdFix.exe**. 
    
    ![Selezionare il file IdFix.exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. Per impostazione predefinita, lo strumento IdFix utilizza multi-Tenant set di regole per testare le voci nella directory. Si tratta della regola destra impostato per la maggior parte dei clienti di Office 365. Tuttavia, se si è un cliente ITAR che offre (traffico internazionale in rami normative) o dedicati di Office 365, è possibile configurare IdFix per l'utilizzo in realtà set di regole dedicato. Se non si è certi di che tipo di cliente è, in modo sicuro è possibile ignorare questo passaggio. Per impostare il set di regole per dedicate, fare clic sull'icona dell'ingranaggio nella barra dei menu e quindi fare clic su **dedicate**.
    
5. Scegliere **Query**.
    
    ![Scegliere query in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Per impostazione predefinita, lo strumento IDFix effettua la ricerca di errori nell'intera directory.
    
    A seconda delle dimensioni della directory, l'esecuzione della query può richiedere un po' di tempo. È possibile controllare lo stato di avanzamento nella parte inferiore della finestra principale dello strumento. Se si sceglie **Annulla**, sarà necessario riavviare dall'inizio.
    
    ![Numero di query e di errore IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Una volta IdFix completata la query, è possibile proseguire e sincronizzare le directory se non sono presenti errori. Se sono presenti errori nella directory, è consigliabile risolverli prima della sincronizzazione. Se si desidera che le informazioni più specifiche relative ai tipi di errori e suggerimenti sul modo migliore per correggere ognuno di essi, vedere i collegamenti alla fine di questo argomento. 
    
    Sebbene non sia obbligatorio correggere gli errori prima della sincronizzazione, ti consigliamo almeno di esaminare tutti quelli restituiti dallo strumenti IDFix.
    
    Ogni errore viene visualizzato in una riga separata nella finestra principale dello strumento. 
    
8. Se accetti la modifica consigliata nella colonna **UPDATE**, nella colonna **ACTION** seleziona l'operazione che desidera che lo strumento IDFix esegua per implementare la modifica, quindi fai clic su **Applica**. Quando fai clic su **Applica**, lo strumento apporta le modifiche nella directory.
    
    Non è necessario fare clic su **Applica** dopo ogni aggiornamento. In realtà, è possibile risolvere diversi errori prima che si fa clic su **Applica** e IdFix verrà modificato tutti alla stessa ora. È possibile ordinare gli errori dal tipo di errore facendo clic su **errori** nella parte superiore della colonna in cui sono elencati i tipi di errore. 
    
    Una strategia consiste nel correggere tutti gli errori dello stesso tipo. ad esempio, eliminare innanzitutto tutti i duplicati e applicarle. Successivamente, correggere gli errori di formato del carattere e così via. Ogni volta che si applicano le modifiche, lo strumento IdFix consente di creare un file di registro distinto che è possibile utilizzare per annullare le modifiche nel caso in cui si effettua un errore. Il [registro delle transazioni](idfix-transaction-log.md) viene archiviato nella cartella in cui è installato IdFix in.  _C:\Deployment Tools\IdFix_ per impostazione predefinita. 
    
    ![Correzione degli errori in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Dopo tutto delle modifiche apportate alla directory, eseguire lo strumento IdFix per verificare che le correzioni apportate non introducano nuovi errori. È possibile ripetere questi passaggi più volte è necessario. È buona norma passare attraverso il processo più volte prima della sincronizzazione.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Voglio ridefinire la mia ricerca o approfondire gli errori, quale altra operazione posso effettuare con lo strumento IDFix?

In questi argomenti, sono disponibili informazioni più approfondite:
  
- [Attributi di directory di preparazione per la sincronizzazione con Office 365 tramite lo strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Dopo aver installato lo strumento ponticello a questo argomento per istruzioni dettagliate su come eseguire lo strumento, si verificheranno gli errori più comuni suggerito correzioni, esempi e procedure consigliate per operazioni da eseguire quando presente un numero elevato di errori. 
- [Riferimenti: Oggetti e attributi sclusi e supportati IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Riferimento: Registro delle transazioni IdFix di Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Video di formazione

Per ulteriori informazioni, vedere la lezione, [installare e utilizzare lo strumento IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), per offerto da Learning LinkedIn.
  

