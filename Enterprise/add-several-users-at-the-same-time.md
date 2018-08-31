---
title: Aggiungere più utenti contemporaneamente a Office 365 - Guida per amministratore
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: 'Informazioni su come aggiungere più utenti di Office 365 per aziende da un elenco in un foglio di calcolo o altri CSV formattazione file. Guardare un video su YouTube che illustra come aggiungere gli account a Office 365. Al termine di questo processo, ogni utente con un account avrà una cassetta postale di Office 365. '
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541165"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>Aggiungere più utenti contemporaneamente a Office 365 - Guida per amministratore

Ogni membro del gruppo è necessario un account utente prima di poter effettuare l'accesso e accedere a servizi di Office 365, come messaggio di posta elettronica e l'ufficio. Se si dispone di una quantità elevata di utenti, è possibile aggiungere gli account contemporaneamente da un foglio di calcolo Excel o altri file salvato in formato CSV. [Dubbi è il formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a>Aggiungere più utenti a Office 365 nell'interfaccia di amministrazione di Office 365

1. Accedere a Office 365 con l'account di lavoro o della scuola. 
    
2. Nell'interfaccia di amministrazione di Office 365, scegli **utenti** \> **utenti attivi**.
    
    ![Nell'interfaccia di amministrazione scegliere utenti e quindi attiva](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. **Ulteriori** elenco a discesa, scegliere **Importa più utenti**.
    
4. Nel Pannello di **importare più utenti** , è possibile scaricare facoltativamente un file CSV di esempio con o senza dati di esempio compilati. 
    
    ![In altre elenco a discesa, selezionare Importa più utenti](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    È necessario includere le **intestazioni di colonna stesso esatto** come nell'esempio 1 del foglio di calcolo (nome utente, nome e così via...). Se si utilizza il modello, viene aperto in uno strumento di modifica di testo, ad esempio Blocco note e prendere in considerazione lasciando solo tutti i dati nella riga 1 e solo immettono dati in righe comprese tra 2 e sotto. 
    
    Foglio di calcolo deve inoltre includere i valori per il nome utente (ad esempio bob@contoso.com) e un nome visualizzato (ad esempio Bob Kelly) per ogni utente. 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. Immettere un percorso di file nella casella oppure scegliere **Sfoglia** per individuare il percorso del file CSV e quindi scegliere **Verify**.
    
    ![È stato verificato il file CSV](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    Se si verificano problemi con il file, il problema viene visualizzato nel riquadro. È inoltre possibile scaricare un file di registro.
    
6. Nella finestra di dialogo **impostare le opzioni utente** è possibile impostare lo stato di accesso e scegliere la licenza del prodotto che verrà assegnata a tutti gli utenti. 
    
7. Nella finestra di dialogo **Visualizza i risultati** è possibile scegliere di inviare i risultati a se stessi o con altri utenti (le password saranno in formato testo normale) ed è possibile visualizzare il numero di utenti sono stato creato, e se è necessario acquistare altre licenze da assegnare ad alcuni dei nuovi utenti. 
    
## <a name="watch-the-video"></a>Guardare il video
<a name="bk_preview"> </a>

 Guardare un breve video che illustra come blocco aggiungere gli utenti. 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a>Passaggi successivi
<a name="bk_preview"> </a>

- Ora che tali utenti dispongono di account, è necessario [scaricare e installare o reinstalla Office 365 o 2016 di Office in un PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Ogni membro del gruppo è possibile installare Office 365 in fino a 5 PC o Mac. 
    
- Ogni persona è possibile [Set up Office apps e posta elettronica di un dispositivo mobile](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) in 5 telefoni, ad esempio iPhone, iPad e telefoni Android e Tablet e Tablet fino a 5. In questo modo che è possibile modificare i file di Office da qualsiasi posizione. 
    
    Per un elenco di end-to-end dei passaggi dell'installazione, vedere [configurare Office 365 per aziende](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) . 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>Ulteriori informazioni su come aggiungere utenti a Office 365
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>Indicazioni è il formato CSV?
<a name="__toc316652088"> </a>

Un file CSV è un file con valori separati da virgola. È possibile creare o modificare un file simile al seguente con qualsiasi editor di testo o un foglio di calcolo, ad esempio Excel.
  
È possibile scaricare [il foglio di calcolo di esempio](https://www.microsoft.com/en-us/download/details.aspx?id=45485) come punto di partenza. Ricordare che Office 365 richiede le intestazioni di colonna della prima riga in modo non sostituiscano con un parametro. 
  
Salvare il file con un nuovo nome e specificare il formato CSV.
  
![Un'immagine come salvare un file di Excel in formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
Quando si salva il file, si otterranno probabilmente un prompt che alcune caratteristiche nel foglio di lavoro andranno persi se si salva il file nel formato CSV. Questo è possibile. Fare clic su **Sì** per continuare. 
  
![Un'immagine del prompt dei comandi è possibile ottenere da Excel in cui viene chiesto se si desidera realmente salvare il file come formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Suggerimenti per la formattazione del foglio di calcolo
<a name="__toc314595848"> </a>

- **è necessario le intestazioni di colonna stesso come per la cartella di lavoro di esempio?** Sì. La cartella di lavoro di esempio contiene le intestazioni di colonna della prima riga. Queste voci sono necessari. Per ogni utente che si desidera aggiungere a Office 365, creare una riga sotto l'intestazione. Se si aggiungere, modificare o eliminare una qualsiasi delle intestazioni di colonna, Office 365 potrebbe non essere in grado di creare utenti dalle informazioni del file. 
    
- **Se non è tutte le informazioni necessarie per ogni utente?** Il nome utente e il nome visualizzato sono necessari e non è possibile aggiungere un nuovo utente senza queste informazioni. Se non si dispone di alcune delle altre informazioni, ad esempio fax, è possibile utilizzare una virgola e un spazio per indicare che il campo deve rimanere vuoto. 
    
- * * Come piccole o grandi dimensioni può essere un foglio di calcolo? * * Il foglio di calcolo deve disporre di almeno due righe. Uno è per le intestazioni di colonna (l'etichetta di colonna dati di utente) e una per l'utente. È possibile avere più di 251 righe. Se si desidera importare più di 250 utenti, è possibile creare più di un foglio di calcolo. 
    
- * * Le lingue che è possibile utilizzare? * * Quando si crea il foglio di calcolo, è possibile immettere le etichette di colonna di dati utente in qualsiasi lingua o caratteri, ma non è necessario modificare l'ordine delle etichette, come illustrato nell'esempio di. È possibile rendere le voci nei campi, utilizzando qualsiasi linguaggio o caratteri e salvataggio dei file in formato Unicode o UTF-8. 
    
- **Se si sono aggiungendo gli utenti da diversi paesi o aree?** Creare una cartella di lavoro separato per ogni area. Sarà necessario scorrere il blocco de l'Assistant ajouter quali ogni foglio di calcolo, offrendo un'unica posizione di tutti gli utenti inclusi nel file di cui si sta lavorando. 
    
- **è previsto un limite al numero di caratteri posso utilizzare?** Nella tabella seguente mostra le etichette di colonna di dati utente e la lunghezza massima per ogni nel foglio di calcolo di esempio. 
    
|**Etichetta di colonna di dati utente**|**Numero massimo di caratteri**|
|:-----|:-----|
|Nome utente (obbligatorio)  <br/> |tra cui 79 il simbolo chiocciola (@), in name@domain formato. \<estensione\>. Alias dell'utente non può superare i 30 caratteri e il nome di dominio non può superare 48 caratteri.  <br/> |
|Nome  <br/> |64  <br/> |
|Cognome  <br/> |64  <br/> |
|Nome visualizzato (obbligatorio)  <br/> |256  <br/> |
|Professione  <br/> |64  <br/> |
|Reparto  <br/> |64  <br/> |
|Numero dell'ufficio  <br/> |128  <br/> |
|Telefono ufficio  <br/> |64  <br/> |
|Cellulare  <br/> |64  <br/> |
|Fax  <br/> |64  <br/> |
|Indirizzo  <br/> |1023  <br/> |
|Città  <br/> |128  <br/> |
|Stato o provincia  <br/> |128  <br/> |
|CAP  <br/> |40  <br/> |
|Paese  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a>Ancora problemi durante l'aggiunta di utenti a Office 365?

- **Fare doppio clic sul foglio di calcolo formattato in modo corretto.** Controllare le intestazioni di colonna per assicurarsi che devono essere uguali le intestazioni nel file di esempio. Verificare che si sta seguendo le regole per numero di caratteri e che ogni campo è separata da una virgola. 
    
- * * Se non viene visualizzata i nuovi utenti in Office 365 subito, attendere alcuni minuti. * * Può richiedere un po' mentre per le modifiche al passaggio tra tutti i servizi di Office 365. 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a>Aggiungere più utenti a Office 365 nell'interfaccia di amministrazione di Office 365 precedente

1. Scaricare [il foglio di calcolo di esempio](https://www.microsoft.com/en-us/download/details.aspx?id=45485) e viene aperta in Excel. 
    
    È necessario includere le **intestazioni di colonna stesso esatto** come nell'esempio 1 del foglio di calcolo (nome utente, nome e così via...). Se si utilizza il modello, prendere in considerazione lasciando solo tutti i dati nella riga 1 e solo immettono dati in righe comprese tra 2 e sotto. 
    
    Foglio di calcolo deve inoltre includere i valori per il nome utente (ad esempio bob@contoso.com) e un nome visualizzato (ad esempio Bob Kelly) per ogni utente. Per lasciare vuoti altri campi, immettere una virgola e un spazio nel campo come illustrato nella figura riportata di seguito. 
    
    ![Un file CVS di esempio con righe vuote specificate](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    Se si dispone di utenti che utilizzano diversi paesi, sarà necessario creare una cartella di lavoro per gli utenti in ogni paese. Ad esempio, un foglio di calcolo in cui sono elencati tutti gli utenti che può essere utilizzato negli Stati Uniti e un altro che elenca tutti gli utenti che può essere utilizzato in Giappone. Ciò avviene perché la disponibilità dei servizi di Office 365 varia in base al paese. 
    
    **Suggerimento:** Prima di aggiungere molti utenti a Office 365, è possibile consigliata con la cartella di lavoro di esempio. Ad esempio, modificare il foglio di calcolo di esempio con i dati per alcuni degli utenti, ad esempio 5 o 10 e salvare il file con un nuovo nome. Eseguire passaggi descritti in questa procedura, verificare i risultati, quindi eliminare i nuovi account e ricominciare nuovamente. In questo modo è possibile practice ottenere tutto il diritto di dati per la situazione. Vedere anche [suggerimenti per la formattazione del foglio di calcolo](add-several-users-at-the-same-time.md#__toc314595848).
    
2. Accedere a Office 365 con l'account di lavoro o della scuola. 
    
3. Passare all'interfaccia di amministrazione di Office 365.
    
4. Per gli utenti di utilizzare servizi di Office 365, è necessario assegnare una licenza. Prima di continuare, è possibile verificare di disporre di licenze sufficiente per tutti i contatti presenti nel foglio di calcolo. Scegliere **fatturazione** \> **sottoscrizioni** per vedere se sono sufficienti. Se è necessario acquistare altre licenze, scegliere * * modificare quantità licenza * *. In alternativa, è possibile eseguire la procedura guidata e assegnare licenze sono, quindi acquistare altre licenze più avanti e rieseguire la procedura guidata. 
    
5. Ora accedere per la maggior parte degli utenti installazione guidata: selezione **utenti** \> **Utenti attivi**. Scegliere ![l'icona per l'aggiunta di numero di utenti a Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) come illustrato nella figura riportata di seguito. 
    
    ![Un'immagine della sezione agli utenti di interfaccia di amministrazione di Office 365](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    La maggior parte aggiungere utenti guidata viene visualizzato e i passaggi per l'aggiunta di un gruppo di utenti a Office 365. 
    
6. Nel passaggio 1: selezionare un file CSV, specificare il proprio foglio di calcolo, come illustrato nella figura riportata di seguito.
    
    ![Passaggio 1 del blocco Aggiunta guidata utenti - File CSV Select](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. Nel passaggio 2: verifica, la procedura guidata indica se il contenuto del foglio di calcolo sia formattato correttamente.
    
    ![Passaggio 2 del blocco Aggiunta guidata utenti - verifica](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. Nel passaggio 3 - impostazioni, scegliere **consentiti** in modo che gli utenti elencati nel foglio di calcolo saranno in grado di utilizzare Office 365. Scegliere il paese in cui questi utenti utilizzeranno Office 365. Tenere presente se alcuni utenti all'interno dell'organizzazione intende utilizzare Office 365 in un paese diverso, creare una cartella di lavoro separato con i relativi nomi ed Esegui il blocco Aggiunta guidata utenti per aggiungere quest'ultimo. 
    
    ![Passaggio 3 del blocco Aggiunta guidata utenti - impostazioni](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. Pagina Assegnazione licenze indica quante licenze sono disponibili. 
    
    ![Passaggio 4 della procedura guidata Aggiungi utenti in blocco - licenze](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    È possibile scegliere di **acquistare altre licenze**, ma lasciare il blocco de l'Assistant ajouter e passare alla **fatturazione** nell'interfaccia di amministrazione di Office 365. Dopo aver acquistare altre licenze, è necessario attendere alcuni minuti per l'ordine di elaborazione e quindi avvia il blocco aggiungere guidata utenti dall'inizio. 
    
    Se si non acquistano altre licenze, non sarà possibile creare account per tutti i contatti presenti nel foglio di calcolo. 
    
    In questo esempio è non acquista eventuali altre licenze e continuare con la maggior parte aggiunta guidata utenti.
    
10. Nel passaggio 5 - invia i risultati, digitare gli indirizzi di posta elettronica delle persone che si desiderano ricevere un messaggio di posta elettronica in cui sono elencati *tutti* i nomi utente di Office 365 e password temporanee per gli utenti nel foglio di calcolo. 
    
    ![Passaggio 5 del blocco Aggiunta guidata utenti - Invia risultati](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    Il seguente messaggio di posta elettronica viene inviato a tutti gli indirizzi di posta elettronica specificato nel passaggio 5 - Invia risultati. Questo messaggio indica quali account sono stati creati. Si noti che non sono stati creati gli account per alcune persone poiché non sono disponibili licenze sufficienti. 
    
    ![Un messaggio di posta elettronica di esempio con informazioni sulle credenziali utente](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    È possibile acquistare ulteriori licenze successivamente e Riesegui aggiungere il blocco guidata utenti con stesso foglio di calcolo. La procedura guidata ignora gli utenti che dispongono di account; nel report dei risultati visualizzato il "nome utente duplicati" per indicare un utente con tali informazioni già disponga di un account.
    
11. Pagina finale nel blocco Aggiunta guidata utenti sono elencati i nomi utente e password temporanee, come illustrato nella figura riportata di seguito.
    
    ![Passaggio 6 del blocco Aggiunta guidata utenti - Invia risultati](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. Dopo aver aggiunto gli utenti a Office 365, è necessario per informarli sulle informazioni sull'account Office 365. Utilizzare il normale processo per la comunicazione nuove password.
    

