---
title: Analiza kodu przy użyciu analizatorów Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a47cb2a5aefd7d20e0b8087f5f3ad735716175
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79431283"
---
# <a name="overview-of-source-code-analyzers"></a>Omówienie analizatorów kodu źródłowego

Analizatory kodu platformy kompilatora platformy .NET ("Roslyn") sprawdzają kod języka C# lub Visual Basic pod kątem stylu, jakości i łatwości konserwacji, projektowania i innych problemów.

- Niektóre analizatory są wbudowane w programie Visual Studio. Identyfikator diagnostyczny lub kod dla tych analizatorów jest w formacie IDExxxx, na przykład IDE0067. Większość z tych wbudowanych analizatorów sprawdza [styl kodu](../ide/code-styles-and-code-cleanup.md)i można skonfigurować preferencje na stronie [opcji edytora tekstu](../ide/code-styles-and-code-cleanup.md) lub w pliku [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Kilka wbudowanych analizatorów spojrzeć na jakość kodu.

- Można zainstalować dodatkowe analizatory jako pakiet NuGet lub rozszerzenie programu Visual Studio. Przykład:

  - [Analizatory FxCop](../code-quality/install-fxcop-analyzers.md), zalecane przez firmę Microsoft analizatory jakości kodu
  - Analizatory innych firm, takie jak [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [Analizatory XUnit](https://www.nuget.org/packages/xunit.analyzers/)i [Analizator sonaru](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Jeśli naruszenia reguły zostaną znalezione przez analizatora, są one zgłaszane w edytorze kodu (jako *falista* pod kodem naruszającym) i w oknie lista błędów.

Wiele reguł analizatora lub *diagnostyki*, mają jeden lub więcej *skojarzonych poprawek kodu,* które można zastosować, aby rozwiązać problem. Diagnostyka analizatora, które są wbudowane w programie Visual Studio każdy ma skojarzoną poprawkę kodu. Poprawki kodu są wyświetlane w menu ikony żarówki wraz z innymi typami [szybkich akcji](../ide/quick-actions.md). Aby uzyskać informacje na temat tych poprawek kodu, zobacz [Wspólne szybkie akcje](../ide/common-quick-actions.md).

![Naruszenie zasad analizy i poprawka kodu szybkiej akcji](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Analiza kodu źródłowego a starsza analiza

Analiza źródła przez analizatory Roslyn zastępuje [starszą analizę](../code-quality/code-analysis-for-managed-code-overview.md) kodu zarządzanego. Wiele starszych reguł analizy zostały już przepisane jako analizatory kodu Roslyn. W przypadku nowszych szablonów projektów, takich jak projekty .NET Core i .NET Standard, starsza analiza nie jest nawet dostępna.

Podobnie jak naruszenia starszych reguł analizy, naruszenia analizy kodu źródłowego są wyświetlane w oknie lista błędów w programie Visual Studio. Ponadto naruszenia analizy kodu źródłowego są również wyświetlane w edytorze kodu jako *squiggles* pod kodem naruszającym. Kolor faliwy zależy od [ustawienia ważności reguły.](../code-quality/use-roslyn-analyzers.md#rule-severity) Na poniższej ilustracji przedstawiono trzy naruszenia&mdash;jednego czerwonego, jednego zielonego i jednego szarego:

![Squiggles w edytorze kodu w programie Visual Studio](media/diagnostics-severity-colors.png)

Analizatory kodu sprawdzić kod w czasie kompilacji, takich jak starsza analiza, jeśli jest włączona, ale również żyć podczas pisania. Można skonfigurować zakres analizy kodu na żywo do wykonania tylko dla bieżącego dokumentu, wszystkie otwarte dokumenty lub całe rozwiązanie. Zobacz [Jak: Konfigurowanie zakresu analizy kodu na żywo](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Błędy w czasie kompilacji i ostrzeżenia z analizatorów kodu są wyświetlane tylko wtedy, gdy analizatory są zainstalowane jako pakiet NuGet. Wbudowane analizatory (na przykład IDE0067 i IDE0068) nigdy nie są uruchamiane podczas kompilacji.

Analizatory kodu Roslyn nie tylko zgłaszają te same typy problemów, które wykonuje starsza analiza, ale ułatwiają naprawienie jednego lub wszystkich wystąpień naruszenia w pliku lub projekcie. Te akcje są nazywane *poprawkami kodu*. Poprawki kodu są specyficzne dla IDE; w programie Visual Studio są one implementowane jako [szybkie akcje.](../ide/quick-actions.md) Nie wszystkie diagnostyki analizatora mają skojarzoną poprawkę kodu.

> [!NOTE]
> Przed wydaniem programu Visual Studio 2019 16.5 opcja menu **Analizowanie** > **analizy kodu** wykonywania starszej analizy. Uruchamianie programu Visual Studio 2019 16.5, uruchom **analizę kodu** menu opcja wykonuje analizatory oparte na Roslyn dla wybranego projektu lub rozwiązania.

Aby odróżnić naruszenia z analizatorów kodu i starszej analizy na liście błędów, spójrz na **narzędzie** kolumny. Jeśli wartość narzędzia pasuje do jednego z zestawów analizatora w **Eksploratorze rozwiązań**, na przykład **Microsoft.CodeQuality.Analyzers**, naruszenie pochodzi z analizatora kodu. W przeciwnym razie naruszenie pochodzi z analizy starszej wersji.

![Kolumna Narzędzia na liście błędów](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> **Właściwość RunCodeAnalysis** MSBuild w pliku projektu ma zastosowanie tylko do starszej analizy. Jeśli zainstalujesz analizatory, ustaw **RunCodeAnalysis** **false** w pliku projektu, aby zapobiec starszej analizy z systemem po kompilacji.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pakiet NuGet a rozszerzenie VSIX

Analizatory kodu Roslyn można zainstalować na projekt za pośrednictwem pakietu NuGet. Niektóre są również dostępne jako rozszerzenie programu Visual Studio, w którym to przypadku mają zastosowanie do dowolnego rozwiązania, które można otworzyć w programie Visual Studio. Istnieją pewne kluczowe różnice w zachowaniu między tymi dwiema metodami [instalowania analizatorów.](../code-quality/install-roslyn-analyzers.md)

### <a name="scope"></a>Zakres

Jeśli zainstalujesz analizatory jako rozszerzenie programu Visual Studio, mają one zastosowanie na poziomie rozwiązania i do wszystkich wystąpień programu Visual Studio. Jeśli zainstalujesz analizatory jako pakiet NuGet, który jest preferowaną metodą, mają one zastosowanie tylko do projektu, w którym zainstalowano pakiet NuGet. W środowiskach zespołowych analizatory zainstalowane jako pakiety NuGet są w zakresie dla *wszystkich deweloperów,* którzy pracują nad tym projektem.

### <a name="build-errors"></a>Błędy kompilacji

Aby reguły były wymuszane w czasie kompilacji, w tym za pośrednictwem wiersza polecenia lub jako część kompilacji ciągłej integracji (CI), należy zainstalować analizatory jako pakiet NuGet. Ostrzeżenia i błędy analizatora nie są wyświetlane w raporcie kompilacji, jeśli zainstalujesz analizatory jako rozszerzenie.

Na poniższej ilustracji przedstawiono dane wyjściowe kompilacji wiersza polecenia z tworzenia projektu, który zawiera naruszenie reguły analizatora:

![Wyjście MSBuild z naruszeniem reguły](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Ważność reguły

Nie można skonfigurować ważności reguł z analizatorów, które zostały zainstalowane jako rozszerzenie programu Visual Studio. Aby skonfigurować [ważność reguły,](../code-quality/use-roslyn-analyzers.md#rule-severity)należy zainstalować analizatory jako pakiet NuGet.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Instalowanie analizatorów kodu w programie Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Używanie analizatorów kodu w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz też

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Napisz własny analizator kodu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK platformy kompilatora .NET](/dotnet/csharp/roslyn-sdk/)
