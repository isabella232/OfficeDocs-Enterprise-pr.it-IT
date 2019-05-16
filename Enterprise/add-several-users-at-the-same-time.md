---
title: Aggiungere più utenti a Office 365 contemporaneamente - Guida dell'amministratore
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
audience: Admin
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
description: 'Informazioni su come aggiungere più utenti a Office 365 for business da un elenco in un foglio di calcolo o in un altro file in formato CSV. Guarda un video su YouTube che spiega come aggiungere account a Office 365. Alla fine di questo processo, ogni utente con un account avrà una cassetta postale di Office 365. '
ms.openlocfilehash: ef4093592d4f6fc8e38ee053b53c73193a821d36
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068692"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>Aggiungere più utenti a Office 365 contemporaneamente - Guida per l'amministratore

Per poter accedere a Office 365 e ai relativi servizi, ad esempio posta elettronica e Office, è necessario che ogni persona del team abbia un account utente. Se il team è composto da numerose persone, è possibile aggiungere tutti gli account contemporaneamente da un foglio di calcolo di Excel o da un altro file salvato in formato CSV. [Che cos'è il formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a>Aggiungere più utenti a Office 365 nell'Interfaccia di amministrazione di Office 365

1. Accedere a Office 365 con l'account di lavoro o della scuola. 
    
2. Nell'Interfaccia di amministrazione di Office 365 scegliere **Utenti** \> **Utenti attivi**.
    
    ![In the Admin center choose Users and then Active users](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. Nel menu a discesa **Altro** scegliere **Importa più utenti**.
    
4. Nel riquadro **Importa più utenti** è possibile scegliere di scaricare un file CSV di esempio con o senza dati di esempio inseriti. 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    Il foglio di calcolo deve includere le **stesse intestazioni di colonna** dell'esempio per il nome utente, il nome, eccetera. Se si usa il modello, aprirlo in un editor di testo, come il Blocco appunti, e lasciare inalterati tutti i dati della riga 1, immettendo i dati solo dalla riga 2 in giù. 
    
    Il foglio di calcolo deve includere anche i valori per il nome utente (ad esempio albertino@contoso.com) e per il nome visualizzato (ad esempio Albertino Mazzanti) di ogni utente. 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. Immettere un percorso di file nella casella oppure scegliere **Sfoglia** per passare al percorso del file CSV e quindi scegliere **Verifica**.
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    Se ci sono problemi con il file, i relativi messaggi vengono visualizzati nel riquadro. È anche possibile scaricare un file di log.
    
6. Nella finestra di dialogo **Imposta opzioni utente** è possibile impostare lo stato di accesso e scegliere la licenza del prodotto che verrà assegnata a tutti gli utenti. 
    
7. Nella finestra di dialogo **Visualizza i risultati** è possibile scegliere di inviare i risultati a se stessi o ad altri utenti (le password saranno in testo normale) ed è possibile vedere quanti utenti sono stati creati e se è necessario acquistare altre licenze da assegnare ad alcuni nuovi utenti. 
    
## <a name="watch-the-video"></a>Guardare il video
<a name="bk_preview"> </a>

 Guardare un breve video che spiega come aggiungere utenti in blocco. 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a>Passaggi successivi
<a name="bk_preview"> </a>

- Ora che queste persone hanno account, devono [scaricare e installare o reinstallare office 365 o office 2016 su un PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Ogni persona del team può installare Office 365 in un totale di 5 PC o Mac. 
    
- Ogni persona può anche [configurare le app di Office e la posta elettronica su un dispositivo mobile su un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) massimo di 5 tablet e 5 telefoni, ad esempio iPhone, iPad, telefoni e Tablet Android. In questo modo, potrà modificare i file di Office ovunque vada. 
    
    Per un elenco end-to-end dei passaggi di configurazione, vedere [configurare Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) . 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>Altre informazioni su come aggiungere utenti a Office 365
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>Che cos'è il formato CSV?
<a name="__toc316652088"> </a>

Un file CSV è un file con valori delimitati da virgole. È possibile creare o modificare un file di questo tipo con qualsiasi editor di testo o foglio di calcolo, ad esempio Excel.
  
Come punto di partenza, è possibile scaricare questo [foglio di calcolo](https://www.microsoft.com/en-us/download/details.aspx?id=45485). Tenere presente che Office 365 richiede intestazioni di colonna nella prima riga, quindi non sostituirle con altro contenuto. 
  
Salvare il file con un nuovo nome e specificare il formato CSV.
  
![Immagine di come salvare un file in formato CSV in Excel](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
Quando si salva il file, è probabile che venga visualizzato un messaggio indicante che alcune caratteristiche della cartella di lavoro andranno perse in formato CSV. Non si tratta di un errore. Fare clic su **Sì** per continuare. 
  
![Immagine del messaggio che potrebbe essere visualizzato in Excel in cui si chiede conferma per salvare il file in formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Suggerimenti per la formattazione del foglio di calcolo
<a name="__toc314595848"> </a>

- **È necessario mantenere le stesse intestazioni di colonna del foglio di calcolo di esempio?** Sì. Il foglio di calcolo di esempio contiene intestazioni di colonna nella prima riga. Queste intestazioni sono obbligatorie. Sotto l'intestazione creare una riga per ogni utente da aggiungere in Office 365. Se si aggiungono intestazioni di colonna oppure si modificano o si eliminano quelle esistenti, Office 365 potrebbe non riuscire a creare gli utenti dalle informazioni del file. 
    
- **Che cosa succede se non si hanno tutte le informazioni necessarie per ogni utente?** I campi obbligatori sono Nome utente e Nome visualizzato, pertanto non è possibile aggiungere un nuovo utente in assenza di tali informazioni. Se non si dispone di altre informazioni, ad esempio il fax, è possibile usare uno spazio seguito da una virgola per indicare che il campo deve rimanere vuoto. 
    
- ** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet. 
    
- ** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format. 
    
- **Che cosa succede se si aggiungono utenti di paesi o aree geografiche diverse?** Creare un foglio di calcolo distinto per ogni area. È necessario eseguire i passaggi della procedura guidata Aggiunta utenti in blocco per ogni foglio di calcolo, specificando una singola area geografica per tutti gli utenti inclusi nel file in uso. 
    
- **È previsto un limite per il numero di caratteri che è possibile usare?** La tabella seguente indica le etichette delle colonne dei dati utente e il numero massimo di caratteri che è possibile usare per ognuna nel foglio di calcolo di esempio. 
    
|**Etichetta colonna dati utente**|**Numero massimo di caratteri**|
|:-----|:-----|
|Nome utente (obbligatorio)  <br/> |79, incluso il simbolo (@), nel formato nome@dominio.\<estensione\>. L'alias dell'utente può essere composto da un massimo di 30 caratteri e il nome di dominio da un massimo di 48 caratteri.  <br/> |
|Nome  <br/> |64  <br/> |
|Cognome  <br/> |64  <br/> |
|Nome visualizzato (obbligatorio)  <br/> |256  <br/> |
|Posizione  <br/> |64  <br/> |
|Reparto  <br/> |64  <br/> |
|Numero ufficio  <br/> |128  <br/> |
|Telefono ufficio  <br/> |64  <br/> |
|Telefono cellulare  <br/> |64  <br/> |
|Fax  <br/> |64  <br/> |
|Indirizzo  <br/> |1023  <br/> |
|Città  <br/> |128  <br/> |
|Provincia  <br/> |128  <br/> |
|CAP  <br/> |40  <br/> |
|Paese o area geografica  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a>Si verificano ancora problemi durante l'aggiunta di utenti a Office 365?

- **Verificare che il foglio di calcolo sia stato formattato correttamente.** Controllare le intestazioni di colonna per verificare che corrispondano a quelle del file di esempio. Assicurarsi di aver rispettato le regole relative al numero massimo di caratteri e di aver usato una virgola per separare i campi. 
    
- ** Se i nuovi utenti non vengono immediatamente visualizzati in Office 365, attendere qualche minuto. ** L'applicazione delle modifiche in tutti i servizi di Office 365 può richiedere tempo. 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a>Aggiungere più utenti a Office 365 nell'Interfaccia di amministrazione di Office 365 precedente

1. Scaricare questo [foglio di calcolo di esempio](https://www.microsoft.com/en-us/download/details.aspx?id=45485) e aprirlo in Excel. 
    
    Il foglio di calcolo deve includere le **stesse intestazioni di colonna** dell'esempio per il nome utente, il nome, eccetera. Se si usa il modello, lasciare inalterati tutti i dati della riga 1, immettendo i dati solo dalla riga 2 in giù. 
    
    Il foglio di calcolo deve includere anche i valori per il nome utente (ad esempio albertino@contoso.com) e per il nome visualizzato (ad esempio Albertino Mazzanti) di ogni utente. Per lasciare vuoti gli altri campi, immettere uno spazio seguito da una virgola nel campo, come illustrato nella figura seguente. 
    
    ![Esempio di file CSV per cui sono state specificate righe vuote](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    In caso di persone che lavorano in paesi diversi, è necessario creare un foglio di calcolo per ogni paese. Creare ad esempio un foglio di calcolo contenente l'elenco di tutti gli utenti che lavorano negli USA e un altro per quelli del Giappone. Il motivo è che la disponibilità dei servizi di Office 365 varia in base all'area geografica. 
    
    **Suggerimento:** prima di aggiungere un numero elevato di utenti a Office 365, è consigliabile esercitarsi con il foglio di calcolo di esempio. Provare a modificare il foglio di calcolo di esempio con i dati di 5 o 10 utenti e salvarlo con un nuovo nome. Eseguire i passaggi descritti in questa procedura, verificare i risultati, quindi eliminare i nuovi account e ricominciare. In questo modo è possibile esercitarsi a recuperare tutti i dati appropriati per la propria situazione. Vedere inoltre [Suggerimenti per la formattazione del foglio di calcolo](add-several-users-at-the-same-time.md#__toc314595848).
    
2. Accedere a Office 365 con l'account di lavoro o della scuola. 
    
3. Passare all'interfaccia di amministrazione di Office 365.
    
4. For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose ** Change license quantity **. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard. 
    
5. A questo punto, per eseguire la procedura guidata Aggiunta utenti in blocco, scegliere **Utenti** \> **Utenti attivi**. Scegliere ![Icona per l'aggiunta di molti utenti in Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png), come illustrato nella figura seguente. 
    
    ![Immagine della sezione Utenti dell'interfaccia di amministrazione di Office 365](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    Verrà visualizzata la procedura guidata Aggiunta utenti in blocco con le istruzioni per l'aggiunta di gruppi di utenti a Office 365. 
    
6. Nel passaggio 1 - Selezione di un file CSV, specificare il proprio foglio di calcolo, come illustrato nella figura seguente.
    
    ![Passaggio 1 della procedura guidata Aggiunta utenti in blocco - Selezione del file CSV](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. Nel passaggio 2 - Verifica, la procedura guidata indica se il contenuto del foglio di calcolo è formattato correttamente.
    
    ![Passaggio 2 della procedura guidata Aggiunta utenti in blocco - Verifica](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. Nel passaggio 3 - Impostazioni, scegliere **Consentito** in modo che le persone elencate nel foglio di calcolo possano usare Office 365. Scegliere inoltre il paese in cui queste persone useranno Office 365. Tenere presente che se alcune persone dell'organizzazione useranno Office 365 in un paese diverso, è necessario creare un foglio di calcolo distinto con i loro nomi ed eseguire di nuovo la procedura guidata Aggiunta utenti in blocco per aggiungerli. 
    
    ![Passaggio 3 della procedura guidata Aggiunta utenti in blocco - Impostazioni](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. La pagina Assegnare le licenze indica quante licenze sono disponibili. 
    
    ![Passaggio 4 della procedura guidata Aggiunta utenti in blocco - Licenze](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    È possibile scegliere **Acquista altre licenze**, ma la procedura guidata Aggiunta utenti in blocco verrà chiusa e si passerà alla sezione **Fatturazione** dell'Interfaccia di amministrazione di Office 365. Dopo aver acquistato altre licenze, è necessario attendere alcuni minuti mentre l'ordine viene elaborato, quindi avviare la procedura guidata Aggiunta utenti in blocco dall'inizio. 
    
    Se non si acquistano altre licenze, gli account non verranno creati per tutti gli utenti elencati del foglio di calcolo. 
    
    In questo esempio non vengono acquistate altre licenze e si prosegue con la procedura guidata Aggiunta utenti in blocco.
    
10. Nel passaggio 5 - Invio dei risultati, digitare gli indirizzi di posta elettronica delle persone a cui si vuole che venga inviato un messaggio di posta elettronica con l'elenco di  *tutti*  i nomi utente di Office 365 e le password temporanee per le persone incluse nel foglio di calcolo. 
    
    ![Passaggio 5 della procedura guidata Aggiunta utenti in blocco - Invio dei risultati](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    Il messaggio seguente viene inviato a tutti gli indirizzi di posta elettronica specificati nel passaggio 5 - Invio dei risultati. Questo messaggio indica quali account sono stati creati. Si noti che per alcune persone non sono stati creati account perché il numero di licenze non è sufficiente. 
    
    ![Esempio di messaggio di posta elettronica con informazioni sulle credenziali utente](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    È possibile acquistare altre licenze in seguito e rieseguire la procedura guidata Aggiunta utenti in blocco con lo stesso foglio di calcolo. La procedura guidata ignora gli utenti che hanno già un account. Nel report dei risultati verrà visualizzato il messaggio "nome utente duplicato", a indicare che qualcuno ha già un account con queste informazioni.
    
11. La pagina finale della procedura guidata Aggiunta utenti in blocco elenca i nomi utente e le password temporanee, come illustrato nella figura seguente.
    
    ![Passaggio 6 della procedura guidata Aggiunta utenti in blocco - Invio dei risultati](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. Dopo aver aggiunto utenti a Office 365, è necessario informarli sul loro account di Office 365. Usare il consueto processo per la comunicazione di nuove password.
    

