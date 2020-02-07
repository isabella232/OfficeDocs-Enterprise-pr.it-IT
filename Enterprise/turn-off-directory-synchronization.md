---
title: Disattivare la sincronizzazione della directory per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Informazioni su come utilizzare PowerShell per disattivare la sincronizzazione della directory per Office 365
ms.openlocfilehash: eab736241372b2d1b6023dc803dff540dded64ae
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841013"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Disattivare la sincronizzazione della directory per Office 365
È possibile utilizzare PowerShell per disattivare la sincronizzazione della directory. Tuttavia, non è consigliabile disattivare la sincronizzazione della directory come passaggio per la risoluzione dei problemi. Se si necessita di assistenza per la risoluzione dei problemi relativi alla sincronizzazione della directory, vedere l'articolo [relativo alla correzione della sincronizzazione della directory per Office 365](fix-problems-with-directory-synchronization.md) . 
  
Se necessario, [contattare il supporto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti aziendali.
  
## <a name="turn-off-directory-synchronization"></a>Disattivare la sincronizzazione della directory  
Per disattivare la sincronizzazione della directory:
  
1. Innanzitutto, installare il software necessario e connettersi alla sottoscrizione di Office 365. Per istruzioni, vedere [connessione con il modulo di Microsoft Azure Active Directory per Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Utilizzare [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) per disabilitare la sincronizzazione della directory: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
