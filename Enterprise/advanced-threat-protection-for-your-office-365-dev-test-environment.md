---
title: Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Riepilogo: Configurare ed effettuare una dimostrazione di protezione di Office 365 avanzate rischio nell''ambiente di sviluppo e di testing di Office 365.'
ms.openlocfilehash: 00b1fc8fea930346f082d3d2302a14dea7ad4309
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="08d4f-103">Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="08d4f-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="08d4f-104">**Riepilogo:** Configurare e illustrare la protezione di Office 365 avanzate rischio nell'ambiente di sviluppo e di testing di Office 365.</span><span class="sxs-lookup"><span data-stu-id="08d4f-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="08d4f-p101">Office 365 avanzate Threat Protection (degli strumenti di analisi) è una funzionalità di Exchange Online Protection (EOP) che consente di mantenere malware fuori la posta elettronica. Con degli strumenti di analisi, creare criteri nell'interfaccia di amministrazione di Exchange (EAC) o la protezione &amp; centro conformità per garantire che gli utenti devono accedere solo collegamenti o allegati nei messaggi di posta elettronica che vengono identificati come non dannoso. Per ulteriori informazioni, vedere [protezione rischio avanzata per gli allegati sicuri e collegamenti sicuri](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="08d4f-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="08d4f-108">Con le istruzioni disponibili in questo articolo, è possibile configurare e testare ATP nella sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="08d4f-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="08d4f-109">Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato</span><span class="sxs-lookup"><span data-stu-id="08d4f-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="08d4f-110">Se si desidera testare degli strumenti di analisi in un modo semplice con i requisiti minimi, seguire le istruzioni in fasi 2 e 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="08d4f-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="08d4f-111">Se si desidera testare degli strumenti di analisi in un'azienda simulata, seguire le istruzioni in [DirSync per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="08d4f-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="08d4f-p102">Il test di ATP non richiede l'ambiente di sviluppo/test aziendale simulato, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di Windows Server AD. Qui viene fornito come un'opzione in modo da poter testare ATP e sperimentarlo in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="08d4f-114">Fase 2: Illustrare il comportamento di recapito di posta elettronica predefinito di Office 365</span><span class="sxs-lookup"><span data-stu-id="08d4f-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="08d4f-115">In questa fase, viene mostrato che prima di configurare i criteri di ATP, i messaggi di posta elettronica potenzialmente dannosi vengono recapitati alle cassette postali di Office 365 senza essere sottoposti a screening o mitigazione.</span><span class="sxs-lookup"><span data-stu-id="08d4f-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="08d4f-116">Aprire Internet Explorer e accedere all'account di Outlook creata nella fase 2 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="08d4f-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="08d4f-117">Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, aprire una sessione privata di Internet Explorer e accedere dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="08d4f-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="08d4f-118">Se si utilizza l'ambiente di sviluppo e di testing di Office 365 enterprise simulato, utilizzare il [portale Azure](https://portal.azure.com) per connettersi alla macchina virtuale CLIENT1 e quindi effettuare l'accesso da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="08d4f-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="08d4f-119">Eseguire Notepad e immettere del testo.</span><span class="sxs-lookup"><span data-stu-id="08d4f-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="08d4f-120">Salvare il file nella cartella documenti come **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="08d4f-121">Nella scheda posta elettronica di Outlook di Internet Explorer, fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="08d4f-122">Nella casella **a**digitare l'indirizzo di posta elettronica del nome di amministratore globale di Office 365 della sottoscrizione di prova.</span><span class="sxs-lookup"><span data-stu-id="08d4f-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="08d4f-123">Per l'oggetto, digitare **i tasti di nuovi**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="08d4f-124">Nel corpo, digitare **che qui è il file**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="08d4f-125">Fare clic su **Collega**, fare doppio clic su **getKeys.js** nella cartella documenti, fare clic su **Collega come copia**e quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="08d4f-126">Fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-126">Click **New**.</span></span>
    
10. <span data-ttu-id="08d4f-127">Nella casella **a**digitare l'indirizzo di posta elettronica del nome di amministratore globale di Office 365 della sottoscrizione di prova.</span><span class="sxs-lookup"><span data-stu-id="08d4f-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="08d4f-128">Per l'oggetto, digitare **New viaggi del sito web**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="08d4f-129">Nel corpo, digitare **inoltrato questo sito**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="08d4f-130">Nel corpo, selezionare il testo di **questo sito** e fare clic sull'icona di collegamento ipertestuale sulla barra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="08d4f-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="08d4f-131">In **URL**digitare **http://www.spamlink.contoso.com/**, fare clic su **OK**e quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="08d4f-132">Aprire un'istanza separata di Internet Explorer in modalità di visualizzazione privata, passare al portale di Office 365 ([https://portal.office.com](https://portal.office.com)) e accedere alla sottoscrizione di prova di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="08d4f-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="08d4f-133">Dalla pagina del portale principale, fare clic su sezioni App e quindi fare clic su **posta elettronica**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="08d4f-134">Posta in arrivo, fare clic sul messaggio con l'oggetto **delle chiavi di nuove**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="08d4f-p103">Nella cartella posta indesiderata, fare clic sul messaggio con l'oggetto del **nuovo sito web di viaggio**. All'interno del messaggio, fare clic sul collegamento di **sito** . Verrà visualizzato un "Oops! Pagina di Internet Explorer Impossibile trovare spamlink.contoso.com.". Questo è il risultato corretto perché non esiste alcuna pagina web in tale posizione.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="08d4f-p104">Si noti che entrambi questi messaggi di posta elettronica potenzialmente pericolosi sono stati recapitati correttamente. Messaggio di posta elettronica **le nuove chiavi** potrebbe contenere non rilevato malware e l'utente è stato autorizzato a fare clic sul collegamento nel messaggio di posta elettronica **nuovo sito web di viaggio** potenzialmente dannoso.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="08d4f-143">Fase 3: configurare i criteri per i collegamenti sicuri e per gli allegati sicuri per ATP</span><span class="sxs-lookup"><span data-stu-id="08d4f-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="08d4f-144">In questa fase, viene creato un criterio per gli allegati sicuri per impedire il recapito di messaggi di posta elettronica contenenti allegati potenzialmente dannosi e un criterio per i collegamenti sicuri per impedire agli utenti di usare URL potenzialmente pericolosi.</span><span class="sxs-lookup"><span data-stu-id="08d4f-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="08d4f-145">Nella scheda **Home page di Microsoft Office** di Internet Explorer, fare clic su tessera di **amministrazione** .</span><span class="sxs-lookup"><span data-stu-id="08d4f-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="08d4f-146">Nel riquadro di spostamento sinistra fare clic su **Admin Center**, quindi scegliere **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="08d4f-147">Nel riquadro di spostamento sinistro della scheda Exchange admin center, fare clic su **Avanzate minacce**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="08d4f-148">Fare clic sulla scheda **allegati attendibili** e quindi fare clic sul segno più.</span><span class="sxs-lookup"><span data-stu-id="08d4f-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="08d4f-149">Nella finestra **nuovo criterio di sicurezza degli allegati** , in **nome**digitare **Criteri allegato protetto - blocco**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="08d4f-150">Per la **risposta malware sconosciuto gli allegati sicuri**, fare clic su **Blocca**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="08d4f-151">Per **reindirizzare degli allegati nel rilevamento**, fare clic su **Abilita reindirizza** e digitare l'indirizzo di posta elettronica dell'account di amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="08d4f-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="08d4f-p105">Per **applicata a**, fare clic sulla freccia e quindi **è il dominio del destinatario**. Nella finestra, scegliere il nome dell'organizzazione (ad esempio contoso.onmicrosoft.com) e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="08d4f-p106">Fare clic su **Salva**. Dopo l'aggiornamento, si dovrebbe essere visibile il nuovo e abilitato **Criteri allegato protetto - blocco**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="08d4f-156">Fare clic sulla scheda **collegamenti attendibili** e quindi fare clic sul segno più.</span><span class="sxs-lookup"><span data-stu-id="08d4f-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="08d4f-157">Nella finestra **nuovo criterio di collegamenti sicuro** , in **nome**digitare **Criteri collegamento protetto**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="08d4f-158">Per **Selezionare l'azione per gli URL potenzialmente pericolosi sconosciuti nei messaggi**, fare clic **su**e quindi selezionare **non consentire agli utenti di fare clic per URL originale**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="08d4f-p107">Per **applicata a**, fare clic sulla freccia e quindi **è il dominio del destinatario**. Nella finestra, scegliere il nome dell'organizzazione (ad esempio contoso.onmicrosoft.com) e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="08d4f-p108">Fare clic su **Salva**. Si dovrebbe essere visibile il nuovo e abilitato **Criteri collegamento protetto**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="08d4f-163">Fase 4: dimostrazione di ATP in azione</span><span class="sxs-lookup"><span data-stu-id="08d4f-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="08d4f-164">In questa fase, viene mostrato come ATP si occupa dei messaggi di posta elettronica potenzialmente dannosi.</span><span class="sxs-lookup"><span data-stu-id="08d4f-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="08d4f-165">Dall'istanza di Internet Explorer utilizzato per inviare il messaggio nella fase 2, nel riquadro di spostamento sinistro, fare clic su **posta inviata.**</span><span class="sxs-lookup"><span data-stu-id="08d4f-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="08d4f-166">Fare clic su posta elettronica denominato **le nuove chiavi**, fare clic sull'icona di freccia verso il basso e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="08d4f-167">Per i nuovi messaggi, nella casella **a**digitare l'indirizzo di posta elettronica il nome di amministratore globale di Office 365 dell'abbonamento prova e quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="08d4f-168">Fare clic su posta elettronica denominato **New viaggi del sito web**, fare clic sull'icona di freccia verso il basso, fare clic su **Rispondi a tutti**e quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="08d4f-p109">Dall'istanza di Internet Explorer utilizzato per configurare i criteri degli strumenti di analisi nella fase 3, fare clic sulla scheda Exchange admin center, fare clic su sezioni App e quindi fare clic su **posta elettronica**. Verrà visualizzata due nuovi messaggi di posta elettronica in arrivo:</span><span class="sxs-lookup"><span data-stu-id="08d4f-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="08d4f-171">Uno intitolato **firmware: le nuove chiavi**</span><span class="sxs-lookup"><span data-stu-id="08d4f-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="08d4f-172">Uno intitolato **firmware: nuovo sito web viaggi**</span><span class="sxs-lookup"><span data-stu-id="08d4f-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="08d4f-p110">Aprire il messaggio di posta elettronica denominato **firmware: nuovo sito web viaggi** e fare clic sul collegamento di **sito** . Verrà visualizzata una pagina "il sito Web è stato classificato come dannose.". Dimostra che degli strumenti di analisi è impedire l'accesso al sito web potenzialmente dannosi.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="08d4f-177">In Exchange admin center scheda di Internet Explorer, nel riquadro di spostamento sinistra fare clic su **flusso di posta**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="08d4f-178">Fare clic sulla scheda **traccia dei messaggi** e fare clic su **Cerca**.</span><span class="sxs-lookup"><span data-stu-id="08d4f-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="08d4f-p111">Nella finestra **Message Trace Results** , fare doppio clic sul messaggio con l'oggetto **delle chiavi di nuove**. Questo messaggio è stato correttamente recapitato alla posta in arrivo. Chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="08d4f-p112">Fare doppio clic sul messaggio con l'oggetto del **nuovo sito web di viaggio**. Questo messaggio è stato correttamente recapitato alla posta in arrivo. Chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="08d4f-p113">Fare doppio clic sul messaggio con l'oggetto **firmware: le nuove chiavi**. Si noti come questo messaggio è stato elaborato da strumenti di analisi e quindi recapitato nella posta in arrivo. Chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="08d4f-p114">Lo scopo del criterio gli allegati sicuri era per avviare la scansione degli allegati per malware. L'allegato getKeys.js è stato consentito perché non è stata determinata da dannoso. Questo passaggio viene illustrato che degli strumenti di analisi è stato viene eseguita un'analisi dell'allegato.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="08d4f-p115">Fare doppio clic sul messaggio con l'oggetto **firmware: nuovo sito web di viaggio**. Si noti che questo messaggio è stato correttamente recapitato alla posta in arrivo.</span><span class="sxs-lookup"><span data-stu-id="08d4f-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="08d4f-193">È ora possibile utilizzare questo ambiente per creare nuovi criteri e sperimentare ATP.</span><span class="sxs-lookup"><span data-stu-id="08d4f-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="08d4f-194">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="08d4f-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="08d4f-195">See Also</span><span class="sxs-lookup"><span data-stu-id="08d4f-195">See Also</span></span>

[<span data-ttu-id="08d4f-196">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="08d4f-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="08d4f-197">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="08d4f-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="08d4f-198">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="08d4f-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="08d4f-199">DirSync per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="08d4f-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="08d4f-200">Cloud App Security per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="08d4f-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="08d4f-201">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="08d4f-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="08d4f-202">Protezione avanzata dalle minacce per allegati e collegamenti sicuri</span><span class="sxs-lookup"><span data-stu-id="08d4f-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


