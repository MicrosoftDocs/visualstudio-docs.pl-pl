---
description: Ten interfejs rozszerza IDebugStackFrame2 do obsługi obsłużonych wyjątków.
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4049b728842e630a0f0b300130362b8efa8ceec0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053207"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Ten interfejs rozszerza [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) do obsługi obsłużonych wyjątków.

## <a name="syntax"></a>Składnia

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , aby obsługiwał przechwycone wyjątki.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj metodę [QueryInterface](/cpp/atl/queryinterface) na `IDebugStackFrame2` interfejsie, aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` uwidacznia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Obsługuje wyjątek dla bieżącej ramki stosu przed wszelkimi regularnymi obsłudze wyjątków.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Zwraca kontekst kodu, jeśli wystąpiło przewinięcie stosu.|

## <a name="remarks"></a>Uwagi
 Przechwycony wyjątek oznacza, że debuger może przetworzyć wyjątek, zanim wszystkie normalne procedury obsługi wyjątków są wywoływane przez czas wykonywania. Przechwycenie wyjątku zasadniczo oznacza, że czas wykonywania poudawać, że jest obecny program obsługi wyjątków, nawet jeśli nie istnieje.

- [InterceptCurrentException —](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) jest wywoływana podczas wszystkich normalnych zdarzeń wywołania zwrotnego wyjątku (Jedyny wyjątek w przypadku debugowania kodu w trybie mieszanym (kod zarządzany i niezarządzany), w tym przypadku nie można przechwycić wyjątku podczas wywołania zwrotnego ostatniej szansy). Jeśli element DE nie jest zaimplementowany `IDebugStackFrame3` lub funkcja de zwraca błąd z IDebugStackFrame3:: `InterceptCurrentException` (takich jak `E_NOTIMPL` ), debuger obsłuży wyjątek zwykle.

 Przechwycenie wyjątku może pozwolić użytkownikowi na wprowadzenie zmian w debugowanym stanie programu, a następnie wznowienie wykonywania w punkcie, w którym został zgłoszony wyjątek.

> [!NOTE]
> Przechwycone wyjątki są dozwolone tylko w kodzie zarządzanym, czyli w programie uruchomionym w środowisku uruchomieniowym języka wspólnego (CLR).

 Aparat debugowania wskazuje, że obsługuje przechwycenie wyjątków przez ustawienie "metricExceptions" na wartość 1 w czasie wykonywania przy użyciu `SetMetric` funkcji. Aby uzyskać więcej informacji, zobacz [pomocników zestawu SDK na potrzeby debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
