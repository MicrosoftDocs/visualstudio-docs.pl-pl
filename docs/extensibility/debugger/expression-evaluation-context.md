---
title: Kontekst oceny wyrażeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738735"
---
# <a name="expression-evaluation-context"></a>Kontekst oceny wyrażenia
Podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania **kontekst oceny wyrażenia:**

- Reprezentuje kontekst do oceny wyrażenia. Ogólnie rzecz biorąc kontekst oceny odpowiada leksykalne zakres, w którym do oceny zmiennych, parametrów, funkcji i metod. Na przykład kontekst oceny wyrażenia skojarzony z ramką stosu zapewni kontekst do oceny zmiennych lokalnych, parametrów metody i elementów członkowskich klasy (jeśli dotyczy).

- Istnieje, gdy program został zatrzymany w punkcie przerwania. Samo wyrażenie jest strukturą danych reprezentującą wyrażenie analizowane, które jest gotowe do powiązania i oceny w danym kontekście.

     Bardziej szczegółowo wyrażenia są tworzone przy użyciu [Metody ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Po obliczeniu wyrażenia generuje ciąg do wydrukowania zawierający nazwę i typ zmiennej lub argumentu oraz jego wartość. Ten ciąg jest wyświetlany w oknie czujki lub w oknie zmiennych lokalnych IDE.

     Biorąc `BSTR` pod uwagę i [interfejs IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) aparat debugowania (DE) można utworzyć interfejs [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) przez analizowanie wyrażenia. Biorąc `IDebugExpression2` pod uwagę interfejs, DE można uzyskać wartość za pomocą synchronicznej lub asynchronicznej oceny wyrażenia. Ta wartość, wraz z nazwą i typem zmiennej lub argumentu, jest wysyłana do IDE do wyświetlania.

## <a name="see-also"></a>Zobacz też
- [Interfejsy oceny ekspresji](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
