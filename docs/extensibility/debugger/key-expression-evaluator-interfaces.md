---
title: Interfejsy ewaluatora wyrażeń | Microsoft Docs
description: Dowiedz się więcej o interfejsach, które należy znać podczas pisania ewaluatora wyrażeń wraz z kontekstem oceny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: abfa4018e763bbbac5ff788f401d0ceb76eb97a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901269"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfejsy ewaluatora wyrażeń klucza
> [!IMPORTANT]
> W Visual Studio 2015 r. ten sposób implementowania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania ewaluatorów wyrażeń CLR, zobacz przykłady ewaluatorów wyrażeń [CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [Ewaluator wyrażeń zarządzanych](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Podczas pisania ewaluatora wyrażeń (EE) wraz z kontekstem oceny należy zapoznać się z następującymi interfejsami.

## <a name="interface-descriptions"></a>Opisy interfejsów

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Ma pojedynczą metodę [GetAddress,](../../extensibility/debugger/reference/idebugaddress-getaddress.md)która pobiera strukturę danych reprezentującą bieżący punkt wykonania. Ta struktura danych jest jednym z trzech argumentów, które aparat debugowania przekazuje do metody [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) w celu oceny wyrażenia. Ten interfejs jest zwykle implementowany przez dostawcę symboli.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Ma [metodę Bind,](../../extensibility/debugger/reference/idebugbinder-bind.md) która pobiera obszar pamięci zawierający bieżącą wartość symbolu. Biorąc pod uwagę zarówno zawierającą metodę, reprezentowaną przez obiekt [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) jak i sam symbol reprezentowany przez obiekt [IDebugField,](../../extensibility/debugger/reference/idebugfield.md) zwraca `IDebugBinder::Bind` wartość symbolu. `IDebugBinder` Jest zwykle implementowany przez DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Reprezentuje prosty typ danych. W przypadku bardziej złożonych typów, takich jak tablice i metody, należy użyć odpowiednio interfejsów pochodnych [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) i [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) to inny ważny interfejs pochodny, który reprezentuje symbole zawierające inne symbole, takie jak metody lub klasy. Interfejs `IDebugField` (i jego pochodne) jest zwykle implementowany przez dostawcę symboli.

     Obiekt może służyć do znalezienia nazwy i typu symbolu, a wraz z obiektem `IDebugField` [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) może służyć do znalezienia jego wartości.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Reprezentuje rzeczywiste bity wartości czasu uruchomienia symbolu. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) przyjmuje [obiekt IDebugField,](../../extensibility/debugger/reference/idebugfield.md) który reprezentuje symbol, i zwraca [obiekt IDebugObject.](../../extensibility/debugger/reference/idebugobject.md) Metoda [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) zwraca wartość symbolu w buforze pamięci. De zwykle implementuje ten interfejs do reprezentowania wartości właściwości w pamięci.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Ten interfejs reprezentuje sam ewaluator wyrażeń. Metoda klucza to [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), która zwraca interfejs [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Ten interfejs reprezentuje analizowane wyrażenie gotowe do oceny. Metoda klucza to [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) która zwraca element IDebugProperty2 reprezentujący wartość i typ wyrażenia.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Ten interfejs reprezentuje wartość i jej typ oraz jest wynikiem oceny wyrażenia.

## <a name="see-also"></a>Zobacz też
- [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)
