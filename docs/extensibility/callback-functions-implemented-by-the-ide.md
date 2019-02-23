---
title: Funkcje wywołania zwrotnego implementowane przez środowisko IDE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc3b4423b54975c773de743b093f882f1fd9c42c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697562"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkcje wywołania zwrotnego implementowane przez środowisko IDE
Aby Integracja z usługą zintegrowanego środowiska programistycznego (IDE) jako Bezproblemowa, jak to możliwe i w celu zapewnienia ujednoliconego końcowego wtyczka do kontroli źródła można użyć funkcji wywołania zwrotnego, które są implementowane przez środowisko IDE. Wtyczka może wywołać te funkcje w odpowiednim czasie podczas operacji kontroli źródła do przekazywania informacji do IDE; IDE może następnie wyświetlić te informacje jako elementy osadzone w ich natywnym interfejsem użytkownika. Użytkownik ma zmniejszenie fragmentacji środowisko, w tym scenariuszu niż Jeśli wtyczka zatrudnionych własnego interfejsu użytkownika.

 Plik nagłówka wymagane jest *scc.h*. Domyślna lokalizacja to *\Program Files\VSIP 8.0\EnvSDK\common\inc\\*. Jest również folder VSIP, który zawiera przykładowe wtyczki kontroli źródła na *\Program Files\VSIP 8.0\MSSCCI\\*.

## <a name="in-this-section"></a>W tej sekcji
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccOpenProject](../extensibility/sccopenproject-function.md) umożliwiające wyświetlanie komunikatów z kontroli źródła wtyczek za pośrednictwem środowiska IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) gdy IDE nie ma pełny dostęp do informacji, która jest dostępna tylko dla wtyczka do kontroli źródła, takich jak uzyskać pełną listę pliki objęte kontrolą wersji.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccQueryChanges](../extensibility/sccquerychanges-function.md) operacji.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operacji.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) opisuje ustawiony przez wywołanie do funkcji wywołania zwrotnego [SccSetOption](../extensibility/sccsetoption-function.md) umożliwiającej wtyczka do kontroli źródła do komunikowania się zmiany nazwy z powrotem do środowiska IDE.

## <a name="related-sections"></a>Sekcje pokrewne
- [SccOpenProject](../extensibility/sccopenproject-function.md) zostanie otwarty projekt.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) sprawdza, czy lista plików dla ich bieżący stan. Ponadto używa `pfnPopulate` funkcję, aby powiadomić obiekt wywołujący, gdy plik jest niezgodny z kryteriami, które dla `nCommand`.

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) sprawdza listy katalogów i plików w projekcie, lub projekty, które są pod kontrolą źródła. Każdy katalog oraz nazwę pliku znaleziono jest przekazywany do funkcji wywołania zwrotnego.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) sprawdza, czy zmiany nazwy, które zostały wprowadzone do listy plików. Każda nazwa pliku jest przekazywany do funkcji wywołania zwrotnego, razem ze statusem zmiany.

- [SccSetOption](../extensibility/sccsetoption-function.md) ustawia szeroką gamę opcji. Każda opcja zaczyna się od `SCC_OPT_xxx` i ma swój własny zestaw zdefiniowanych wartości.

- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md) opisuje zawartość sekcji odwołanie do zestawu SDK wtyczki kontroli źródła.