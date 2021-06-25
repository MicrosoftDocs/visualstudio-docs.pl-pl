---
title: Funkcje wywołania zwrotnego zaimplementowane przez program IDE | Microsoft Docs
description: Dowiedz się więcej o funkcjach wywołania zwrotnego, które wtyczka może wywołać w odpowiednim czasie podczas operacji kontroli źródła w celu przekazania informacji do środowiska IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 78ce3a9cdd183cff0518ee3c6da9326c63297a85
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899150"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkcje wywołania zwrotnego implementowane przez ide
Aby zapewnić możliwie bezproblemową integrację ze zintegrowanym środowiskiem projektowym (IDE) i zapewnić ujednolicone środowisko użytkownika końcowego, wtyczka kontroli źródła może używać funkcji wywołania zwrotnego implementowanych przez środowisko IDE. Wtyczka może wywołać te funkcje w odpowiednim czasie podczas operacji kontroli źródła w celu przekazania informacji do środowiska IDE. Ide może następnie wyświetlać te informacje jako osadzone elementy w natywnym interfejsie użytkownika. W tym scenariuszu użytkownik ma mniej pofragmentowane środowisko niż w przypadku, gdy wtyczka korzysta z własnego interfejsu użytkownika.

 Wymagany plik nagłówkowy to *scc.h.* Domyślna lokalizacja to *\Program Files\VSIP 8.0\EnvSDK\common\inc. \\* Znajduje się on również w folderze VSIP, który zawiera przykład wtyczki kontroli źródła w folderze *\Program Files\VSIP 8.0\MSSCCI. \\*

## <a name="in-this-section"></a>W tej sekcji
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Opisuje funkcję wywołania zwrotnego używaną przez funkcję [SccOpenProject](../extensibility/sccopenproject-function.md) do wyświetlania komunikatów z wtyczki kontroli źródła za pośrednictwem środowiska IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Opisuje funkcję wywołania zwrotnego, która jest używana przez kontrolkę [SccPopulateList,](../extensibility/sccpopulatelist-function.md) gdy idee nie mają pełnego dostępu do informacji dostępnych tylko dla wtyczki kontroli źródła, takich jak pełna lista plików w ramach kontroli wersji.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Opisuje funkcję wywołania zwrotnego używaną przez operację [SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Opisuje funkcję wywołania zwrotnego używaną przez operację [SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Opisuje funkcję wywołania zwrotnego ustawioną przez wywołanie [SccSetOption,](../extensibility/sccsetoption-function.md) które umożliwia wtyczce kontroli kodu źródłowego komunikowanie zmian nazw z powrotem do środowiska IDE.

## <a name="related-sections"></a>Powiązane sekcje
- [SccOpenProject](../extensibility/sccopenproject-function.md) Otwiera projekt.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Sprawdza listę plików ich bieżącego stanu. Ponadto funkcja używa funkcji do powiadamiania wywołującego, gdy plik nie spełnia `pfnPopulate` kryteriów dla `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Sprawdza listę katalogów i plików w projekcie lub projektach, które są pod kontrolą źródła. Każdy znaleziony katalog i nazwa pliku są przekazywane do funkcji wywołania zwrotnego.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Sprawdza zmiany nazw, które zostały wprowadzone na liście plików. Każda nazwa pliku jest przekazywana do funkcji wywołania zwrotnego wraz z jej stanem zmiany.

- [SccSetOption](../extensibility/sccsetoption-function.md) Ustawia szeroką gamę opcji. Każda opcja rozpoczyna się `SCC_OPT_xxx` od i ma własny zdefiniowany zestaw wartości.

- [Wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md) Opisuje zawartość sekcji referencyjnej zestawu SDK wtyczki kontroli kodu źródłowego.
