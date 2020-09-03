---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720929"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Ten interfejs jest wysyłany przez aparat debugowania (DE) do Menedżera debugowania sesji (SDM) podczas tworzenia właściwości, która jest skojarzona z określonym dokumentem.

## <a name="syntax"></a>Składnia

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Element DE implementuje ten interfejs, aby zgłosić, że właściwość została utworzona. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu. Ten interfejs jest implementowany, jeśli nie utworzył właściwości skojarzonej ze skryptem, który został załadowany lub utworzony, oraz jeśli ten skrypt ma być wyświetlany w IDE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Powoduje utworzenie i wysłanie tego obiektu zdarzenia w celu zgłoszenia właściwości. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metodę `IDebugPropertyCreateEvent2` interfejsu.

|Metoda|Opis|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Pobiera nową właściwość.|

## <a name="remarks"></a>Uwagi
 Jeśli z właściwością jest skojarzony określony dokument lub skrypt, element DE może wysłać to zdarzenie do modelu SDM w celu zaktualizowania okna **dokumenty skryptu** nazwą dokumentu. Model SDM wywoła [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) z argumentem, `guidDocument` Aby pobrać `VARIANT` zawierający go wskaźnik [IUnknown](/cpp/atl/iunknown) . Model SDM wywoła metodę [QueryInterface](/cpp/atl/queryinterface) na tym wskaźniku, aby pobrać Interfejs [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , który jest używany do aktualizacji okna **dokumenty skryptu** .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
