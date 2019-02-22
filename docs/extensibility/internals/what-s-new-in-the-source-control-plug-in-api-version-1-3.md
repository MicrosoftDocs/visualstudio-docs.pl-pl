---
title: Co&#39;s Nowość w źródle kontrolować wtyczki API w wersji 1.3 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b61e56fcef8bbbe8e9f36a39580eae14ad582d5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645982"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;s Nowość w źródle kontrolować wtyczki API w wersji 1.3
API wtyczki kontroli źródła w wersji 1.3 wprowadzono następujące nowe funkcje do zapewnienia bardziej zaawansowanych kontroli.

## <a name="changes"></a>Zmiany
 Jesteś nowym użytkownikiem API wtyczki kontroli źródła w wersji 1.3 są następujące funkcje:

|Funkcja|Omówienie|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Zezwala na dodatkowe możliwości usługi bits, należy podać|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Umożliwia badanie plików, które mają nowszych wersji w bazie danych kontroli wersji niż na dysku lokalnym|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Umożliwia badanie stanu zmiany nazwy (zmienia nazwę, dodań i usunięć) dla określonych plików|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Umożliwia badanie plików i katalogów w bazie danych kontroli wersji|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Określona lista plików z bazy danych kontroli wersji są dodawane do bieżącego projektu|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Wykonuje silent "Pobierz" określonych plików (bez interfejsu użytkownika znajduje się)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Zezwala na dostęp do opcji specyficzne dla użytkownika|

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)