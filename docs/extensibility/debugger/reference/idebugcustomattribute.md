---
title: IDebugCustomAttribute | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732677"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Ten interfejs reprezentuje atrybut niestandardowy i może podać nazwę, element nadrzędny i typ klasy atrybutu.

## <a name="syntax"></a>Składnia

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs w celu obsługi atrybutów niestandardowych skojarzonych z symbolem. Zazwyczaj jest implementowany na własny obiekt.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) zwraca ten interfejs. Wywołanie [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) metoda zwraca [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugCustomAttribute`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Pobiera pole, do którego dołączony jest bieżący atrybut.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Pobiera typ klasy atrybutu niestandardowego.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Pobiera nazwę atrybutu niestandardowego.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Pobiera informacje o atrybutach jako obiekt blob bajtów.|

## <a name="remarks"></a>Uwagi
 Atrybut niestandardowy jest strukturą języka C#, która dostarcza niestandardowych metadanych skojarzonych z określoną klasą lub metodą.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
