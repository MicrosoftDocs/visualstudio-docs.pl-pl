---
title: Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 171eb8810d74df5c1058ba055e598d04f9164633
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658292"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego

Proces *przekształcania szablonu tekstu* pobiera plik *szablonu tekstu* jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe. Aparat przekształcania tekstu można wywołać z rozszerzenia programu Visual Studio lub z aplikacji autonomicznej uruchomionej na komputerze, na którym jest zainstalowany program Visual Studio. Należy jednak podać *hosta tworzenia szablonów tekstu*. Ta klasa łączy szablon ze środowiskiem, znajdując zasoby, takie jak zestawy i dołączane pliki, oraz zajmując się obsługą danych wyjściowych i komunikatów o błędach.

> [!TIP]
> Jeśli piszesz pakiet lub rozszerzenie, które będzie działać w programie Visual Studio, rozważ użycie usługi Text tworzenia szablonów zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Nie zaleca się używania przekształceń szablonu tekstu w aplikacjach serwerowych. Zaleca się używanie przekształceń szablonu tekstu tylko w pojedynczych wątkach. Jest to spowodowane tym, że aparat szablonów tekstowych ponownie używa pojedynczego elementu AppDomain do tłumaczenia, skompilowania i wykonania szablonów. Przetłumaczony kod nie jest odporny na wielowątkowość. Aparat służy do przetwarzania plików szeregowo, tak jak w projekcie programu Visual Studio w czasie projektowania.
>
> W przypadku aplikacji w czasie wykonywania Rozważ użycie wstępnie przetworzonych szablonów tekstowych: zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Jeśli aplikacja używa zestawu szablonów, które są ustalane w czasie kompilacji, łatwiej jest używać wstępnie przetworzonych szablonów tekstowych. Możesz również użyć tej metody, jeśli aplikacja zostanie uruchomiona na komputerze, na którym nie zainstalowano programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Wykonywanie szablonu tekstu w aplikacji

Aby wykonać szablon tekstowy, należy wywołać metodę ProcessTemplate <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Aplikacja musi znaleźć i dostarczyć szablon oraz musi obsłużyć dane wyjściowe.

 W parametrze `host` należy podać klasę implementującą [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Jest to wywoływane zwrotnie przez aparat.

 Host musi mieć możliwość rejestrowania błędów, rozpoznawania odwołań do zestawu i dołączania plików, podawania domeny aplikacji, w której można wykonać szablon, a także wywoływania odpowiednich procesorów dla każdej dyrektywy.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> jest zdefiniowany w **pliku Microsoft. VisualStudio. TextTemplating. \* 0. dll**, a [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) jest zdefiniowany w **Microsoft. VisualStudio. TextTemplating. Interfaces. \*.0. dll**.

## <a name="in-this-section"></a>W tej sekcji
 [Przewodnik: Tworzenie niestandardowego hosta szablonu tekstu](../modeling/walkthrough-creating-a-custom-text-template-host.md) Pokazuje, jak utworzyć niestandardowy host szablonu tekstu, który sprawia, że funkcjonalność szablonu tekstu jest dostępna poza programem Visual Studio.

## <a name="reference"></a>Tematy pomocy
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Sekcje pokrewne

- [Proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md) opisuje sposób działania transformacji tekstu oraz elementy, które można dostosować.
- [Tworzenie niestandardowych procesorów dyrektyw z szablonem tekstu T4](../modeling/creating-custom-t4-text-template-directive-processors.md) zawiera omówienie procesorów dyrektywy tekstu.