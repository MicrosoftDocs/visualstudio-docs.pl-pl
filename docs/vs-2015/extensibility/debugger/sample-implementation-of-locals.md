---
title: Przykładowy implementacji zmiennych lokalnych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab81718837f6af8a230348d5e0a34f1da0a2c7bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092048"
---
# <a name="sample-implementation-of-locals"></a>Przykłady implementacji zmiennych lokalnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Poniżej przedstawiono omówienie, jak Visual Studio uzyskuje dostęp do zmiennych lokalnych dla metody z Ewaluator wyrażeń (EE):  
  
1. Program Visual Studio wywołuje aparat debugowania (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) można pobrać [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje wszystkie właściwości ramki stosu, w tym zmienne lokalne.  
  
2. `IDebugStackFrame2::GetDebugProperty` wywołania [metody GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) uzyskać obiekt, który opisuje metodę, w którym wystąpił punkt przerwania. DE dostarcza dostawca symboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adres ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)), a obiekt wiążący ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3. `IDebugExpressionEvaluator::GetMethodProperty` wywołania [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) z podanym `IDebugAddress` można uzyskać [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) reprezentujący metodę, zawierający podany adres.  
  
4. `IDebugContainerField` Zostaje przesłane zapytanie interfejsu [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfejsu. Jest to interfejs, który zapewnia dostęp do zmiennych lokalnych metody.  
  
5. `IDebugExpressionEvaluator::GetMethodProperty` tworzy klasę (o nazwie `CFieldProperty` w przykładzie), który zawiera `IDebugProperty2` interfejsu do reprezentowania metody zmiennych lokalnych. `IDebugMethodField` Obiekt jest umieszczany w tym `CFieldProperty` obiektu wraz z `IDebugSymbolProvider`, `IDebugAddress` i `IDebugBinder` obiektów.  
  
6. Gdy `CFieldProperty` co inicjacja obiektu, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) jest wywoływana w `IDebugMethodField` obiektu w celu uzyskania [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) strukturę, która zawiera wszystkie informacje zawiera temat sama metoda .  
  
7. `IDebugExpressionEvaluator::GetMethodProperty` Zwraca `CFieldProperty` obiektu jako `IDebugProperty2` obiektu.  
  
8. Visual Studio wywołania [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) na zwracanego `IDebugProperty2` obiektu z filtrem `guidFilterLocalsPlusArgs`. Spowoduje to zwrócenie [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiekt zawierający metodę zmiennych lokalnych. To wyliczenie jest wypełniane przez wywołania [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) i [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio wywołania [dalej](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) uzyskać [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) strukturę dla każdej lokalnej. Ta struktura zawiera wskaźnik do `IDebugProperty2` interfejsu lokalnej.  
  
10. Visual Studio wywołania [getpropertyinfo —](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) dla każdej lokalnej można uzyskać nazwę, wartość i typ lokalnego. Jest to informacja, która jest wyświetlana w **lokalne** okna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie metody GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 W tym artykule opisano implementację [metody GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Wyliczanie zmiennych lokalnych](../../extensibility/debugger/enumerating-locals.md)  
 W tym artykule opisano, jak aparat debugowania (DE) nawiązuje połączenie wyliczanie zmiennych lokalnych lub argumentów.  
  
 [Pobieranie właściwości lokalnych](../../extensibility/debugger/getting-local-properties.md)  
 W tym artykule opisano, jak DE dzwoni do pobierania nazwy, typ i wartość jednego lub więcej zmiennych lokalnych.  
  
 [Pobieranie wartości lokalnych](../../extensibility/debugger/getting-local-values.md)  
 W tym artykule omówiono uzyskiwania wartości elementu lokalnego, który wymaga usług obiekt integratora, określone przez kontekst oceny.  
  
 [Ocenianie zmiennych lokalnych](../../extensibility/debugger/evaluating-locals.md)  
 W tym artykule wyjaśniono, jak są obliczane zmiennych lokalnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 Zawiera argumenty, które są przekazywane, gdy DE wywołuje Ewaluator wyrażeń (EE).  
  
 [Przykładowe MyCEE](http://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Demonstruje jedno z podejść do tworzenia ewaluatora wyrażeń dla języków MyC implementacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)
