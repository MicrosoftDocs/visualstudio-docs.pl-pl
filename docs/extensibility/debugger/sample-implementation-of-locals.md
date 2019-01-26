---
title: Przykładowy implementacji zmiennych lokalnych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd9bfaf04d1c121c3aa019e7e01393ae1ca5635d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922954"
---
# <a name="sample-implementation-of-locals"></a>Przykłady implementacji zmiennych lokalnych
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Uzyskać informacji o implementowaniu ewaluatory wyrażeń CLR, zobacz [ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykładowe ewaluatora wyrażeń zarządzane](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Poniżej przedstawiono omówienie, jak Visual Studio pobiera zmienne dla metody z Ewaluator wyrażeń (EE):  
  
1.  Program Visual Studio wywołuje aparat debugowania (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) można pobrać [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje wszystkie właściwości ramki stosu, w tym zmienne lokalne.  
  
2.  `IDebugStackFrame2::GetDebugProperty` wywołania [metody GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) do obiektu, który opisuje metodę, w którym wystąpił punkt przerwania. DE dostarcza dostawca symboli ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adres ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)), a obiekt wiążący ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` wywołania [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) z podanym `IDebugAddress` można uzyskać [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) reprezentujący metodę, zawierający podany adres.  
  
4.  `IDebugContainerField` Zostaje przesłane zapytanie interfejsu [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfejsu. Jest to interfejs, który zapewnia dostęp do zmiennych lokalnych metody.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` tworzy klasę (o nazwie `CFieldProperty` w przykładzie), które jest uruchamiane `IDebugProperty2` interfejsu do reprezentowania metody zmiennych lokalnych. `IDebugMethodField` Obiekt jest umieszczany w tym `CFieldProperty` obiektu wraz z `IDebugSymbolProvider`, `IDebugAddress`, i `IDebugBinder` obiektów.  
  
6.  Gdy `CFieldProperty` co inicjacja obiektu, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) jest wywoływana w `IDebugMethodField` można uzyskać [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) strukturę, która zawiera wszystkie informacje zawiera temat sama metoda.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Zwraca `CFieldProperty` obiektu jako `IDebugProperty2` obiektu.  
  
8.  Visual Studio wywołania [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) w zwracanym `IDebugProperty2` obiektu z filtrem `guidFilterLocalsPlusArgs`, co powoduje zwrócenie [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiekt zawierający metodę zmiennych lokalnych. To wyliczenie jest wypełniane przez wywołania [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) i [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio wywołania [dalej](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) uzyskać [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) strukturę dla każdej lokalnej. Ta struktura zawiera wskaźnik do `IDebugProperty2` interfejsu lokalnej.  
  
10. Visual Studio wywołania [getpropertyinfo —](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) dla każdej lokalnej można uzyskać nazwę, wartość i typ lokalnego. Te informacje są wyświetlane w **lokalne** okna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie metody GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 W tym artykule opisano implementację [metody GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Wyliczanie zmiennych lokalnych](../../extensibility/debugger/enumerating-locals.md)  
 W tym artykule opisano, jak aparat debugowania (DE) nawiązuje połączenie wyliczanie zmiennych lokalnych lub argumentów.  
  
 [Pobieranie właściwości lokalnych](../../extensibility/debugger/getting-local-properties.md)  
 W tym artykule opisano, jak DE dzwoni do pobierania nazwy, typ i wartość jednego lub więcej zmiennych lokalnych.  
  
 [Pobieranie wartości lokalnych](../../extensibility/debugger/getting-local-values.md)  
 W tym artykule omówiono pobieranie wartości elementu lokalnego, który wymaga usług obiekt integratora, określone przez kontekst oceny.  
  
 [Oceń zmiennych lokalnych](../../extensibility/debugger/evaluating-locals.md)  
 W tym artykule wyjaśniono, jak są obliczane zmiennych lokalnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 Zawiera argumenty, które są przekazywane, gdy DE wywołuje Ewaluator wyrażeń (EE).  
  
 [Przykładowe MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Demonstruje jedno z podejść do tworzenia ewaluatora wyrażeń dla języków MyC implementacji.  
  
## <a name="see-also"></a>Zobacz także  
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)