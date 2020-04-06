---
title: Co&#39;nowego w interfejsie API wtyczki kontroli źródła w wersji 1.3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703360"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;nowego w interfejsie API wtyczki kontroli źródła w wersji 1.3
Interfejs API dodatku 1.3 wtyczki kontroli źródła wprowadza następujące nowe funkcje zapewniające bardziej zaawansowaną kontrolę.

## <a name="changes"></a>Zmiany
 Następujące funkcje są nowe w interfejsie API wtyczki kontroli źródła w wersji 1.3:

|Funkcja|Omówienie|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Umożliwia zgłaszanie dodatkowych bitów możliwości|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Umożliwia badanie plików, które mają nowsze wersje w bazie danych kontroli wersji niż na dysku lokalnym|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Umożliwia badanie stanu zmian nazw (zmiany nazw, uzupełnienia i usunięcia) dla określonych plików|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Umożliwia badanie katalogów i plików w bazie danych kontroli wersji|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Dodaje określoną listę plików z bazy danych kontroli wersji do bieżącego projektu|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Wykonuje ciche "Get" określonych plików (nie jest wyświetlany interfejs użytkownika)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Umożliwia dostęp do opcji specyficznych dla użytkownika|

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
