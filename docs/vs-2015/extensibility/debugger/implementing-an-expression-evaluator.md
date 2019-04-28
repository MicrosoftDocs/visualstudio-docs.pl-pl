---
title: Implementowanie ewaluatora wyrażeń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82e6f1fb4e6f78c7fb1f614144f9a836d9676fb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436354"
---
# <a name="implementing-an-expression-evaluator"></a>Implementowanie ewaluatora wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Obliczenia wyrażenia jest wzajemne oddziaływania wykresów złożonych aparat debugowania (DE), dostawca symboli (SP), obiekt integratora i Ewaluator wyrażeń (EE) sam. Te cztery składniki są połączone za interfejsów implementowanych przez jeden składnik i używane przez inny.  
  
 EE pobiera wyrażenie DE w postaci ciągu i analizuje ani nie ocenia je. EE implementuje następujące interfejsy, które są używane przez DE:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  EE wywołuje obiekt integratora dostarczonych przez DE, aby uzyskać wartość symboli i obiektów. EE wykorzystuje następujące interfejsy, które są implementowane przez DE:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Implementuje EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` udostępnia mechanizm do opisywania wynikiem oceny wyrażenia, takie jak zmienna lokalna, podstawowy lub obiekt, do programu Visual Studio, który następnie wyświetla odpowiednie informacje w **lokalne**,  **Obejrzyj**, lub **bezpośrednie** okna.  
  
  PS otrzymuje EE przez DE podczas jego poprosi o podanie informacji. PS implementuje interfejsy, które opisują adresów i pola, takie jak następujące interfejsy i ich pochodne:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE zużywa wszystkich tych interfejsów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Strategia implementacji ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definiuje proces trzech kroków strategia implementacji ewaluatora (EE) wyrażeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
