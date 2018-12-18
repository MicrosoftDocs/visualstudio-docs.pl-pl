---
title: IDebugStackFrame3 | Dokumentacja firmy Microsoft
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
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e09851f4cfd8418db8b11a08f0ba13a5a133b94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791946"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs rozszerza [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) aby obsłużyć wyjątki przechwycone.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obsługiwany wyjątki przechwycone przez interfejs.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugStackFrame2` interfejsu w celu uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod odziedziczone [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Obsługuje wyjątek dla bieżącej ramki stosu przed żadnych wyjątków regularne.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Zwraca kontekst kodu, gdyby wystąpić odwijania stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Wyjątek przechwycone oznacza, że debuger może przetwarzać wyjątku przed wywołaniem dowolnej procedury obsługi wyjątków normalne są w czasie wykonywania. Przechwytuje wyjątek zasadniczo oznacza w czasie wykonywania poudawać, że jest obecny, nawet wtedy, gdy nie ma obsługi wyjątków.  
  
 [Interceptcurrentexception —](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) jest wywoływana podczas wszystkich zdarzeń wywołania zwrotnego normalny wyjątek (Jedynym wyjątkiem jest, Jeśli debugujesz kod trybu mieszanego (kodu zarządzanego i niezarządzanego), w którym to przypadku wyjątku nie może zostać przechwycone podczas Wywołanie zwrotne ostatniej szansy). Jeśli nie implementuje DE `IDebugStackFrame3`, lub DE zwraca błąd z IDebugStackFrame3::`InterceptCurrentException` (takie jak `E_NOTIMPL`), debuger będzie zwykle obsłużyć wyjątek, a następnie.  
  
 Przechwycenie wyjątku, debuger umożliwia użytkownikowi dokonać zmian stanu debugowanego programu, a następnie Wznów wykonywanie w punkcie, w którym został zgłoszony wyjątek.  
  
> [!NOTE]
>  Przechwycone wyjątki są dozwolone tylko w kodzie zarządzanym, oznacza to, w programie, który jest uruchomiony w ramach środowiska uruchomieniowego języka wspólnego (CLR).  
  
 Aparat debugowania wskazuje, że obsługuje wyjątki przechwytujący przez ustawienie "metricExceptions" na wartość 1 w czasie wykonywania za pomocą `SetMetric` funkcji. Aby uzyskać więcej informacji, zobacz [pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

