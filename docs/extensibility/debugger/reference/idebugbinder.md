---
title: IDebugBinder | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0e425a1790c2452e56061c8f4adee3c473e4b58
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859264"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs wiąże pola symboli, zazwyczaj są zwracane przez dostawcę symboli w kontekście pamięci lub obiekt, który zawiera bieżącą wartość symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs obsługuje oceny wyrażeń i muszą być zaimplementowane przez aparat debugowania (DE).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest używany w procesie oceny wyrażenia i jest zwykle używana w implementacji [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugBinder`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Pobiera kontekst pamięci lub obiekt, który zawiera bieżącą wartość symbolu.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Określa typu run-time obiektu.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konwertuje adres lokalizacji lub pamięci obiektu kontekstu pamięci.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Pobiera [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiekt wykorzystywany do tworzenia parametrów funkcji.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Pobiera dokładnie tego samego typu zmiennej.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs zwraca obiekty, które są używane przez ewaluatora wyrażeń w przeanalizować drzewa. Ewaluator wyrażeń analizuje wyrażenie przy użyciu dostawcy symbolu można przekonwertować symboli w wyrażeniu do wystąpień [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), opisywać każdy symbol pod względem typu i lokalizacji w kodzie źródłowym. [Powiązać](../../../extensibility/debugger/reference/idebugbinder-bind.md) konwertuje metody `IDebugField` obiekty do [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów, które połączenia lub powiązać symbol typu na rzeczywistą wartość w pamięci. Te `IDebugObject` obiekty są następnie zapisywane w drzewo analizy do późniejszego obliczenia.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)