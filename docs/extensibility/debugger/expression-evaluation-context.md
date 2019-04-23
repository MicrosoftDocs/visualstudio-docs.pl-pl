---
title: Kontekst oceny wyrażeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f8e2347595a5bf7723c4a72b1f57a3f42a2ab5a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069715"
---
# <a name="expression-evaluation-context"></a>Kontekst oceny wyrażeń
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania **oceny wyrażenia kontekstu**:

- Reprezentuje kontekst do obliczenia wyrażenia. Ogólnie rzecz biorąc kontekst oceny odpowiada zakresie leksykalnym, w którym można obliczyć wartości zmiennych, parametrów, funkcje i metody. Na przykład oceny wyrażenia kontekstu skojarzonego z ramką stosu zapewni kontekście ocenianie zmiennych lokalnych, parametrów metod i składowych klasy (jeśli dotyczy).

- Występuje po zatrzymaniu w punkcie przerwania programu. Wyrażenia jest strukturą danych, reprezentujący przeanalizowany wyrażenie, które jest gotowe do powiązania i oceny w danym kontekście.

     Bardziej szczegółowo wyrażenia są tworzone przy użyciu [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody. Gdy wyrażenie jest obliczane, generuje drukowalnych ciąg zawierający nazwę i typ zmiennej lub argumentu i jego wartość. Ten ciąg jest wyświetlany w oknie czujki lub okno zmiennych lokalnych w IDE.

     Biorąc pod uwagę `BSTR` i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu, aparat debugowania (DE) można utworzyć [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, analizując wyrażenia. Biorąc pod uwagę `IDebugExpression2` interfejsu, DE może pobrać wartość do obliczenia wyrażenia synchroniczna lub asynchroniczna. Tę wartość, wraz z nazwą i typ zmiennej lub argumentu, są wysyłane do IDE do wyświetlenia.

## <a name="see-also"></a>Zobacz także
- [Interfejsy oceny wyrażenia](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)