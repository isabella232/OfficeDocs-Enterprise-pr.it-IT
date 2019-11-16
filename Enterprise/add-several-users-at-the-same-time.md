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
ms.openlocfilehash: a719b2626eada8abe225a6951af4a2d292667856
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "38030730"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="b5667-105">Aggiungere più utenti a Office 365 contemporaneamente - Guida per l'amministratore</span><span class="sxs-lookup"><span data-stu-id="b5667-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="b5667-p102">Per poter accedere a Office 365 e ai relativi servizi, ad esempio posta elettronica e Office, è necessario che ogni persona del team abbia un account utente. Se il team è composto da numerose persone, è possibile aggiungere tutti gli account contemporaneamente da un foglio di calcolo di Excel o da un altro file salvato in formato CSV. [Che cos'è il formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="b5667-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="b5667-109">Aggiungere più utenti a Office 365 nell'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b5667-109">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="b5667-110">Accedere a Office 365 con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="b5667-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="b5667-111">Nell'interfaccia di **amministrazione scegliere** \> utenti **attivi**.</span><span class="sxs-lookup"><span data-stu-id="b5667-111">In the admin center, choose **Users** \> **Active users**.</span></span>
    
    ![Nell'interfaccia di amministrazione scegliere utenti e quindi utenti attivi](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
    
3. <span data-ttu-id="b5667-113">Nel riquadro **Importa più utenti** è possibile scegliere di scaricare un file CSV di esempio con o senza dati di esempio inseriti.</span><span class="sxs-lookup"><span data-stu-id="b5667-113">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="b5667-115">Il foglio di calcolo deve includere le **stesse intestazioni di colonna** dell'esempio per il nome utente, il nome, eccetera. Se si usa il modello, aprirlo in un editor di testo, come il Blocco appunti, e lasciare inalterati tutti i dati della riga 1, immettendo i dati solo dalla riga 2 in giù.</span><span class="sxs-lookup"><span data-stu-id="b5667-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="b5667-116">Il foglio di calcolo deve includere anche i valori per il nome utente (ad esempio albertino@contoso.com) e per il nome visualizzato (ad esempio Albertino Mazzanti) di ogni utente.</span><span class="sxs-lookup"><span data-stu-id="b5667-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

4. <span data-ttu-id="b5667-117">Immettere un percorso di file nella casella oppure scegliere **Sfoglia** per passare al percorso del file CSV e quindi scegliere **Verifica**.</span><span class="sxs-lookup"><span data-stu-id="b5667-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="b5667-p103">Se ci sono problemi con il file, i relativi messaggi vengono visualizzati nel riquadro. È anche possibile scaricare un file di log.</span><span class="sxs-lookup"><span data-stu-id="b5667-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="b5667-121">Nella finestra di dialogo **Imposta opzioni utente** è possibile impostare lo stato di accesso e scegliere la licenza del prodotto che verrà assegnata a tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="b5667-121">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="b5667-122">Nella finestra di dialogo **Visualizza i risultati** è possibile scegliere di inviare i risultati a se stessi o ad altri utenti (le password saranno in testo normale) ed è possibile vedere quanti utenti sono stati creati e se è necessario acquistare altre licenze da assegnare ad alcuni nuovi utenti.</span><span class="sxs-lookup"><span data-stu-id="b5667-122">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="b5667-123">Guardare il video</span><span class="sxs-lookup"><span data-stu-id="b5667-123">Watch the video</span></span>
<span data-ttu-id="b5667-124"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="b5667-124"></span></span>

 <span data-ttu-id="b5667-125">Guardare un breve video che spiega come aggiungere utenti in blocco.</span><span class="sxs-lookup"><span data-stu-id="b5667-125">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="b5667-126">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b5667-126">Next steps</span></span>
<span data-ttu-id="b5667-127"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="b5667-127"></span></span>

- <span data-ttu-id="b5667-128">Ora che queste persone hanno account, devono [scaricare e installare o reinstallare office 365 o office 2016 su un PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="b5667-128">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="b5667-129">Ogni persona del team può installare Office 365 in un totale di 5 PC o Mac.</span><span class="sxs-lookup"><span data-stu-id="b5667-129">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="b5667-130">Ogni persona può anche [configurare le app di Office e la posta elettronica su un dispositivo mobile su un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) massimo di 5 tablet e 5 telefoni, ad esempio iPhone, iPad, telefoni e Tablet Android.</span><span class="sxs-lookup"><span data-stu-id="b5667-130">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="b5667-131">In questo modo, potrà modificare i file di Office ovunque vada.</span><span class="sxs-lookup"><span data-stu-id="b5667-131">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="b5667-132">Per un elenco end-to-end dei passaggi di configurazione, vedere [configurare Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) .</span><span class="sxs-lookup"><span data-stu-id="b5667-132">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="b5667-133">Altre informazioni su come aggiungere utenti a Office 365</span><span class="sxs-lookup"><span data-stu-id="b5667-133">More information about how to add users to Office 365</span></span>
<span data-ttu-id="b5667-134"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="b5667-134"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="b5667-135">Che cos'è il formato CSV?</span><span class="sxs-lookup"><span data-stu-id="b5667-135">Not sure what CSV format is?</span></span>
<span data-ttu-id="b5667-136"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="b5667-136"></span></span>

<span data-ttu-id="b5667-p106">Un file CSV è un file con valori delimitati da virgole. È possibile creare o modificare un file di questo tipo con qualsiasi editor di testo o foglio di calcolo, ad esempio Excel.</span><span class="sxs-lookup"><span data-stu-id="b5667-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="b5667-p107">Come punto di partenza, è possibile scaricare questo [foglio di calcolo](https://www.microsoft.com/download/details.aspx?id=45485). Tenere presente che Office 365 richiede intestazioni di colonna nella prima riga, quindi non sostituirle con altro contenuto.</span><span class="sxs-lookup"><span data-stu-id="b5667-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="b5667-141">Salvare il file con un nuovo nome e specificare il formato CSV.</span><span class="sxs-lookup"><span data-stu-id="b5667-141">Save the file with a new name, and specify CSV format.</span></span>
  
![Immagine di come salvare un file in formato CSV in Excel](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="b5667-p108">Quando si salva il file, è probabile che venga visualizzato un messaggio indicante che alcune caratteristiche della cartella di lavoro andranno perse in formato CSV. Non si tratta di un errore. Fare clic su **Sì** per continuare.</span><span class="sxs-lookup"><span data-stu-id="b5667-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Immagine del messaggio che potrebbe essere visualizzato in Excel in cui si chiede conferma per salvare il file in formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="b5667-147">Suggerimenti per la formattazione del foglio di calcolo</span><span class="sxs-lookup"><span data-stu-id="b5667-147">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="b5667-148"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="b5667-148"></span></span>

- <span data-ttu-id="b5667-p109">**È necessario mantenere le stesse intestazioni di colonna del foglio di calcolo di esempio?** Sì. Il foglio di calcolo di esempio contiene intestazioni di colonna nella prima riga. Queste intestazioni sono obbligatorie. Sotto l'intestazione creare una riga per ogni utente da aggiungere in Office 365. Se si aggiungono intestazioni di colonna oppure si modificano o si eliminano quelle esistenti, Office 365 potrebbe non riuscire a creare gli utenti dalle informazioni del file.</span><span class="sxs-lookup"><span data-stu-id="b5667-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="b5667-p110">**Che cosa succede se non si hanno tutte le informazioni necessarie per ogni utente?** I campi obbligatori sono Nome utente e Nome visualizzato, pertanto non è possibile aggiungere un nuovo utente in assenza di tali informazioni. Se non si dispone di altre informazioni, ad esempio il fax, è possibile usare uno spazio seguito da una virgola per indicare che il campo deve rimanere vuoto.</span><span class="sxs-lookup"><span data-stu-id="b5667-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="b5667-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="b5667-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="b5667-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="b5667-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="b5667-p113">**Che cosa succede se si aggiungono utenti di paesi o aree geografiche diverse?** Creare un foglio di calcolo distinto per ogni area. È necessario eseguire i passaggi della procedura guidata Aggiunta utenti in blocco per ogni foglio di calcolo, specificando una singola area geografica per tutti gli utenti inclusi nel file in uso.</span><span class="sxs-lookup"><span data-stu-id="b5667-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="b5667-p114">**È previsto un limite per il numero di caratteri che è possibile usare?** La tabella seguente indica le etichette delle colonne dei dati utente e il numero massimo di caratteri che è possibile usare per ognuna nel foglio di calcolo di esempio.</span><span class="sxs-lookup"><span data-stu-id="b5667-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="b5667-171">**Etichetta colonna dati utente**</span><span class="sxs-lookup"><span data-stu-id="b5667-171">**User data column label**</span></span>|<span data-ttu-id="b5667-172">**Numero massimo di caratteri**</span><span class="sxs-lookup"><span data-stu-id="b5667-172">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b5667-173">Nome utente (obbligatorio)</span><span class="sxs-lookup"><span data-stu-id="b5667-173">User Name (Required)</span></span>  <br/> |<span data-ttu-id="b5667-p115">79, incluso il simbolo (@), nel formato nome@dominio.\<estensione\>. L'alias dell'utente può essere composto da un massimo di 30 caratteri e il nome di dominio da un massimo di 48 caratteri.</span><span class="sxs-lookup"><span data-stu-id="b5667-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="b5667-176">Nome</span><span class="sxs-lookup"><span data-stu-id="b5667-176">First Name</span></span>  <br/> |<span data-ttu-id="b5667-177">64</span><span class="sxs-lookup"><span data-stu-id="b5667-177">64</span></span>  <br/> |
|<span data-ttu-id="b5667-178">Cognome</span><span class="sxs-lookup"><span data-stu-id="b5667-178">Last Name</span></span>  <br/> |<span data-ttu-id="b5667-179">64</span><span class="sxs-lookup"><span data-stu-id="b5667-179">64</span></span>  <br/> |
|<span data-ttu-id="b5667-180">Nome visualizzato (obbligatorio)</span><span class="sxs-lookup"><span data-stu-id="b5667-180">Display Name (required)</span></span>  <br/> |<span data-ttu-id="b5667-181">256</span><span class="sxs-lookup"><span data-stu-id="b5667-181">256</span></span>  <br/> |
|<span data-ttu-id="b5667-182">Posizione</span><span class="sxs-lookup"><span data-stu-id="b5667-182">Job Title</span></span>  <br/> |<span data-ttu-id="b5667-183">64</span><span class="sxs-lookup"><span data-stu-id="b5667-183">64</span></span>  <br/> |
|<span data-ttu-id="b5667-184">Reparto</span><span class="sxs-lookup"><span data-stu-id="b5667-184">Department</span></span>  <br/> |<span data-ttu-id="b5667-185">64</span><span class="sxs-lookup"><span data-stu-id="b5667-185">64</span></span>  <br/> |
|<span data-ttu-id="b5667-186">Numero ufficio</span><span class="sxs-lookup"><span data-stu-id="b5667-186">Office Number</span></span>  <br/> |<span data-ttu-id="b5667-187">128</span><span class="sxs-lookup"><span data-stu-id="b5667-187">128</span></span>  <br/> |
|<span data-ttu-id="b5667-188">Telefono ufficio</span><span class="sxs-lookup"><span data-stu-id="b5667-188">Office Phone</span></span>  <br/> |<span data-ttu-id="b5667-189">64</span><span class="sxs-lookup"><span data-stu-id="b5667-189">64</span></span>  <br/> |
|<span data-ttu-id="b5667-190">Telefono cellulare</span><span class="sxs-lookup"><span data-stu-id="b5667-190">Mobile Phone</span></span>  <br/> |<span data-ttu-id="b5667-191">64</span><span class="sxs-lookup"><span data-stu-id="b5667-191">64</span></span>  <br/> |
|<span data-ttu-id="b5667-192">Fax</span><span class="sxs-lookup"><span data-stu-id="b5667-192">Fax</span></span>  <br/> |<span data-ttu-id="b5667-193">64</span><span class="sxs-lookup"><span data-stu-id="b5667-193">64</span></span>  <br/> |
|<span data-ttu-id="b5667-194">Indirizzo</span><span class="sxs-lookup"><span data-stu-id="b5667-194">Address</span></span>  <br/> |<span data-ttu-id="b5667-195">1023</span><span class="sxs-lookup"><span data-stu-id="b5667-195">1023</span></span>  <br/> |
|<span data-ttu-id="b5667-196">Città</span><span class="sxs-lookup"><span data-stu-id="b5667-196">City</span></span>  <br/> |<span data-ttu-id="b5667-197">128</span><span class="sxs-lookup"><span data-stu-id="b5667-197">128</span></span>  <br/> |
|<span data-ttu-id="b5667-198">Provincia</span><span class="sxs-lookup"><span data-stu-id="b5667-198">State or Province</span></span>  <br/> |<span data-ttu-id="b5667-199">128</span><span class="sxs-lookup"><span data-stu-id="b5667-199">128</span></span>  <br/> |
|<span data-ttu-id="b5667-200">CAP</span><span class="sxs-lookup"><span data-stu-id="b5667-200">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="b5667-201">40</span><span class="sxs-lookup"><span data-stu-id="b5667-201">40</span></span>  <br/> |
|<span data-ttu-id="b5667-202">Paese o area geografica</span><span class="sxs-lookup"><span data-stu-id="b5667-202">Country or Region</span></span>  <br/> |<span data-ttu-id="b5667-203">128</span><span class="sxs-lookup"><span data-stu-id="b5667-203">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="b5667-204">Si verificano ancora problemi durante l'aggiunta di utenti a Office 365?</span><span class="sxs-lookup"><span data-stu-id="b5667-204">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="b5667-p116">**Verificare che il foglio di calcolo sia stato formattato correttamente.** Controllare le intestazioni di colonna per verificare che corrispondano a quelle del file di esempio. Assicurarsi di aver rispettato le regole relative al numero massimo di caratteri e di aver usato una virgola per separare i campi.</span><span class="sxs-lookup"><span data-stu-id="b5667-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="b5667-p117">\*\* Se i nuovi utenti non vengono immediatamente visualizzati in Office 365, attendere qualche minuto. \*\* L'applicazione delle modifiche in tutti i servizi di Office 365 può richiedere tempo.</span><span class="sxs-lookup"><span data-stu-id="b5667-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-admin-center"></a><span data-ttu-id="b5667-210">Aggiungere più utenti a Office 365 nell'interfaccia di amministrazione precedente</span><span class="sxs-lookup"><span data-stu-id="b5667-210">Add multiple users to Office 365 in the old admin center</span></span>

1. <span data-ttu-id="b5667-211">Scaricare questo [foglio di calcolo di esempio](https://www.microsoft.com/download/details.aspx?id=45485) e aprirlo in Excel.</span><span class="sxs-lookup"><span data-stu-id="b5667-211">Download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="b5667-212">Il foglio di calcolo deve includere le **stesse intestazioni di colonna** dell'esempio per il nome utente, il nome, eccetera. Se si usa il modello, lasciare inalterati tutti i dati della riga 1, immettendo i dati solo dalla riga 2 in giù.</span><span class="sxs-lookup"><span data-stu-id="b5667-212">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="b5667-p118">Il foglio di calcolo deve includere anche i valori per il nome utente (ad esempio albertino@contoso.com) e per il nome visualizzato (ad esempio Albertino Mazzanti) di ogni utente. Per lasciare vuoti gli altri campi, immettere uno spazio seguito da una virgola nel campo, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="b5667-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Esempio di file CSV per cui sono state specificate righe vuote](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="b5667-p119">In caso di persone che lavorano in paesi diversi, è necessario creare un foglio di calcolo per ogni paese. Creare ad esempio un foglio di calcolo contenente l'elenco di tutti gli utenti che lavorano negli USA e un altro per quelli del Giappone. Il motivo è che la disponibilità dei servizi di Office 365 varia in base all'area geografica.</span><span class="sxs-lookup"><span data-stu-id="b5667-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="b5667-p120">**Suggerimento:** prima di aggiungere un numero elevato di utenti a Office 365, è consigliabile esercitarsi con il foglio di calcolo di esempio. Provare a modificare il foglio di calcolo di esempio con i dati di 5 o 10 utenti e salvarlo con un nuovo nome. Eseguire i passaggi descritti in questa procedura, verificare i risultati, quindi eliminare i nuovi account e ricominciare. In questo modo è possibile esercitarsi a recuperare tutti i dati appropriati per la propria situazione. Vedere inoltre [Suggerimenti per la formattazione del foglio di calcolo](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="b5667-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="b5667-224">Accedere a Office 365 con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="b5667-224">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="b5667-225">Accedere all'interfaccia di amministrazione.</span><span class="sxs-lookup"><span data-stu-id="b5667-225">Go to the admin center.</span></span>
    
4. <span data-ttu-id="b5667-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span><span class="sxs-lookup"><span data-stu-id="b5667-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="b5667-p122">A questo punto, per eseguire la procedura guidata Aggiunta utenti in blocco, scegliere **Utenti** \> **Utenti attivi**. Scegliere ![Icona per l'aggiunta di molti utenti in Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png), come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="b5667-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Immagine della sezione utenti dell'interfaccia di amministrazione](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="b5667-234">Verrà visualizzata la procedura guidata Aggiunta utenti in blocco con le istruzioni per l'aggiunta di gruppi di utenti a Office 365.</span><span class="sxs-lookup"><span data-stu-id="b5667-234">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="b5667-235">Nel passaggio 1 - Selezione di un file CSV, specificare il proprio foglio di calcolo, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="b5667-235">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Passaggio 1 della procedura guidata Aggiunta utenti in blocco - Selezione del file CSV](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="b5667-237">Nel passaggio 2 - Verifica, la procedura guidata indica se il contenuto del foglio di calcolo è formattato correttamente.</span><span class="sxs-lookup"><span data-stu-id="b5667-237">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Passaggio 2 della procedura guidata Aggiunta utenti in blocco - Verifica](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="b5667-p123">Nel passaggio 3 - Impostazioni, scegliere **Consentito** in modo che le persone elencate nel foglio di calcolo possano usare Office 365. Scegliere inoltre il paese in cui queste persone useranno Office 365. Tenere presente che se alcune persone dell'organizzazione useranno Office 365 in un paese diverso, è necessario creare un foglio di calcolo distinto con i loro nomi ed eseguire di nuovo la procedura guidata Aggiunta utenti in blocco per aggiungerli.</span><span class="sxs-lookup"><span data-stu-id="b5667-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Passaggio 3 della procedura guidata Aggiunta utenti in blocco - Impostazioni](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="b5667-243">La pagina Assegnare le licenze indica quante licenze sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="b5667-243">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Passaggio 4 della procedura guidata Aggiunta utenti in blocco - Licenze](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="b5667-245">È possibile scegliere **Acquista altre licenze**, ma si lascerà la procedura guidata Aggiunta utenti in blocco e si passa alla **fatturazione** nell'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="b5667-245">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Microsoft 365 admin center.</span></span> <span data-ttu-id="b5667-246">Dopo aver acquistato altre licenze, è necessario attendere alcuni minuti mentre l'ordine viene elaborato, quindi avviare la procedura guidata Aggiunta utenti in blocco dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="b5667-246">After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="b5667-247">Se non si acquistano altre licenze, gli account non verranno creati per tutti gli utenti elencati del foglio di calcolo.</span><span class="sxs-lookup"><span data-stu-id="b5667-247">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="b5667-248">In questo esempio non vengono acquistate altre licenze e si prosegue con la procedura guidata Aggiunta utenti in blocco.</span><span class="sxs-lookup"><span data-stu-id="b5667-248">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="b5667-249">Nel passaggio 5 - Invio dei risultati, digitare gli indirizzi di posta elettronica delle persone a cui si vuole che venga inviato un messaggio di posta elettronica con l'elenco di  *tutti*  i nomi utente di Office 365 e le password temporanee per le persone incluse nel foglio di calcolo.</span><span class="sxs-lookup"><span data-stu-id="b5667-249">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Passaggio 5 della procedura guidata Aggiunta utenti in blocco - Invio dei risultati](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="b5667-p125">Il messaggio seguente viene inviato a tutti gli indirizzi di posta elettronica specificati nel passaggio 5 - Invio dei risultati. Questo messaggio indica quali account sono stati creati. Si noti che per alcune persone non sono stati creati account perché il numero di licenze non è sufficiente.</span><span class="sxs-lookup"><span data-stu-id="b5667-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Esempio di messaggio di posta elettronica con informazioni sulle credenziali utente](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="b5667-p126">È possibile acquistare altre licenze in seguito e rieseguire la procedura guidata Aggiunta utenti in blocco con lo stesso foglio di calcolo. La procedura guidata ignora gli utenti che hanno già un account. Nel report dei risultati verrà visualizzato il messaggio "nome utente duplicato", a indicare che qualcuno ha già un account con queste informazioni.</span><span class="sxs-lookup"><span data-stu-id="b5667-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="b5667-257">La pagina finale della procedura guidata Aggiunta utenti in blocco elenca i nomi utente e le password temporanee, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="b5667-257">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Passaggio 6 della procedura guidata Aggiunta utenti in blocco - Invio dei risultati](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="b5667-p127">Dopo aver aggiunto utenti a Office 365, è necessario informarli sul loro account di Office 365. Usare il consueto processo per la comunicazione di nuove password.</span><span class="sxs-lookup"><span data-stu-id="b5667-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

