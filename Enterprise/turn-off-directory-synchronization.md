---
title: Disattiva la sincronizzazione della directory per Microsoft 365
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
description: Informazioni su come utilizzare PowerShell per disattivare la sincronizzazione della directory per Microsoft 365
ms.openlocfilehash: 935d7e26c7b99aba876500e6b9d428557aed5b9c
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906209"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Disattiva la sincronizzazione della directory per Microsoft 365
È possibile utilizzare PowerShell per disattivare la sincronizzazione della directory. Tuttavia, non è consigliabile disattivare la sincronizzazione della directory come passaggio per la risoluzione dei problemi. Se si necessita di assistenza per la risoluzione dei problemi relativi alla sincronizzazione della directory, vedere l'articolo [relativo alla correzione della sincronizzazione della directory per Microsoft 365](fix-problems-with-directory-synchronization.md) . 
  
Se necessario, [contattare il supporto](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per i prodotti aziendali.
  
## <a name="turn-off-directory-synchronization"></a>Disattivare la sincronizzazione della directory  
Per disattivare la sincronizzazione della directory:
  
1. Innanzitutto, installare il software necessario e connettersi alla sottoscrizione Microsoft 365. Per istruzioni, vedere [connessione con il modulo di Microsoft Azure Active Directory per Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Utilizzare [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) per disabilitare la sincronizzazione della directory: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
