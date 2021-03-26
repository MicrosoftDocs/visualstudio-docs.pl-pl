---
title: Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła
description: Dowiedz się więcej na temat ciągów, które są kluczami służącymi do uzyskiwania dostępu do rejestru, aby znaleźć informacje o dodatku kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b61c13973ac6668814fbc3ba076b373d6e0b1e44
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056301"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła
Następujące ciągi są kluczami służącymi do uzyskiwania dostępu do rejestru w celu znalezienia informacji o wtyczce kontroli źródła.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` i `STR_SCCPROVIDERNAME` są kluczami rejestru lub wartościami używanymi do rejestrowania biblioteki DLL jako wtyczki kontroli źródła dla programu Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` i `SCC_STATUS_FILE` są używane do opisywania formatu MSSCCPRJ. Plik SCC.

## <a name="string-keys-and-values"></a>Klucze i wartości ciągów

|Klucz|Wartość|
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
|`SCC_NSE`|Rozszerzenie przestrzeni nazw|
|`SCC_NSE_PREFIX`|Prefiks Protocal|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
