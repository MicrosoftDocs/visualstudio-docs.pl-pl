---
title: Wyświetlanie lokalnych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738931"
---
# <a name="display-locals"></a>Pokaż lokalnych
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wykonanie zawsze odbywa się w kontekście metody, znanej również jako metoda zawierająca lub bieżąca metoda. Po wstrzymaniu wykonywania visual studio wywołuje aparat debugowania (DE), aby uzyskać listę zmiennych lokalnych i argumentów, łącznie nazywanych lokalnymi metodami. Visual Studio wyświetla te lokalne i ich wartości w oknie **Zmiennych lokalnych.**

 Aby wyświetlić lokalnych, DE wywołuje [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metody należącej do EE i nadaje mu kontekst oceny, czyli dostawcy symbolu (SP), bieżący adres wykonywania i obiekt spinacza. Aby uzyskać więcej informacji, zobacz [Kontekst oceny](../../extensibility/debugger/evaluation-context.md). Jeśli wywołanie zakończy `IDebugExpressionEvaluator::GetMethodProperty` się pomyślnie, metoda zwraca [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiektu, który reprezentuje metodę, która zawiera bieżący adres wykonywania.

 DE wywołuje [EnumChildren,](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) aby uzyskać [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiektu, który jest filtrowany, aby powrócić tylko lokalnych i wyliczane do tworzenia listy [struktur DEBUG_PROPERTY_INFO.](../../extensibility/debugger/reference/debug-property-info.md) Każda struktura zawiera nazwę, typ i wartość lokalnego. Typ i wartość są przechowywane jako sformatowane ciągi, odpowiednie do wyświetlania. Nazwa, typ i wartość są zazwyczaj wyświetlane razem w jednym wierszu okna **Locals.**

> [!NOTE]
> Okna **QuickWatch** i **Watch** wyświetlają również zmienne o tym samym formacie nazwy, wartości i typu. Jednak te wartości są uzyskiwane przez wywołanie `IDebugProperty2::EnumChildren` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zamiast .

## <a name="in-this-section"></a>W tej sekcji
 [Przykładowa implementacja miejscowych](../../extensibility/debugger/sample-implementation-of-locals.md) Używa przykładów, aby przejść przez proces wdrażania lokalnych.

## <a name="related-sections"></a>Powiązane sekcje
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) Wyjaśnia, że gdy aparat debugowania (DE) wywołuje oceniającego wyrażenie (EE), przekazuje trzy argumenty.

## <a name="see-also"></a>Zobacz też
 [Napisz ewaluatora wyrażenia CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
