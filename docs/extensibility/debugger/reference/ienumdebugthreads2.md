---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e3771545d4a5fe545382344d17ed5ea929999d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852781"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Ten interfejs wylicza wątki uruchomione w bieżącej sesji debugowania.

## <a name="syntax"></a>Składnia

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować listę wątków w programie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumThreads —](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) , aby uzyskać ten interfejs reprezentujący listę wszystkich wątków w wszystkich programach uruchomionych w procesie. Wywołaj [EnumThreads —](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) , aby uzyskać ten interfejs reprezentujący listę wątków uruchomionych w programie.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugThreads2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Pobiera określoną liczbę wątków w sekwencji wyliczania.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Pomija określoną liczbę wątków w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczeniowy jak bieżący.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Pobiera liczbę wątków w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio zwykle uzyskuje ten interfejs, aby zaktualizować okno **wątki** , a także uzyskać pierwszy wątek listy, aby wywołać [wykonywanie](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [kontynuowanie](../../../extensibility/debugger/reference/idebugprocess3-continue.md)i [krok](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Wykonaj polecenie](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
