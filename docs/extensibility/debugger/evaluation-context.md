---
title: Kontekst oceny | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738803"
---
# <a name="evaluation-context"></a>Kontekst oceny
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Gdy aparat debugowania (DE) wywołuje oceniającego wyrażenie (EE), trzy argumenty, które są przekazywane do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) określić kontekst do znajdowania i oceny symboli, jak pokazano w poniższej tabeli.

## <a name="arguments"></a>Argumenty

|Argument|Opis|
|--------------|-----------------|
|`pSymbolProvider`|[Interfejs IDebugSymbolProvider,](../../extensibility/debugger/reference/idebugsymbolprovider.md) który określa program obsługi symboli (SH), który ma być używany do identyfikowania symbolu.|
|`pAddress`|Interfejs [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) który określa bieżący punkt wykonania. Ten interfejs znajduje metodę, która zawiera wykonywany kod.|
|`pBinder`|Interfejs [IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) który znajduje wartość i typ symbolu, pod jakimas.|

 `IDebugParsedExpression::EvaluateSync`zwraca interfejs [IDebugProperty2 reprezentujący](../../extensibility/debugger/reference/idebugproperty2.md) wynikową wartość i jego typ.

## <a name="see-also"></a>Zobacz też
- [Interfejsy oceniającego kluczowe wyrażenia](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Wyświetlanie lokalnych](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
