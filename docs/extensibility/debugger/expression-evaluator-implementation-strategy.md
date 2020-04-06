---
title: Strategia wdrażania ewaluatora ekspresji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738667"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia wdrażania ewaluacji wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Jednym z podejść do szybkiego tworzenia oceniającego wyrażenie (EE) jest najpierw zaimplementowanie minimalnego kodu niezbędnego do wyświetlania zmiennych lokalnych w oknie **Zmienne lokalne.** Warto zdać sobie sprawę, że każdy wiersz w oknie **Locals** wyświetla nazwę, typ i wartość zmiennej lokalnej i że wszystkie trzy są reprezentowane przez obiekt [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md) Nazwa, typ i wartość zmiennej lokalnej jest `IDebugProperty2` uzyskiwana z obiektu przez wywołanie jego [Metody GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Aby uzyskać więcej informacji na temat wyświetlania zmiennych lokalnych w oknie **Zmienne lokalne,** zobacz [Wyświetlanie lokalnych .](../../extensibility/debugger/displaying-locals.md)

## <a name="discussion"></a>Dyskusji
 Możliwa sekwencja implementacji rozpoczyna się od implementacji [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). [Analizowanie](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) i [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metody muszą być zaimplementowane do wyświetlania lokalnych. Wywołanie `IDebugExpressionEvaluator::GetMethodProperty` `IDebugProperty2` zwraca obiekt, który reprezentuje metodę: czyli [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) obiektu. Same metody nie są wyświetlane w oknie **Zmiennych** lokalnych.

 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metoda powinna być zaimplementowana dalej. Aparat debugowania (DE) wywołuje tę metodę, aby uzyskać listę `IDebugProperty2::EnumChildren` `guidFilter` zmiennych `guidFilterLocalsPlusArgs`lokalnych i argumentów, przekazując argument . `IDebugProperty2::EnumChildren`wywołuje [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) i [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), łącząc wyniki w jednym wyliczeniu. Zobacz [Wyświetlanie lokalnych, aby](../../extensibility/debugger/displaying-locals.md) uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też
- [Implementowanie oceniającego wyrażenie](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Pokaż lokalnych](../../extensibility/debugger/displaying-locals.md)
