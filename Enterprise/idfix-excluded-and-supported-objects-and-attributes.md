---
title: Oggetti e attributi esclusi e supportati di IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Vengono elencati gli attributi esclusi e supportati dallo strumento IdFix.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541266"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Oggetti e attributi esclusi e supportati di IdFix
Sono disponibili due insiemi di regole mantenute da IdFix; Multi-tenant e Dedicati/ITAR. A questo punto, le due regole impostate escludono gli stessi oggetti, attributi e valori di attributi dalla ricerca. Ciò potrebbe cambiare nelle versioni future.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Esclusione errori Multi-tenant e Dedicati utilizzate da IdFix
In questa sezione sono elencati oggetti, attributi e valori IdFix esclude la ricerca di directory. L'asterisco (\*) è un carattere jolly che può essere sostituito da altri caratteri.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Oggetti, attributi e valori esclusi durante una ricerca IdFix

|**Esclusione**|**Esempio**|
|:-----|:-----|
|Sfrutti\* |Amministratore |
|{CAS_\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |Collegamento ms-DS KrbTgt |
|IUSR _\* |IUSR _ *machinename* |
|IWAM\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contiene "\0ACNF:"|"\0ACNF: *GUID* " |
|L'oggetto contiene l'attributo IsCriticalSystemObject |Vedere [attributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Oggetti e attributi Multi-Tenant e Dedicati verificati da IdFix
Nella sezione "Oggetti e attributi preparazione Directory" in [Prepare gli attributi di directory per la sincronizzazione con Office 365 tramite lo strumento IdFix](prepare-directory-attributes-for-synch-with-idfix.md)sono descritti gli attributi che vengono controllati per gli errori da IdFix.
  

