---
description: Ten interfejs reprezentuje właściwość ramki stosu, właściwość dokumentu programu lub inną właściwość.
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5d20f0bd3727860f32e111baad2d2513590e880
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064803"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Ten interfejs reprezentuje właściwość ramki stosu, właściwość dokumentu programu lub inną właściwość. Właściwość jest zwykle wynikiem obliczenia wyrażenia.

> [!NOTE]
> Tego zastosowania właściwości "Property" nie należy mylić z tym, że oznacza zmienną składową klasy, chociaż `IDebugProperty2` może reprezentować taką jednostkę.

## <a name="syntax"></a>Składnia

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do reprezentowania określonego rodzaju wartości. Na przykład wartość może być wartością liczbową w wyniku obliczenia wyrażenia, kontekstu pamięci używanego do wyświetlania pamięci lub listy rejestrów i ich wartości.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , aby uzyskać ten interfejs, który reprezentuje wynik oceny. `IDebugExpression2::EvaluateAsync` zwraca ten interfejs, wysyłając Interfejs [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) do modelu SDM, który z kolei wywołuje metodę [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) w celu pobrania właściwości.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) zwraca ten interfejs, aby zapewnić skojarzony dokument skryptu.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) zwraca ten interfejs, aby reprezentować wartość zwracaną funkcji.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) zwraca ten interfejs, aby reprezentować różne właściwości programu, takie jak nazwa lub kontekst pamięci.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) zwraca ten interfejs, aby reprezentować różne właściwości ramki stosu, takich jak zmienne lokalne.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugProperty2` .

|Metoda|Opis|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Wypełnia strukturę [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) opisującą właściwość.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Ustawia wartość właściwości z ciągu.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Ustawia wartość właściwości z wartości danego odwołania.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Wylicza elementy podrzędne właściwości.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Zwraca element nadrzędny właściwości.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Zwraca właściwość opisującą najbardziej pochodną Właściwość właściwości.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Zwraca bajty pamięci, które tworzą wartość właściwości.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Zwraca kontekst pamięci dla wartości właściwości.|
|[GetSize —](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Zwraca rozmiar wartości właściwości w bajtach.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Zwraca odwołanie do wartości tej właściwości.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Zwraca rozszerzone informacje o właściwości.|

## <a name="remarks"></a>Uwagi
 Właściwość, w postaci reprezentowanej przez `IDebugProperty2` interfejs, może być uważana za wartość o nazwie, typie i adresie. W bardziej ogólnych warunkach `IDebugProperty2` może reprezentować wszystkie elementy, które mają strukturę hierarchiczną z węzłami nadrzędnymi i podrzędnymi.

 Właściwość jest zwykle nietrwała, długotrwały tylko tak długo, jak bieżąca Ramka stosu, na przykład. Z drugiej strony odwołanie, które jest reprezentowane przez interfejs [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , trwa tak długo, jak wartość pozostanie w pamięci.

 IDE może użyć interfejsu, `IDebugProperty2` Aby umożliwić użytkownikom przeglądanie i modyfikowanie właściwości w czasie wykonywania.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
