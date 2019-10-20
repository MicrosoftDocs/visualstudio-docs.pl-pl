---
title: Analiza kodu przy użyciu analizatorów Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 388667485f27b59e46a1c39d95b37ddc413240ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649135"
---
# <a name="overview-of-source-code-analyzers"></a>Przegląd analizatorów kodu źródłowego

.NET Compiler Platform ("Roslyn") analizatory kodu sprawdzają C# kod lub Visual Basic w celu uzyskania stylu, jakości i utrzymania, projektowania i innych problemów.

- Niektóre analizatory są wbudowane w program Visual Studio. Identyfikator diagnostyki lub kod dla tych analizatorów ma format IDExxxx, na przykład IDE0067. Większość z tych wbudowanych analizatorów sprawdza [styl kodu](../ide/code-styles-and-code-cleanup.md)i można skonfigurować preferencje na [stronie Opcje edytora tekstu](../ide/code-styles-and-code-cleanup.md) lub w [pliku EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Kilku wbudowanych analizatorów Przyjrzyj się jakości kodu.

- Możesz zainstalować dodatkowe analizatory jako pakiet NuGet lub rozszerzenie programu Visual Studio. Na przykład:

  - [Analizatory FxCop](../code-quality/install-fxcop-analyzers.md), zalecane przez firmę Microsoft analizatory jakości kodu
  - [Analizatory](https://www.nuget.org/packages/SonarAnalyzer.CSharp/) stron trzecich, takie jak [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [przeanaliz XUnit](https://www.nuget.org/packages/xunit.analyzers/)i Sonar

Jeśli wykryto naruszenia reguł przez analizator, są one raportowane w edytorze kodu (jako *zygzak w kodzie* błędu) i w oknie Lista błędów.

Wiele reguł analizatorów lub *diagnostyki*ma jedną lub więcej skojarzonych *poprawek kodu* , które można zastosować, aby rozwiązać problem. Diagnostyka analizatora wbudowana w program Visual Studio ma skojarzoną poprawkę kodu. Poprawki kodu są wyświetlane w menu ikony żarówki wraz z innymi typami [szybkich akcji](../ide/quick-actions.md). Aby uzyskać informacje na temat tych poprawek kodu, zobacz [Common Quick Actions](../ide/common-quick-actions.md).

![Naruszenie analizatora i szybka czynność usuwania kodu](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Analiza kodu źródłowego w porównaniu do starszej analizy

Analiza źródła przez analizatory Roslyn zastępuje [starszą analizę](../code-quality/code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. Wiele starszych reguł analizy zostało już zapisaną jako analizatory kodu Roslyn. W przypadku nowszych szablonów projektów, takich jak .NET Core i projekty .NET Standard, Starsza analiza nie jest jeszcze dostępna.

Podobnie jak w przypadku starszych naruszeń reguł analizy, naruszenia analizy kodu źródłowego są wyświetlane w oknie Lista błędów w programie Visual Studio. Ponadto naruszenia analizy kodu *źródłowego są również* wyświetlane w edytorze kodu jako zygzaky w kodzie błędu. Kolor zygzaka zależy od [Ustawienia ważności](../code-quality/use-roslyn-analyzers.md#rule-severity) reguły. Na poniższej ilustracji przedstawiono trzy naruszenia &mdash;one czerwony, jeden zielony i jeden szary:

![Zygzaky w edytorze kodu w programie Visual Studio](media/diagnostics-severity-colors.png)

Analizatory kodu sprawdzają kod w czasie kompilacji, na przykład w starszej analizie, jeśli jest włączona, ale również na żywo podczas pisania. Po włączeniu [pełnej analizy rozwiązań](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis)analizatory kodu zapewniają również analizę czasu projektowania plików kodu, które nie są otwarte w edytorze.

> [!TIP]
> Błędy i ostrzeżenia czasu kompilacji są wyświetlane tylko wtedy, gdy analizatory są zainstalowani jako pakiet NuGet. Wbudowane analizatory (na przykład IDE0067 i IDE0068) nigdy nie są uruchamiane podczas kompilacji.

Tylko analizatory kodu Roslyn raportują te same typy problemów, które są używane w starszej analizie, ale ułatwiają rozwiązanie jednego lub wszystkich wystąpień naruszenia w pliku lub projekcie. Te akcje są nazywane *poprawkami kodu*. Poprawki kodu są specyficzne dla środowiska IDE; w programie Visual Studio są one implementowane jako [szybkie akcje](../ide/quick-actions.md). Nie cała Diagnostyka analizatora ma skojarzoną poprawkę kodu.

> [!NOTE]
> Opcja **analizuj**  > **Uruchom analizę kodu** ma zastosowanie tylko do starszej analizy.

Aby rozróżnić naruszenia od analizatorów kodu i starszej analizy w Lista błędów, należy zapoznać się z kolumną **Narzędzia** . Jeśli wartość narzędzia pasuje do jednego z zestawów analizatorów w **Eksplorator rozwiązań**, na przykład **Microsoft. CodeQuality. analizatory**, naruszenie pochodzi z analizatora kodu. W przeciwnym razie naruszenie pochodzi ze starszej wersji analizy.

![Kolumna narzędzia w Lista błędów](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Właściwość **RunCodeAnalysis** MSBuild w pliku projektu ma zastosowanie tylko do starszej analizy. Jeśli instalujesz analizatory, ustaw **RunCodeAnalysis** na **false** w pliku projektu, aby zapobiec uruchamianiu starszej analizy po kompilacji.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pakiet NuGet a rozszerzenie VSIX

Analizatory kodu Roslyn można instalować dla poszczególnych projektów za pośrednictwem pakietu NuGet. Niektóre z nich są również dostępne jako rozszerzenie programu Visual Studio, w takim przypadku mają zastosowanie do dowolnego rozwiązania, które jest otwierane w programie Visual Studio. Istnieją pewne kluczowe różnice między tymi dwiema metodami [instalacji analizatorów](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Zakres

Jeśli instalujesz analizatory jako rozszerzenie programu Visual Studio, są one stosowane na poziomie rozwiązania i we wszystkich wystąpieniach programu Visual Studio. Jeśli instalujesz analizatory jako pakiet NuGet, który jest preferowaną metodą, są one stosowane tylko do projektu, w którym zainstalowano pakiet NuGet. W środowiskach zespołu analizatory zainstalowane jako pakiety NuGet są w zakresie dla *wszystkich deweloperów* , którzy pracują nad tym projektem.

### <a name="build-errors"></a>Błędy kompilacji

Aby reguły były wymuszane w czasie kompilacji, w tym za pomocą wiersza polecenia lub w ramach kompilacji ciągłej integracji (CI), należy zainstalować analizatory jako pakiet NuGet. Ostrzeżenia i błędy analizatora nie są wyświetlane w raporcie kompilacji, jeśli analizatory są instalowane jako rozszerzenie.

Na poniższej ilustracji przedstawiono dane wyjściowe kompilacji wiersza polecenia z kompilowania projektu, który zawiera naruszenie reguły analizatora:

![Dane wyjściowe MSBuild z naruszeniem reguły](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Ważność reguły

Nie można skonfigurować ważności reguł z analizatorów, które zostały zainstalowane jako rozszerzenie programu Visual Studio. Aby skonfigurować [ważność reguły](../code-quality/use-roslyn-analyzers.md#rule-severity), zainstaluj analizatory jako pakiet NuGet.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Instalowanie analizatorów kodu w programie Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Korzystanie z analizatorów kodu w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Napisz własny analizator kodu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
