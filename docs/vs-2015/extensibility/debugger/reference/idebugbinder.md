---
title: IDebugBinder | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30f4ae83134ae1ac2dceea991fe65b0d1ae191f2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788267"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

