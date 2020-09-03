---
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732677"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Ten interfejs reprezentuje atrybut niestandardowy i może podawać nazwę, element nadrzędny i typ klasy atrybutu.

## <a name="syntax"></a>Składnia

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs, aby obsługiwał atrybuty niestandardowe skojarzone z symbolem. Zwykle jest ona zaimplementowana dla własnego obiektu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) zwraca ten interfejs. Wywołanie metody [EnumCustomAttributes —](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) zwraca interfejs [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugCustomAttribute` .

|Metoda|Opis|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Pobiera pole, do którego jest dołączony bieżący atrybut.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Pobiera typ klasy atrybutu niestandardowego.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Pobiera nazwę atrybutu niestandardowego.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Pobiera informacje o atrybucie jako obiekt BLOB bajtów.|

## <a name="remarks"></a>Uwagi
 Atrybut niestandardowy to struktura języka C#, która dostarcza niestandardowe metadane skojarzone z konkretną klasą lub metodą.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
