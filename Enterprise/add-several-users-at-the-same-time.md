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
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="8fc02-105">Aggiungere più utenti contemporaneamente a Office 365 - Guida per amministratore</span><span class="sxs-lookup"><span data-stu-id="8fc02-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="8fc02-p102">Ogni membro del gruppo è necessario un account utente prima di poter effettuare l'accesso e accedere a servizi di Office 365, come messaggio di posta elettronica e l'ufficio. Se si dispone di una quantità elevata di utenti, è possibile aggiungere gli account contemporaneamente da un foglio di calcolo Excel o altri file salvato in formato CSV. [Dubbi è il formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="8fc02-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a><span data-ttu-id="8fc02-109">Aggiungere più utenti a Office 365 nell'interfaccia di amministrazione di Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc02-109">Add multiple users to Office 365 in the Office 365 admin center</span></span>

1. <span data-ttu-id="8fc02-110">Accedere a Office 365 con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="8fc02-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="8fc02-111">Nell'interfaccia di amministrazione di Office 365, scegli **utenti** \> **utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="8fc02-111">In the Office 365 admin center, choose **Users** \> **Active users**.</span></span>
    
    ![Nell'interfaccia di amministrazione scegliere utenti e quindi attiva](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. <span data-ttu-id="8fc02-113">**Ulteriori** elenco a discesa, scegliere **Importa più utenti**.</span><span class="sxs-lookup"><span data-stu-id="8fc02-113">In the **More** drop-down, choose **Import multiple users**.</span></span>
    
4. <span data-ttu-id="8fc02-114">Nel Pannello di **importare più utenti** , è possibile scaricare facoltativamente un file CSV di esempio con o senza dati di esempio compilati.</span><span class="sxs-lookup"><span data-stu-id="8fc02-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![In altre elenco a discesa, selezionare Importa più utenti](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="8fc02-116">È necessario includere le **intestazioni di colonna stesso esatto** come nell'esempio 1 del foglio di calcolo (nome utente, nome e così via...). Se si utilizza il modello, viene aperto in uno strumento di modifica di testo, ad esempio Blocco note e prendere in considerazione lasciando solo tutti i dati nella riga 1 e solo immettono dati in righe comprese tra 2 e sotto.</span><span class="sxs-lookup"><span data-stu-id="8fc02-116">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="8fc02-117">Foglio di calcolo deve inoltre includere i valori per il nome utente (ad esempio bob@contoso.com) e un nome visualizzato (ad esempio Bob Kelly) per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="8fc02-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="8fc02-118">Immettere un percorso di file nella casella oppure scegliere **Sfoglia** per individuare il percorso del file CSV e quindi scegliere **Verify**.</span><span class="sxs-lookup"><span data-stu-id="8fc02-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![È stato verificato il file CSV](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="8fc02-p103">Se si verificano problemi con il file, il problema viene visualizzato nel riquadro. È inoltre possibile scaricare un file di registro.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
6. <span data-ttu-id="8fc02-122">Nella finestra di dialogo **impostare le opzioni utente** è possibile impostare lo stato di accesso e scegliere la licenza del prodotto che verrà assegnata a tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="8fc02-122">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
7. <span data-ttu-id="8fc02-123">Nella finestra di dialogo **Visualizza i risultati** è possibile scegliere di inviare i risultati a se stessi o con altri utenti (le password saranno in formato testo normale) ed è possibile visualizzare il numero di utenti sono stato creato, e se è necessario acquistare altre licenze da assegnare ad alcuni dei nuovi utenti.</span><span class="sxs-lookup"><span data-stu-id="8fc02-123">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="8fc02-124">Guardare il video</span><span class="sxs-lookup"><span data-stu-id="8fc02-124">Watch the video</span></span>
<span data-ttu-id="8fc02-125"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="8fc02-125"></span></span>

 <span data-ttu-id="8fc02-126">Guardare un breve video che illustra come blocco aggiungere gli utenti.</span><span class="sxs-lookup"><span data-stu-id="8fc02-126">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="8fc02-127">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="8fc02-127">Next steps</span></span>
<span data-ttu-id="8fc02-128"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="8fc02-128"></span></span>

- <span data-ttu-id="8fc02-p104">Ora che tali utenti dispongono di account, è necessario [scaricare e installare o reinstalla Office 365 o 2016 di Office in un PC o Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Ogni membro del gruppo è possibile installare Office 365 in fino a 5 PC o Mac.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p104">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="8fc02-p105">Ogni persona è possibile [Set up Office apps e posta elettronica di un dispositivo mobile](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) in 5 telefoni, ad esempio iPhone, iPad e telefoni Android e Tablet e Tablet fino a 5. In questo modo che è possibile modificare i file di Office da qualsiasi posizione.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p105">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets. This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="8fc02-133">Per un elenco di end-to-end dei passaggi dell'installazione, vedere [configurare Office 365 per aziende](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) .</span><span class="sxs-lookup"><span data-stu-id="8fc02-133">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="8fc02-134">Ulteriori informazioni su come aggiungere utenti a Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc02-134">More information about how to add users to Office 365</span></span>
<span data-ttu-id="8fc02-135"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="8fc02-135"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="8fc02-136">Indicazioni è il formato CSV?</span><span class="sxs-lookup"><span data-stu-id="8fc02-136">Not sure what CSV format is?</span></span>
<span data-ttu-id="8fc02-137"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="8fc02-137"></span></span>

<span data-ttu-id="8fc02-p106">Un file CSV è un file con valori separati da virgola. È possibile creare o modificare un file simile al seguente con qualsiasi editor di testo o un foglio di calcolo, ad esempio Excel.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="8fc02-p107">È possibile scaricare [il foglio di calcolo di esempio](https://www.microsoft.com/en-us/download/details.aspx?id=45485) come punto di partenza. Ricordare che Office 365 richiede le intestazioni di colonna della prima riga in modo non sostituiscano con un parametro.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="8fc02-142">Salvare il file con un nuovo nome e specificare il formato CSV.</span><span class="sxs-lookup"><span data-stu-id="8fc02-142">Save the file with a new name, and specify CSV format.</span></span>
  
![Un'immagine come salvare un file di Excel in formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="8fc02-p108">Quando si salva il file, si otterranno probabilmente un prompt che alcune caratteristiche nel foglio di lavoro andranno persi se si salva il file nel formato CSV. Questo è possibile. Fare clic su **Sì** per continuare.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Un'immagine del prompt dei comandi è possibile ottenere da Excel in cui viene chiesto se si desidera realmente salvare il file come formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="8fc02-148">Suggerimenti per la formattazione del foglio di calcolo</span><span class="sxs-lookup"><span data-stu-id="8fc02-148">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="8fc02-149"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="8fc02-149"></span></span>

- <span data-ttu-id="8fc02-p109">**è necessario le intestazioni di colonna stesso come per la cartella di lavoro di esempio?** Sì. La cartella di lavoro di esempio contiene le intestazioni di colonna della prima riga. Queste voci sono necessari. Per ogni utente che si desidera aggiungere a Office 365, creare una riga sotto l'intestazione. Se si aggiungere, modificare o eliminare una qualsiasi delle intestazioni di colonna, Office 365 potrebbe non essere in grado di creare utenti dalle informazioni del file.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="8fc02-p110">**Se non è tutte le informazioni necessarie per ogni utente?** Il nome utente e il nome visualizzato sono necessari e non è possibile aggiungere un nuovo utente senza queste informazioni. Se non si dispone di alcune delle altre informazioni, ad esempio fax, è possibile utilizzare una virgola e un spazio per indicare che il campo deve rimanere vuoto.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="8fc02-p111">* * Come piccole o grandi dimensioni può essere un foglio di calcolo? * * Il foglio di calcolo deve disporre di almeno due righe. Uno è per le intestazioni di colonna (l'etichetta di colonna dati di utente) e una per l'utente. È possibile avere più di 251 righe. Se si desidera importare più di 250 utenti, è possibile creare più di un foglio di calcolo.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p111">** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="8fc02-p112">* * Le lingue che è possibile utilizzare? * * Quando si crea il foglio di calcolo, è possibile immettere le etichette di colonna di dati utente in qualsiasi lingua o caratteri, ma non è necessario modificare l'ordine delle etichette, come illustrato nell'esempio di. È possibile rendere le voci nei campi, utilizzando qualsiasi linguaggio o caratteri e salvataggio dei file in formato Unicode o UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p112">** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="8fc02-p113">**Se si sono aggiungendo gli utenti da diversi paesi o aree?** Creare una cartella di lavoro separato per ogni area. Sarà necessario scorrere il blocco de l'Assistant ajouter quali ogni foglio di calcolo, offrendo un'unica posizione di tutti gli utenti inclusi nel file di cui si sta lavorando.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="8fc02-p114">**è previsto un limite al numero di caratteri posso utilizzare?** Nella tabella seguente mostra le etichette di colonna di dati utente e la lunghezza massima per ogni nel foglio di calcolo di esempio.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="8fc02-172">**Etichetta di colonna di dati utente**</span><span class="sxs-lookup"><span data-stu-id="8fc02-172">**User data column label**</span></span>|<span data-ttu-id="8fc02-173">**Numero massimo di caratteri**</span><span class="sxs-lookup"><span data-stu-id="8fc02-173">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8fc02-174">Nome utente (obbligatorio)</span><span class="sxs-lookup"><span data-stu-id="8fc02-174">User Name (Required)</span></span>  <br/> |<span data-ttu-id="8fc02-p115">tra cui 79 il simbolo chiocciola (@), in name@domain formato. \<estensione\>. Alias dell'utente non può superare i 30 caratteri e il nome di dominio non può superare 48 caratteri.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="8fc02-177">Nome</span><span class="sxs-lookup"><span data-stu-id="8fc02-177">First Name</span></span>  <br/> |<span data-ttu-id="8fc02-178">64</span><span class="sxs-lookup"><span data-stu-id="8fc02-178">64</span></span>  <br/> |
|<span data-ttu-id="8fc02-179">Cognome</span><span class="sxs-lookup"><span data-stu-id="8fc02-179">Last Name</span></span>  <br/> |<span data-ttu-id="8fc02-180">64</span><span class="sxs-lookup"><span data-stu-id="8fc02-180">64</span></span>  <br/> |
|<span data-ttu-id="8fc02-181">Nome visualizzato (obbligatorio)</span><span class="sxs-lookup"><span data-stu-id="8fc02-181">Display Name (required)</span></span>  <br/> |<span data-ttu-id="8fc02-182">256</span><span class="sxs-lookup"><span data-stu-id="8fc02-182">256</span></span>  <br/> |
|<span data-ttu-id="8fc02-183">Professione</span><span class="sxs-lookup"><span data-stu-id="8fc02-183">Job Title</span></span>  <br/> |<span data-ttu-id="8fc02-184">64</span><span class="sxs-lookup"><span data-stu-id="8fc02-184">64</span></span>  <br/> |
|<span data-ttu-id="8fc02-185">Reparto</span><span class="sxs-lookup"><span data-stu-id="8fc02-185">Department</span></span>  <br/> |<span data-ttu-id="8fc02-186">64</span><span class="sxs-lookup"><span data-stu-id="8fc02-186">64</span></span>  <br/> |
|<span data-ttu-id="8fc02-187">Numero dell'ufficio</span><span class="sxs-lookup"><span data-stu-id="8fc02-187">Office Number</span></span>  <br/> |<span data-ttu-id="8fc02-188">128</span><span class="sxs-lookup"><span data-stu-id="8fc02-188">128</span></span>  <br/> |
|<span data-ttu-id="8fc02-189">Telefono ufficio</span><span class="sxs-lookup"><span data-stu-id="8fc02-189">Office Phone</span></span>  <br/> |<span data-ttu-id="8fc02-190">64</span><span class="sxs-lookup"><span data-stu-id="8fc02-190">64</span></span>  <br/> |
|<span data-ttu-id="8fc02-191">Cellulare</span><span class="sxs-lookup"><span data-stu-id="8fc02-191">Mobile Phone</span></span>  <br/> |<span data-ttu-id="8fc02-192">64</span><span class="sxs-lookup"><span data-stu-id="8fc02-192">64</span></span>  <br/> |
|<span data-ttu-id="8fc02-193">Fax</span><span class="sxs-lookup"><span data-stu-id="8fc02-193">Fax</span></span>  <br/> |<span data-ttu-id="8fc02-194">64</span><span class="sxs-lookup"><span data-stu-id="8fc02-194">64</span></span>  <br/> |
|<span data-ttu-id="8fc02-195">Indirizzo</span><span class="sxs-lookup"><span data-stu-id="8fc02-195">Address</span></span>  <br/> |<span data-ttu-id="8fc02-196">1023</span><span class="sxs-lookup"><span data-stu-id="8fc02-196">1023</span></span>  <br/> |
|<span data-ttu-id="8fc02-197">Città</span><span class="sxs-lookup"><span data-stu-id="8fc02-197">City</span></span>  <br/> |<span data-ttu-id="8fc02-198">128</span><span class="sxs-lookup"><span data-stu-id="8fc02-198">128</span></span>  <br/> |
|<span data-ttu-id="8fc02-199">Stato o provincia</span><span class="sxs-lookup"><span data-stu-id="8fc02-199">State or Province</span></span>  <br/> |<span data-ttu-id="8fc02-200">128</span><span class="sxs-lookup"><span data-stu-id="8fc02-200">128</span></span>  <br/> |
|<span data-ttu-id="8fc02-201">CAP</span><span class="sxs-lookup"><span data-stu-id="8fc02-201">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="8fc02-202">40</span><span class="sxs-lookup"><span data-stu-id="8fc02-202">40</span></span>  <br/> |
|<span data-ttu-id="8fc02-203">Paese</span><span class="sxs-lookup"><span data-stu-id="8fc02-203">Country or Region</span></span>  <br/> |<span data-ttu-id="8fc02-204">128</span><span class="sxs-lookup"><span data-stu-id="8fc02-204">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="8fc02-205">Ancora problemi durante l'aggiunta di utenti a Office 365?</span><span class="sxs-lookup"><span data-stu-id="8fc02-205">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="8fc02-p116">**Fare doppio clic sul foglio di calcolo formattato in modo corretto.** Controllare le intestazioni di colonna per assicurarsi che devono essere uguali le intestazioni nel file di esempio. Verificare che si sta seguendo le regole per numero di caratteri e che ogni campo è separata da una virgola.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="8fc02-p117">* * Se non viene visualizzata i nuovi utenti in Office 365 subito, attendere alcuni minuti. * * Può richiedere un po' mentre per le modifiche al passaggio tra tutti i servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p117">** If you don't see the new users in Office 365 right away, wait a few minutes. ** It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a><span data-ttu-id="8fc02-211">Aggiungere più utenti a Office 365 nell'interfaccia di amministrazione di Office 365 precedente</span><span class="sxs-lookup"><span data-stu-id="8fc02-211">Add multiple users to Office 365 in the old Office 365 admin center</span></span>

1. <span data-ttu-id="8fc02-212">Scaricare [il foglio di calcolo di esempio](https://www.microsoft.com/en-us/download/details.aspx?id=45485) e viene aperta in Excel.</span><span class="sxs-lookup"><span data-stu-id="8fc02-212">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="8fc02-213">È necessario includere le **intestazioni di colonna stesso esatto** come nell'esempio 1 del foglio di calcolo (nome utente, nome e così via...). Se si utilizza il modello, prendere in considerazione lasciando solo tutti i dati nella riga 1 e solo immettono dati in righe comprese tra 2 e sotto.</span><span class="sxs-lookup"><span data-stu-id="8fc02-213">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="8fc02-p118">Foglio di calcolo deve inoltre includere i valori per il nome utente (ad esempio bob@contoso.com) e un nome visualizzato (ad esempio Bob Kelly) per ogni utente. Per lasciare vuoti altri campi, immettere una virgola e un spazio nel campo come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Un file CVS di esempio con righe vuote specificate](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="8fc02-p119">Se si dispone di utenti che utilizzano diversi paesi, sarà necessario creare una cartella di lavoro per gli utenti in ogni paese. Ad esempio, un foglio di calcolo in cui sono elencati tutti gli utenti che può essere utilizzato negli Stati Uniti e un altro che elenca tutti gli utenti che può essere utilizzato in Giappone. Ciò avviene perché la disponibilità dei servizi di Office 365 varia in base al paese.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="8fc02-p120">**Suggerimento:** Prima di aggiungere molti utenti a Office 365, è possibile consigliata con la cartella di lavoro di esempio. Ad esempio, modificare il foglio di calcolo di esempio con i dati per alcuni degli utenti, ad esempio 5 o 10 e salvare il file con un nuovo nome. Eseguire passaggi descritti in questa procedura, verificare i risultati, quindi eliminare i nuovi account e ricominciare nuovamente. In questo modo è possibile practice ottenere tutto il diritto di dati per la situazione. Vedere anche [suggerimenti per la formattazione del foglio di calcolo](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="8fc02-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="8fc02-225">Accedere a Office 365 con l'account di lavoro o della scuola.</span><span class="sxs-lookup"><span data-stu-id="8fc02-225">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="8fc02-226">Passare all'interfaccia di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc02-226">Go to the Office 365 admin center.</span></span>
    
4. <span data-ttu-id="8fc02-p121">Per gli utenti di utilizzare servizi di Office 365, è necessario assegnare una licenza. Prima di continuare, è possibile verificare di disporre di licenze sufficiente per tutti i contatti presenti nel foglio di calcolo. Scegliere **fatturazione** \> **sottoscrizioni** per vedere se sono sufficienti. Se è necessario acquistare altre licenze, scegliere * * modificare quantità licenza * *. In alternativa, è possibile eseguire la procedura guidata e assegnare licenze sono, quindi acquistare altre licenze più avanti e rieseguire la procedura guidata.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose ** Change license quantity **. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="8fc02-p122">Ora accedere per la maggior parte degli utenti installazione guidata: selezione **utenti** \> **Utenti attivi**. Scegliere ![l'icona per l'aggiunta di numero di utenti a Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Un'immagine della sezione agli utenti di interfaccia di amministrazione di Office 365](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="8fc02-235">La maggior parte aggiungere utenti guidata viene visualizzato e i passaggi per l'aggiunta di un gruppo di utenti a Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc02-235">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="8fc02-236">Nel passaggio 1: selezionare un file CSV, specificare il proprio foglio di calcolo, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="8fc02-236">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Passaggio 1 del blocco Aggiunta guidata utenti - File CSV Select](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="8fc02-238">Nel passaggio 2: verifica, la procedura guidata indica se il contenuto del foglio di calcolo sia formattato correttamente.</span><span class="sxs-lookup"><span data-stu-id="8fc02-238">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Passaggio 2 del blocco Aggiunta guidata utenti - verifica](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="8fc02-p123">Nel passaggio 3 - impostazioni, scegliere **consentiti** in modo che gli utenti elencati nel foglio di calcolo saranno in grado di utilizzare Office 365. Scegliere il paese in cui questi utenti utilizzeranno Office 365. Tenere presente se alcuni utenti all'interno dell'organizzazione intende utilizzare Office 365 in un paese diverso, creare una cartella di lavoro separato con i relativi nomi ed Esegui il blocco Aggiunta guidata utenti per aggiungere quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Passaggio 3 del blocco Aggiunta guidata utenti - impostazioni](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="8fc02-244">Pagina Assegnazione licenze indica quante licenze sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="8fc02-244">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Passaggio 4 della procedura guidata Aggiungi utenti in blocco - licenze](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="8fc02-p124">È possibile scegliere di **acquistare altre licenze**, ma lasciare il blocco de l'Assistant ajouter e passare alla **fatturazione** nell'interfaccia di amministrazione di Office 365. Dopo aver acquistare altre licenze, è necessario attendere alcuni minuti per l'ordine di elaborazione e quindi avvia il blocco aggiungere guidata utenti dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p124">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Office 365 admin center. After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="8fc02-248">Se si non acquistano altre licenze, non sarà possibile creare account per tutti i contatti presenti nel foglio di calcolo.</span><span class="sxs-lookup"><span data-stu-id="8fc02-248">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="8fc02-249">In questo esempio è non acquista eventuali altre licenze e continuare con la maggior parte aggiunta guidata utenti.</span><span class="sxs-lookup"><span data-stu-id="8fc02-249">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="8fc02-250">Nel passaggio 5 - invia i risultati, digitare gli indirizzi di posta elettronica delle persone che si desiderano ricevere un messaggio di posta elettronica in cui sono elencati *tutti* i nomi utente di Office 365 e password temporanee per gli utenti nel foglio di calcolo.</span><span class="sxs-lookup"><span data-stu-id="8fc02-250">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Passaggio 5 del blocco Aggiunta guidata utenti - Invia risultati](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="8fc02-p125">Il seguente messaggio di posta elettronica viene inviato a tutti gli indirizzi di posta elettronica specificato nel passaggio 5 - Invia risultati. Questo messaggio indica quali account sono stati creati. Si noti che non sono stati creati gli account per alcune persone poiché non sono disponibili licenze sufficienti.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Un messaggio di posta elettronica di esempio con informazioni sulle credenziali utente](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="8fc02-p126">È possibile acquistare ulteriori licenze successivamente e Riesegui aggiungere il blocco guidata utenti con stesso foglio di calcolo. La procedura guidata ignora gli utenti che dispongono di account; nel report dei risultati visualizzato il "nome utente duplicati" per indicare un utente con tali informazioni già disponga di un account.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="8fc02-258">Pagina finale nel blocco Aggiunta guidata utenti sono elencati i nomi utente e password temporanee, come illustrato nella figura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="8fc02-258">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Passaggio 6 del blocco Aggiunta guidata utenti - Invia risultati](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="8fc02-p127">Dopo aver aggiunto gli utenti a Office 365, è necessario per informarli sulle informazioni sull'account Office 365. Utilizzare il normale processo per la comunicazione nuove password.</span><span class="sxs-lookup"><span data-stu-id="8fc02-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

