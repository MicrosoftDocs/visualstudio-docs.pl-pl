---
title: Ewaluator wyrażeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738690"
---
# <a name="expression-evaluator"></a>Wyrażenie
Oceniający wyrażenia (EE) zbadać składni języka do analizy i oceny zmiennych i wyrażeń w czasie wykonywania, dzięki czemu mają być wyświetlane przez użytkownika, gdy IDE jest w trybie przerwania.

## <a name="use-expression-evaluators"></a>Używanie ewaluatorów wyrażeń
 Wyrażenia są tworzone przy użyciu [metody ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) w następujący sposób:

1. Aparat debugowania (DE) implementuje interfejs [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. Pakiet debugowania `IDebugExpressionContext2` pobiera obiekt z interfejsu [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) a następnie wywołuje `IDebugStackFrame2::ParseText` metodę na nim, aby uzyskać [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu.

3. Pakiet debugowania wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metody lub [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metody, aby uzyskać wartość wyrażenia. `IDebugExpression2::EvaluateAsync`jest wywoływana z okna Command/Immediate. Wszystkie inne składniki `IDebugExpression2::EvaluateSync`interfejsu użytkownika wywołać .

4. Wynikiem oceny wyrażenia jest [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiektu, który zawiera nazwę, typ i wartość wyniku oceny wyrażenia.

   Podczas oceny wyrażenia EE wymaga informacji ze składnika dostawcy symbolu. Dostawca symbolu dostarcza symboliczne informacje używane do identyfikowania i rozumienia analizowanego wyrażenia.

   Po zakończeniu oceny wyrażenia asynchronicznego zdarzenie asynchroniczne jest wysyłane przez DE za pośrednictwem menedżera debugowania sesji (SDM), aby powiadomić IDE, że ocena wyrażenia została zakończona. I wynik oceny jest następnie zwracany z `IDebugExpression2::EvaluateSync` wywołania do metody.

## <a name="implementation-notes"></a>Uwagi o implementacji
 Aparaty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania oczekują, aby porozmawiać z oceniającego wyrażenie przy użyciu interfejsów wspólnego środowiska wykonawczego języka (CLR). W rezultacie oceniający wyrażenie, który [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] współpracuje z aparatami debugowania, musi obsługiwać program CLR (pełną listę wszystkich interfejsów debugowania CLR można znaleźć w pliku debugref.doc, który jest częścią [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
