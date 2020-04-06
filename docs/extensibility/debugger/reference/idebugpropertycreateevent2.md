---
title: IDebugPropertyCreateEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720929"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Ten interfejs jest wysyłany przez aparat debugowania (DE) do menedżera debugowania sesji (SDM) podczas tworzenia właściwości skojarzonej z określonym dokumentem.

## <a name="syntax"></a>Składnia

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do raportu, że właściwość została utworzona. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten interfejs. Moduł SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do `IDebugEvent2` interfejsu. Ten interfejs jest implementowany, jeśli DE stworzył właściwość skojarzoną ze skryptem, który został załadowany lub utworzony i jeśli ten skrypt musi pojawić się w IDE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia do raportu właściwość została utworzona. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) która jest dostarczana przez SDM, gdy jest dołączony do programu jest debugowany.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugPropertyCreateEvent2` przedstawiono metodę interfejsu.

|Metoda|Opis|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Pobiera nową właściwość.|

## <a name="remarks"></a>Uwagi
 Jeśli właściwość ma określony dokument lub skrypt skojarzony z nim, DE można wysłać to zdarzenie do SDM w celu zaktualizowania **okna Dokumenty skryptu** z nazwą dokumentu. SDM wywoła [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) z `guidDocument` argumentem, `VARIANT` aby pobrać zawierający wskaźnik [IUnknown.](/cpp/atl/iunknown) Moduł SDM wywoła [QueryInterface](/cpp/atl/queryinterface) na tym wskaźniku, aby pobrać interfejs [IDebugDocument2,](../../../extensibility/debugger/reference/idebugdocument2.md) który jest używany do aktualizacji okna **Dokumenty skryptu.**

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
