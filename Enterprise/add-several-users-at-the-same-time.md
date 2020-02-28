---
title: Aggiungere più utenti a Office 365 contemporaneamente - Guida dell'amministratore
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
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
ms.openlocfilehash: 0d0416662bf4934d3373f1ab7ac23c8055ad3098
ms.sourcegitcommit: 6ad59ab24a5dc8d27f448ca7fe4f6bdf7ab28066
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2020
ms.locfileid: "42316015"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="027e3-105">Aggiungere più utenti a Office 365 contemporaneamente - Guida per l'amministratore</span><span class="sxs-lookup"><span data-stu-id="027e3-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="027e3-p102">Per poter accedere a Office 365 e ai relativi servizi, ad esempio posta elettronica e Office, è necessario che ogni persona del team abbia un account utente. Se il team è composto da numerose persone, è possibile aggiungere tutti gli account contemporaneamente da un foglio di calcolo di Excel o da un altro file salvato in formato CSV. [Che cos'è il formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="027e3-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
> [!NOTE] 
> <span data-ttu-id="027e3-109">Se non si usa la nuova interfaccia di amministrazione di Microsoft 365, è possibile attivarla selezionando l'opzione **Prova la nuova interfaccia di amministrazione** che si trova nella parte superiore della home page.</span><span class="sxs-lookup"><span data-stu-id="027e3-109">If you're not using the new Microsoft 365 admin center, you can turn it on by selecting the **Try the new admin center** toggle located at the top of the Home page.</span></span>

## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="027e3-110">Aggiungere più utenti a Office 365 nell'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="027e3-110">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="027e3-111">Accedere a Office 365 con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="027e3-111">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="027e3-112">Nell'interfaccia di **amministrazione scegliere** \> utenti **attivi**.</span><span class="sxs-lookup"><span data-stu-id="027e3-112">In the admin center, choose **Users** \> **Active users**.</span></span>

3. <span data-ttu-id="027e3-113">Selezionare **Aggiungi più utenti**.</span><span class="sxs-lookup"><span data-stu-id="027e3-113">Select **Add multiple users**.</span></span>

4. <span data-ttu-id="027e3-114">Nel riquadro **Importa più utenti** è possibile scegliere di scaricare un file CSV di esempio con o senza dati di esempio inseriti.</span><span class="sxs-lookup"><span data-stu-id="027e3-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    <span data-ttu-id="027e3-115">Il foglio di calcolo deve includere le **stesse intestazioni di colonna** dell'esempio per il nome utente, il nome, eccetera. Se si usa il modello, aprirlo in un editor di testo, come il Blocco appunti, e lasciare inalterati tutti i dati della riga 1, immettendo i dati solo dalla riga 2 in giù.</span><span class="sxs-lookup"><span data-stu-id="027e3-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="027e3-116">Il foglio di calcolo deve includere anche i valori per il nome utente (ad esempio albertino@contoso.com) e per il nome visualizzato (ad esempio Albertino Mazzanti) di ogni utente.</span><span class="sxs-lookup"><span data-stu-id="027e3-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="027e3-117">Immettere un percorso di file nella casella oppure scegliere **Sfoglia** per passare al percorso del file CSV e quindi scegliere **Verifica**.</span><span class="sxs-lookup"><span data-stu-id="027e3-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
  
    <span data-ttu-id="027e3-p103">Se ci sono problemi con il file, i relativi messaggi vengono visualizzati nel riquadro. È anche possibile scaricare un file di log.</span><span class="sxs-lookup"><span data-stu-id="027e3-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="027e3-120">Nella finestra di dialogo **Imposta opzioni utente** è possibile impostare lo stato di accesso e scegliere la licenza del prodotto che verrà assegnata a tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="027e3-120">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="027e3-121">Nella finestra di dialogo **Visualizza i risultati** è possibile scegliere di inviare i risultati a se stessi o ad altri utenti (le password saranno in testo normale) ed è possibile vedere quanti utenti sono stati creati e se è necessario acquistare altre licenze da assegnare ad alcuni nuovi utenti.</span><span class="sxs-lookup"><span data-stu-id="027e3-121">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="027e3-122">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="027e3-122">Next steps</span></span>
<span data-ttu-id="027e3-123"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="027e3-123"><a name="bk_preview"> </a></span></span>

- <span data-ttu-id="027e3-124">Ora che queste persone hanno account, devono [scaricare e installare o reinstallare office 365 o office 2016 su un PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="027e3-124">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="027e3-125">Ogni persona del team può installare Office 365 in un totale di 5 PC o Mac.</span><span class="sxs-lookup"><span data-stu-id="027e3-125">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="027e3-126">Ogni persona può anche [configurare le app di Office e la posta elettronica su un dispositivo mobile su un](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) massimo di 5 tablet e 5 telefoni, ad esempio iPhone, iPad, telefoni e Tablet Android.</span><span class="sxs-lookup"><span data-stu-id="027e3-126">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="027e3-127">In questo modo, potrà modificare i file di Office ovunque vada.</span><span class="sxs-lookup"><span data-stu-id="027e3-127">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="027e3-128">Per un elenco end-to-end dei passaggi di configurazione, vedere [configurare Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) .</span><span class="sxs-lookup"><span data-stu-id="027e3-128">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="027e3-129">Altre informazioni su come aggiungere utenti a Office 365</span><span class="sxs-lookup"><span data-stu-id="027e3-129">More information about how to add users to Office 365</span></span>
<span data-ttu-id="027e3-130"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="027e3-130"><a name="bk_preview"> </a></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="027e3-131">Che cos'è il formato CSV?</span><span class="sxs-lookup"><span data-stu-id="027e3-131">Not sure what CSV format is?</span></span>
<span data-ttu-id="027e3-132"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="027e3-132"><a name="__toc316652088"> </a></span></span>

<span data-ttu-id="027e3-p106">Un file CSV è un file con valori delimitati da virgole. È possibile creare o modificare un file di questo tipo con qualsiasi editor di testo o foglio di calcolo, ad esempio Excel.</span><span class="sxs-lookup"><span data-stu-id="027e3-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="027e3-p107">Come punto di partenza, è possibile scaricare questo [foglio di calcolo](https://www.microsoft.com/download/details.aspx?id=45485). Tenere presente che Office 365 richiede intestazioni di colonna nella prima riga, quindi non sostituirle con altro contenuto.</span><span class="sxs-lookup"><span data-stu-id="027e3-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="027e3-137">Salvare il file con un nuovo nome e specificare il formato CSV.</span><span class="sxs-lookup"><span data-stu-id="027e3-137">Save the file with a new name, and specify CSV format.</span></span>
  
![Immagine di come salvare un file in formato CSV in Excel](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="027e3-p108">Quando si salva il file, è probabile che venga visualizzato un messaggio indicante che alcune caratteristiche della cartella di lavoro andranno perse in formato CSV. Non si tratta di un errore. Fare clic su **Sì** per continuare.</span><span class="sxs-lookup"><span data-stu-id="027e3-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Immagine del messaggio che potrebbe essere visualizzato in Excel in cui si chiede conferma per salvare il file in formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="027e3-143">Suggerimenti per la formattazione del foglio di calcolo</span><span class="sxs-lookup"><span data-stu-id="027e3-143">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="027e3-144"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="027e3-144"><a name="__toc314595848"> </a></span></span>

- <span data-ttu-id="027e3-p109">**È necessario mantenere le stesse intestazioni di colonna del foglio di calcolo di esempio?** Sì. Il foglio di calcolo di esempio contiene intestazioni di colonna nella prima riga. Queste intestazioni sono obbligatorie. Sotto l'intestazione creare una riga per ogni utente da aggiungere in Office 365. Se si aggiungono intestazioni di colonna oppure si modificano o si eliminano quelle esistenti, Office 365 potrebbe non riuscire a creare gli utenti dalle informazioni del file.</span><span class="sxs-lookup"><span data-stu-id="027e3-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="027e3-p110">**Che cosa succede se non si hanno tutte le informazioni necessarie per ogni utente?** I campi obbligatori sono Nome utente e Nome visualizzato, pertanto non è possibile aggiungere un nuovo utente in assenza di tali informazioni. Se non si dispone di altre informazioni, ad esempio il fax, è possibile usare uno spazio seguito da una virgola per indicare che il campo deve rimanere vuoto.</span><span class="sxs-lookup"><span data-stu-id="027e3-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="027e3-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="027e3-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="027e3-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="027e3-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="027e3-p113">**Che cosa succede se si aggiungono utenti di paesi o aree geografiche diverse?** Creare un foglio di calcolo distinto per ogni area. È necessario eseguire i passaggi della procedura guidata Aggiunta utenti in blocco per ogni foglio di calcolo, specificando una singola area geografica per tutti gli utenti inclusi nel file in uso.</span><span class="sxs-lookup"><span data-stu-id="027e3-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="027e3-p114">**È previsto un limite per il numero di caratteri che è possibile usare?** La tabella seguente indica le etichette delle colonne dei dati utente e il numero massimo di caratteri che è possibile usare per ognuna nel foglio di calcolo di esempio.</span><span class="sxs-lookup"><span data-stu-id="027e3-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="027e3-167">**Etichetta colonna dati utente**</span><span class="sxs-lookup"><span data-stu-id="027e3-167">**User data column label**</span></span>|<span data-ttu-id="027e3-168">**Numero massimo di caratteri**</span><span class="sxs-lookup"><span data-stu-id="027e3-168">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="027e3-169">Nome utente (obbligatorio)</span><span class="sxs-lookup"><span data-stu-id="027e3-169">User Name (Required)</span></span>  <br/> |<span data-ttu-id="027e3-170">79, incluso il simbolo (@), nel formato nome@dominio.\<estensione\>.</span><span class="sxs-lookup"><span data-stu-id="027e3-170">79 including the at sign (@), in the format name@domain.\<extension\>.</span></span> <span data-ttu-id="027e3-171">L'alias dell'utente non può superare i 50 caratteri e il nome di dominio non può superare i 48 caratteri.</span><span class="sxs-lookup"><span data-stu-id="027e3-171">The user's alias cannot exceed 50 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="027e3-172">Nome</span><span class="sxs-lookup"><span data-stu-id="027e3-172">First Name</span></span>  <br/> |<span data-ttu-id="027e3-173">64</span><span class="sxs-lookup"><span data-stu-id="027e3-173">64</span></span>  <br/> |
|<span data-ttu-id="027e3-174">Cognome</span><span class="sxs-lookup"><span data-stu-id="027e3-174">Last Name</span></span>  <br/> |<span data-ttu-id="027e3-175">64</span><span class="sxs-lookup"><span data-stu-id="027e3-175">64</span></span>  <br/> |
|<span data-ttu-id="027e3-176">Nome visualizzato (obbligatorio)</span><span class="sxs-lookup"><span data-stu-id="027e3-176">Display Name (required)</span></span>  <br/> |<span data-ttu-id="027e3-177">256</span><span class="sxs-lookup"><span data-stu-id="027e3-177">256</span></span>  <br/> |
|<span data-ttu-id="027e3-178">Posizione</span><span class="sxs-lookup"><span data-stu-id="027e3-178">Job Title</span></span>  <br/> |<span data-ttu-id="027e3-179">64</span><span class="sxs-lookup"><span data-stu-id="027e3-179">64</span></span>  <br/> |
|<span data-ttu-id="027e3-180">Reparto</span><span class="sxs-lookup"><span data-stu-id="027e3-180">Department</span></span>  <br/> |<span data-ttu-id="027e3-181">64</span><span class="sxs-lookup"><span data-stu-id="027e3-181">64</span></span>  <br/> |
|<span data-ttu-id="027e3-182">Numero ufficio</span><span class="sxs-lookup"><span data-stu-id="027e3-182">Office Number</span></span>  <br/> |<span data-ttu-id="027e3-183">128</span><span class="sxs-lookup"><span data-stu-id="027e3-183">128</span></span>  <br/> |
|<span data-ttu-id="027e3-184">Telefono ufficio</span><span class="sxs-lookup"><span data-stu-id="027e3-184">Office Phone</span></span>  <br/> |<span data-ttu-id="027e3-185">64</span><span class="sxs-lookup"><span data-stu-id="027e3-185">64</span></span>  <br/> |
|<span data-ttu-id="027e3-186">Telefono cellulare</span><span class="sxs-lookup"><span data-stu-id="027e3-186">Mobile Phone</span></span>  <br/> |<span data-ttu-id="027e3-187">64</span><span class="sxs-lookup"><span data-stu-id="027e3-187">64</span></span>  <br/> |
|<span data-ttu-id="027e3-188">Fax</span><span class="sxs-lookup"><span data-stu-id="027e3-188">Fax</span></span>  <br/> |<span data-ttu-id="027e3-189">64</span><span class="sxs-lookup"><span data-stu-id="027e3-189">64</span></span>  <br/> |
|<span data-ttu-id="027e3-190">Indirizzo</span><span class="sxs-lookup"><span data-stu-id="027e3-190">Address</span></span>  <br/> |<span data-ttu-id="027e3-191">1023</span><span class="sxs-lookup"><span data-stu-id="027e3-191">1023</span></span>  <br/> |
|<span data-ttu-id="027e3-192">Città</span><span class="sxs-lookup"><span data-stu-id="027e3-192">City</span></span>  <br/> |<span data-ttu-id="027e3-193">128</span><span class="sxs-lookup"><span data-stu-id="027e3-193">128</span></span>  <br/> |
|<span data-ttu-id="027e3-194">Provincia</span><span class="sxs-lookup"><span data-stu-id="027e3-194">State or Province</span></span>  <br/> |<span data-ttu-id="027e3-195">128</span><span class="sxs-lookup"><span data-stu-id="027e3-195">128</span></span>  <br/> |
|<span data-ttu-id="027e3-196">CAP</span><span class="sxs-lookup"><span data-stu-id="027e3-196">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="027e3-197">40</span><span class="sxs-lookup"><span data-stu-id="027e3-197">40</span></span>  <br/> |
|<span data-ttu-id="027e3-198">Paese o area geografica</span><span class="sxs-lookup"><span data-stu-id="027e3-198">Country or Region</span></span>  <br/> |<span data-ttu-id="027e3-199">128</span><span class="sxs-lookup"><span data-stu-id="027e3-199">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="027e3-200">Si verificano ancora problemi durante l'aggiunta di utenti a Office 365?</span><span class="sxs-lookup"><span data-stu-id="027e3-200">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="027e3-p116">**Verificare che il foglio di calcolo sia stato formattato correttamente.** Controllare le intestazioni di colonna per verificare che corrispondano a quelle del file di esempio. Assicurarsi di aver rispettato le regole relative al numero massimo di caratteri e di aver usato una virgola per separare i campi.</span><span class="sxs-lookup"><span data-stu-id="027e3-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="027e3-204">**Se i nuovi utenti di Office 365 non sono visibili subito, attendere qualche minuto.**</span><span class="sxs-lookup"><span data-stu-id="027e3-204">**If you don't see the new users in Office 365 right away, wait a few minutes.**</span></span> <span data-ttu-id="027e3-205">La modifica di tutti i servizi di Office 365 può richiedere un po' di tempo.</span><span class="sxs-lookup"><span data-stu-id="027e3-205">It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="related-articles"></a><span data-ttu-id="027e3-206">Articoli correlati</span><span class="sxs-lookup"><span data-stu-id="027e3-206">Related articles</span></span>

[<span data-ttu-id="027e3-207">Aggiungere gli utenti singolarmente o in blocco a Office 365</span><span class="sxs-lookup"><span data-stu-id="027e3-207">Add users individually or in bulk to Office 365</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)




