---
title: Scaricare ed eseguire lo strumento Microsoft 365 IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Come scaricare ed eseguire lo strumento Microsoft 365 IdFix per facilitare la pulizia dei servizi di dominio Active Directory (AD DS) prima di sincronizzarlo con Microsoft 365.
ms.openlocfilehash: dde12d7e16aad8488fe067888eacdf1c80e1a037
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711596"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a>Scaricare ed eseguire lo strumento Microsoft 365 IdFix

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.

IdFix identifica gli errori quali duplicati e problemi di formattazione nel dominio di servizi di dominio Active Directory prima di eseguire la sincronizzazione con Microsoft 365. 
  
Per completare correttamente questa attività, è importante avere familiarità con gli oggetti utente, gruppo e contatto in Active Directory Domain Services.
  
Se non si riesce a completare questa attività, è possibile provare un paio di metodi alternativi. Questi metodi sono più semplici, ma potrebbero richiedere più tempo o avere degli svantaggi. Tali limiti sono elencati di seguito:
  
- **Eseguire la sincronizzazione della directory senza eseguire lo strumento IdFix** 

  È possibile sincronizzare la directory senza eseguire lo strumento IdFix, ma questo metodo non è consigliato. Correggere gli errori prima di eseguire la sincronizzazione richiede meno tempo e consente di effettuare la transizione nel cloud senza problemi. 

- **Contattare un consulente** 

  Richiedere l'assistenza di un esperto può consentire agli utenti aziendali di diventare subito operativi, nonché di sincronizzare la directory. 
    
## <a name="what-you-need-to-run-idfix"></a>Requisiti per eseguire IDFix

Il modo più facile per iniziare a usare IDFix è scaricarlo in un computer associato al dominio di Active Directory Domain Services aziendale. È possibile eseguirlo sul controller di dominio, ma non è obbligatorio.
  
### <a name="idfix-hardware-requirements"></a>Requisiti hardware di IDFix

Il computer in cui si scarica lo strumento IDFix deve soddisfare i requisiti hardware minimi seguenti:
  
- 4 GB di RAM
- 2 MB di spazio libero sul disco rigido
   
### <a name="idfix-software-requirements"></a>Requisiti software di IDFix

Il computer in cui si Scarica IdFix deve essere aggiunto allo stesso dominio AD DS da cui si desidera sincronizzare gli utenti con Microsoft 365. 

Inoltre, nel computer deve essere installato .NET Framework 4.0. Se si esegue Windows Server 2008 o versione successiva, è probabile che .NET Framework sia già installato. In caso contrario, è possibile [scaricare .NET 4.0 dall'Area download](https://go.microsoft.com/fwlink/p/?LinkId=400475) o con Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisiti di autorizzazione per IdFix

L'account utente usato per eseguire lo strumento IdFix deve disporre di accesso in lettura e scrittura al dominio di AD DS.
  
Se non si è certi che l'account utente soddisfi questi requisiti e non si sa come verificarlo, è comunque possibile scaricare ed eseguire IdFix. Se l'account utente non dispone delle autorizzazioni necessarie, verrà semplicemente visualizzato un errore quando si prova a eseguirlo.
  
## <a name="download-and-extract-idfix"></a>Scaricare ed estrarre IdFix

Seguire queste istruzioni. 
  
1. Accedere al computer in cui si vuole eseguire lo strumento IdFix.
    
2. Accedere al sito [dello strumento di correzione degli errori di IdFix DirSync](https://github.com/microsoft/idfix) .
    
3. Fare clic su **Avvia** nella sezione **avvio ClickOnce** per scaricare il file zip. Aprire il file zip.
    
4. Nella finestra **IdFix** scegliere **Estrai** e quindi **Estrai tutto**. Per impostazione predefinita, IdFix viene estratto in `C:\Users\<your user name>\Documents\IdFix`. 
    
5. Scegliere **Estrai**.

I passaggi possono variare in base alla versione di Windows e al browser Internet.
    
## <a name="run-the-idfix-tool"></a>Eseguire lo strumento IdFix

Dopo aver scaricato ed estratto IdFix, eseguirlo per cercare problemi nel dominio di AD DS.
  
1. Usando un account che dispone di accesso in lettura/scrittura al dominio di AD DS, accedere al computer in cui è stato scaricato IdFix.
    
2. In Esplora file passare al percorso di estrazione dello strumento IdFix. Se si è scelta la cartella predefinita durante l'estrazione, passare a `C:\Users\<your user name>\Documents\IdFix`. 
    
3. Fare doppio clic su **IdFix.exe**. 
  
4. Per impostazione predefinita, IdFix utilizza il set di regole multi-tenant per controllare le voci nella directory. Si tratta del set di regole appropriato per la maggior parte dei clienti di Microsoft 365. Tuttavia, se si è un cliente Microsoft 365 dedicato o internazionale per il traffico di armi (ITAR)), è possibile configurare IdFix per l'utilizzo del set di regole dedicato. Se non si sa a quale tipologia di cliente si appartiene, è possibile saltare questo passaggio. Per impostare il set di regole su Dedicato, selezionare l'icona dell'ingranaggio nella barra dei menu e scegliere **Dedicato**.
    
5. Scegliere **Query**.
    
    ![Scegliere Query in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Per impostazione predefinita, lo strumento IDFix effettua la ricerca di errori nell'intera directory.
    
    A seconda della dimensione della directory, l'esecuzione della query può richiedere un po' di tempo. È possibile visualizzare l'avanzamento della procedura nella parte inferiore della finestra principale dello strumento. Se si fa clic su **Annulla**, si dovrà ripetere la procedura dall'inizio.
  
7. Al termine dell'esecuzione della query da parte dello strumento IdFix e se non vengono segnalati errori, è possibile procedere con la sincronizzazione della directory. Se sono presenti errori nella directory, è consigliabile correggerli prima di eseguire la sincronizzazione. Per ulteriori informazioni, vedere [preparare gli attributi della directory per la sincronizzazione con Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) .
    
    Sebbene non sia obbligatorio correggere gli errori prima della sincronizzazione, ti consigliamo almeno di esaminare tutti quelli restituiti dallo strumenti IDFix.
    
    Ogni errore viene visualizzato in una riga separata nella finestra principale dello strumento. 
    
8. Se si accetta la modifica consigliata nella colonna **UPDATE**, nella colonna **ACTION** selezionare l'operazione che si desidera che lo strumento IdFix esegua per implementare la modifica, quindi fare clic su **Applica**. Quando si fa clic su **Applica**, lo strumento apporta le modifiche nella directory.
    
    Non è necessario fare clic su **Applica** dopo ogni aggiornamento. È possibile correggere diversi errori prima di fare clic su **Applica** in modo che lo strumento IdFix li modifichi in contemporanea. È possibile ordinare gli errori per tipo facendo clic su **ERROR** all'inizio della colonna che elenca i tipi di errore. 
    
    Una possibile strategia consiste nel correggere tutti gli errori dello stesso tipo. Ad esempio, correggere prima tutti i duplicati e applicarli. Correggere quindi gli errori relativi al formato dei caratteri e così via. Ogni volta che si applicano le modifiche, lo strumento IdFix crea un file di log separato che può essere usato per annullare le modifiche, in caso di errore. Il [registro delle transazioni](idfix-transaction-log.md) è archiviato nella cartella in cui è stato estratto IdFix, che è _C:\Users \<your user name> \Documents\IdFix_ per impostazione predefinita. 
    
    ![Correggere gli errori in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Dopo aver apportato tutte le modifiche alla directory, eseguire di nuovo lo strumento IdFix per assicurarsi che le correzioni non abbiano introdotto nuovi errori. È possibile ripetere la procedura tutte le volte che è necessario. È consigliabile ripetere il processo più volte prima di eseguire la sincronizzazione.
    
## <a name="additional-resources-on-idfix"></a>Altre risorse su IdFix 

- [Oggetti e attributi esclusi e supportati da IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Registro delle transazioni di Microsoft 365 IdFix](idfix-transaction-log.md)
    
## <a name="video-training"></a>Video di formazione

Per altre informazioni, vedere la lezione [Installare e usare lo strumento IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), offerta da LinkedIn Learning.
  

