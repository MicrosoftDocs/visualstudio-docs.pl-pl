---
title: Co&#39;nowego w interfejsie API dodatku plug-in kontroli źródła w wersji 1,3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f45eeb3c57d5339b1e9fd66951dcbb60970e108
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721587"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;nowego w interfejsie API dodatku plug-in kontroli źródła w wersji 1,3
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

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)