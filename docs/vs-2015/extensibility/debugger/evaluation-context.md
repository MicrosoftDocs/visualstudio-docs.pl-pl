---
title: Kontekst oceny | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28b36cfcb66dc4345843f9bcb1e7c7461b0fc6bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793534"
---
# <a name="evaluation-context"></a>Kontekst oceny
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Gdy aparat debugowania (DE) wywołuje Ewaluator wyrażeń (EE), trzy argumenty przekazywane do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) określenia kontekstu do odnajdywania i oceny symbole, jak pokazano w poniższej tabeli.  
  
## <a name="arguments"></a>Argumenty  
  
|Argument|Opis|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfejs, który określa obsługi symboli (SH) ma być używany do identyfikowania symbolu.|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfejs, który określa bieżący punkt wykonania. Można to znaleźć metodę, która zawiera kod wykonywany.|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfejsu, który może służyć do znajdowania wartości i typ symbolu, biorąc pod uwagę jego nazwę.|  
  
 `IDebugParsedExpression::EvaluateSync` Zwraca [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu reprezentujących wartości wynikowej i jej typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy ewaluatora wyrażeń klucza](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
