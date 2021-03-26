---
title: Kontekst oceny | Microsoft Docs
description: 'Gdy aparat debugowania wywołuje ewaluatora wyrażeń, argumenty określają kontekst do znajdowania i oceniania symboli: pSymbolProvider, pAddress i pBinder.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35ccfc921f8175a92b0a082798ce8ccc44990d2e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096984"
---
# <a name="evaluation-context"></a>Kontekst oceny
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Gdy aparat debugowania (DE) wywołuje ewaluatora wyrażeń (EE), trzy argumenty, które są przekazane do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) określają kontekst szukania i oceny symboli, jak pokazano w poniższej tabeli.

## <a name="arguments"></a>Argumenty

|Argument|Opis|
|--------------|-----------------|
|`pSymbolProvider`|Interfejs [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) , który określa procedurę obsługi symboli (SH), która będzie używana do identyfikowania symbolu.|
|`pAddress`|Interfejs [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) , który określa bieżący punkt wykonania. Ten interfejs umożliwia znalezienie metody zawierającej wykonywany kod.|
|`pBinder`|Interfejs [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) , który znajduje wartość i typ symbolu, który ma nazwę.|

 `IDebugParsedExpression::EvaluateSync` Zwraca interfejs [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) reprezentujący wartość wynikową i jej typ.

## <a name="see-also"></a>Zobacz też
- [Interfejsy ewaluatora wyrażeń klucza](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Wyświetlanie ustawień lokalnych](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
