---
title: Przykład implementacji lokalnych | Microsoft Docs
description: Dowiedz się, Visual Studio w tym artykule pobiera lokalne wartości dla metody z ewaluatora wyrażeń.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ac52f1524c4be2e4a7afcbd21fb437977fb663e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902283"
---
# <a name="sample-implementation-of-locals"></a>Przykładowa implementacja lokalizacji lokalnych
> [!IMPORTANT]
> W Visual Studio 2015 r. ten sposób implementowania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania ewaluatorów wyrażeń CLR, zobacz [ClR expression evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) (Ewaluatory wyrażeń CLR) i Managed expression evaluator sample (Przykład zarządzanego [ewaluatora wyrażeń).](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Poniżej przedstawiono omówienie sposobu Visual Studio lokalnych dla metody z ewaluatora wyrażeń (EE):

1. Visual Studio wywołuje element [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) aparatu debugowania w celu uzyskania obiektu [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) reprezentującego wszystkie właściwości ramki stosu, w tym obiekty lokalne.

2. `IDebugStackFrame2::GetDebugProperty` Wywołuje [Metodę GetMethodProperty,](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) aby uzyskać obiekt opisujący metodę, w której miało miejsce punkt przerwania. De dostarcza dostawcę symboli ([IDebugSymbolProvider),](../../extensibility/debugger/reference/idebugsymbolprovider.md)adres ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) i binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` Wywołuje [metodę GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) z podanym obiektem , aby uzyskać element `IDebugAddress` [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) reprezentujący metodę zawierającą określony adres.

4. Interfejs `IDebugContainerField` jest wyszukiwany dla [interfejsu IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Jest to interfejs, który zapewnia dostęp do lokalizacji lokalnych metody.

5. `IDebugExpressionEvaluator::GetMethodProperty` Iniektuje klasę (wywoływaną w przykładzie), która uruchamia `CFieldProperty` `IDebugProperty2` interfejs reprezentujący lokalne metody. Obiekt `IDebugMethodField` jest umieszczany w tym `CFieldProperty` obiekcie wraz z `IDebugSymbolProvider` obiektami , i `IDebugAddress` `IDebugBinder` .

6. Podczas inicjowania obiektu metoda GetInfo jest wywoływana na obiekcie w celu uzyskania struktury FIELD_INFO zawierającej wszystkie wyświetlane informacje o `CFieldProperty` samej [](../../extensibility/debugger/reference/idebugfield-getinfo.md) `IDebugMethodField` metodzie. [](../../extensibility/debugger/reference/field-info.md)

7. `IDebugExpressionEvaluator::GetMethodProperty` Funkcja `CFieldProperty` zwraca obiekt jako `IDebugProperty2` obiekt .

8. Visual Studio obiekt [Enum Wyliczeniowy](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) dla zwróconego obiektu za pomocą filtru , który zwraca obiekt `IDebugProperty2` `guidFilterLocalsPlusArgs` [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) zawierający lokalne dane metody. To wyliczenie jest wypełniane przez wywołania do [enumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) i [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio [wywołań Dalej,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) aby uzyskać [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) strukturę dla każdego lokalnego. Ta struktura zawiera wskaźnik do `IDebugProperty2` interfejsu lokalnego.

10. Visual Studio [getPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) dla każdego lokalnego uzyskać nazwę, wartość i typ lokalnego. Te informacje są wyświetlane w **oknie Locals (Lokalne).**

## <a name="in-this-section"></a>W tej sekcji
 [Implementowanie getMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Opisuje implementację [getMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Wyliczanie wartości regionalnych](../../extensibility/debugger/enumerating-locals.md) Opisuje sposób, w jaki aparat debugowania (DE) wykonuje wywołanie w celu wyliczenia zmiennych lokalnych lub argumentów.

 [Uzyskiwanie właściwości lokalnych](../../extensibility/debugger/getting-local-properties.md) Opisuje, jak DE wykonuje wywołanie, aby uzyskać nazwę, typ i wartość co najmniej jednego lokalnego.

 [Uzyskiwanie wartości lokalnych](../../extensibility/debugger/getting-local-values.md) W tym artykule omówiono pobieranie wartości lokalnej, która wymaga usług obiektu binder podanego w kontekście oceny.

 [Ocenianie lokalizacji lokalnych](../../extensibility/debugger/evaluating-locals.md) Wyjaśnia, jak są oceniane wartości lokalne.

## <a name="related-sections"></a>Powiązane sekcje
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) Dostarcza argumenty, które są przekazywane, gdy DE wywołuje ewaluator wyrażeń (EE).

 [Przykładowy kod MyCEE](/previous-versions/) Demonstruje jedno podejście implementacji do tworzenia ewaluatora wyrażeń dla języka MyC.

## <a name="see-also"></a>Zobacz też
- [Wyświetlanie lokalizacji lokalnych](../../extensibility/debugger/displaying-locals.md)