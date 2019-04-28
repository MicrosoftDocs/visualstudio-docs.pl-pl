---
title: Kontekst oceny | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 273325b8263af6f3fbacb96ece0b1194e0d5850f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411343"
---
# <a name="evaluation-context"></a>Kontekst oceny
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Uzyskać informacji o implementowaniu ewaluatory wyrażeń CLR, zobacz [ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykładowe ewaluatora wyrażeń zarządzane](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Kiedy aparat debugowania (DE) wywołuje Ewaluator wyrażeń (EE), trzech argumentów, są przekazywane do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) określenia kontekstu do odnajdywania i oceny symbole, jak pokazano w poniższej tabeli.

## <a name="arguments"></a>Argumenty

|Argument|Opis|
|--------------|-----------------|
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfejs, który określa obsługi symboli (SH) ma być używany do identyfikowania symbolu.|
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfejs, który określa bieżący punkt wykonania. Ten interfejs umożliwia znalezienie metodę, która zawiera kod wykonywany.|
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfejs, który znajduje się wartość i typ symbolu nadać jej nazwę.|

 `IDebugParsedExpression::EvaluateSync` Zwraca [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu reprezentujących wartości wynikowej i jej typu.

## <a name="see-also"></a>Zobacz także
- [Interfejsy ewaluatora wyrażeń klucza](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)