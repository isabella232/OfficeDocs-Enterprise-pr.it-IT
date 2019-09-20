---
title: Collaborare con gli utenti in un documento
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Informazioni su come collaborare con gli utenti di un documento in SharePoint e OneDrive.
ms.openlocfilehash: c0c74f2457e9b25b37355c58ed18f120261e3364
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992405"
---
# <a name="collaborate-with-guests-on-a-document"></a>Collaborare con gli utenti in un documento

Se è necessario collaborare con gli ospiti nei documenti di SharePoint o OneDrive, è possibile inviare un collegamento di condivisione al documento. In questo articolo verranno illustrati i passaggi di configurazione di Microsoft 365 necessari per configurare i collegamenti di condivisione per SharePoint e OneDrive.

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

## <a name="sharepoint-organization-level-sharing-settings"></a>Impostazioni di condivisione a livello di organizzazione di SharePoint

Affinché gli utenti dispongano dell'accesso a un documento in SharePoint o OneDrive, è necessario che le impostazioni di condivisione a livello di organizzazione di SharePoint e OneDrive consentano la condivisione con gli utenti.

Le impostazioni a livello di organizzazione per SharePoint determinano le impostazioni disponibili per i singoli siti di SharePoint. Le impostazioni del sito non possono essere più permissive rispetto alle impostazioni a livello di organizzazione. L'impostazione a livello di organizzazione per OneDrive determina il livello di condivisione disponibile nelle raccolte OneDrive degli utenti.

Per SharePiont e OneDrive, se si desidera consentire la condivisione di file e cartelle con utenti anonimi, scegliere **chiunque**. Se si desidera garantire che tutti gli utenti siano in grado di eseguire l'autenticazione, scegliere **clienti nuovi ed esistenti**. 

Per SharePoint, scegliere l'impostazione più permissiva che sarà necessaria per qualsiasi sito dell'organizzazione.

![Schermata delle impostazioni di condivisione a livello di organizzazione di SharePoint](media/sharepoint-organization-external-sharing-controls.png)


Per impostare le impostazioni di condivisione a livello di organizzazione di SharePoint

1. Nell'interfaccia di amministrazione di Microsoft 365, nella barra di spostamento a sinistra, in interfaccia di **Amministrazione**, fare clic su **SharePoint**.
2. Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento a sinistra, fare clic su **condivisione**.
3. Verificare che la condivisione esterna per SharePoint o OneDrive sia impostata su chiunque o su un **utente** **nuovo o esistente**. Si noti che l'impostazione di OneDrive non può essere più permissiva dell'impostazione di SharePoint.
4. Se sono state apportate modifiche, fare clic su **Salva**.

## <a name="sharepoint-organization-level-default-link-settings"></a>Impostazioni di collegamento predefinite a livello di organizzazione di SharePoint

Le impostazioni predefinite per il collegamento di file e cartelle determinano l'opzione di collegamento visualizzata all'utente per impostazione predefinita quando condividono un file o una cartella. Gli utenti possono modificare il tipo di collegamento in una delle altre opzioni prima della condivisione, se necessario.

Tenere presente che questa impostazione influisce sui siti di SharePoint nell'organizzazione, nonché OneDrive.

Scegliere il tipo di collegamento selezionato per impostazione predefinita quando gli utenti condividono file e cartelle:

- **Tutti gli utenti con il collegamento** : scegliere questa opzione se si prevede di condividere un gran quantità di file e cartelle in modo anonimo. Se si desidera consentire collegamenti a *tutti gli utenti* , ma sono preoccupati per la condivisione accidentale anonima, prendere in considerazione una delle altre opzioni come impostazione predefinita. Questo tipo di collegamento è disponibile solo se è stata abilitata la condivisione di **utenti** .
- **Solo persone nell'organizzazione** : scegliere questa opzione se si prevede che la maggior parte della condivisione di file e cartelle sia con le persone all'interno dell'organizzazione.
- **Persone specifiche** : considerare questa opzione se si prevede di eseguire un sacco di condivisione di file e cartelle con gli utenti. Questo tipo di collegamento è compatibile con gli utenti e richiede l'autenticazione.
 
![Schermata di impostazioni di condivisione di file e cartelle a livello di organizzazione di SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


Per impostare le impostazioni dei collegamenti predefiniti a livello di organizzazione di SharePoint e OneDrive

1. Passare alla pagina condivisione nell'interfaccia di amministrazione di SharePoint.
2. In **collegamenti a file e cartelle**selezionare il collegamento di condivisione predefinito che si desidera utilizzare.
3. Se sono state apportate modifiche, fare clic su **Salva**.

## <a name="sharepoint-site-level-sharing-settings"></a>Impostazioni di condivisione a livello di sito di SharePoint

Se si condividono file e fodlers che si trovano in un sito di SharePoint, è necessario controllare anche le impostazioni di condivisione a livello di sito per il sito.

![Schermata delle impostazioni di condivisione esterna del sito di SharePoint](media/sharepoint-site-external-sharing-settings.png)

Per impostare le impostazioni di condivisione a livello di sito
1. Nell'interfaccia di amministrazione di SharePoint, nella barra di spostamento sinistra, espandere **siti** e fare clic su **siti attivi**.
2. Selezionare il sito appena creato.
3. Sulla barra multifunzione fare clic su **condivisione**.
4. Verificare che la condivisione sia impostata su **tutti gli utenti** o **gli ospiti nuovi e esistenti**.
5. Se sono state apportate modifiche, fare clic su **Salva**.

## <a name="invite-users"></a>Invitare gli utenti

Le impostazioni di condivisione Guest sono ora configurate, quindi gli utenti possono ora condividere file e cartelle con gli ospiti. Per ulteriori informazioni, vedere [condivisione di file e cartelle di OneDrive](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) e [condivisione di file o cartelle di SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) .

## <a name="see-also"></a>Vedere anche