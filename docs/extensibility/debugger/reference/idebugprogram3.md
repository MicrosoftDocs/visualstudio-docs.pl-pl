---
title: Program IDebug3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722645"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Ten interfejs reprezentuje program, który jest uruchomiony w procesie i rozszerza [Execute,](../../../extensibility/debugger/reference/idebugprogram2-execute.md) podając informacje o wątku.

## <a name="syntax"></a>Składnia

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) i dostawca portu niestandardowego implementują ten interfejs do reprezentowania programu w procesie. Menedżer debugowania sesji (SDM) implementuje również ten interfejs, aby dostarczyć informacje do [dołączania](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 [Zdarzenie IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zwraca ten interfejs dla nowego programu. Ten interfejs jest również używany jako parametr dla wielu metod na wielu interfejsach.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugProgram3`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Wykonuje program. Wątek jest zwracany, aby dać debugera informacji, na którym wątku użytkownik jest wyświetlane podczas wykonywania.|

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Uwagi
 Program jest kontenerem wątku uruchomionym w określonej architekturze w czasie wykonywania, podczas gdy proces składa się z jednego lub więcej programów.

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
