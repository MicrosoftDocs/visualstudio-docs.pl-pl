---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6d8f869e519d9500f1ea8f3bb33a3ee098f5cfd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325418"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Ten interfejs wylicza wątki uruchomione w bieżącej sesji debugowania.

## <a name="syntax"></a>Składnia

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący listę wątków w programie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [enumthreads —](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) uzyskać ten interfejs reprezentujący listę wszystkich wątków we wszystkich programów uruchomionych w ramach procesu. Wywołaj [enumthreads —](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) uzyskać ten interfejs reprezentujący listę wątków uruchomionych w programie.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IEnumDebugThreads2`.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Pobiera określoną liczbę wątków w kolejności wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Pomija określoną liczbę wątków w kolejności wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżący.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Pobiera liczbę wątków w moduł wyliczający.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio zwykle uzyskuje tego interfejsu, aby zaktualizować **wątków** okna również, aby otrzymać pierwszym wątkiem listy, aby wywołać [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md), i [Kroku](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
