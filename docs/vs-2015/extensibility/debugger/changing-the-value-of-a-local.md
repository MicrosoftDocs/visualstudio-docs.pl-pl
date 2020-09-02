---
title: Zmiana wartości elementu lokalnego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782552"
---
# <a name="changing-the-value-of-a-local"></a>Zmienianie wartości zmiennej lokalnej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Gdy nowa wartość zostanie wpisana w polu wartość w oknie **zmiennych lokalnych** , pakiet debugowania przekaże ciąg, tak jak wpisano, do ewaluatora wyrażeń (EE). Program EE szacuje ten ciąg, który może zawierać prostą wartość lub wyrażenie, i przechowuje wartość wynikową w skojarzonym elemencie lokalnym.  
  
 Jest to przegląd procesu zmiany wartości lokalnej:  
  
1. Gdy użytkownik wprowadzi nową wartość, program Visual Studio wywołuje [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) na obiekcie [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) skojarzonym z elementem lokalnym.  
  
2. Metoda `IDebugProperty2::SetValueAsString` wykonuje następujące zadania:  
  
   1. Oblicza ciąg w celu utworzenia wartości.  
  
   2. Wiąże skojarzony obiekt [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , aby uzyskać obiekt [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) .  
  
   3. Konwertuje wartość na serię bajtów.  
  
   4. Wywołuje metodę [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) , aby umieścić bajty wartości w pamięci, dzięki czemu debugowany program może uzyskać do nich dostęp.  
  
3. Program Visual Studio odświeża wyświetlacze **lokalne** (zobacz [Wyświetlanie ustawień lokalnych](../../extensibility/debugger/displaying-locals.md) w celu uzyskania szczegółowych informacji).  
  
   Ta procedura służy również do zmiany wartości zmiennej w oknie **czujki** , z wyjątkiem tego, `IDebugProperty2` że jest obiektem skojarzonym z wartością lokalnego, która jest używana zamiast `IDebugProperty2` obiektu skojarzonego z samym elementem lokalnym.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykład implementacji zmieniania wartości](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Używa przykładu MyCEE, aby przejść przez proces zmieniania wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)
