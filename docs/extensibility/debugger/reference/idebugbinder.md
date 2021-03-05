---
description: Ten interfejs wiąże pole symbol, zwykle zwracane przez dostawcę symboli, do kontekstu pamięci lub obiektu, który zawiera bieżącą wartość symbolu.
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: febe22338ddeaf275b37ae09c76921c91ec509da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143626"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs wiąże pole symbol, zwykle zwracane przez dostawcę symboli, do kontekstu pamięci lub obiektu, który zawiera bieżącą wartość symbolu.

## <a name="syntax"></a>Składnia

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs obsługuje obliczanie wyrażeń i musi być zaimplementowany przez aparat debugowania (DE).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest używany w procesie szacowania wyrażenia i jest zazwyczaj używany w implementacji [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugBinder` .

|Metoda|Opis|
|------------|-----------------|
|[Węglowodor](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Pobiera kontekst pamięci lub obiekt, który zawiera bieżącą wartość symbolu.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Określa typ obiektu w czasie wykonywania.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konwertuje lokalizację obiektu lub adres pamięci na kontekst pamięci.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Pobiera obiekt [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) używany do tworzenia parametrów funkcji.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Pobiera dokładny typ dla zmiennej.|

## <a name="remarks"></a>Uwagi
 Ten interfejs zwraca obiekty, które są używane przez ewaluatora wyrażeń w drzewach analizy. Ewaluatora wyrażeń analizuje wyrażenie przy użyciu dostawcy symboli do konwersji symboli w wyrażeniu na wystąpienia elementu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), które opisują każdy symbol pod względem jego typu i lokalizacji w kodzie źródłowym. Metoda [bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) konwertuje `IDebugField` obiekty na obiekty [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , które łączą lub powiążą typ symbolu z rzeczywistą wartością w pamięci. Te `IDebugObject` obiekty są następnie przechowywane w drzewie analizy na potrzeby późniejszej oceny.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
