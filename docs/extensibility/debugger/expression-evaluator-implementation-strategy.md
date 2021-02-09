---
title: Strategia implementacji ewaluatora wyrażeń | Microsoft Docs
description: Poznaj strategię tworzenia ewaluatora wyrażeń, wykonując najpierw kod, aby wyświetlić zmienne lokalne w oknie zmiennych lokalnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d7527c361a889d5aa1f19ec7a211f8aeb8dcbd15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921391"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia implementacji ewaluatora wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Jednym z metod szybkiego tworzenia ewaluatora wyrażeń jest zaimplementowanie w pierwszej kolejności minimalnego kodu niezbędnego do wyświetlenia zmiennych lokalnych w oknie **lokalne** . Warto pamiętać, że każdy wiersz w oknie **zmiennych lokalnych** wyświetla nazwę, typ i wartość zmiennej lokalnej oraz że wszystkie trzy są reprezentowane przez obiekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Nazwa, typ i wartość zmiennej lokalnej są uzyskiwane z `IDebugProperty2` obiektu przez wywołanie jego metody [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Aby uzyskać więcej informacji o sposobie wyświetlania zmiennych lokalnych w oknie **lokalne** , zobacz [Wyświetlanie ustawień lokalnych](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Dyskusja
 Możliwa sekwencja implementacji rozpoczyna się od implementacji [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Metody [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) i [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) muszą być zaimplementowane do wyświetlania elementów lokalnych. Wywołanie `IDebugExpressionEvaluator::GetMethodProperty` zwraca `IDebugProperty2` obiekt, który reprezentuje metodę: to jest obiekt [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Same metody nie są wyświetlane w oknie **zmiennych lokalnych** .

 Metoda [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) powinna zostać zaimplementowana dalej. Aparat debugowania (DE) wywołuje tę metodę, aby uzyskać listę zmiennych lokalnych i argumentów przez przekazanie `IDebugProperty2::EnumChildren` `guidFilter` argumentu `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` wywołuje metody [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) i [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), łącząc wyniki w jednym wyliczeniu. Aby uzyskać więcej informacji, zobacz temat [Wyświetlanie elementów lokalnych](../../extensibility/debugger/displaying-locals.md) .

## <a name="see-also"></a>Zobacz też
- [Implementowanie ewaluatora wyrażeń](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Wyświetl elementy lokalne](../../extensibility/debugger/displaying-locals.md)
