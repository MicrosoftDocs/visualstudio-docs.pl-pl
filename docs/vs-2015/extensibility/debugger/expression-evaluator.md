---
title: Ewaluator wyrażeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48763a1e943a63f129c4fa72c0885d0a287b2b31
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736022"
---
# <a name="expression-evaluator"></a>Ewaluator wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ewaluatory wyrażeń (EE) Sprawdź składnię języka do analizy i Szacowanie zmiennych i wyrażeń w czasie wykonywania, umożliwiając im wyświetlanie przez użytkownika, gdy IDE jest w trybie przerwania.  
  
## <a name="using-expression-evaluators"></a>Za pomocą Ewaluatory wyrażeń  
 Wyrażenia są tworzone przy użyciu [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody w następujący sposób:  
  
1. Aparat debugowania (DE) implementuje [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu.  
  
2. Pobiera pakiet debugowania `IDebugExpressionContext2` obiektu z [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu, a następnie wywołania `IDebugStackFrame2::ParseText` metody je, aby uzyskać [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu.  
  
3. Wywołania pakietu debugowania [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metody lub [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodę, aby uzyskać wartość wyrażenia. `IDebugExpression2::EvaluateAsync` jest wywoływana z polecenia/bezpośrednim. Innych składników interfejsu użytkownika Wywołaj `IDebugExpression2::EvaluateSync`.  
  
4. Wynikiem obliczenia wyrażenia jest [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który zawiera nazwę, typ i wartość wyniku obliczenia wyrażenia.  
  
   Podczas obliczania wyrażenia EE wymaga informacji z składnika dostawcy symboli. Dostawca symboli dostarcza informacji symbolicznych, używany do identyfikowania i zrozumienia przeanalizowany wyrażenia.  
  
   Po zakończeniu oceny wyrażenia asynchroniczne Zdarzenie asynchroniczne wysyłany przez DE za pośrednictwem Menedżer debugowania sesji (SDM) do powiadamiania IDE zakończeniu oceny wyrażenia. Po zakończeniu oceny wyrażenia synchroniczne wynik obliczenia jest zwracany z wywołania `IDebugExpression2::EvaluateSync` metody.  
  
## <a name="implementation-notes"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Silniki debugowania chcą skontaktować się z Ewaluator wyrażeń przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W wyniku ewaluatora wyrażeń działające z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] silniki debugowania musi obsługiwać środowiska CLR (pełna lista wszystkich CLR profilowanie interfejsów znajduje się w debugref.doc, który jest częścią programu [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]).  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)

