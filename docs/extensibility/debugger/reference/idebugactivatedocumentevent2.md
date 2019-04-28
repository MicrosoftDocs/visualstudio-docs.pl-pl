---
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd113dec63d98e54e72cc68c333d009db4e35a04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923951"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Aparat debugowania (DE) używa tego interfejsu, aby zażądać dokumentu do załadowania.

## <a name="syntax"></a>Składnia

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs, gdy potrzebny do otwarcia pliku źródłowego. Ten interfejs jest implementowany tylko przez silniki debugowania, które pracować, lub są częścią interpretery skryptu. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (SDM używa [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła tego obiektu zdarzenie, kiedy zachodzi potrzeba otwarty plik źródłowy. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego dostarczonych przez model SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugActivateDocumentEvent2`.

|Metody|Opis|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Pobiera dokument, aby aktywować.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Pobiera kontekst dokumentu, który opisuje sytuację, w tym dokumencie.|

## <a name="remarks"></a>Uwagi
 Typowy scenariusz, w którym ten interfejs jest wykorzystywany jest, jeśli wystąpi błąd analizy w kodzie skryptu na stronie HTML, skrypt DE wysyła ten interfejs SDM wyświetlany dokument z błąd analizy.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)