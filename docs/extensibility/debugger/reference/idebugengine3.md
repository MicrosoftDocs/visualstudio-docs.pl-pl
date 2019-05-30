---
title: IDebugEngine3 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01f15e088635af30bd36919e3da46dee8b8c237b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352444"
---
# <a name="idebugengine3"></a>IDebugEngine3
Reprezentuje aparat debugowania pojedynczego (DE), sterująca debugowanie jednego lub więcej modułów.

## <a name="syntax"></a>Składnia

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardowe DE (jeśli ją obsługuje symbole) Aby włączyć stan JustMyCode. Ten interfejs muszą być zaimplementowane przez DE, jeśli obsługuje symboli i JustMyCode.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływane przez Menedżer debugowania sesji (SDM) do przekazania na temat opcji użytkownika dla lokalizacji, z którego można załadować symboli. Jest również nazywany, aby ustawić identyfikator GUID aparatu, gdy zostanie uruchomiony (ten identyfikator GUID jest określane na podstawie od momentu rejestracji aparat). SDM wywołuje również tego interfejsu, aby ustawić stan JustMyCode oraz ustawić wszystkie wyjątki znane przez debuger do określonego stanu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod odziedziczone [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` interfejsu udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Ustawia ścieżki lub ścieżek, które DE będzie używać do wyszukiwania symboli debugowania.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Ładuje symbole dla wszystkich modułów, których nie zainstalowano jeszcze symbole załadowane.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informuje DE o JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Określa identyfikator GUID DE od metryki.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Ustaw wszystkie wyjątki jest aktualnie oczekujących do określonego stanu.|

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)