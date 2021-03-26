---
title: Co &apos; nowego w interfejsie API wtyczki kontroli źródła 1,3
description: Dowiedz się więcej na temat Nowości w interfejsie API dodatku plug-in kontroli źródła w wersji 1,3, która wprowadza nowe funkcje, aby zapewnić bardziej zaawansowaną kontrolę.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ab9079248931758efbcfcd792ce3c79ccffb270
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074265"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;s w interfejsie API dodatku plug-in kontroli źródła w wersji 1,3
Interfejs API wtyczki kontroli źródła w wersji 1,3 wprowadza następujące nowe funkcje, aby zapewnić bardziej zaawansowaną kontrolę.

## <a name="changes"></a>Zmiany
 Następujące funkcje są nowe dla interfejsu API dodatku plug-in kontroli źródła w wersji 1,3:

|Funkcja|Omówienie|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Zezwala na raportowanie dodatkowych bitów możliwości|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Umożliwia badanie plików z nowszymi wersjami w bazie danych kontroli wersji niż na dysku lokalnym|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Umożliwia badanie stanu zmian nazw (zmiany nazw, dodatków i usunięć) dla określonych plików|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Umożliwia badanie katalogów i plików w bazie danych kontroli wersji|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Dodaje określoną listę plików z bazy danych kontroli wersji do bieżącego projektu|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Wykonuje ciche "Pobieranie" określonych plików (nie jest wyświetlany żaden interfejs użytkownika)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Zezwala na dostęp do opcji specyficznych dla użytkownika|

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
