---
title: Implementowanie ewaluatora wyrażeń | Microsoft Docs
description: Dowiedz się więcej na temat oceniania wyrażenia, które obejmuje aparat debugowania, dostawcę symboli, obiekt spinacza oraz ewaluatora wyrażeń.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121bd17e2343cfbba509e85d78ba37b57964f895
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947674"
---
# <a name="implement-an-expression-evaluator"></a>Implementowanie ewaluatora wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ocenianie wyrażenia to złożona współpraca między aparatem debugowania (DE), dostawcą symboli (SP), obiektem spinacza oraz ewaluatora wyrażeń (EE). Te cztery składniki są połączone przez interfejsy, które są implementowane przez jeden składnik i zużywane przez inny.

 EE Pobiera wyrażenie od DE w formie ciągu i analizuje je lub oblicza. Na stronie EE są uruchamiane następujące interfejsy, które są używane przez DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE wywołują obiekt spinacza dostarczony przez DE, aby uzyskać wartość symboli i obiektów. Na stronie EE są używane następujące interfejsy, które są implementowane przez DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  Na stronie EE są uruchamiane [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` zapewnia mechanizm do opisywania wyniku oceny wyrażenia, takiego jak zmienna lokalna, pierwotna lub obiekt do programu Visual Studio, który następnie wyświetla odpowiednie informacje w oknie **zmiennych lokalnych**, **czujka** lub **natychmiastowe** .

  Po otrzymaniu monitu o podanie informacji odnosi się do EE. SP uruchamia interfejsy, które opisują adresy i pola, takie jak następujące interfejsy i ich pochodne:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  Na stronie EE są używane wszystkie te interfejsy.

## <a name="in-this-section"></a>W tej sekcji
 [Strategia implementacji ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Definiuje proces trzech etapów dla strategii implementacji dla ewaluatora wyrażeń.

## <a name="see-also"></a>Zobacz też
- [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
