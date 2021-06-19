---
title: Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego
description: Dowiedz się, że proces przekształcania szablonu tekstu przyjmuje plik szablonu tekstowego jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a301df6edaf8558ade5c8a297f233b58de6d8f4e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390935"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego

Proces *przekształcania szablonu tekstu* przyjmuje plik szablonu *tekstowego* jako dane wejściowe i generuje plik tekstowy jako dane wyjściowe. Aparat przekształcania tekstu można wywołać z rozszerzenia Visual Studio lub z autonomicznej aplikacji uruchomionej na maszynie, na której Visual Studio zainstalowana. Należy jednak podać hosta szablonów *tekstu*. Ta klasa łączy szablon ze środowiskiem, znajdując zasoby, takie jak zestawy i dołączane pliki, oraz zajmując się obsługą danych wyjściowych i komunikatów o błędach.

> [!TIP]
> Jeśli piszesz pakiet lub rozszerzenie, które będzie uruchamiane w programie Visual Studio, rozważ użycie usługi szablonów tekstu zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [Temat Invoking Text Transformation in a VS Extension (Wywołania przekształcenia tekstu w rozszerzeniu programu VS).](../modeling/invoking-text-transformation-in-a-vs-extension.md)

> [!NOTE]
> Nie zaleca się używania przekształceń szablonu tekstu w aplikacjach serwerowych. Zaleca się używanie przekształceń szablonu tekstu tylko w pojedynczych wątkach. Jest to spowodowane tym, że aparat szablonów tekstowych ponownie używa pojedynczego elementu AppDomain do tłumaczenia, skompilowania i wykonania szablonów. Przetłumaczony kod nie jest odporny na wielowątkowość. Aparat jest przeznaczony do przetwarzania plików szeregowo, ponieważ znajdują się w Visual Studio projektu w czasie projektowania.
>
> W przypadku aplikacji w czasie uruchamiania rozważ użycie wstępnie przetworzonych szablonów tekstowych: zobacz [Run-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md)(Generowanie tekstu w czasie uruchamiania przy użyciu szablonów tekstowych T4).

Jeśli aplikacja używa zestawu szablonów, które są ustalane w czasie kompilacji, łatwiej jest używać wstępnie przetworzonych szablonów tekstowych. Tej metody można również użyć, jeśli aplikacja będzie działać na maszynie, na której Visual Studio nie jest zainstalowana. Aby uzyskać więcej informacji, zobacz Run-Time Text Generation with T4 Text Templates (Generowanie tekstu [w czasie uruchamiania za pomocą szablonów tekstowych T4).](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="execute-a-text-template-in-your-application"></a>Wykonywanie szablonu tekstowego w aplikacji

Aby wykonać szablon tekstowy, wywołaj metodę ProcessTemplate metody <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> :

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Aplikacja musi znaleźć i dostarczyć szablon oraz musi obsłużyć dane wyjściowe.

 W `host` parametrze należy podać klasę, która implementuje [klasę ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Jest to wywoływane zwrotnie przez aparat.

 Host musi mieć możliwość rejestrowania błędów, rozpoznawania odwołań do zestawu i dołączania plików, podawania domeny aplikacji, w której można wykonać szablon, a także wywoływania odpowiednich procesorów dla każdej dyrektywy.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> Jest zdefiniowany w **Microsoft.VisualStudio.TextTemplating. \*.0.dll**, a [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) jest zdefiniowany w **Microsoft.VisualStudio.TextTemplating.Interfaces. \***.0.dll.

## <a name="in-this-section"></a>W tej sekcji
 [Przewodnik: tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md) Pokazuje, jak utworzyć niestandardowego hosta szablonu tekstu, który udostępnia funkcje szablonu tekstu poza Visual Studio.

## <a name="reference"></a>Odwołanie
 [Itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Sekcje pokrewne

- [Proces przekształcania szablonu tekstu opisuje](../modeling/the-text-template-transformation-process.md) sposób działania przekształcania tekstu i części, które można dostosować.
- [Artykuł Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md) (Tworzenie niestandardowych procesorów dyrektyw szablonów tekstowych T4) zawiera omówienie procesorów dyrektyw szablonów tekstowych.
