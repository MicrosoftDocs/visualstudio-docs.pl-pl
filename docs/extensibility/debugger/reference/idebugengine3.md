---
description: Reprezentuje pojedynczy aparat debugowania, który steruje debugowaniem co najmniej jednego modułu.
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3a10f439ba344b71cd31fd990928b7804b6c11d4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066193"
---
# <a name="idebugengine3"></a>IDebugEngine3
Reprezentuje pojedynczy aparat debugowania, który steruje debugowaniem co najmniej jednego modułu.

## <a name="syntax"></a>Składnia

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardową DE (jeśli obsługuje symbole) w celu włączenia stanu JustMyCode. Ten interfejs musi być zaimplementowany przez DE, jeśli obsługuje symbole i JustMyCode.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany przez Menedżera debugowania sesji (SDM) do przekazywania opcji użytkownika dla lokalizacji, z których mają zostać załadowane symbole. Jest również wywoływana, aby ustawić identyfikator GUID aparatu podczas jego tworzenia (identyfikator GUID jest oparty na metrykach od momentu rejestracji aparatu). Model SDM wywołuje również ten interfejs, aby ustawić stan JustMyCode i ustawić wszystkie wyjątki znane przez debuger do określonego stanu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` interfejs uwidacznia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Ustawia ścieżkę lub ścieżki, które będą używane przez DE do wyszukiwania symboli debugowania.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Ładuje symbole dla wszystkich modułów, które nie mają jeszcze załadowanych symboli.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informuje o tym informacje o JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Ustawia DE GUID na podstawie metryk.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Ustaw wszystkie wyjątki aktualnie oczekujące na określony stan.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
