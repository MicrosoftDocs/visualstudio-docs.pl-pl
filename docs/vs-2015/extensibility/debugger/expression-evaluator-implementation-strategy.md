---
title: Strategia implementacji ewaluatora wyrażeń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824701"
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategia implementacji ewaluatora wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Jednym z metod szybkiego tworzenia ewaluatora wyrażeń jest zaimplementowanie w pierwszej kolejności minimalnego kodu niezbędnego do wyświetlenia zmiennych lokalnych w oknie **lokalne** . Warto pamiętać, że każdy wiersz w oknie **zmiennych lokalnych** wyświetla nazwę, typ i wartość zmiennej lokalnej oraz że wszystkie trzy są reprezentowane przez obiekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Nazwę, typ i wartość zmiennej lokalnej można uzyskać z `IDebugProperty2` obiektu przez wywołanie jego metody [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Aby uzyskać więcej informacji o sposobie wyświetlania zmiennych lokalnych w oknie **lokalne** , zobacz [Wyświetlanie ustawień lokalnych](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Dyskusja  
 Możliwa sekwencja implementacji rozpoczyna się od implementacji [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Metody [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) i [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) muszą być zaimplementowane do wyświetlania elementów lokalnych. Wywołanie `IDebugExpressionEvaluator::GetMethodProperty` zwraca `IDebugProperty2` obiekt, który reprezentuje metodę: to jest obiekt [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Same metody nie są wyświetlane w oknie **zmiennych lokalnych** .  
  
 Metoda [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) powinna zostać zaimplementowana dalej. Aparat debugowania (DE) wywołuje tę metodę, aby uzyskać listę zmiennych lokalnych i argumentów przez przekazanie `IDebugProperty2::EnumChildren` `guidFilter` argumentu `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` wywołuje metody [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) i [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), łącząc wyniki w jednym wyliczeniu. Aby uzyskać więcej informacji, zobacz [Wyświetlanie ustawień lokalnych](../../extensibility/debugger/displaying-locals.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie ewaluatora wyrażeń](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)
