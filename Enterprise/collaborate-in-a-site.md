---
title: Collaborare con gli utenti in un sito
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Informazioni su come collaborare con gli utenti in un sito di SharePoint.
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017314"
---
# <a name="collaborate-with-guests-in-a-site"></a>Collaborare con gli utenti in un sito

Se è necessario collaborare con gli utenti tra documenti, dati ed elenchi, è possibile utilizzare un sito di SharePoint. I siti di SharePoint moderni sono connessi a gruppi di Office 365 che possono gestire l'appartenenza al sito e fornire strumenti di collaborazione aggiuntivi quali una cassetta postale condivisa e un calendario.

In questo articolo verranno illustrati i passaggi di configurazione di Microsoft 365 necessari per configurare un sito di SharePoint per la collaborazione con gli utenti.

## <a name="azure-organizational-relationships-settings"></a>Impostazioni delle relazioni organizzative di Azure

La condivisione in Microsoft 365 è regolata al livello più alto dalle impostazioni delle relazioni organizzative in Azure Active Directory. Se la condivisione Guest è disabilitata o limitata in Azure AD, queste verranno sostituite da tutte le impostazioni di condivisione configurate in Microsoft 365.

Controllare le impostazioni delle relazioni organizzative per garantire che la condivisione con gli ospiti non sia bloccata.

![Schermata della pagina delle impostazioni delle relazioni organizzative di Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

Per impostare le impostazioni delle relazioni organizzative

1. Accedere a Microsoft Azure all'indirizzo [https://portal.azure.com](https://portal.azure.com).
2. Nel riquadro di spostamento a sinistra, fare clic su **Azure Active Directory**.
3. Nel riquadro **Panoramica** fare clic su **relazioni organizzative**.
4. Nel riquadro **relazioni organizzative** fare clic su **Impostazioni**.
5. Verificare che **gli amministratori e gli utenti del ruolo invitato ospite possano invitare** e che **i membri possano invitare** siano entrambi impostati su **Sì**.
6. Se sono state apportate modifiche, fare clic su **Salva**.

Prendere nota delle impostazioni nella sezione **vincoli di collaborazione** . Verificare che i domini degli utenti con cui si desidera collaborare non siano bloccati.

## <a name="office-365-groups-guest-settings"></a>Office 365 gruppi Guest Settings

I siti di SharePoint moderni utilizzano i gruppi di Office 365 per controllare l'accesso al sito. Le impostazioni di Office 365 groups Guest devono essere attivate affinché l'accesso guest in siti di SharePoint funzioni.

![Schermata di Office 365 gruppi Guest Settings in Microsoft 365 Admin Center](media/office-365-groups-guest-settings.png)

Per impostare le impostazioni di Office 365 groups Guest

1. Nell'interfaccia di amministrazione di Microsoft 365, nel riquadro di spostamento a sinistra, espandere **Impostazioni**.
2. Fare clic su **servizi & componenti**aggiuntivi.
3. Nell'elenco, fare clic su **gruppi di Office 365**.
4. Verificare che i membri del gruppo Consenti al di **fuori dell'organizzazione accedano al contenuto del gruppo** e che i proprietari del **gruppo aggiungano persone all'esterno dell'organizzazione ai gruppi di caselle di** controllo siano entrambe controllate.
5. Se sono state apportate modifiche, fare clic su **Salva modifiche**.


## <a name="sharepoint-organization-level-sharing-settings"></a>Impostazioni di condivisione a livello di organizzazione di SharePoint

Affinché gli utenti dispongano dell'accesso ai siti di SharePoint, le impostazioni di condivisione a livello dell'organizzazione di SharePoint devono consentire la condivisione con gli utenti.

Le impostazioni a livello di organizzazione determinano le impostazioni disponibili per i singoli siti. Le impostazioni del sito non possono essere più permissive rispetto alle impostazioni a livello di organizzazione.

Se si desidera consentire la condivisione di file e cartelle con utenti anonimi, scegliere **nessuno**. Se si desidera garantire che tutti gli utenti siano in grado di eseguire l'autenticazione, scegliere **clienti nuovi ed esistenti**. Scegliere l'impostazione più permissiva che sarà necessaria per qualsiasi sito dell'organizzazione.

![Schermata delle impostazioni di condivisione a livello di organizzazione di SharePoint](media/sharepoint-organization-external-sharing-controls.png)


Per impostare le impostazioni di condivisione a livello di organizzazione di SharePoint

1. Nell'interfaccia di amministrazione di Microsoft 365, nella barra di spostamento a sinistra, in interfaccia di **Amministrazione**, fare clic su **SharePoint**.
2. Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento a sinistra, fare clic su **condivisione**.
3. Assicurarsi che la condivisione esterna per SharePoint sia impostata su **tutti gli utenti** o **gli ospiti nuovi e esistenti**.
4. Se sono state apportate modifiche, fare clic su **Salva**.

## <a name="create-a-site"></a>Creare un sito

Il passaggio successivo consiste nel creare il sito che si intende utilizzare per la collaborazione con gli utenti.

Per creare un sito
1. Nell'interfaccia di amministrazione di SharePoint, in **siti**, fare clic su **siti attivi**.
2. Fare clic su **Crea**.
3. Fare clic su **sito del team**.
4. Digitare il nome di un sito e immettere un nome per il proprietario del gruppo (proprietario del sito).
5. In **Impostazioni avanzate**scegliere se si desidera che sia un sito pubblico o privato.
6. Fare clic su **Avanti**.
7. Fare clic su **Fine**.

Gli utenti verranno invitati in un secondo momento. Successivamente, è importante controllare le impostazioni di condivisione a livello di sito per il sito.

## <a name="sharepoint-site-level-sharing-settings"></a>Impostazioni di condivisione a livello di sito di SharePoint

Controllare le impostazioni di condivisione a livello di sito per assicurarsi che consentano il tipo di accesso desiderato per il sito. Ad esempio, se si impostano le impostazioni a livello di organizzazione per tutti gli **utenti**, ma si desidera che tutti gli ospiti eseguano l'autenticazione per questo sito, assicurarsi che le impostazioni di condivisione a livello di sito siano impostate su **ospiti nuovi e esistenti**.

Si noti che il sito non può essere condiviso con utenti anonimi (impostazione**chiunque** ), ma è possibile eseguire singoli file e cartelle.

![Schermata delle impostazioni di condivisione esterna del sito di SharePoint](media/sharepoint-site-external-sharing-settings.png)

Per impostare le impostazioni di condivisione a livello di sito
1. Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento sinistra, espandere **siti** e fare clic su **siti attivi**.
2. Selezionare il sito appena creato.
3. Sulla barra multifunzione fare clic su **condivisione**.
4. Verificare che la condivisione sia impostata su **tutti gli utenti** o **gli ospiti nuovi e esistenti**.
5. Se sono state apportate modifiche, fare clic su **Salva**.

## <a name="invite-users"></a>Invitare gli utenti

Le impostazioni di condivisione Guest sono ora configurate, quindi è possibile iniziare ad aggiungere utenti interni e ospiti al sito. L'accesso al sito è controllato tramite il gruppo Office 365 associato, quindi verranno aggiunti gli utenti.

Per invitare gli utenti interni a un gruppo
1. Passare al sito in cui si desidera aggiungere gli utenti.
2. Fare clic su **membri** in alto a destra.
3. Fare clic su **Aggiungi membri**.
4. Digitare i nomi o gli indirizzi di posta elettronica degli utenti che si desidera invitare al sito e quindi fare clic su **Salva**.

Gli utenti guest non possono essere aggiunti dal sito. È necessario aggiungerli utilizzando Outlook sul Web.

Per invitare gli ospiti a un sito
1. In **gruppi**, in Outlook sul Web, fare clic sul gruppo in cui si desidera aggiungere i membri.
2. Aprire la scheda contatto di gruppo e quindi, in **altre opzioni** (...), fare clic su **Aggiungi membri**.
3. Digitare gli indirizzi di posta elettronica degli utenti che si desidera invitare e quindi fare clic su **Aggiungi**.
4. Fare clic su **Chiudi**.

## <a name="see-also"></a>Vedere anche