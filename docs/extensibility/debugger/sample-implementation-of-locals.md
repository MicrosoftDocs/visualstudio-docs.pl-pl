---
title: Przykładowa implementacja elementów lokalnych | Microsoft Docs
description: Dowiedz się, w jaki sposób program Visual Studio pobiera zmienne lokalne dla metody z ewaluatora wyrażeń w tym artykule.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4bf07dc6f47391af14c878021c742c2cb461bc85
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070417"
---
# <a name="sample-implementation-of-locals"></a>Przykładowa implementacja elementów lokalnych
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Poniżej przedstawiono omówienie sposobu, w jaki program Visual Studio pobiera zmienne lokalne dla metody z ewaluatora wyrażeń (EE):

1. Program Visual Studio wywołuje [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) aparatu debugowania, aby uzyskać obiekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje wszystkie właściwości ramki stosu, łącznie z lokalnymi.

2. `IDebugStackFrame2::GetDebugProperty` wywołuje [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) , aby uzyskać obiekt, który opisuje metodę, w której wystąpił punkt przerwania. DE dostawy dostawca symboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adres ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) i spinacz ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` wywołuje [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) z podanym `IDebugAddress` obiektem, aby uzyskać [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) , który reprezentuje metodę zawierającą określony adres.

4. `IDebugContainerField`Interfejs jest pytany dla interfejsu [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Jest to interfejs, który zapewnia dostęp do zmiennych lokalnych metody.

5. `IDebugExpressionEvaluator::GetMethodProperty` tworzy wystąpienie klasy (wywoływana `CFieldProperty` w przykładzie), która uruchamia `IDebugProperty2` interfejs do reprezentowania ustawień lokalnych metody. `IDebugMethodField`Obiekt jest umieszczony w tym `CFieldProperty` obiekcie wraz z `IDebugSymbolProvider` `IDebugAddress` obiektami,, i `IDebugBinder` .

6. Po `CFieldProperty` zainicjowaniu obiektu [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) jest wywoływana na obiekcie, `IDebugMethodField` Aby uzyskać strukturę [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) , która zawiera wszystkie informacje, które można wyświetlić.

7. `IDebugExpressionEvaluator::GetMethodProperty` zwraca `CFieldProperty` obiekt jako `IDebugProperty2` obiekt.

8. Program Visual Studio wywołuje [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) na zwracanym `IDebugProperty2` obiekcie z filtrem `guidFilterLocalsPlusArgs` , który zwraca obiekt [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) zawierający elementy lokalne metody. To wyliczenie jest wypełniane przez wywołania do [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) i [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Program Visual Studio wywołuje [obok](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) siebie strukturę [DEBUG_PROPERTY_INFOą](../../extensibility/debugger/reference/debug-property-info.md) dla każdego lokalnego. Ta struktura zawiera wskaźnik do `IDebugProperty2` interfejsu dla lokalnego.

10. Program Visual Studio wywołuje [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) dla każdego lokalnego, aby uzyskać nazwę, wartość i typ lokalnego. Te informacje są wyświetlane w oknie **zmiennych lokalnych** .

## <a name="in-this-section"></a>W tej sekcji
 [Implementuj GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Opisuje implementację programu [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Wyliczanie zmiennych lokalnych](../../extensibility/debugger/enumerating-locals.md) Opisuje, jak aparat debugowania (DE) wykonuje wywołanie wyliczające zmienne lokalne lub argumenty.

 [Pobierz właściwości lokalne](../../extensibility/debugger/getting-local-properties.md) Opisuje, jak cofnięte jest wywołanie pobrania nazwy, typu i wartości co najmniej jednego elementu lokalnego.

 [Pobierz wartości lokalne](../../extensibility/debugger/getting-local-values.md) W tym artykule omówiono pobieranie wartości lokalnej, która wymaga usług obiektu spinacza danego kontekstu szacowania.

 [Oceń wartości lokalne](../../extensibility/debugger/evaluating-locals.md) Wyjaśnia, jak są oceniane wartości lokalne.

## <a name="related-sections"></a>Sekcje pokrewne
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) Dostarcza argumenty, które są przesyłane, gdy wywołują ewaluatora wyrażeń.

 [Przykład mycee](/previous-versions/) Przedstawia jedno podejście implementacji do tworzenia ewaluatora wyrażeń dla języka MyC.

## <a name="see-also"></a>Zobacz też
- [Wyświetlanie ustawień lokalnych](../../extensibility/debugger/displaying-locals.md)