---
title: Pisanie ewaluatora wyrażeń środowiska uruchomieniowego Common Language | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2db9290f35c2b12469ecf96633967c2979b370e5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54765484"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Pisanie ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ewaluator wyrażeń (EE) jest część aparat debugowania (DE), który obsługuje składnia i semantyka języka programowania, który debugowany kod. Wyrażenia muszą być ocenione w ramach języka programowania. Na przykład w przypadku niektórych języków wyrażenia "A + B" oznacza "suma A i B." W innych językach to samo wyrażenie może oznaczać "lub B." W związku z tym oddzielny EE muszą być napisane dla każdego z języków programowania, która generuje kod obiektu debugowanego w środowisku IDE programu Visual Studio.  
  
 Niektóre aspekty pakietu debugowania programu Visual Studio należy interpretować kodu w kontekście języka programowania. Na przykład, gdy wykonanie zatrzymuje się w punkcie przerwania, a wszystkie wyrażenia, które użytkownik wpisał w **Obejrzyj** okna musi być obliczane i wyświetlane. Ponadto użytkownik może zmienić wartość zmiennej lokalnej, wpisując wyrażenia na **Obejrzyj** okna lub **bezpośrednie** okna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Środowisko uruchomieniowe języka wspólnego i ocenianie wyrażeń](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Wyjaśniono, że gdy własności język programowania jest integrowany w środowisku IDE programu Visual Studio, pisania EE zdolne do oceny wyrażenia w kontekście własności języka umożliwia skompiluj go do języka Microsoft intermediate language (MSIL) bez konieczności pisania aparatu debugowania.  
  
 [Architektura ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator-architecture.md)  
 W tym artykule omówiono jak implementować interfejsy EE wymagane i wywoływać wspólnego języka środowiska uruchomieniowego symbol dostawcy i interfejsy integratorów modeli.  
  
 [Rejestrowanie ewaluatora wyrażeń](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Zauważa, że EE musi zarejestrować się jako fabrykę klas środowiska uruchomieniowego języka wspólnego i środowiska uruchomieniowe Visual Studio.  
  
 [Implementowanie ewaluatora wyrażeń](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 W tym artykule opisano, jak procesu oceny wyrażenia zawiera aparat debugowania (DE), dostawca symboli (SP), obiekt integratora i Ewaluator wyrażeń (EE).  
  
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)  
 W tym artykule opisano, jak to zrobić, gdy wstrzymuje wykonywanie, debugowanie pakietu wywołuje bibliotekę DE, aby uzyskać listę zmiennych lokalnych i argumentów.  
  
 [Ocenianie wyrażenia okna wyrażeń kontrolnych](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Dokumenty, jak pakietu debugowania programu Visual Studio wywołuje DE, aby określić bieżącą wartość każde wyrażenie w swojej listy obserwowanych.  
  
 [Zmienianie wartości zmiennej lokalnej](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 W tym artykule wyjaśniono, że podczas zmieniania wartości zmiennej lokalnej, każdy wiersz w oknie zmienne lokalne ma skojarzony obiekt, który zawiera nazwę, typ i bieżącą wartość zmiennej lokalnej.  
  
 [Implementowanie wizualizatorów typu i przeglądarek niestandardowych](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 W tym artykule wyjaśniono, wybór interfejsu muszą być implementowane przez składnik, który obsługuje wizualizatorów typu i przeglądarek niestandardowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
