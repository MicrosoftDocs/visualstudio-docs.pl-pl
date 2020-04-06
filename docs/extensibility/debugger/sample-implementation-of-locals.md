---
title: Przykładowe wdrożenie miejscowych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713070"
---
# <a name="sample-implementation-of-locals"></a>Przykładowa implementacja miejscowych
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Poniżej przedstawiono omówienie sposobu, w jaki program Visual Studio pobiera miejscowych dla metody z oceniającego wyrażenie (EE):

1. Visual Studio wywołuje aparat debugowania (DE) [GetDebugProperty,](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) aby uzyskać [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiektu, który reprezentuje wszystkie właściwości ramki stosu, w tym lokalnych.

2. `IDebugStackFrame2::GetDebugProperty`wywołuje [GetMethodProperty,](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) aby uzyskać obiekt, który opisuje metodę, w której punkt przerwania się stało. DE dostarcza dostawcę symboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adres ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) i spoiwo ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty`wywołuje [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) z `IDebugAddress` dostarczonym obiektem, aby uzyskać [IDebugContainerField,](../../extensibility/debugger/reference/idebugcontainerfield.md) który reprezentuje metodę zawierającą określony adres.

4. Interfejs `IDebugContainerField` jest wyszukiwany dla interfejsu [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Jest to interfejs, który daje dostęp do lokalnych metod.

5. `IDebugExpressionEvaluator::GetMethodProperty`wystąpienia klasy (wywoływane `CFieldProperty` w przykładzie), `IDebugProperty2` który uruchamia interfejs do reprezentowania lokalnych metody. Obiekt `IDebugMethodField` zostanie umieszczony `CFieldProperty` w tym `IDebugSymbolProvider`obiekcie wraz z obiektem , `IDebugAddress`i `IDebugBinder` obiektami.

6. Po `CFieldProperty` zainicjowaniu obiektu [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) jest wywoływana na `IDebugMethodField` obiekcie, aby uzyskać [strukturę FIELD_INFO,](../../extensibility/debugger/reference/field-info.md) która zawiera wszystkie wyświetlane informacje o samej metodzie.

7. `IDebugExpressionEvaluator::GetMethodProperty`zwraca `CFieldProperty` obiekt jako `IDebugProperty2` obiekt.

8. Visual Studio wywołuje [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) na zwrócony `IDebugProperty2` obiekt z filtrem `guidFilterLocalsPlusArgs`, który zwraca [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiekt zawierający lokalnych metod. To wyliczenie jest wypełniane przez wywołania [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) i [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio wywołuje [Next,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) aby uzyskać [strukturę DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) dla każdego lokalnego. Ta struktura zawiera wskaźnik `IDebugProperty2` do interfejsu dla lokalnego.

10. Visual Studio wywołuje [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) dla każdego lokalnego, aby uzyskać nazwę, wartość i typ lokalnego. Te informacje są wyświetlane w oknie **Zmiennoprawno-Miejscowi.**

## <a name="in-this-section"></a>W tej sekcji
 [Implementowanie właściwości GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Opisuje implementację [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Wyliczaj mieszkańców](../../extensibility/debugger/enumerating-locals.md) Opisuje, jak aparat debugowania (DE) wywołuje wyliczyć zmienne lokalne lub argumenty.

 [Uzyskaj właściwości lokalne](../../extensibility/debugger/getting-local-properties.md) Opisuje, jak DE wykonuje wywołanie, aby uzyskać nazwę, typ i wartość jednego lub więcej miejscowych.

 [Uzyskaj wartości lokalne](../../extensibility/debugger/getting-local-values.md) W tym artykule omówiono uzyskanie wartości lokalnej, która wymaga usług obiektu spinacza podane przez kontekst oceny.

 [Ocena mieszkańców](../../extensibility/debugger/evaluating-locals.md) Wyjaśnia, jak mieszkańcy są oceniane.

## <a name="related-sections"></a>Powiązane sekcje
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) Zawiera argumenty, które są przekazywane, gdy DE wywołuje oceniającego wyrażenie (EE).

 [Próbka MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) Demonstruje jedno podejście implementacji do tworzenia oceniającego wyrażenie dla języka MyC.

## <a name="see-also"></a>Zobacz też
- [Wyświetlanie lokalnych](../../extensibility/debugger/displaying-locals.md)
