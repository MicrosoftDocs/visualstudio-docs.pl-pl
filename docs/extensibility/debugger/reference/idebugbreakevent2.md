---
title: IDebugBreakEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735394"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Ten interfejs informuje menedżera debugowania sesji (SDM), że podział asynchroniczne został pomyślnie ukończony.

## <a name="syntax"></a>Składnia

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do obsługi przerw użytkownika w programie. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten `IDebugEvent2` interfejs (SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 SDM wywołuje [CauseBreak,](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) gdy użytkownik zażądał, aby program jest debugowany do wstrzymania. Po pomyślnym wstrzymaniu programu DE wysyła `IDebugBreakEvent2` zdarzenie. To zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez SDM po podłączeniu do programu, który jest debugowany.

## <a name="remarks"></a>Uwagi
 Na przykład użytkownik może wybrać polecenie **Podziel wszystko** w menu **Debugowania,** aby wyrwać się z programu z nieskończoną pętlą. SDM mówi programowi, aby zatrzymać, wywołując [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). DE wysyła, `IDebugBreakEvent2` gdy program w końcu się zatrzyma.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
