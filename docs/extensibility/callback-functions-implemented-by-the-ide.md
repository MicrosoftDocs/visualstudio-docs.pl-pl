---
title: Funkcje wywołania zwrotnego implementowane przez środowisko IDE | Microsoft Docs
description: Dowiedz się więcej na temat funkcji wywołania zwrotnego, które wtyczka może wywoływać w odpowiednim czasie podczas operacji kontroli źródła w celu przekazania informacji do środowiska IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e2e361551fbe03b7f0ef41b19c5d4136aa50472
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068105"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkcje wywołania zwrotnego zaimplementowane przez IDE
Aby zapewnić bezproblemową integrację z zintegrowanym środowiskiem programistycznym (IDE) i zapewniać ujednolicone środowisko użytkownika końcowego, wtyczka do kontroli źródła może korzystać z funkcji wywołania zwrotnego, które są implementowane przez IDE. Wtyczka może wywoływać te funkcje w odpowiednim czasie podczas operacji kontroli źródła, aby przekazać informacje do środowiska IDE; IDE może wyświetlić te informacje jako osadzone elementy w macierzystym interfejsie użytkownika. Użytkownik ma mniej pofragmentowane środowisko w tym scenariuszu, niż w przypadku, gdy wtyczka korzysta z własnego interfejsu użytkownika.

 Wymagany plik nagłówkowy to *SCC. h*. Domyślna lokalizacja to *\Program Files\VSIP 8.0 \ EnvSDK\common\inc \\*. Jest również w folderze VSIP, który ma przykład wtyczki kontroli źródła w *folderze \Program Files\VSIP 8.0 \ MSSCCI \\*.

## <a name="in-this-section"></a>W tej sekcji
- [LpTextOutProc](../extensibility/lptextoutproc.md) Opisuje funkcję wywołania zwrotnego, która jest używana przez [SccOpenProject](../extensibility/sccopenproject-function.md) do wyświetlania komunikatów z wtyczki kontroli źródła za pośrednictwem IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Opisuje funkcję wywołania zwrotnego, która jest używana przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) , gdy IDE nie ma pełnego dostępu do informacji, które są dostępne tylko dla wtyczki kontroli źródła, takich jak kompletna lista plików w ramach kontroli wersji.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Opisuje funkcję wywołania zwrotnego, która jest używana przez operację [SccQueryChanges](../extensibility/sccquerychanges-function.md) .

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Opisuje funkcję wywołania zwrotnego, która jest używana przez operację [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) .

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Opisuje funkcję wywołania zwrotnego ustawioną przez wywołanie [SccSetOption](../extensibility/sccsetoption-function.md) , która umożliwia wtyczki kontroli źródła w celu komunikowania się zmian nazw z powrotem do IDE.

## <a name="related-sections"></a>Sekcje pokrewne
- [SccOpenProject](../extensibility/sccopenproject-function.md) Otwiera projekt.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Bada listę plików do ich bieżącego stanu. Ponadto program używa `pfnPopulate` funkcji do powiadamiania wywołującego, gdy plik jest niezgodny z kryteriami dla `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Bada listę katalogów i plików w projekcie lub projektach, które znajdują się pod kontrolą źródła. Każdy znaleziony katalog i nazwa pliku są przesyłane do funkcji wywołania zwrotnego.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Bada zmiany nazw, które zostały wprowadzone do listy plików. Każda nazwa pliku jest przenoszona do funkcji wywołania zwrotnego wraz ze stanem zmiany.

- [SccSetOption](../extensibility/sccsetoption-function.md) Ustawia szeroką gamę opcji. Każda opcja rozpoczyna się od `SCC_OPT_xxx` i ma swój własny zdefiniowany zestaw wartości.

- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md) Opisuje zawartość sekcji Reference zestawu SDK wtyczki kontroli źródła.
