---
title: Configurare gruppi e utenti per un ambiente di sviluppo/test per la campagna politica
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Riepilogo: Creare Office 365 e mobilità aziendale + sottoscrizioni di valutazione di sicurezza (EMS) con gli utenti e gruppi per un ambiente di sviluppo e di testing politici campagne."
ms.openlocfilehash: e876c8770651c3f23c06c9c499bdaabca52da353
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>Configurare gruppi e utenti per un ambiente di sviluppo/test per la campagna politica

 **Riepilogo:** Creazione di Office 365 e mobilità aziendale + sottoscrizioni di valutazione di sicurezza (EMS) con gli utenti e gruppi per un ambiente di sviluppo e di testing politici campagne.
  
Utilizzare le istruzioni riportate in questo articolo per creare un ambiente di sviluppo e di testing che include gli account utente semplificata e gruppi per la soluzione [Microsoft Security Guidance for campagne politici, ricchi e altre organizzazioni Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) .
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: creare l'ambiente di sviluppo/test di Office 365

In questa fase per ottenere le sottoscrizioni di valutazione di Office 365 E5 e mobilità aziendale + E5 di sicurezza (EMS) per le organizzazioni che rappresenta una campagna politica fittizia.
  
Per prima cosa, seguire le istruzioni nella **fase 2** dell' [ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md).
  
Successivamente, Esegui l'iscrizione per la sottoscrizione di prova EMS E5 e come aggiungerla alla stessa organizzazione la sottoscrizione di prova di Office 365.
  
1. Se necessario, accedere al portale di Office 365 con le credenziali dell'account amministratore globale della sottoscrizione di prova. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Fare clic sul riquadro **Amministratore**.
    
3. Scheda di **interfaccia di amministrazione di Office** nel browser, nel riquadro di spostamento sinistra fare clic su **fatturazione > servizi di acquisto**.
    
4. Nella pagina **servizi di acquisto** individuare l'elemento di **sicurezza E5 + mobilità aziendale** . Posizionare il puntatore del mouse su di esso e fare clic su **Start versione di valutazione gratuita**.
    
5. Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.
    
6. Nella pagina **Ricevuta ordine**, fare clic su **Continua**.
    
Successivamente, abilitare la licenza E5 EMS per l'account amministratore globale.
  
1. Nella scheda **Centro di amministrazione di Office 365** nel browser, nel riquadro di spostamento sinistra fare clic su **utenti > utenti attivi**.
    
2. Fare clic sull'account di amministratore globale e quindi fare clic su **Modifica** per **le licenze del prodotto**.
    
3. Nel riquadro di **licenze per i prodotti** , attivare la licenza del prodotto per la **mobilità aziendale + E5 di sicurezza** per **in**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>Fase 2: Creare e configurare i gruppi di Azure Active Directory (AD)

In questa fase, vengono creati e configurati i gruppi di Azure AD per la campagna.
  
Creare innanzitutto un insieme di gruppi per una campagna politico tipica con il portale di Azure.
  
1. In una scheda distinta nel browser, accedere al portale di Azure in [https://portal.azure.com](https://portal.azure.com). Se necessario, accedere con le credenziali dell'account amministratore globale per la sottoscrizione di valutazione di Office 365 E5.
    
2. Nel portale di Azure, fare clic su **Azure Active Directory > utenti e gruppi > tutti i gruppi di**.
    
3. Eseguire la procedura seguente per ogni nome di gruppo in questo elenco:
    
  - Personale senior e strategico
    
  - Personale IT
    
  - Personale di analisi
    
  - Personale di base regolare
    
  - Personale delle operazioni
    
  - Personale di campo
    
1. Su blade **tutti i gruppi** , fare clic su **+ nuovo gruppo**.
    
2. Digitare il nome del gruppo dall'elenco **nome**.
    
3. Selezionare **utente dinamica** di **appartenenza**.
    
4. Fare clic su **Sì** per **caratteristiche di attivare Office**.
    
5. Fare clic su **Add query dinamica**.
    
6. In **aggiungere gli utenti cui**, selezionare **reparto**.
    
7. Nel campo successivo, selezionare **è uguale a**.
    
8. Nel campo successivo, digitare il nome del gruppo dall'elenco.
    
9. Fare clic su **Add query**e quindi fare clic su **Crea**.
    
10. Fare clic su **utenti e gruppi: tutti i gruppi**.
    
Punto, configurare i gruppi in modo che i membri vengono assegnati automaticamente le licenze di Office 365 E5 ed EMS E5.
  
1. Nel portale di Azure, fare clic su **Azure Active Directory > licenze > tutti i prodotti**.
    
2. Nell'elenco, selezionare **mobilità aziendale + sicurezza E5** e **Office 365 Enterprise E5**e quindi fare clic su **+ assegnare**.
    
3. In blade **assegnare licenze** , fare clic su **utenti e gruppi**.
    
4. Nell'elenco dei gruppi, selezionare quanto segue:
    
  - Personale di analisi
    
  - Personale di campo
    
  - Personale IT
    
  - Personale delle operazioni
    
  - Personale di base regolare
    
  - Personale senior e strategico
    
5. Fare clic su **Seleziona**e quindi fare clic su **Assegna**.
    
6. Chiudere la scheda del portale di Azure nel browser.
    
## <a name="phase-3-add-your-user-accounts"></a>Fase 3: Aggiungere gli account utente

In questa fase, si aggiungono gli account utente di esempio per la campagna politica.
  
Innanzitutto, si [Connetti con il modulo di Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Successivamente, inserire il nome dell'organizzazione, la posizione e una password comune; eseguire quindi questi comandi dal prompt dei comandi di PowerShell o Integrated Script Environment (ISE):
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> L'utilizzo di una password di comune è per l'automazione e semplicità di configurazione per un ambiente di sviluppo e di testing. Ciò non è consigliata per le sottoscrizioni di produzione. Come si accede con ognuno di questi nuovi account utente, verrà richiesto di modificare la password. 
  
Seguire questi passaggi per verificare che l'appartenenza ai gruppi dinamici e le licenze basate su gruppi funzionino correttamente.
  
1. Nella scheda **Home page di Microsoft Office** del browser, fare clic su tessera di **amministrazione** .
    
2. Dalla nuova scheda di **interfaccia di amministrazione di Office** del browser, fare clic su **utenti**.
    
3. Nell'elenco di utenti, fare clic su **candidato**.
    
4. Nel riquadro in cui sono elencati le proprietà dell'account utente **Candidate** , verificare che:
    
  - È un membro del gruppo **Senior e personale strategico** (in **appartenenza a gruppi**).
    
  - È stata assegnata la **mobilità aziendale + sicurezza E5** e **Office 365 Enterprise E5** licenze ( **licenze per i prodotti**).
    
5. Chiudere il riquadro di account utente **candidato** .
    
## <a name="record-values-for-future-reference"></a>Registrare i valori per consultarli in futuro

Registrare questi valori per utilizzarli con le sottoscrizioni di valutazione di Office 365 ed EMS per questo ambiente di sviluppo/test:
  
- Nome dell'organizzazione della sottoscrizione di valutazione: _______________________________________________  
    
    Ad esempio, per il nome di dominio della sottoscrizione di valutazione di contoso.onmicrosoft.com, il nome dell'azienda è "contoso".
    
- Il nome di amministratore globale di Office 365: ___.onmicrosoft.com
    
    Registrare la password per questo account e la password iniziale comune per gli altri account utente in un luogo sicuro.
    
## <a name="next-step"></a>Passaggio successivo

Creare quattro diversi tipi di siti del team SharePoint Online in questo ambiente di sviluppo e di testing e [creare siti del team in un ambiente di sviluppo e di testing politici campagne](create-team-sites-in-a-political-campaign-dev-test-environment.md).
  
## <a name="see-also"></a>Vedere anche

[Guida sulla sicurezza Microsoft per organizzazioni che si occupano della campagna politica, no profit e altre organizzazioni agili](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Creare siti del team in un ambiente di sviluppo e di testing campagne politici](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)




