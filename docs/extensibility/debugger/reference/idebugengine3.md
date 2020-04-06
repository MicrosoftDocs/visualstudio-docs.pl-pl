---
title: IDebugEngine3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730652"
---
# <a name="idebugengine3"></a>IDebugEngine3
Reprezentuje pojedynczy aparat debugowania (DE), który kontroluje debugowanie jednego lub więcej modułów.

## <a name="syntax"></a>Składnia

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardowe DE (jeśli obsługuje symbole), aby włączyć stan JustMyCode. Ten interfejs musi być zaimplementowany przez DE, jeśli obsługuje symbole i JustMyCode.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany przez menedżera debugowania sesji (SDM) do przekazywania opcji użytkownika dla lokalizacji, z których można załadować symbole. Jest również wywoływana, aby ustawić identyfikator GUID aparatu, gdy jest tworzone (ten identyfikator GUID jest oparty na metryki od czasu rejestracji aparatu). SDM wywołuje również ten interfejs, aby ustawić stan JustMyCode i ustawić wszystkie wyjątki znane przez debugera do określonego stanu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod dziedziczonych z [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) `IDebugEngine3` interfejs udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Ustawia ścieżkę lub ścieżki, które DE będzie używać do wyszukiwania symboli debugowania.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Ładuje symbole dla wszystkich modułów, które nie zostały jeszcze załadowane.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informuje DE o informacji JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Ustawia identyfikator GUID DE z metryk.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Ustaw wszystkie wyjątki aktualnie zaległe do określonego stanu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
