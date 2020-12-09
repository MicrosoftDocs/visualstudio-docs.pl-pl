---
title: Wyświetlanie elementów lokalnych | Microsoft Docs
description: Zapoznaj się z listą zmiennych lokalnych i argumentów, łącznie nazywanymi lokalnymi metody, które są wyświetlane po wstrzymaniu wykonywania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ddc7bc564e4e294144eeb3fa34db8bdf73971053
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915547"
---
# <a name="display-locals"></a>Wyświetl elementy lokalne
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wykonywanie zawsze odbywa się w kontekście metody, znanej również jako zawierająca metodę lub bieżącą metodę. Gdy wykonywanie jest wstrzymane, program Visual Studio wywołuje aparat debugowania (DE), aby uzyskać listę zmiennych lokalnych i argumentów, łącznie nazywanych lokalnymi metodami. Program Visual Studio wyświetla te ustawienia regionalne i ich wartości w oknie **zmiennych lokalnych** .

 Aby wyświetlić elementy lokalne, odwołuje się do metody [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) należącej do EE i nadaje mu kontekst oceny, czyli dostawcę symboli (SP), bieżący adres wykonywania i obiekt spinacza. Aby uzyskać więcej informacji, zobacz temat informacje o [kontekście oceny](../../extensibility/debugger/evaluation-context.md). Jeśli wywołanie powiedzie się, `IDebugExpressionEvaluator::GetMethodProperty` Metoda zwraca obiekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje metodę, która zawiera bieżący adres wykonania.

 Nocalls [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) uzyskać obiekt [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , który jest filtrowany w celu zwrócenia tylko wartości lokalnych i wyliczeniowych, aby utworzyć listę struktur [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) . Każda struktura zawiera nazwę, typ i wartość lokalnego. Typ i wartość są przechowywane jako sformatowane ciągi, odpowiednie do wyświetlania. Nazwa, typ i wartość są zwykle wyświetlane razem w jednym wierszu okna **zmiennych lokalnych** .

> [!NOTE]
> W oknach **QuickWatch** i **Watch** są również wyświetlane zmienne o takim samym formacie jak nazwa, wartość i typ. Jednak te wartości są uzyskiwane przez wywołanie [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zamiast `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>W tej sekcji
 [Przykładowa implementacja elementów lokalnych](../../extensibility/debugger/sample-implementation-of-locals.md) Używa przykładów do przechodzenia przez proces wdrażania elementów lokalnych.

## <a name="related-sections"></a>Sekcje pokrewne
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) Wyjaśniono, że gdy aparat debugowania (Niemcy) wywołuje ewaluatora wyrażeń (EE), przekazuje trzy argumenty.

## <a name="see-also"></a>Zobacz też
 [Napisz ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
