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
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Elenca gli attributi che sono esclusi e supportati dallo strumento IdFix.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085085"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Oggetti e attributi esclusi e supportati di IdFix
Sono disponibili due insiemi di regole mantenute da IdFix; Multi-tenant e Dedicati/ITAR. A questo punto, le due regole impostate escludono gli stessi oggetti, attributi e valori di attributi dalla ricerca. Ciò potrebbe cambiare nelle versioni future.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Esclusione errori Multi-tenant e Dedicati utilizzate da IdFix
In questa sezione vengono elencati gli oggetti, gli attributi e i valori che IdFix esclude dalla ricerca della directory. L'asterisco (\*) è un carattere jolly che può essere sostituito da altri caratteri.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Oggetti, attributi e valori esclusi durante una ricerca IdFix

|**Esclusione**|**Esempio**|
|:-----|:-----|
|Scelta\* |Amministratore |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-Link |
|IUSR\* |IUSR _ *machineName* |
|IWAM\*  |IWAM_ *nomecomputer* |
|MSOL\* |MSOL_AD_SYNC |
|supporto\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinto contiene "\0ACNF:"|"\0ACNF: *GUID* " |
|L'oggetto contiene l'attributo IsCriticalSystemObject |Vedere [attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Oggetti e attributi Multi-Tenant e Dedicati verificati da IdFix
Gli attributi che vengono controllati per gli errori da IdFix sono descritti nella sezione "preparazione degli attributi e degli oggetti directory" in [Prepare Directory Attributes for Synchronization with Office 365 by using the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md).
  

