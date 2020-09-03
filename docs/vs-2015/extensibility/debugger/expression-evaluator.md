---
title: Ewaluatora wyrażeń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 423df66e8bd6bc1257a32236aa4ffbb28b80d655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152740"
---
# <a name="expression-evaluator"></a>Ewaluator wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Oceny wyrażeń (EE) sprawdzają składnię języka, aby analizować i oceniać zmienne i wyrażenia w czasie wykonywania, umożliwiając ich wyświetlanie przez użytkownika, gdy IDE jest w trybie przerwania.  
  
## <a name="using-expression-evaluators"></a>Używanie ocen wyrażeń  
 Wyrażenia są tworzone przy użyciu metody [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) w następujący sposób:  
  
1. Aparat debugowania (DE) implementuje interfejs [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
2. Pakiet debugowania pobiera `IDebugExpressionContext2` obiekt z interfejsu [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , a następnie wywołuje `IDebugStackFrame2::ParseText` metodę na nim, aby uzyskać obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
3. Pakiet debugowania wywołuje metodę [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub metodę [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) w celu pobrania wartości wyrażenia. `IDebugExpression2::EvaluateAsync` jest wywoływany z okna polecenie/Immediate. Wszystkie inne składniki interfejsu użytkownika są wywoływane `IDebugExpression2::EvaluateSync` .  
  
4. Wynik obliczania wyrażenia jest obiektem [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który zawiera nazwę, typ i wartość wyniku oceny wyrażenia.  
  
   Podczas obliczania wyrażenia EE wymaga informacji od składnika dostawcy symboli. Dostawca symboli dostarcza informacje symboliczne służące do identyfikowania i analizowania wyanalizowanego wyrażenia.  
  
   Gdy szacowanie wyrażeń asynchronicznych zostało zakończone, zdarzenie asynchroniczne jest wysyłane przez cały czas przez Menedżera debugowania sesji (SDM) w celu powiadomienia środowiska IDE o ukończeniu oceny wyrażenia. Po zakończeniu obliczania wyrażenia synchronicznego wynik oceny jest zwracany z wywołania `IDebugExpression2::EvaluateSync` metody.  
  
## <a name="implementation-notes"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Aparaty debugowania oczekują na rozmowę z ewaluatora wyrażeń przy użyciu interfejsów aparatu plików wykonywalnych języka wspólnego (CLR). W związku z tym, ewaluatora wyrażeń, która współpracuje z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aparatami debugowania, musi obsługiwać środowisko CLR (kompletna lista wszystkich interfejsów debugowania CLR znajduje się w debugref.doc, który jest częścią [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] ).  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)
