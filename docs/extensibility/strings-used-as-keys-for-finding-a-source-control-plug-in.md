---
title: Ciągi używane jako klucze do znalezienia wtyczki kontroli źródła
description: Dowiedz się więcej o ciągach, które są kluczami dostępu do rejestru, aby znaleźć informacje o wtyczce kontroli kodu źródłowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f25a105c442fa4a1ff8ed0f95b9c49272d751932
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899388"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła
Następujące ciągi to klucze służące do uzyskiwania dostępu do rejestru w celu znalezienia informacji o wtyczce kontroli źródła.

 `STR_SCC_PROVIDER_REG_LOCATION`, , i są kluczami rejestru lub wartościami używanymi do rejestrowania bibliotek DLL jako wtyczki kontroli źródła dla `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH` `STR_SCCPROVIDERNAME` Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE` , i są używane `SCC_STATUS_FILE` do opisywania formatu MSSCCPRJ. Plik SCC.

## <a name="string-keys-and-values"></a>Klucze ciągów i wartości

|Klucz|Wartość|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|Sccserverpath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Kontrola kodu źródłowego|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|Scc|
|`SCC_FILE_SIGNATURE`|Plik kontroli kodu źródłowego|
|`SCC_NSE`|Rozszerzenie przestrzeni nazw|
|`SCC_NSE_PREFIX`|Prefiks protokalny|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
