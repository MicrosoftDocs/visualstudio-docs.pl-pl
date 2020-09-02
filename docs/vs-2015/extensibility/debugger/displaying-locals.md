---
title: Wyświetlanie elementów lokalnych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cdbba0cfa48792127accc71cba75f8542556d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793722"
---
# <a name="displaying-locals"></a>Wyświetlanie zmiennych lokalnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wykonywanie zawsze odbywa się w kontekście metody, znanej również jako zawierająca metodę lub bieżącą metodę. Gdy wykonywanie jest wstrzymane, program Visual Studio wywołuje aparat debugowania (DE), aby uzyskać listę zmiennych lokalnych i argumentów, łącznie nazywanych lokalnymi metodami. Program Visual Studio wyświetla te ustawienia regionalne i ich wartości w oknie **zmiennych lokalnych** .  
  
 Aby wyświetlić elementy lokalne, odwołuje się do metody [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) należącej do EE i nadaje mu kontekst oceny, czyli dostawcę symboli (SP), bieżący adres wykonywania i obiekt spinacza. Aby uzyskać więcej informacji, zobacz temat informacje o [kontekście oceny](../../extensibility/debugger/evaluation-context.md). Jeśli wywołanie powiedzie się, `IDebugExpressionEvaluator::GetMethodProperty` Metoda zwraca obiekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje metodę, która zawiera bieżący adres wykonania.  
  
 Nocalls [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) uzyskać obiekt [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , który jest filtrowany w celu zwrócenia tylko wartości lokalnych i wyliczeniowych, aby utworzyć listę struktur [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) . Każda struktura zawiera nazwę, typ i wartość lokalnego. Typ i wartość są przechowywane jako sformatowane ciągi, odpowiednie do wyświetlania. Nazwa, typ i wartość są zwykle wyświetlane razem w jednym wierszu okna **zmiennych lokalnych** .  
  
> [!NOTE]
> W oknach **QuickWatch** i **Watch** są również wyświetlane zmienne o takim samym formacie jak nazwa, wartość i typ. Jednak te wartości są uzyskiwane przez wywołanie [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zamiast `IDebugProperty2::EnumChildren` .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykłady implementacji zmiennych lokalnych](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Używa przykładów do przechodzenia przez proces wdrażania elementów lokalnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 Wyjaśniono, że gdy aparat debugowania (Niemcy) wywołuje ewaluatora wyrażeń (EE), przekazuje trzy argumenty.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
