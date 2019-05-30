---
title: IDebugCustomAttribute | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae596c781d864f97087371fcb10595aa5f6a8ee9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346126"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Ten interfejs reprezentuje atrybutu niestandardowego, a ma ona nazwę, nadrzędny i typem klasy atrybutu.

## <a name="syntax"></a>Składnia

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs w celu zapewnienia obsługi niestandardowe atrybuty powiązane z symbolem. Jest on zwykle implementowany własnego obiektu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [dalej](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) zwraca ten interfejs. Wywołanie [enumcustomattributes —](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) metoda zwraca [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugCustomAttribute`.

|Metoda|Opis|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Pobiera pola, do której jest dołączony bieżący atrybut.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Pobiera typ klasy atrybutu niestandardowego.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Pobiera nazwę atrybutu niestandardowego.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Pobiera informacje o atrybutach jako obiekt blob bajtów.|

## <a name="remarks"></a>Uwagi
 Atrybut niestandardowy jest strukturą dla języka C#, który dostarcza niestandardowych metadanych skojarzonych z konkretną klasą lub metody.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)