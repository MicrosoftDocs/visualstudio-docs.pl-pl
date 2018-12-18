---
title: Zmienianie wartości zmiennej lokalnej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 166b4d22ec24f3137044ab19255abb15b109fbe0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807223"
---
# <a name="changing-the-value-of-a-local"></a>Zmienianie wartości zmiennej lokalnej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Po wpisaniu nową wartość w polu wartość **lokalne** oknie Debugowanie pakietu przekazuje ciąg, ponieważ wpisany Ewaluator wyrażeń (EE). EE daje w wyniku tego ciągu, który może zawierać proste wartość lub wyrażenie, a przechowuje wartość wynikową w lokalnej skojarzone.  
  
 To omówienie procesu zmiany wartości zmiennej lokalnej:  
  
1. Gdy użytkownik wprowadzi nową wartość, program Visual Studio wywołuje [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) na [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt skojarzony z lokalnym.  
  
2. `IDebugProperty2::SetValueAsString` wykonuje następujące zadania:  
  
   1.  Wylicza wartość ciągu do uzyskiwania wartości.  
  
   2.  Wiąże skojarzonego [IDebugField](../../extensibility/debugger/reference/idebugfield.md) obiektu w celu uzyskania [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) obiektu.  
  
   3.  Konwertuje wartość na serię bajtów.  
  
   4.  Wywołania [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) można umieścić wartości bajtów do pamięci, aby program poddawany mają do nich dostęp.  
  
3. Odświeża programu Visual Studio **zmiennych lokalnych** wyświetlania (patrz [wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md) Aby uzyskać szczegółowe informacje).  
  
   Ta procedura umożliwia również zmienić wartość zmiennej w **Obejrzyj** okno z wyjątkiem sytuacji kiedy `IDebugProperty2` obiekt skojarzony z wartością lokalnej, która jest używana zamiast `IDebugProperty2` obiekt skojarzony z lokalnym samego siebie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykład implementacji zmieniania wartości](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Używa przykładowych MyCEE, aby przejść przez proces zmiany wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)

