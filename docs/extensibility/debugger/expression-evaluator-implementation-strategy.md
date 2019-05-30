---
title: Strategia implementacji ewaluatora wyrażeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee0842f8375faeca7e715d4b20c73ca13598dbc3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353741"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia implementacji ewaluatora wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Uzyskać informacji o implementowaniu ewaluatory wyrażeń CLR, zobacz [ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykładowe ewaluatora wyrażeń zarządzane](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Jedno z podejść do szybkiego tworzenia ewaluatora wyrażeń (EE) jest najpierw implementacja minimalne kod wymagany do wyświetlania zmiennych lokalnych w **lokalne** okna. Warto należy pamiętać, że każdy wiersz w **lokalne** okna wyświetla nazwę, typ i wartość zmiennej lokalnej, a wszystkie trzy są reprezentowane przez [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiektu. Nazwa, typ i wartość zmiennej lokalnej jest uzyskiwana z `IDebugProperty2` obiektu przez wywołanie jego [getpropertyinfo —](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Aby uzyskać więcej informacji o sposobie wyświetlaniu zmiennych lokalnych w **lokalne** okna, zobacz [wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Dyskusja
 Sekwencja możliwą implementację zaczyna się od wykonania [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). [Przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) i [metody GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metody muszą być zaimplementowane w celu wyświetlenia zmiennych lokalnych. Wywoływanie `IDebugExpressionEvaluator::GetMethodProperty` zwraca `IDebugProperty2` obiekt, który reprezentuje metodę: oznacza to, że [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) obiektu. Metody sami nie są wyświetlane w **lokalne** okna.

 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metody, które powinny być zrealizowane dalej. Aparat debugowania (DE) wywołuje tę metodę, aby uzyskać listę zmiennych lokalnych i argumenty, przekazując `IDebugProperty2::EnumChildren` `guidFilter` argument `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` wywołania [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) i [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), łączenie wyników w jednym wyliczenia. Zobacz [wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także
- [Implementowanie ewaluatora wyrażeń](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)