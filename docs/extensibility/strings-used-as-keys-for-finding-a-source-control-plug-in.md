---
title: Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31c2b30fb41976cdbbab13fa22d438c63bddbbef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331705"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła
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
|`SCC_STATUS_FILE`|MSSCCPRJ.SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Plik kontroli kodu źródłowego|
|`SCC_NSE`|Rozszerzenie Namespace|
|`SCC_NSE_PREFIX`|Prefiks od protokołu|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)