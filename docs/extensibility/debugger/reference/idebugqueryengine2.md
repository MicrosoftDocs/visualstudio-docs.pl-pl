---
title: IDebugQueryEngine2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbe3444d5bcdb31a4ef7619b123041f459a09852
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916412"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Ten interfejs umożliwia sesji debugowania manager (SDM) pobrać interfejs, który reprezentuje aparat debugowania (DE).

## <a name="syntax"></a>Składnia

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs na obiektach, które implementują najpopularniejsze interfejsy DE (takie jak [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), i [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) w Aby zezwolić na dostęp do [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejsu DE, sam.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [QueryInterface](/cpp/atl/queryinterface) w typowym interfejsie DE uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugQueryEngine2`.

|Metoda|Opis|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Pobiera interfejs aparatu (DE) niestandardowe debugowania.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest zwykle implementowany w obiekcie, który implementuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejs w celu zapewnienia obsługi uporządkowane przyczynowości krokowego wykonywania funkcji, czyli gdy debuger jest przechodzenie z funkcji, dalej funkcję do wykonania, nie może być poprzedniej funkcji na stosie, ale funkcja w innym wątku całkowicie. Aby uzyskać pełną definicję "przyczynowości", zobacz [słownik debugera w usłudze Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)