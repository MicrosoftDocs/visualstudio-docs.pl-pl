---
title: IDebugBinder | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735974"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs wiąże pole symbolu, zwykle zwracane przez dostawcę symbolu, z kontekstem pamięci lub obiektem zawierającym bieżącą wartość symbolu.

## <a name="syntax"></a>Składnia

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs obsługuje ocenę wyrażenia i musi być zaimplementowana przez aparat debugowania (DE).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest używany w procesie oceny wyrażenia i jest zazwyczaj używany w implementacji [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugBinder`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Pobiera kontekst pamięci lub obiekt, który zawiera bieżącą wartość symbolu.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Określa typ czasu wykonywania obiektu.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konwertuje lokalizację obiektu lub adres pamięci na kontekst pamięci.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Pobiera [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiektu używanego do tworzenia parametrów funkcji.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Pobiera dokładny typ dla zmiennej.|

## <a name="remarks"></a>Uwagi
 Ten interfejs zwraca obiekty, które są używane przez oceniającego wyrażenie w drzewach analizy. Oceniający wyrażenie analizuje wyrażenie za pomocą dostawcy symboli do konwersji symboli w wyrażeniu na wystąpienia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), które opisują każdy symbol pod względem jego typu i lokalizacji w kodzie źródłowym. Bind [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) Metoda konwertuje `IDebugField` obiekty do [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów, które łączą lub wiążą typ symbolu do rzeczywistej wartości w pamięci. Obiekty `IDebugObject` te są następnie przechowywane w drzewie analizy do późniejszej oceny.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
