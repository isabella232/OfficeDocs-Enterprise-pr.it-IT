---
title: Funzionalità multi-Geo in Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Espandere la presenza di Office 365 a più aree geografiche con funzionalità multi-geo in Exchange Online.
ms.openlocfilehash: 5f34a2da47b9767aa9dfe22c6be7237951128960
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849922"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="9838a-103">Funzionalità multi-Geo in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9838a-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="9838a-p101">Le funzionalità multi-Geo in Office 365 consentono di un singolo tenant possono estendersi su più aree geografiche. Quando è abilitata la multi-geo, i clienti possono selezionare il percorso del contenuto delle cassette postali Exchange Online (dati statici) singoli per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="9838a-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations. When multi-geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="9838a-p102">La posizione di tenant iniziale (noto come posizione centrale) è determinata in base all'indirizzo fatturazione. Quando è abilitata la multi-geo, è possibile effettuare le cassette postali nelle posizioni satellitari aggiuntive per:</span><span class="sxs-lookup"><span data-stu-id="9838a-p102">Your initial tenant location (referred to as the central location) is determined based on your billing address. When multi-geo is enabled, you can place mailboxes in additional satellite locations by:</span></span>

- <span data-ttu-id="9838a-108">Creazione di una nuova cassetta postale di Exchange Online direttamente in una posizione satellitare.</span><span class="sxs-lookup"><span data-stu-id="9838a-108">Creating a new Exchange Online mailbox directly in a satellite location.</span></span>

- <span data-ttu-id="9838a-109">Spostamento di una cassetta postale di Exchange Online in una posizione satellitare.</span><span class="sxs-lookup"><span data-stu-id="9838a-109">Moving an existing Exchange Online mailbox into a satellite location.</span></span>

- <span data-ttu-id="9838a-110">Onboarding una cassetta postale da un'organizzazione di Exchange locale direttamente in una posizione satellitare.</span><span class="sxs-lookup"><span data-stu-id="9838a-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location.</span></span>

<span data-ttu-id="9838a-111">Sono disponibili per l'utilizzo in una configurazione Multi-Geo geo posizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="9838a-111">The following geo locations are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="9838a-112">Asia Pacifico</span><span class="sxs-lookup"><span data-stu-id="9838a-112">Asia Pacific</span></span>

- <span data-ttu-id="9838a-113">Australia</span><span class="sxs-lookup"><span data-stu-id="9838a-113">Australia</span></span>

- <span data-ttu-id="9838a-114">Canada</span><span class="sxs-lookup"><span data-stu-id="9838a-114">Canada</span></span>

- <span data-ttu-id="9838a-115">Unione Europea</span><span class="sxs-lookup"><span data-stu-id="9838a-115">European Union</span></span>

- <span data-ttu-id="9838a-116">Francia</span><span class="sxs-lookup"><span data-stu-id="9838a-116">France</span></span>

- <span data-ttu-id="9838a-117">India (attualmente disponibili solo per i clienti con indirizzi fatturazione in India)</span><span class="sxs-lookup"><span data-stu-id="9838a-117">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="9838a-118">Giappone</span><span class="sxs-lookup"><span data-stu-id="9838a-118">Japan</span></span>

- <span data-ttu-id="9838a-119">Corea</span><span class="sxs-lookup"><span data-stu-id="9838a-119">Korea</span></span>

- <span data-ttu-id="9838a-120">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="9838a-120">United Kingdom</span></span>

- <span data-ttu-id="9838a-121">Stati Uniti</span><span class="sxs-lookup"><span data-stu-id="9838a-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="9838a-122">Configurazione dei prerequisiti</span><span class="sxs-lookup"><span data-stu-id="9838a-122">Prerequisite configuration</span></span>
<span data-ttu-id="9838a-p103">Prima di iniziare a utilizzare funzionalità Multi-Geo di Exchange Online, Microsoft è necessario configurare il tenant di Exchange Online per il supporto multi-geo. Questo processo di configurazione occasionale viene attivato dopo aver ordinato che multi-Geo di Office 365 e le licenze visualizzata nel tenant. Il processo di configurazione occasionale dovrebbe richiedere in genere meno di 30 giorni per il completamento. Per ordinare Office 365 Multi-Geo, contattare il rappresentante Microsoft. Per ulteriori informazioni, vedere https://aka.ms/Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="9838a-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for multi-geo support. This one-time configuration process is triggered after you order Office 365 Multi-Geo and the licenses show up in your tenant. This one-time configuration process should typically take less than 30 days to complete. To order Office 365 Multi-Geo, contact your Microsoft representative. For more information, see https://aka.ms/Multi-Geo.</span></span>

<span data-ttu-id="9838a-p104">Si riceverà le notifiche nel [Centro messaggi di Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) al termine della configurazione. Configurazione viene attivata automaticamente dopo le licenze multi-geo visualizzata nel tenant.</span><span class="sxs-lookup"><span data-stu-id="9838a-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your multi-geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="9838a-130">Spostamenti e la posizione della cassetta postale</span><span class="sxs-lookup"><span data-stu-id="9838a-130">Mailbox placement and moves</span></span>
<span data-ttu-id="9838a-131">Al termine di operazioni di configurazione preliminari multi-geo, Microsoft Exchange Online rispetta l'attributo **PreferredDataLocation** per gli oggetti utente in Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9838a-131">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="9838a-p105">Exchange Online Sincronizza la proprietà **PreferredDataLocation** di Azure Active Directory nella proprietà **MailboxRegion** nel servizio directory di Exchange Online. Il valore di **MailboxRegion** determina geografica in cui verranno inserite cassette postali degli utenti e le cassette postali di archiviazione associato. Non è possibile configurare primario della cassetta postale e archiviazione cassette postali un utente di cui si trovano in sedi diverse geo. Una sola posizione geografica può essere configurata per ogni oggetto utente.</span><span class="sxs-lookup"><span data-stu-id="9838a-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations. Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="9838a-136">Quando **PreferredDataLocation** è configurato su un utente con una cassetta postale esistente, la cassetta postale verrà inserite in una coda di trasferimento e automaticamente spostati nella posizione geografica specificato.</span><span class="sxs-lookup"><span data-stu-id="9838a-136">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="9838a-137">Quando **PreferredDataLocation** è configurato su un utente senza una cassetta postale esistente, la cassetta postale di cui eseguire il provisioning in una posizione geografica specificato.</span><span class="sxs-lookup"><span data-stu-id="9838a-137">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="9838a-138">Quando si **PreferredDataLocation** non viene specificato un utente, la cassetta postale verrà effettuata nella posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="9838a-138">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the central location.</span></span>

- <span data-ttu-id="9838a-139">Se il codice **PreferredDataLocation** non corretto (ad esempio un tipo di NAN anziché nomi), verrà effettuata la cassetta postale nella posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="9838a-139">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the central location.</span></span>

<span data-ttu-id="9838a-p106">**Nota**: funzionalità multi-geo e Skype per le riunioni Online Business regionale ospitata utilizzare la proprietà **PreferredDataLocation** per gli oggetti utente per individuare i servizi. Se si configurano i valori **PreferredDataLocation** per gli oggetti utente per le riunioni regionale ospitate, la cassetta postale per gli utenti verrà automaticamente spostata nella posizione specificata geo dopo multi-geo è abilitato nel tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="9838a-p106">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="9838a-142">Limitazioni per le funzionalità per la Multi-Geo in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9838a-142">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="9838a-p107">Solo cassette postali degli utenti, cassette postali delle risorse (sale e attrezzature cassette postali) e le cassette postali condivise supportano funzionalità multi-geo. Pubblica cassette postali delle cartelle e i gruppi di Office 365 rimanere nella posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="9838a-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support multi-geo features. Public Folder Mailboxes and Office 365 Groups remain in the central location.</span></span>
 
2. <span data-ttu-id="9838a-p108">Sicurezza e conformità caratteristiche (ad esempio, il controllo ed eDiscovery) disponibili nell'interfaccia di amministrazione di Exchange (EAC) non sono disponibili nelle organizzazioni con più geo. In realtà, è necessario utilizzare [centro conformità e sicurezza di Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) per configurare le caratteristiche di sicurezza e conformità.</span><span class="sxs-lookup"><span data-stu-id="9838a-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="9838a-p109">Outlook per gli utenti Mac potrebbero verificarsi una perdita temporanea di accesso alla cartella di archivio Online durante lo spostamento delle relative cassette postali in una nuova posizione geografica. Questa condizione si verifica quando il primario dell'utente e cassette postali di archiviazione si trovano nei percorsi geo diversi, perché spostamenti delle cassette postali tra Geo possono completare in momenti diversi.</span><span class="sxs-lookup"><span data-stu-id="9838a-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location. This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="9838a-p110">Gli utenti non possono condividere *cartelle delle cassette postali* tra diverse ubicazioni geo in Outlook sul web (precedentemente noto come Outlook Web App o OWA). Ad esempio, un utente nell'Unione europea non può utilizzare Outlook sul web per aprire una cartella condivisa in una cassetta postale che si trova negli Stati Uniti. Tuttavia, Outlook sul Web users possibile aprire *altre cassette postali* in Geos diversi utilizzando una finestra separata del browser, come descritto in [aprire la cassetta postale di un'altra persona in una finestra separata del browser in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="9838a-p110">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="9838a-152">**Nota**: la condivisione delle cartelle delle cassette postali tra geo è supportata in Outlook in Windows.</span><span class="sxs-lookup"><span data-stu-id="9838a-152">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="9838a-153">Amministrazione</span><span class="sxs-lookup"><span data-stu-id="9838a-153">Administration</span></span> 
<span data-ttu-id="9838a-p111">Per visualizzare e configurare le proprietà geo multi nell'ambiente Office 365, è necessario remote PowerShell. Per ulteriori informazioni sui vari moduli PowerShell utilizzati per gestire Office 365, vedere [gestione di Office 365 ed Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="9838a-p111">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="9838a-p112">È necessario il [Modulo di PowerShell di Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o versioni successive in V1. x per visualizzare la proprietà **PreferredDataLocation** per gli oggetti utente. Gli oggetti utente sincronizzati da connettere AAD in AAD non possono avere i valori **PreferredDataLocation** modificati direttamente tramite PowerShell AAD. Gli oggetti utente solo cloud possono essere modificati tramite PowerShell AAD. Per connettersi a PowerShell di Azure Active Directory, vedere [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="9838a-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="9838a-160">Per connettersi a Exchange Online PowerShell, vedere [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="9838a-160">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="9838a-161">Connettersi direttamente a un livello geografico specifico tramite Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="9838a-161">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="9838a-p113">In genere, Exchange Online PowerShell si connetterà alla posizione geografica predefinita. Tuttavia, è inoltre possibile connettere direttamente in posizioni non predefinite geo. A causa dei miglioramenti delle prestazioni, è consigliabile connettersi direttamente alla posizione geografica non predefinito quando si gestiscono solo gli utenti in tale posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="9838a-p113">Typically, Exchange Online PowerShell will connect to the default geo location. But, you can also connect directly to non-default geo locations. Because of performance improvements, we recommend connecting directly to the non-default geo location when you only manage users in that geo location.</span></span>

<span data-ttu-id="9838a-p114">Per connettersi a un determinato livello geografico, il parametro *ConnectionUri* è diverso da quello istruzioni connessione regolari. Il resto dei comandi e i valori sono gli stessi. I passaggi sono:</span><span class="sxs-lookup"><span data-stu-id="9838a-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="9838a-168">Nel computer locale, aprire Windows PowerShell ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9838a-168">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="9838a-169">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro o scuola account e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="9838a-169">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="9838a-p115">Sostituire `<emailaddress>` con l'indirizzo di posta elettronica di **qualsiasi** cassetta postale nella posizione geografica di destinazione e utilizzare il seguente comando. Le autorizzazioni per la cassetta postale e relazione con le proprie credenziali nel passaggio 1 non sono un fattore; l'indirizzo di posta elettronica semplicemente indica a Exchange Online where per la connessione.</span><span class="sxs-lookup"><span data-stu-id="9838a-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="9838a-172">Ad esempio, se olga@contoso.onmicrosoft.com è l'indirizzo di posta elettronica di una cassetta postale valida in geografica a cui connettersi, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9838a-172">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="9838a-173">Eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9838a-173">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="9838a-174">Requisiti di versione Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="9838a-174">Azure AD Connect version requirements</span></span>
<span data-ttu-id="9838a-p116">Connettere AAD versione 1.1.524.0 o versione successivo è l'unico metodo supportato per l'impostazione della proprietà **PreferredDataLocation** per gli oggetti utente che vengono sincronizzati da Active Directory locale. Gli oggetti utente sincronizzati da connettere AAD in AAD non possono avere i valori **PreferredDataLocation** modificati direttamente tramite PowerShell AAD. Gli oggetti utente solo cloud possono essere modificati tramite PowerShell AAD. Per istruzioni dettagliate, vedere [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="9838a-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="9838a-179">Codici geo</span><span class="sxs-lookup"><span data-stu-id="9838a-179">Geo Codes</span></span>
<span data-ttu-id="9838a-p117">I codici tre lettere per specificare il livello geografico nella proprietà **PreferredDataLocation** . Nella tabella seguente sono elencati i codici di Geos disponibili:</span><span class="sxs-lookup"><span data-stu-id="9838a-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="9838a-182">Geo</span><span class="sxs-lookup"><span data-stu-id="9838a-182">Geo</span></span> |<span data-ttu-id="9838a-183">Codice</span><span class="sxs-lookup"><span data-stu-id="9838a-183">Code</span></span> |
|---------|---------|
|<span data-ttu-id="9838a-184">Asia/Pacifico</span><span class="sxs-lookup"><span data-stu-id="9838a-184">Asia/Pacific</span></span> |<span data-ttu-id="9838a-185">APC</span><span class="sxs-lookup"><span data-stu-id="9838a-185">APC</span></span> |
|<span data-ttu-id="9838a-186">Australia</span><span class="sxs-lookup"><span data-stu-id="9838a-186">Australia</span></span> |<span data-ttu-id="9838a-187">AUS</span><span class="sxs-lookup"><span data-stu-id="9838a-187">AUS</span></span> |
|<span data-ttu-id="9838a-188">Canada</span><span class="sxs-lookup"><span data-stu-id="9838a-188">Canada</span></span> |<span data-ttu-id="9838a-189">CAN</span><span class="sxs-lookup"><span data-stu-id="9838a-189">CAN</span></span> |
|<span data-ttu-id="9838a-190">Unione Europea</span><span class="sxs-lookup"><span data-stu-id="9838a-190">European Union</span></span> |<span data-ttu-id="9838a-191">EUR</span><span class="sxs-lookup"><span data-stu-id="9838a-191">EUR</span></span> |
|<span data-ttu-id="9838a-192">Francia</span><span class="sxs-lookup"><span data-stu-id="9838a-192">France</span></span> |<span data-ttu-id="9838a-193">FRA</span><span class="sxs-lookup"><span data-stu-id="9838a-193">FRA</span></span>|
|<span data-ttu-id="9838a-194">India</span><span class="sxs-lookup"><span data-stu-id="9838a-194">India</span></span> |<span data-ttu-id="9838a-195">RICERCA</span><span class="sxs-lookup"><span data-stu-id="9838a-195">IND</span></span> |
|<span data-ttu-id="9838a-196">Giappone</span><span class="sxs-lookup"><span data-stu-id="9838a-196">Japan</span></span> |<span data-ttu-id="9838a-197">JPN</span><span class="sxs-lookup"><span data-stu-id="9838a-197">JPN</span></span> |
|<span data-ttu-id="9838a-198">Corea</span><span class="sxs-lookup"><span data-stu-id="9838a-198">Korea</span></span> |<span data-ttu-id="9838a-199">KOR</span><span class="sxs-lookup"><span data-stu-id="9838a-199">KOR</span></span> |
|<span data-ttu-id="9838a-200">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="9838a-200">United Kingdom</span></span> |<span data-ttu-id="9838a-201">GBR</span><span class="sxs-lookup"><span data-stu-id="9838a-201">GBR</span></span> |
|<span data-ttu-id="9838a-202">Stati Uniti</span><span class="sxs-lookup"><span data-stu-id="9838a-202">United States</span></span> |<span data-ttu-id="9838a-203">NAM</span><span class="sxs-lookup"><span data-stu-id="9838a-203">NAM</span></span> |

<span data-ttu-id="9838a-p118">**Nota**: le proprietà **PreferredDataLocation** e **MailboxRegion** sono stringhe con alcun controllo degli errori. Se si immette un valore non valido (ad esempio NAN) della cassetta postale verrà inserita nel livello geografico predefinito.</span><span class="sxs-lookup"><span data-stu-id="9838a-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="9838a-206">Visualizzazione Geos disponibili configurati nell'organizzazione Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9838a-206">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="9838a-207">Per visualizzare l'elenco dei Geos configurati nell'organizzazione Exchange Online, eseguire il seguente comando in Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9838a-207">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="9838a-208">L'output del comando avrà questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="9838a-208">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="9838a-209">Visualizzare il valore predefinito Geo per l'organizzazione Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9838a-209">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="9838a-210">Per visualizzare il livello geografico predefinito dell'organizzazione Exchange Online, eseguire il comando seguente in Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9838a-210">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="9838a-211">L'output del comando avrà questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="9838a-211">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="9838a-212">Individuare la posizione geografica di una cassetta postale</span><span class="sxs-lookup"><span data-stu-id="9838a-212">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="9838a-213">Il cmdlet **Get-Mailbox** in Exchange Online PowerShell viene visualizzato il seguente multi-geo relative proprietà per le cassette postali:</span><span class="sxs-lookup"><span data-stu-id="9838a-213">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="9838a-p119">**Database**: le prime 3 lettere del nome del database corrispondono al codice Geo, che fornisce le informazioni della cassetta postale in cui attualmente si trova. Proprietà deve essere utilizzata per cassette postali di archiviazione Online **ArchiveDatabase** .</span><span class="sxs-lookup"><span data-stu-id="9838a-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="9838a-216">**MailboxRegion**: Specifica il codice di ubicazione geografica che è stato impostato dall'amministratore (sincronizzato da **PreferredDataLocation** in Azure Active Directory).</span><span class="sxs-lookup"><span data-stu-id="9838a-216">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="9838a-217">**MailboxRegionLastUpdateTime**: indica MailboxRegion dell'ultimo aggiornamento (automaticamente o manualmente).</span><span class="sxs-lookup"><span data-stu-id="9838a-217">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="9838a-218">Per visualizzare le proprietà per una cassetta postale, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="9838a-218">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="9838a-219">Ad esempio, per visualizzare le informazioni di livello geografico per chris@contoso.onmicrosoft.com cassetta postale, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9838a-219">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="9838a-220">L'output del comando avrà questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="9838a-220">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="9838a-221">**Nota:** Se il codice di posizione geografica nel nome del database non corrisponde a quello **MailboxRegion** , la cassetta postale sarà verrà automaticamente inserito in una coda di trasferimento e spostata la posizione geografica specificato dal parametro valore **MailboxRegion** (Exchange Online Cerca un mancata corrispondenza tra i valori delle proprietà).</span><span class="sxs-lookup"><span data-stu-id="9838a-221">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="9838a-222">Spostare una cassetta postale solo cloud esistente a un livello geografico specifico</span><span class="sxs-lookup"><span data-stu-id="9838a-222">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="9838a-p120">Un utente solo cloud è un utente non syncrhonized al tenant tramite la connessione AAD. L'utente è stato creato direttamente in Azure Active Directory. Utilizzare il cmdlet **Get-MsolUser** e **Set-MsolUser** nel modulo Azure Active Directory per Windows PowerShell per visualizzare o specificare geografica in cui verrà archiviata un solo cloud cassetta postale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="9838a-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="9838a-226">Per visualizzare il valore **PreferredDataLocation** per un utente, utilizzare la seguente sintassi in Azure Active Directory PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9838a-226">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="9838a-227">Ad esempio, per visualizzare il valore **PreferredDataLocation** michelle@contoso.onmicrosoft.com utente, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9838a-227">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="9838a-228">L'output del comando avrà questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="9838a-228">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="9838a-229">Per modificare il valore **PreferredDataLocation** per un oggetto utente solo cloud, utilizzare la sintassi seguente in Azure Active Directory PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9838a-229">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="9838a-230">Ad esempio, per impostare il valore **PreferredDataLocation** su geo Unione europea (EUR) per michelle@contoso.onmicrosoft.com utente, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9838a-230">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="9838a-231">**Note**:</span><span class="sxs-lookup"><span data-stu-id="9838a-231">**Notes**:</span></span>

- <span data-ttu-id="9838a-p121">Come spiegato in precedenza è possibile utilizzare questa procedura per gli oggetti utente sincronizzato da Active Directory locale. È necessario modificare il valore **PreferredDataLocation** utilizzando AAD Connect. Per ulteriori informazioni, vedere [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="9838a-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="9838a-235">Il tempo necessario per spostare un mailboxfrom che relativa geo corrente nella nuova posizione geografica desiderata dipende da diversi fattori:</span><span class="sxs-lookup"><span data-stu-id="9838a-235">How long it takes to relocate a mailboxfrom its current geo to the new desired geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="9838a-236">La dimensione e tipo di cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="9838a-236">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="9838a-237">Il numero di cassette postali da spostare.</span><span class="sxs-lookup"><span data-stu-id="9838a-237">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="9838a-238">Disponibilità delle risorse di spostamento.</span><span class="sxs-lookup"><span data-stu-id="9838a-238">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="9838a-239">Spostamento disabilitate le cassette postali presenti conservazione per controversia legale</span><span class="sxs-lookup"><span data-stu-id="9838a-239">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="9838a-p122">Disabilitate le cassette postali conservazione per controversia legale che vengono conservate per scopi non possono essere spostati modificando i valori **PreferredDataLocation** nello stato disabilitato eDiscovery. Per spostare una cassetta postale disabilitata sulla conservazione per controversia legale:</span><span class="sxs-lookup"><span data-stu-id="9838a-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="9838a-242">Assegnare temporaneamente una licenza per la cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="9838a-242">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="9838a-243">Modificare **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="9838a-243">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="9838a-244">Rimuovere la licenza dalla cassetta postale dopo che è stata spostata nella posizione geografica selezionato in rimetterlo in stato disabilitato.</span><span class="sxs-lookup"><span data-stu-id="9838a-244">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="9838a-245">Creare nuove cassette postali cloud in un determinato livello geografico</span><span class="sxs-lookup"><span data-stu-id="9838a-245">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="9838a-246">Per creare una nuova cassetta postale in una posizione geografica specifici, è necessario eseguire una della procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="9838a-246">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="9838a-p123">Configurare il valore **PreferredDataLocation** come descritto nella precedente sezione *prima* che cassetta postale viene creata in Exchange Online. Ad esempio, è possibile configurare il valore **PreferredDataLocation** su un utente prima di assegnare una licenza.</span><span class="sxs-lookup"><span data-stu-id="9838a-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="9838a-249">Assegnare una licenza contemporaneamente che si imposta il valore **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="9838a-249">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="9838a-250">Per creare un nuovo solo cloud con licenza utente (non AAD connessione sincronizzati) in un livello geografico specifico, utilizzare la sintassi seguente in Azure Active Directory PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9838a-250">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="9838a-251">In questo esempio crea un nuovo account utente per Elizabeth Brunner con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="9838a-251">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="9838a-252">Nome dell'entità utente: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="9838a-252">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="9838a-253">Nome: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="9838a-253">First name: Elizabeth</span></span>

- <span data-ttu-id="9838a-254">Cognome: Brunner</span><span class="sxs-lookup"><span data-stu-id="9838a-254">Last name: Brunner</span></span>

- <span data-ttu-id="9838a-255">Nome visualizzato Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="9838a-255">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="9838a-256">Password: generato casualmente e illustrate nei risultati del comando (dal momento che non viene utilizzato il parametro *Password* )</span><span class="sxs-lookup"><span data-stu-id="9838a-256">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="9838a-257">Licenza: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="9838a-257">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="9838a-258">Posizione: Australia (Australia)</span><span class="sxs-lookup"><span data-stu-id="9838a-258">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="9838a-259">Per ulteriori informazioni sulla creazione di nuovi account utente e la ricerca di valori LicenseAssignment in PowerShell di Azure Active Directory, vedere [creare gli account utente con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="9838a-259">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="9838a-p124">**Nota:** Se si utilizza Exchange Online PowerShell per abilitare una cassetta postale e la cassetta postale da creare direttamente in Geo specificato in **PreferredDataLocation**è necessario, è necessario utilizzare un cmdlet di Exchange Online, ad esempio **Enable-Mailbox** o \*\*New-Mailbox \*\*direttamente sul servizio cloud. Se si utilizza il cmdlet di Exchange locale **Enable-RemoteMailbox** , verrà creata la cassetta postale in Geo predefinito.</span><span class="sxs-lookup"><span data-stu-id="9838a-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="9838a-262">Esistenti incorporato cassette postali locali in un determinato livello geografico</span><span class="sxs-lookup"><span data-stu-id="9838a-262">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="9838a-263">È possibile utilizzare gli strumenti di onboarding standard e i processi per eseguire la migrazione di una cassetta postale da un'organizzazione di Exchange locale a Exchange Online, tra cui il [dashboard di migrazione in EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e il cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) di Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9838a-263">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="9838a-p125">Il primo passaggio consiste nel verificare che un oggetto utente esiste per ciascuna cassetta postale essere onboarded e verificare che il valore **PreferredDataLocation** corretto è configurato in Azure Active Directory. Gli strumenti di on-boarding rispettano il valore **PreferredDataLocation** e verranno eseguita la migrazione di cassette postali direttamente a Geo specificato.</span><span class="sxs-lookup"><span data-stu-id="9838a-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="9838a-266">In alternativa, è possibile utilizzare la procedura seguente per le cassette postali incorporate direttamente in una posizione geografica specifico utilizzando il cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9838a-266">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="9838a-p126">Verificare l'oggetto utente per ciascuna cassetta postale da onboarded e che **PreferredDataLocation** sia impostata sul valore desiderato in Azure Active Directory. Il valore di **PreferredDataLocation** verrà sincronizzato con l'attributo **MailboxRegion** dell'oggetto utente di posta elettronica corrispondente in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9838a-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="9838a-269">Connettersi direttamente a satellitari specifico Geo utilizzando le istruzioni di connessione da più indietro in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="9838a-269">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="9838a-270">In Exchange Online PowerShell, archiviare le credenziali di amministratore locale che viene utilizzato per eseguire una migrazione delle cassette postali in una variabile eseguendo il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9838a-270">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="9838a-271">In Exchange Online PowerShell, creare un nuovo **New-MoveRequest** simile a quello riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9838a-271">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="9838a-272">Ripetere il passaggio #4 per ogni cassetta postale che è necessario eseguire la migrazione da Exchange locale al percorso satellitari che attualmente si è connessi.</span><span class="sxs-lookup"><span data-stu-id="9838a-272">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="9838a-273">Se è necessario eseguire la migrazione di cassette postali aggiuntive in un percorso diverso satellitari, ripetere i passaggi da 2 a 4 per ogni località satellitari specifico.</span><span class="sxs-lookup"><span data-stu-id="9838a-273">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="9838a-274">Creazione di report multi-Geo</span><span class="sxs-lookup"><span data-stu-id="9838a-274">Multi-Geo Reporting</span></span>
<span data-ttu-id="9838a-p127">**Report di utilizzo della Multi-Geo** nell'interfaccia di amministrazione di Office 365 viene visualizzato il numero di utenti dalla posizione geografica. Il rapporto viene visualizzato distribuzione degli utenti per il mese corrente e vengono forniti dati cronologici per gli ultimi 6 mesi.</span><span class="sxs-lookup"><span data-stu-id="9838a-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by geo location. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
