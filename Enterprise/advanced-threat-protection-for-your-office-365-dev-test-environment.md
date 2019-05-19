---
title: Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "Riepilogo: configurazione e dimostrazione di Office 365 Advanced Threat Protection nell'ambiente di sviluppo/test di Office 365."
ms.openlocfilehash: 274f8558d23714a73e0891500dac5d5e007b6be2
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162419"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="654c8-103">Advanced Threat Protection per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="654c8-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="654c8-104">**Riepilogo:** configurazione e dimostrazione di Office 365 Advanced Threat Protection nell'ambiente di sviluppo/test di Office 365.</span><span class="sxs-lookup"><span data-stu-id="654c8-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="654c8-105">Office 365 Advanced Threat Protection (ATP) è una funzionalità di Exchange Online Protection (EOP) che consente di escludere il malware dalla posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="654c8-105">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span> <span data-ttu-id="654c8-106">Con ATP, è possibile creare criteri nell'interfaccia di amministrazione di Exchange (EAC) o &amp; nel centro sicurezza e conformità che consentono agli utenti di accedere solo ai collegamenti o agli allegati nei messaggi di posta elettronica identificati come non dannosi.</span><span class="sxs-lookup"><span data-stu-id="654c8-106">With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious.</span></span> <span data-ttu-id="654c8-107">Per ulteriori informazioni, vedere [Protezione avanzata dalle minacce per allegati e collegamenti sicuri](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="654c8-107">For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="654c8-108">Con le istruzioni disponibili in questo articolo, è possibile configurare e testare ATP nella sottoscrizione di valutazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="654c8-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="654c8-109">Fase 1: creare l'ambiente di sviluppo/test di Office 365 aziendale leggero o simulato</span><span class="sxs-lookup"><span data-stu-id="654c8-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="654c8-110">Se si desidera testare ATP in modo semplice con i requisiti minimi, seguire le istruzioni riportate nelle fasi 2 e 3 dell' [ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="654c8-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="654c8-111">Se si desidera testare ATP in un'azienda simulata, seguire le istruzioni in [dirsync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="654c8-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="654c8-112">Testing ATP non richiede l'ambiente di sviluppo/testing dell'organizzazione simulata, che include una rete Intranet simulata connessa a Internet e la sincronizzazione della directory per una foresta di servizi di dominio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="654c8-112">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="654c8-113">Qui viene fornito come un'opzione in modo da poter testare ATP e sperimentarlo in un ambiente che rappresenta un'organizzazione tipica.</span><span class="sxs-lookup"><span data-stu-id="654c8-113">It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="654c8-114">Fase 2: dimostrare il comportamento di recapito della posta elettronica predefinito di Office 365</span><span class="sxs-lookup"><span data-stu-id="654c8-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="654c8-115">In questa fase, viene mostrato che prima di configurare i criteri di ATP, i messaggi di posta elettronica potenzialmente dannosi vengono recapitati alle cassette postali di Office 365 senza essere sottoposti a screening o mitigazione.</span><span class="sxs-lookup"><span data-stu-id="654c8-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="654c8-116">Aprire Internet Explorer e accedere all'account di Outlook creato nella fase 2 dell'ambiente di [sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="654c8-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="654c8-117">Se è in uso l'ambiente di sviluppo/test di Office 365 leggero, aprire una sessione privata di Internet Explorer e accedere dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="654c8-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="654c8-118">Se si utilizza l'ambiente di sviluppo/test di Office 365 per l'organizzazione simulata, utilizzare il [portale di Azure](https://portal.azure.com) per connettersi alla macchina virtuale CLIENT1 e quindi eseguire l'accesso da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="654c8-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="654c8-119">Eseguire Notepad e immettere del testo.</span><span class="sxs-lookup"><span data-stu-id="654c8-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="654c8-120">Salvare il file nella cartella Documenti come  **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="654c8-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="654c8-121">Dalla scheda Posta di Outlook di Internet Explorer, fare clic su **Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="654c8-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="654c8-122">In **A**, digitare l'indirizzo di posta elettronica dell'amministratore globale di Office 365 della sottoscrizione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="654c8-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="654c8-123">Per l'oggetto, digitare **Nuove chiavi**.</span><span class="sxs-lookup"><span data-stu-id="654c8-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="654c8-124">Nel corpo del messaggio, digitare **Ecco il file**.</span><span class="sxs-lookup"><span data-stu-id="654c8-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="654c8-125">Fare clic su **Allega**, fare doppio clic su **getKeys.js** nella cartella Documenti, fare clic su **Allega come copia**, quindi su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="654c8-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="654c8-126">Fare clic su **Nuova regola**.</span><span class="sxs-lookup"><span data-stu-id="654c8-126">Click **New**.</span></span>
    
10. <span data-ttu-id="654c8-127">In **A**, digitare l'indirizzo di posta elettronica dell'amministratore globale di Office 365 della sottoscrizione di valutazione.</span><span class="sxs-lookup"><span data-stu-id="654c8-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="654c8-128">Per l'oggetto, digitare **Nuovo sito Web di viaggi**.</span><span class="sxs-lookup"><span data-stu-id="654c8-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="654c8-129">Nel corpo del messaggio, digitare **Qualcuno mi ha inoltrato questo sito**.</span><span class="sxs-lookup"><span data-stu-id="654c8-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="654c8-130">Nel corpo del messaggio, selezionare il testo **questo sito** e fare clic sull'icona del collegamento ipertestuale nella barra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="654c8-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="654c8-131">In **URL**Digitare **http://www.spamlink.contoso.com/**, fare clic su **OK**, quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="654c8-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="654c8-132">Aprire un'istanza separata di Internet Explorer in modalità esplorazione privata, accedere all'interfaccia di amministrazione di Microsoft 365[https://admin.microsoft.com](https://admin.microsoft.com)() e accedere alla sottoscrizione di valutazione di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="654c8-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="654c8-133">Dalla pagina principale del portale, fare clic sul riquadro delle app, quindi su **Posta**.</span><span class="sxs-lookup"><span data-stu-id="654c8-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="654c8-134">Nella Posta in arrivo, fare clic sul messaggio con l'oggetto **Nuove chiavi**.</span><span class="sxs-lookup"><span data-stu-id="654c8-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="654c8-135">Nella cartella posta indesiderata, fare clic sul messaggio con il **nuovo sito Web di viaggio**soggetto.</span><span class="sxs-lookup"><span data-stu-id="654c8-135">In the Junk Mail folder, click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="654c8-136">All'interno del messaggio, fare clic sul collegamento **sito** .</span><span class="sxs-lookup"><span data-stu-id="654c8-136">Within the message, click the **this site** link.</span></span> <span data-ttu-id="654c8-137">Dovrebbe essere visualizzato un "Oops!</span><span class="sxs-lookup"><span data-stu-id="654c8-137">You should see a "Oops!</span></span> <span data-ttu-id="654c8-138">Internet Explorer non è stato in grado di trovare spamlink.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="654c8-138">Internet Explorer could not find spamlink.contoso.com."</span></span> <span data-ttu-id="654c8-139">video.</span><span class="sxs-lookup"><span data-stu-id="654c8-139">page.</span></span> <span data-ttu-id="654c8-140">Questo è il risultato corretto perché non è presente alcuna pagina Web in tale posizione.</span><span class="sxs-lookup"><span data-stu-id="654c8-140">This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="654c8-p104">Si noti che questi messaggi di posta elettronica potenzialmente dannosi sono stati recapitati correttamente. Il messaggio di posta elettronica **Nuove chiavi** potrebbe contenere malware non rilevato e l'utente ha potuto fare clic sul collegamento potenzialmente dannoso nel messaggio di posta elettronica **Nuovo sito Web di viaggi**.</span><span class="sxs-lookup"><span data-stu-id="654c8-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="654c8-143">Fase 3: configurare i criteri per i collegamenti sicuri e per gli allegati sicuri per ATP</span><span class="sxs-lookup"><span data-stu-id="654c8-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="654c8-144">In questa fase, viene creato un criterio per gli allegati sicuri per impedire il recapito di messaggi di posta elettronica contenenti allegati potenzialmente dannosi e un criterio per i collegamenti sicuri per impedire agli utenti di usare URL potenzialmente pericolosi.</span><span class="sxs-lookup"><span data-stu-id="654c8-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="654c8-145">Nella scheda **Microsoft Office Home** di Internet Explorer, fare clic sul riquadro **amministratore** .</span><span class="sxs-lookup"><span data-stu-id="654c8-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="654c8-146">Nella barra di spostamento a sinistra, fare clic su **Interfacce di amministrazione**, quindi su **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="654c8-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="654c8-147">Nella barra di spostamento a sinistra della scheda dell'interfaccia di amministrazione di Exchange, fare clic su **protezione avanzata minacce**.</span><span class="sxs-lookup"><span data-stu-id="654c8-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="654c8-148">Fare clic sulla scheda **allegati sicuri** e quindi fare clic sul segno più.</span><span class="sxs-lookup"><span data-stu-id="654c8-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="654c8-149">Nella finestra **nuovo criterio allegati sicuri** , in **nome**, digitare **Safe Attachment Policy-Block**.</span><span class="sxs-lookup"><span data-stu-id="654c8-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="654c8-150">Per la **risposta malware sconosciuto degli allegati sicuri**, fare clic su **blocca**.</span><span class="sxs-lookup"><span data-stu-id="654c8-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="654c8-151">Per **Reindirizza allegato quando rilevato**, fare clic su **Abilita reindirizzamento** e digitare l'indirizzo di posta elettronica dell'account di amministratore globale di Office 365 in uso.</span><span class="sxs-lookup"><span data-stu-id="654c8-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="654c8-152">Per **Applicato a**, fare clic sulla freccia in giù, quindi fare clic su **Il dominio del destinatario è**.</span><span class="sxs-lookup"><span data-stu-id="654c8-152">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="654c8-153">Nella finestra fare clic sul nome dell'organizzazione, ad esempio contoso.onmicrosoft.com, e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="654c8-153">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="654c8-154">Fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="654c8-154">Click **Save**.</span></span> <span data-ttu-id="654c8-155">Dopo l'aggiornamento, dovrebbe essere visualizzato il blocco nuovo e abilitato per i **criteri degli allegati sicuri**.</span><span class="sxs-lookup"><span data-stu-id="654c8-155">After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="654c8-156">Fare clic sulla scheda **collegamenti sicuri** e quindi fare clic sul segno più.</span><span class="sxs-lookup"><span data-stu-id="654c8-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="654c8-157">Nella finestra **nuovi criteri collegamenti sicuri**, in **Nome**, digitare **Criteri collegamenti sicuri**.</span><span class="sxs-lookup"><span data-stu-id="654c8-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="654c8-158">Per **Seleziona l'azione da eseguire quando vengono rilevati URL sconosciuti potenzialmente dannosi nei messaggi**, fare clic su **Attiva**, quindi selezionare **Non consentire clickthrough all'URL originale da parte degli utenti**.</span><span class="sxs-lookup"><span data-stu-id="654c8-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="654c8-159">Per **Applicato a**, fare clic sulla freccia in giù, quindi fare clic su **Il dominio del destinatario è**.</span><span class="sxs-lookup"><span data-stu-id="654c8-159">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="654c8-160">Nella finestra fare clic sul nome dell'organizzazione, ad esempio contoso.onmicrosoft.com, e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="654c8-160">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="654c8-p108">Fare clic su **Salva**. Verrà visualizzato il nuovo **criterio collegamenti sicuri** abilitato.</span><span class="sxs-lookup"><span data-stu-id="654c8-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="654c8-163">Fase 4: dimostrazione di ATP in azione</span><span class="sxs-lookup"><span data-stu-id="654c8-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="654c8-164">In questa fase, viene mostrato come ATP si occupa dei messaggi di posta elettronica potenzialmente dannosi.</span><span class="sxs-lookup"><span data-stu-id="654c8-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="654c8-165">Dall'istanza di Internet Explorer utilizzata per inviare il messaggio di posta elettronica nella fase 2, nella barra di spostamento sinistra fare clic su **elementi inviati.**</span><span class="sxs-lookup"><span data-stu-id="654c8-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="654c8-166">Fare clic sul messaggio di posta elettronica intitolato le **nuove chiavi**, fare clic sull'icona freccia in giù e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="654c8-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="654c8-167">Per il nuovo messaggio, in **A**, digitare l'indirizzo di posta elettronica dell'amministratore globale di Office 365 della sottoscrizione di valutazione, quindi fare clic su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="654c8-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="654c8-168">Fare clic sul **sito Web di nuovo viaggio**di posta elettronica dal titolo, fare clic sull'icona freccia in giù, fare clic su **Rispondi a tutto**e quindi su **Invia**.</span><span class="sxs-lookup"><span data-stu-id="654c8-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="654c8-p109">Dall'istanza di Internet Explorer utilizzata per configurare i criteri ATP nella fase 3, fare clic sulla scheda dell'interfaccia di amministrazione di Exchange, selezionare il riquadro delle app e infine fare clic su **Posta**. Vengono visualizzati due nuovi messaggi di posta elettronica nella Posta in arrivo:</span><span class="sxs-lookup"><span data-stu-id="654c8-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="654c8-171">Uno dal titolo **Fw: Nuove chiavi**</span><span class="sxs-lookup"><span data-stu-id="654c8-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="654c8-172">Uno dal titolo **Fw: Nuovo sito Web di viaggi**</span><span class="sxs-lookup"><span data-stu-id="654c8-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="654c8-173">Aprire il messaggio di posta elettronica dal titolo **FW: nuovo sito Web di viaggio** e fare clic sul collegamento **sito** .</span><span class="sxs-lookup"><span data-stu-id="654c8-173">Open the email message titled **Fw: New travel web site** and click the **this site** link.</span></span> <span data-ttu-id="654c8-174">Dovrebbe essere visualizzato un "questo sito Web è stato classificato come dannoso".</span><span class="sxs-lookup"><span data-stu-id="654c8-174">You should see a "This website has been classified as malicious."</span></span> <span data-ttu-id="654c8-175">video.</span><span class="sxs-lookup"><span data-stu-id="654c8-175">page.</span></span> <span data-ttu-id="654c8-176">Questo dimostra che ATP impedisce di accedere al sito Web potenzialmente dannoso.</span><span class="sxs-lookup"><span data-stu-id="654c8-176">This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="654c8-177">Nella scheda dell'interfaccia di amministrazione di Exchange di Internet Explorer, nella barra di spostamento a sinistra, fare clic su **flusso di posta**.</span><span class="sxs-lookup"><span data-stu-id="654c8-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="654c8-178">Fare clic sulla scheda **Traccia messaggio** e quindi fare clic su **ricerca**.</span><span class="sxs-lookup"><span data-stu-id="654c8-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="654c8-179">Nella finestra **Risultati traccia messaggi**, fare doppio clic sul messaggio con l'oggetto **Nuove chiavi**.</span><span class="sxs-lookup"><span data-stu-id="654c8-179">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**.</span></span> <span data-ttu-id="654c8-180">Questo messaggio è stato correttamente recapitato nella posta in arrivo.</span><span class="sxs-lookup"><span data-stu-id="654c8-180">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="654c8-181">Chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="654c8-181">Close this window.</span></span>
    
10. <span data-ttu-id="654c8-182">Fare doppio clic sul messaggio con l'oggetto **Nuovo sito Web di viaggi**.</span><span class="sxs-lookup"><span data-stu-id="654c8-182">Double-click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="654c8-183">Questo messaggio è stato correttamente recapitato nella posta in arrivo.</span><span class="sxs-lookup"><span data-stu-id="654c8-183">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="654c8-184">Chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="654c8-184">Close this window.</span></span>
    
11. <span data-ttu-id="654c8-185">Fare doppio clic sul messaggio con l'oggetto **Fw: Nuove chiavi**.</span><span class="sxs-lookup"><span data-stu-id="654c8-185">Double-click the message with the subject **Fw: Your new keys**.</span></span> <span data-ttu-id="654c8-186">Tenere presente che il messaggio è stato elaborato da ATP e quindi recapitato nella posta in arrivo.</span><span class="sxs-lookup"><span data-stu-id="654c8-186">Note how this message was processed by ATP and then delivered to the Inbox.</span></span> <span data-ttu-id="654c8-187">Chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="654c8-187">Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="654c8-188">Lo scopo del criterio degli allegati sicuri consisteva nell'avviare l'analisi degli allegati per il codice dannoso.</span><span class="sxs-lookup"><span data-stu-id="654c8-188">The purpose of the safe attachments policy was to begin scanning attachments for malicious code.</span></span> <span data-ttu-id="654c8-189">L'allegato getKeys. js è stato consentito perché non è stato determinato come dannoso.</span><span class="sxs-lookup"><span data-stu-id="654c8-189">The getKeys.js attachment was allowed because it was not determined to be malicious.</span></span> <span data-ttu-id="654c8-190">In questo passaggio viene mostrato che ATP ha eseguito un'analisi dell'allegato.</span><span class="sxs-lookup"><span data-stu-id="654c8-190">This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="654c8-191">Fare doppio clic sul messaggio con l'oggetto **Fw: Nuovo sito Web di viaggi**.</span><span class="sxs-lookup"><span data-stu-id="654c8-191">Double-click the message with the subject **Fw: New travel web site**.</span></span> <span data-ttu-id="654c8-192">Tenere presente che il messaggio è stato correttamente recapitato nella posta in arrivo.</span><span class="sxs-lookup"><span data-stu-id="654c8-192">Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="654c8-193">È ora possibile utilizzare questo ambiente per creare nuovi criteri e sperimentare ATP.</span><span class="sxs-lookup"><span data-stu-id="654c8-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="654c8-194">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli nella serie di guide dei lab di test di Office 365.</span><span class="sxs-lookup"><span data-stu-id="654c8-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="654c8-195">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="654c8-195">See Also</span></span>

[<span data-ttu-id="654c8-196">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="654c8-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="654c8-197">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="654c8-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="654c8-198">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="654c8-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="654c8-199">DirSync per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="654c8-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="654c8-200">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="654c8-200">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="654c8-201">Protezione avanzata dalle minacce per allegati e collegamenti sicuri</span><span class="sxs-lookup"><span data-stu-id="654c8-201">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


