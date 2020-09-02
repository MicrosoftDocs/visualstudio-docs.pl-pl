---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec8b26f422ca39b771a47f8eb60ee862d7d388f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568372"
---
# <a name="idebugexpression2"></a>IDebugExpression2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs przedstawia przeanalizowane wyrażenie gotowe do powiązania i oceniania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować wyrażenie analizowane gotowe do oceny.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zwraca ten interfejs. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zwraca interfejs [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Te interfejsy są dostępne tylko wtedy, gdy debugowany program został wstrzymany i dostępna jest Ramka stosu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugExpression2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Oblicza to wyrażenie asynchronicznie.|  
|[Anuluj](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zakończenie obliczania wyrażeń asynchronicznych.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy program został zatrzymany, Menedżer debugowania sesji (SDM) uzyskuje ramkę stosu od DE z wywołaniem do [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Model SDM następnie wywołuje [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby uzyskać Interfejs [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Następuje wywołanie [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) do utworzenia `IDebugExpression2` interfejsu, który reprezentuje wyrażenie analizowane gotowe do oceny.  
  
 Model SDM wywołuje [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , aby faktycznie oszacować wyrażenie i utworzyć wartość.  
  
 W implementacji programu `IDebugExpressionContext2::ParseText` , de używa funkcji com, `CoCreateInstance` Aby utworzyć wystąpienie ewaluatora wyrażeń i uzyskać Interfejs [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) (Zobacz przykład w `IDebugExpressionEvaluator` interfejsie). A następnie wywołuje metodę [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , aby uzyskać Interfejs [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Ten interfejs jest używany w implementacji `IDebugExpression2::EvaluateSync` i `IDebugExpression2::EvaluateAsync` w celu przeprowadzenia oceny.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
