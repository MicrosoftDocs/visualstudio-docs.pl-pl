---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d22a58021a744cc71b8df3acb8e577d853aa2829
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889996"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Ten interfejs reprezentuje program uruchomiony w procesie i rozszerza [wykonywanie](../../../extensibility/debugger/reference/idebugprogram2-execute.md) przez podanie informacji o wątku.

## <a name="syntax"></a>Składnia

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) i dostawca portu niestandardowego implementują ten interfejs, aby reprezentować program w procesie. Menedżer debugowania sesji (SDM) implementuje także ten interfejs, aby podać informacje do [dołączenia](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Zdarzenie [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zwraca ten interfejs dla nowego programu. Ten interfejs jest również używany jako parametr dla wielu metod w wielu interfejsach.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugProgram3` .

|Metoda|Opis|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Wykonuje program. Wątek jest zwracany w celu udostępnienia informacji debugera, które są wyświetlane podczas wykonywania przez użytkownika.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Uwagi
 Program jest kontenerem wątków działającym w określonej architekturze czasu wykonywania, podczas gdy proces składa się z jednego lub kilku programów.

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
