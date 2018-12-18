---
title: Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 693f4560d181aa765946bdd971f835ee651daed1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759952"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następujące ciągi są klucze służące do uzyskiwania dostępu do rejestru, aby znaleźć informacje o kontroli źródła wtyczek.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, i `STR_SCCPROVIDERNAME` kluczy rejestru i wartości używane do rejestrowania biblioteki DLL jako wtyczka do kontroli źródła dla programu Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, i `SCC_STATUS_FILE` są używane do opisywania formatu MSSCCPRJ. Plik SCC.  
  
## <a name="string-keys-and-values"></a>Ciąg kluczy i wartości  
  
|Key|Wartość|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Kontrola kodu źródłowego|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|  
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ. SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|Plik kontroli kodu źródłowego|  
|`SCC_NSE`|Rozszerzenie Namespace|  
|`SCC_NSE_PREFIX`|Prefiks od protokołu|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)   
 [Porady: Instalowanie wtyczki kontroli źródła](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)

