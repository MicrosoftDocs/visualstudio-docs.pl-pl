---
title: Kluczowe interfejsy ewaluatora wyrażeń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39dc13c1cc1960b0b5cad6c88b2617ea326e7875
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781358"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfejsy ewaluatora wyrażeń klucza
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Podczas pisania ewaluatora wyrażeń (EE) wraz z kontekstu oceny, należy zapoznać się z następujących interfejsów.  
  
## <a name="interface-descriptions"></a>Opis interfejsu  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Zawiera jedną metodę [getaddress —](../../extensibility/debugger/reference/idebugaddress-getaddress.md), która pobiera strukturę danych, reprezentuje bieżący punkt wykonania. Ta struktura danych jest jednym z trzech argumentów, aparat debugowania (DE) przekazane przez [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) metody, można obliczyć wartości wyrażenia. Ten interfejs jest zwykle implementowany przez dostawcę symboli.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Ma [powiązać](../../extensibility/debugger/reference/idebugbinder-bind.md) metody, która pobiera obszaru pamięci, która zawiera bieżącą wartość symbolu. Biorąc pod uwagę zarówno metodą zawierającą, reprezentowane przez [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) obiekt i symboli, reprezentowane przez [IDebugField](../../extensibility/debugger/reference/idebugfield.md) obiektu `IDebugBinder::Bind` zwraca wartość symbolu. `IDebugBinder` Zazwyczaj jest implementowany przez DE.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Reprezentuje prosty typ danych. W przypadku bardziej złożonych typów, takich jak tablice i metody, użyj pochodnej [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) i [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfejsy odpowiednio. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) jest inny ważne pochodnej interfejs, który reprezentuje symbole zawierające innych symboli, takich jak metod lub klas. `IDebugField` Interfejsu (i ich pochodne) jest zwykle implementowana przez dostawcę symboli.  
  
     `IDebugField` Obiekt może być używane, aby znaleźć nazwę i typ symbolu i wraz z [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) obiektów, można znaleźć jego wartość.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Reprezentuje rzeczywisty bity wartość symbolu w czasie wykonywania. [Powiąż](../../extensibility/debugger/reference/idebugbinder-bind.md) przyjmuje [IDebugField](../../extensibility/debugger/reference/idebugfield.md) obiektu, który reprezentuje symbol, a następnie zwraca [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) obiektu. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) metoda zwraca wartość symbolu w buforze pamięci. DE zwykle implementuje ten interfejs reprezentujący wartość właściwości w pamięci.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Ten interfejs reprezentuje ewaluatora wyrażenia, sam. Metoda klucza jest [przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), co powoduje zwrócenie [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfejsu.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Ten interfejs reprezentuje wyrażenie przeanalizowany, gotowy do obliczenia. Metoda klucza jest [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) co powoduje zwrócenie wiadomość IDebugProperty2 reprezentujący wartość i typ wyrażenia.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Ten interfejs reprezentuje wartość, jak i jej typ i jest wynikiem oceny wyrażenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)
