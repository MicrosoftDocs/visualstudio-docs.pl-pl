---
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 531ff846f2488193ed7f3d9f200a1a4ea04df6f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730330"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Aparat debugowania (DE) wysyła ten interfejs do Menedżera debugowania sesji (SDM), gdy program ma wykonać swój pierwszy Instruktaż dotyczący kodu użytkownika.

## <a name="syntax"></a>Składnia

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Element DE implementuje ten interfejs w ramach zwykłych operacji. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Po załadowaniu i wysłaniu tego obiektu zdarzenia podczas debugowania program jest gotowy do wykonania pierwszej instrukcji kodu użytkownika. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.

## <a name="remarks"></a>Uwagi
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) jest wysyłana, gdy program ma wykonać pierwszą instrukcję. Na przykład, `IDebugEntryPoint2` jest wysyłany, gdy program ma wykonać `main` funkcję użytkownika.

 Gdy ANULUJe `IDebugEntryPointEvent2` , bieżąca pozycja kodu powinna znajdować się na pierwszej instrukcji kodu użytkownika, na przykład `main` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
