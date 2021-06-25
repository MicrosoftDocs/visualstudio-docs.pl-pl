---
title: Kontekst | Microsoft Docs
description: 'Gdy aparat debugowania wywołuje ewaluator wyrażeń, argumenty określają kontekst znajdowania i oceniania symboli: pSymbolProvider, pAddress i pBinder.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6c3ab6fe53ad288089dc88587e06547573d80cb9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898581"
---
# <a name="evaluation-context"></a>Kontekst oceny
> [!IMPORTANT]
> W Visual Studio 2015 r. ten sposób implementowania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania ewaluatorów wyrażeń CLR, zobacz [ClR expression evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) (Ewaluatory wyrażeń CLR) i Managed expression evaluator sample (Przykład ewaluatora [wyrażeń zarządzanych).](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Gdy aparat debugowania (DE) wywołuje ewaluator wyrażeń (EE), trzy argumenty przekazywane do [narzędzia EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) określają kontekst znajdowania i oceniania symboli, jak pokazano w poniższej tabeli.

## <a name="arguments"></a>Argumenty

|Argument|Opis|
|--------------|-----------------|
|`pSymbolProvider`|Interfejs [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) określający program obsługi symboli (SH), który ma być używany do identyfikowania symbolu.|
|`pAddress`|Interfejs [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) określający bieżący punkt wykonania. Ten interfejs znajduje metodę, która zawiera wykonywany kod.|
|`pBinder`|Interfejs [IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) który znajduje wartość i typ symbolu na jego nazwie.|

 `IDebugParsedExpression::EvaluateSync` Zwraca interfejs [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) reprezentujący wartość wynikową i jej typ.

## <a name="see-also"></a>Zobacz też
- [Interfejsy ewaluatora wyrażeń kluczowych](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Wyświetlanie lokalizacji lokalnych](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
