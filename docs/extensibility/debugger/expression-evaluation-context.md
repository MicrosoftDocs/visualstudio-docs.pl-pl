---
title: Kontekst oceny wyrażeń | Microsoft Docs
description: Dowiedz się więcej o kontekście oceny wyrażeń, który reprezentuje kontekst oceny wyrażeń i istnieje, gdy program zatrzymał się w punkcie przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73eeafb95c7e4d52f69109c5eb7c06eb48bd8d88
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901217"
---
# <a name="expression-evaluation-context"></a>Kontekst oceny wyrażeń
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowaniu kontekst **oceny wyrażeń:**

- Reprezentuje kontekst oceny wyrażeń. Ogólnie rzecz biorąc, kontekst oceny odpowiada zakresowi leksykalnemu, w którym można oceniać zmienne, parametry, funkcje i metody. Na przykład kontekst oceny wyrażeń skojarzony z ramką stosu zapewni kontekst do oceny zmiennych lokalnych, parametrów metody i składowych klasy (jeśli ma to zastosowanie).

- Istnieje, gdy program zatrzymał się w punkcie przerwania. Samo wyrażenie jest strukturą danych reprezentującą analizowane wyrażenie, które jest gotowe do powiązania i oceny w danym kontekście.

     Bardziej szczegółowo wyrażenia są tworzone przy użyciu [metody ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Gdy wyrażenie jest oceniane, generuje ciąg drukowalny zawierający nazwę i typ zmiennej lub argumentu oraz jego wartość. Ten ciąg jest wyświetlany w okno wyrażeń kontrolnych lub w oknie Locals (Lokalne) środowiska IDE.

     Mając interfejs `BSTR` [i IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) aparat debugowania (DE) może utworzyć interfejs [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) analizując wyrażenie. Biorąc pod `IDebugExpression2` uwagę interfejs DE może uzyskać wartość za pośrednictwem synchronicznej lub asynchronicznej oceny wyrażeń. Ta wartość, wraz z nazwą i typem zmiennej lub argumentu, jest wysyłana do środowiska IDE w celu wyświetlenia.

## <a name="see-also"></a>Zobacz też
- [Interfejsy oceny wyrażeń](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
