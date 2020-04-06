---
title: IDebugStackFrame3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719469"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Ten interfejs rozszerza [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) do obsługi przechwyconych wyjątków.

## <a name="syntax"></a>Składnia

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) do obsługi przechwyconych wyjątków.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na interfejsie, `IDebugStackFrame2` aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod dziedziczonych z [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) `IDebugStackFrame3` udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Obsługuje wyjątek dla bieżącej ramki stosu przed dowolną regularną obsługą wyjątków.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Zwraca kontekst kodu, jeśli wystąpiło odwiodowanie stosu.|

## <a name="remarks"></a>Uwagi
 Przechwycony wyjątek oznacza, że debuger może przetworzyć wyjątek, zanim wszelkie normalne procedury obsługi wyjątków są wywoływane przez czas wykonywania. Przechwytywanie wyjątku zasadniczo oznacza, że czas wykonywania udawać, że istnieje program obsługi wyjątków obecny nawet wtedy, gdy nie ma.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) jest wywoływana podczas wszystkich normalnych zdarzeń wywołania zwrotnego wyjątku (jedynym wyjątkiem jest, jeśli debugowanie kodu trybu mieszanego (kod zarządzany i niezarządzane), w którym to przypadku wyjątek nie może zostać przechwycony podczas wywołania zwrotnego ostatniej szansy). Jeśli DE nie implementuje `IDebugStackFrame3`, lub DE zwraca błąd z IDebugStackFrame3::`InterceptCurrentException` (na przykład `E_NOTIMPL`), a następnie debuger będzie obsługiwać wyjątek normalnie.

 Przechwytując wyjątek, debuger może zezwolić użytkownikowi na wprowadzanie zmian w stanie debugowanego programu, a następnie wznowienie wykonywania w punkcie, w którym został zgłoszony wyjątek.

> [!NOTE]
> Przechwycone wyjątki są dozwolone tylko w kodzie zarządzanym, czyli w programie uruchomionym w ramach środowiska wykonawczego języka wspólnego (CLR).

 Aparat debugowania wskazuje, że obsługuje przechwytywanie wyjątków, ustawiając "metricExceptions" do wartości `SetMetric` 1 w czasie wykonywania przy użyciu funkcji. Aby uzyskać więcej informacji, zobacz [Pomocnicy SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
