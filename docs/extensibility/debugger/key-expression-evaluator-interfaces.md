---
title: Interfejsy ewaluatora wyrażeń klucza | Microsoft Docs
description: Dowiedz się więcej o interfejsach, z którymi należy się zapoznać, gdy piszesz ewaluatora wyrażeń, wraz z kontekstem oceny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95c32b76893e0de7f31e56df81bf12c831452bfe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945932"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfejsy ewaluatora wyrażeń klucza
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Podczas pisania ewaluatora wyrażeń (EE), wraz z kontekstem oceny, należy zapoznać się z poniższymi interfejsami.

## <a name="interface-descriptions"></a>Opisy interfejsów

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Ma pojedynczą metodę [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), która pobiera strukturę danych, która reprezentuje bieżący punkt wykonania. Ta struktura danych jest jednym z trzech argumentów przekazywanych przez aparat debugowania do metody [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) w celu obliczenia wyrażenia. Ten interfejs jest zwykle implementowany przez dostawcę symboli.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Ma metodę [bind](../../extensibility/debugger/reference/idebugbinder-bind.md) , która pobiera obszar pamięci, który zawiera bieżącą wartość symbolu. Dana metoda zawierająca, reprezentowana przez obiekt [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) i sam symbol reprezentowane przez obiekt [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , `IDebugBinder::Bind` zwraca wartość symbolu. `IDebugBinder` jest zwykle zaimplementowany przez DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Reprezentuje prosty typ danych. W przypadku bardziej złożonych typów, takich jak tablice i metody, należy odpowiednio użyć pochodnych interfejsów [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) i [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) jest innym ważnym interfejsem pochodnym, który reprezentuje symbole zawierające inne symbole, takie jak metody lub klasy. `IDebugField`Interfejs (i jego pochodne) są zwykle implementowane przez dostawcę symboli.

     `IDebugField`Obiekt może służyć do znajdowania nazwy i typu symbolu oraz, wraz z obiektem [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) , może służyć do znalezienia jego wartości.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Reprezentuje rzeczywiste bity wartości czasu wykonywania symbolu. [Powiązanie](../../extensibility/debugger/reference/idebugbinder-bind.md) pobiera obiekt [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , który reprezentuje symbol i zwraca obiekt [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) . Metoda [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) zwraca wartość symbolu w buforze pamięci. Zazwyczaj implementuje ten interfejs, aby reprezentować wartość właściwości w pamięci.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Ten interfejs reprezentuje Ewaluatora wyrażenia. Kluczowa Metoda jest [analizowana](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), która zwraca interfejs [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Ten interfejs reprezentuje wyrażenie analizowane gotowe do oceny. Kluczową metodą jest [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , która zwraca IDebugProperty2 reprezentujący wartość i typ wyrażenia.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Ten interfejs reprezentuje wartość i jej typ oraz jest wynikiem obliczania wyrażenia.

## <a name="see-also"></a>Zobacz też
- [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)
