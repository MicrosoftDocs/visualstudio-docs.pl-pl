---
title: Wdrażanie oceniającego wyrażenie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738538"
---
# <a name="implement-an-expression-evaluator"></a>Implementowanie oceniającego wyrażenie
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ocena wyrażenia jest złożoną interagry między aparat debugowania (DE), dostawca symbolu (SP), obiekt spinacza i oceniający wyrażenie (EE). Te cztery składniki są połączone przez interfejsy, które są implementowane przez jeden składnik i używane przez inny.

 EE przyjmuje wyrażenie z DE w postaci ciągu i analizuje lub ocenia go. EE uruchamia następujące interfejsy, które są używane przez DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE wywołuje obiekt spinacza, dostarczone przez DE, aby uzyskać wartość symboli i obiektów. EE zużywa następujące interfejsy, które są implementowane przez DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE uruchamia [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`udostępnia mechanizm opisujący wynik oceny wyrażenia, takich jak zmienna lokalna, prymitywne lub obiekt visual studio, który następnie wyświetla odpowiednie informacje w **locals**, **Watch**, lub **natychmiastowe** okna.

  SP jest przekazytrywalna EE przez DE, gdy prosi o informacje. Sp uruchamia interfejsy opisujące adresy i pola, takie jak następujące interfejsy i ich pochodne:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE zużywa wszystkie te interfejsy.

## <a name="in-this-section"></a>W tej sekcji
 [Strategia wdrażania ewaluacji wyrażeń](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definiuje trzyetapowy proces strategii wdrażania oceniającego wyrażenia (EE).

## <a name="see-also"></a>Zobacz też
- [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
