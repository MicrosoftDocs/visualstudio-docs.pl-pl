---
title: Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2f10b239b4307b94c1f3b62b8e0a29767b22aaf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796757"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Przekształcenia szablonu tekstu* przetwarzanie trwa *szablon tekstowy* pliku jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe. Można wywołać aparat przekształcenia tekstu z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia, lub z samodzielnej aplikacji uruchomionej na komputerze, na którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest zainstalowany. Jednakże, należy podać *hosta szablonów tekstowych*. Ta klasa łączy szablon ze środowiskiem, znajdując zasoby, takie jak zestawy i dołączane pliki, oraz zajmując się obsługą danych wyjściowych i komunikatów o błędach.  
  
> [!TIP]
>  Jeśli piszesz pakiet lub rozszerzenie, która jest uruchamiana w ramach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], rozważ użycie usługi szablonów tekstowych zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Nie zaleca się używania przekształceń szablonu tekstu w aplikacjach serwerowych. Zaleca się używanie przekształceń szablonu tekstu tylko w pojedynczych wątkach. Jest to spowodowane tym, że aparat szablonów tekstowych ponownie używa pojedynczego elementu AppDomain do tłumaczenia, skompilowania i wykonania szablonów. Przetłumaczony kod nie jest odporny na wielowątkowość. Aparat jest przeznaczony do przetwarzania plików pojedynczo, ponieważ są one [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu w czasie projektowania.  
>   
>  Dla aplikacji środowiska wykonawczego, należy wziąć pod uwagę przy użyciu szablonów tekstowych wstępnie przetworzony: zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Jeśli aplikacja używa zestawu szablonów, które są ustalane w czasie kompilacji, łatwiej jest używać wstępnie przetworzonych szablonów tekstowych. Można również użyć tego podejścia, jeśli aplikacja jest uruchamiana na komputerze, na którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie jest zainstalowany. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="executing-a-text-template-in-your-application"></a>Wykonywanie szablonu tekstu w aplikacji  
 Aby wykonać szablon tekstowy, wywołaj metodę ProcessTemplate <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 Aplikacja musi znaleźć i dostarczyć szablon oraz musi obsłużyć dane wyjściowe.  
  
 W `host` parametrów, należy podać klasę, która implementuje <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Jest to wywoływane zwrotnie przez aparat.  
  
 Host musi mieć możliwość rejestrowania błędów, rozpoznawania odwołań do zestawu i dołączania plików, podawania domeny aplikacji, w której można wykonać szablon, a także wywoływania odpowiednich procesorów dla każdej dyrektywy.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> jest zdefiniowany w **Microsoft.VisualStudio.TextTemplating.\*. 0 Biblioteka dll**, i <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> jest zdefiniowany w **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0 Biblioteka dll**.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przewodnik: Tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Dowiesz się, jak utworzyć niestandardowego hosta szablonu tekstu, dzięki której poza dostępne funkcje szablonu tekstu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Proces przekształcania szablonu tekstowego](../modeling/the-text-template-transformation-process.md)  
 W tym artykule opisano, jak działa transformacja tekstu i które części można dostosować.  
  
 [Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Zawiera omówienie procesorów dyrektyw szablonu tekstu.
