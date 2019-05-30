---
title: IDebugProgram3 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cfc29f300bc9f28f857424a7a91b4b6bfd3bf82
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331527"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Ten interfejs reprezentuje program, który jest uruchomiony w procesie i rozszerza [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) , podając informacje o wątku.

## <a name="syntax"></a>Składnia

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) i dostawcy niestandardowego portu należy zaimplementować ten interfejs do reprezentowania program w procesie. Menedżer debugowania sesji (SDM) również implementuje ten interfejs, aby zapewnić informacje [Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzeń zwraca ten interfejs dla nowego programu. Ten interfejs jest również używany jako parametr dla wielu metod w wielu interfejsach.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugProgram3`.

|Metoda|Opis|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Wykonuje program. Wątek jest zwracany do przedstawienia informacji debugera, na który wątek wyświetlanie użytkownika podczas wykonywania.|

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Uwagi
 Program jest kontenerem wątków, uruchomiony w ramach określonej architektury czasu wykonywania, podczas procesu składa się z jednego lub wielu programów.

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)