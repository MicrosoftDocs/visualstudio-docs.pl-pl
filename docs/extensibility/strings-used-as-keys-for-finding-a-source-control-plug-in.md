---
title: Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699712"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła
Następujące ciągi są klucze dostępu do rejestru, aby znaleźć informacje o dodatku plug-in kontroli źródła.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH`i `STR_SCCPROVIDERNAME` są klucze rejestru lub wartości używane do rejestrowania biblioteki DLL jako wtyczki kontroli źródła dla programu Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE`, `SCC_STATUS_FILE` i są używane do opisania formatu MSSCCPRJ. SCC.

## <a name="string-keys-and-values"></a>Klucze i wartości ciągu

|Klucz|Wartość|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Oprogramowanie\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey (DostawcaRegKey)|
|`STR_SCCPROVIDERPATH`|Sccserverpath|
|`STR_SCCPROVIDERNAME`|Nazwa SCCServer|
|`STR_SCC_INI_SECTION`|Kontrola kodu źródłowego|
|`STR_SCC_INI_KEY`|ŹródłoKontroliControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|Scc|
|`SCC_FILE_SIGNATURE`|Plik kontroli kodu źródłowego|
|`SCC_NSE`|Rozszerzenie obszaru nazw|
|`SCC_NSE_PREFIX`|Prefiks protokału|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|PomocKończy|
|`STR_UI_LANGUAGE`|Język UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Oprogramowanie\Microsoft\SourceSafe|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
