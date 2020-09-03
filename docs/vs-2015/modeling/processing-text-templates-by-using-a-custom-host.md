---
title: Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71f18fbbf9f2d5c587c2cd0961c6625467f4f298
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652454"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces *przekształcania szablonu tekstu* pobiera plik *szablonu tekstu* jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe. Aparat przekształcania tekstu można wywołać z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia lub z aplikacji autonomicznej uruchomionej na komputerze, na którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest zainstalowany program. Należy jednak podać *hosta tworzenia szablonów tekstu*. Ta klasa łączy szablon ze środowiskiem, znajdując zasoby, takie jak zestawy i dołączane pliki, oraz zajmując się obsługą danych wyjściowych i komunikatów o błędach.

> [!TIP]
> Jeśli piszesz pakiet lub rozszerzenie, które zostanie uruchomione w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , rozważ użycie usługi Text tworzenia szablonów zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Nie zaleca się używania przekształceń szablonu tekstu w aplikacjach serwerowych. Zaleca się używanie przekształceń szablonu tekstu tylko w pojedynczych wątkach. Jest to spowodowane tym, że aparat szablonów tekstowych ponownie używa pojedynczego elementu AppDomain do tłumaczenia, skompilowania i wykonania szablonów. Przetłumaczony kod nie jest odporny na wielowątkowość. Aparat służy do przetwarzania plików szeregowo, ponieważ znajdują się w projekcie w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] czasie projektowania.
>
> W przypadku aplikacji w czasie wykonywania Rozważ użycie wstępnie przetworzonych szablonów tekstowych: zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Jeśli aplikacja używa zestawu szablonów, które są ustalane w czasie kompilacji, łatwiej jest używać wstępnie przetworzonych szablonów tekstowych. Możesz również użyć tej metody, jeśli aplikacja zostanie uruchomiona na komputerze, na którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie jest zainstalowany. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="executing-a-text-template-in-your-application"></a>Wykonywanie szablonu tekstu w aplikacji
 Aby wykonać szablon tekstowy, należy wywołać metodę ProcessTemplate <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> :

```
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Aplikacja musi znaleźć i dostarczyć szablon oraz musi obsłużyć dane wyjściowe.

 W `host` parametrze należy podać klasę implementującą [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Jest to wywoływane zwrotnie przez aparat.

 Host musi mieć możliwość rejestrowania błędów, rozpoznawania odwołań do zestawu i dołączania plików, podawania domeny aplikacji, w której można wykonać szablon, a także wywoływania odpowiednich procesorów dla każdej dyrektywy.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> jest zdefiniowane w **Microsoft. VisualStudio. TextTemplating. \*.0.dll**, a [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) jest zdefiniowane w **Microsoft. VisualStudio. TextTemplating. Interfaces. \*.0.dll**.

## <a name="in-this-section"></a>W tej sekcji
 [Przewodnik: Tworzenie niestandardowego hosta szablonu tekstu](../modeling/walkthrough-creating-a-custom-text-template-host.md) Pokazuje, jak utworzyć niestandardowy host szablonu tekstu, który umożliwia dostęp do funkcji szablonu tekstu poza programem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="reference"></a>Dokumentacja
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Sekcje pokrewne
 [Proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md) Opisuje sposób działania transformacji tekstu oraz elementów, które można dostosować.

 [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Zawiera omówienie procesorów dyrektywy tekstu.
