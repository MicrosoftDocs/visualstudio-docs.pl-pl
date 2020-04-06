---
title: Funkcje wywołania zwrotnego zaimplementowane przez IDE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739892"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkcje wywołania zwrotnego zaimplementowane przez IDE
Aby integracja ze zintegrowanym środowiskiem programistycznym (IDE) była jak najbardziej płynna i aby zapewnić ujednolicone środowisko użytkownika końcowego, wtyczka kontroli źródła może używać funkcji wywołania zwrotnego, które są implementowane przez IDE. Wtyczka może wywołać te funkcje w odpowiednim czasie podczas operacji kontroli źródła, aby przekazać informacje do IDE; IDE można następnie wyświetlić te informacje jako elementy osadzone w jego macierzystego interfejsu użytkownika. Użytkownik ma mniej pofragmentowane środowisko w tym scenariuszu niż jeśli plug-in zatrudniony własny interfejs użytkownika.

 Wymagany plik nagłówka *to scc.h*. Domyślną lokalizacją jest *\Program Files\VSIP 8.0\EnvSDK\common\inc\\*. Znajduje się również w folderze VSIP, który ma przykład wtyczki kontroli źródła w *\Program Files\VSIP 8.0\MSSCCI\\*.

## <a name="in-this-section"></a>W tej sekcji
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) W tym artykule opisano funkcję wywołania zwrotnego, która jest używana przez [SccOpenProject](../extensibility/sccopenproject-function.md) do wyświetlania komunikatów z wtyczki formantu źródłowego za pośrednictwem IDE.

- [POPLISTFUNC (POPLISTFUNC)](../extensibility/poplistfunc.md) W tym artykule opisano funkcję wywołania zwrotnego, która jest używana przez [SccPopulateList,](../extensibility/sccpopulatelist-function.md) gdy IDE nie ma pełnego dostępu do informacji, które są dostępne tylko dla wtyczki kontroli źródła, takich jak pełna lista plików pod kontrolą wersji.

- [QUERYCHANGESFUNC (WYSZUKIWANIE ZMIAN)](../extensibility/querychangesfunc.md) W tym artykule opisano funkcję wywołania zwrotnego, która jest używana przez [SccQueryChanges](../extensibility/sccquerychanges-function.md) operacji.

- [POPDIRLISTFUNC (POPDIRLISTFUNC)](../extensibility/popdirlistfunc.md) W tym artykule opisano funkcję wywołania zwrotnego, która jest używana przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operacji.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) W tym artykule opisano funkcję wywołania zwrotnego ustawioną przez wywołanie [SccSetOption,](../extensibility/sccsetoption-function.md) która umożliwia wtyczkę kontroli źródła do komunikowania zmian nazw z powrotem do IDE.

## <a name="related-sections"></a>Powiązane sekcje
- [SccOpenProjekt](../extensibility/sccopenproject-function.md) Otwiera projekt.

- [Lista SccPopulateList](../extensibility/sccpopulatelist-function.md) Sprawdza listę plików pod kątem ich bieżącego stanu. Ponadto używa `pfnPopulate` tej funkcji do powiadamiania rozmówcy, gdy plik nie `nCommand`spełnia kryteriów programu .

- [Lista SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Sprawdza listę katalogów i plików w projekcie lub projektach, które są pod kontrolą źródła. Każda znaleziona nazwa katalogu i pliku jest przekazywana do funkcji wywołania zwrotnego.

- [Zmiany W SccQueryChanges](../extensibility/sccquerychanges-function.md) Sprawdza zmiany nazw, które zostały wprowadzone na liście plików. Każda nazwa pliku jest przekazywana do funkcji wywołania zwrotnego wraz z jego stanem zmiany.

- [SccSetOption (SccSetOption)](../extensibility/sccsetoption-function.md) Ustawia szeroką gamę opcji. Każda opcja rozpoczyna `SCC_OPT_xxx` się i ma swój własny zdefiniowany zestaw wartości.

- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md) Opisuje zawartość sekcji referencyjnej zestawu SDK dodatku Source Control Plug-in.
