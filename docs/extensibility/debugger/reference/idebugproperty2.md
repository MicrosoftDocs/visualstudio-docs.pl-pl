---
title: IDebugProperty2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721224"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Ten interfejs reprezentuje właściwość ramki stosu, właściwość dokumentu programu lub inną właściwość. Właściwość jest zwykle wynikiem oceny wyrażenia.

> [!NOTE]
> To użycie "właściwość" nie należy mylić z tym znaczenie `IDebugProperty2` zmiennej członkowskiej klasy, chociaż może reprezentować taką jednostkę.

## <a name="syntax"></a>Składnia

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do reprezentowania określonego rodzaju wartości. Na przykład wartość może być wartością liczbową w wyniku oceny wyrażenia, kontekstu pamięci używanego do wyświetlania pamięci lub listy rejestrów i ich wartości.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync,](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) aby uzyskać ten interfejs, który reprezentuje wynik oceny. `IDebugExpression2::EvaluateAsync`zwraca ten interfejs, wysyłając interfejs [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) do SDM, który z kolei wywołuje [GetResult,](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) aby pobrać właściwość.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) zwraca ten interfejs, aby zapewnić skojarzony dokument skryptu.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) zwraca ten interfejs do reprezentowania wartości zwracanej funkcji.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) zwraca ten interfejs do reprezentowania różnych właściwości programu, takich jak nazwa lub kontekst pamięci.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) zwraca ten interfejs do reprezentowania różnych właściwości ramki stosu, takich jak zmienne lokalne.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugProperty2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Wypełnia [strukturę DEBUG_PROPERTY_INFO,](../../../extensibility/debugger/reference/debug-property-info.md) która opisuje właściwość.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Ustawia wartość właściwości z ciągu.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Ustawia wartość właściwości z wartości danego odwołania.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Wylicza korżyny właściwości.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Zwraca element nadrzędny właściwości.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Zwraca właściwość, która opisuje najczęściej pochodną właściwość właściwości.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Zwraca bajty pamięci, które tworzą wartość właściwości.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Zwraca kontekst pamięci dla wartości właściwości.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Zwraca rozmiar (w bajtach) wartości właściwości.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Zwraca odwołanie do wartości tej właściwości.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Zwraca rozszerzone informacje o właściwości.|

## <a name="remarks"></a>Uwagi
 Właściwość, reprezentowana przez `IDebugProperty2` interfejs, może być traktowane jako wartość z nazwą, typem i adresem. W bardziej ogólnych `IDebugProperty2` warunkach może reprezentować wszystko, co ma strukturę hierarchiczną, z rodzicami i węzłami podrzędnymi.

 Właściwość jest zwykle przejściowe, trwające tylko tak długo, jak bieżąca ramka stosu, na przykład. Z drugiej strony odwołanie, reprezentowane przez interfejs [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) trwa tak długo, jak wartość pozostaje w pamięci.

 IDE można użyć `IDebugProperty2` interfejsu, aby umożliwić użytkownikom przeglądanie i modyfikowanie właściwości w czasie wykonywania.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
