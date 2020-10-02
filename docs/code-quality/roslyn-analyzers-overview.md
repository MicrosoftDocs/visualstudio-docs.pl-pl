---
title: Analiza kodu przy użyciu analizatorów Roslyn
ms.date: 09/01/2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e8c99677396ab9b3d005d4079fd37fa633df4913
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658441"
---
# <a name="overview-of-source-code-analysis"></a>Przegląd analizy kodu źródłowego

Analizatory .NET Compiler Platform (Roslyn) sprawdzają kod C# lub Visual Basic w celu uzyskania stylu, jakości, utrzymania, projektowania i innych problemów. Ta Inspekcja lub Analiza odbywa się w czasie projektowania we wszystkich otwartych plikach.

Analizatory mogą być podzielone na następujące grupy:

- Analizatory [stylów kodu](/visualstudio/ide/editorconfig-code-style-settings-reference?view=vs-2019&preserve-view=true#convention-categories) są wbudowane w program Visual Studio. Identyfikator diagnostyki lub kod dla tych analizatorów ma format IDExxxx, na przykład IDE0067. Preferencje można skonfigurować na [stronie Opcje edytora tekstu](../ide/code-styles-and-code-cleanup.md) lub w [pliku EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options). Począwszy od platformy .NET 5,0, analizatory stylów kodu są dołączone do zestawu .NET SDK i mogą być ściśle wymuszane jako ostrzeżenia lub błędy kompilacji. Aby uzyskać więcej informacji, zobacz [tutaj](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis).

- Analizatory [jakości kodu](/dotnet/fundamentals/code-analysis/quality-rules/index) są teraz dołączone do zestawu SDK programu .NET 5 i domyślnie włączone. Identyfikator diagnostyki lub kod dla tych analizatorów ma format CAxxxx, na przykład CA1822. Aby uzyskać więcej informacji, zobacz [Omówienie analizy jakości kodu platformy .NET](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis).

- Analizatory stron trzecich można instalować jako pakiet NuGet lub rozszerzenie programu Visual Studio. [Analizatory](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)stron trzecich, takie jak [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), analizatorze [XUnit](https://www.nuget.org/packages/xunit.analyzers/)i sonar.

## <a name="severity-levels-of-analyzers"></a>Poziomy ważności analizatorów

Każdy Analizator ma jeden z następujących poziomów ważności:

| Ważność (Eksplorator rozwiązań) | Ważność (plik EditorConfig) | Zachowanie w czasie kompilacji | Zachowanie edytora |
|-|-|-|
| Błąd | `error` | Naruszenia są wyświetlane jako *Błędy* w Lista błędów i w danych wyjściowych kompilacji w wierszu polecenia i powodują niepowodzenie kompilacji.| Kod powodujący problemy jest podkreślony czerwoną czerwoną ramką na pasku przewijania. |
| Ostrzeżenie | `warning` | Naruszenia są wyświetlane jako *ostrzeżenia* w Lista błędów i w danych wyjściowych kompilacji wiersza polecenia, ale nie powodują awarii kompilacji. | Kod powodujący problemy jest podkreślony zieloną, zieloną ramką na pasku przewijania. |
| Info | `suggestion` | Naruszenia są wyświetlane jako *komunikaty* w Lista błędów, a nie w danych wyjściowych kompilacji wiersza polecenia. | Kod powodujący problemy jest podkreślony szarym i oznaczonym przez małe szare pole na pasku przewijania. |
| Ukryty | `silent` | Niewidoczny dla użytkownika. | Niewidoczny dla użytkownika. Diagnostyka jest jednak raportowana w aparacie diagnostyki IDE. |
| Brak | `none` | Całkowicie pomijane. | Całkowicie pomijane. |
| Domyślny | `default` | Odnosi się do domyślnej wagi reguły. Aby określić, jaka jest wartość domyślna dla reguły, należy poszukać w okno Właściwości. | Odnosi się do domyślnej wagi reguły. |

Jeśli wykryto naruszenia reguł przez analizator, są one raportowane w edytorze kodu (jako *zygzak w kodzie* błędu) i w oknie Lista błędów.

![Naruszenie analizatora w oknie Lista błędów](../code-quality/media/code-analysis-error-list.png)

Naruszenia analizatora zgłoszone na liście błędów pasują do [ustawienia poziomu ważności](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) reguły. Naruszenia analizatora są również wyświetlane w edytorze kodu jako zygzaky w kodzie, którego kod jest nieprawidłowy. Na poniższej ilustracji przedstawiono trzy naruszenia &mdash; jednego błędu (czerwony zygzak), jedno ostrzeżenie (zielony zygzak) i jedną sugestię (trzy szare kropki):

![Zygzaky w edytorze kodu w programie Visual Studio](media/diagnostics-severity-colors.png)

Wiele reguł analizatorów lub *diagnostyki*ma jedną lub więcej skojarzonych *poprawek kodu* , które można zastosować, aby poprawić naruszenie reguły. Poprawki kodu są wyświetlane w menu ikony żarówki wraz z innymi typami [szybkich akcji](../ide/quick-actions.md). Aby uzyskać informacje na temat tych poprawek kodu, zobacz [Common Quick Actions](../ide/quick-actions.md).

![Naruszenie analizatora i szybka czynność usuwania kodu](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Konfigurowanie poziomów ważności analizatora

Można skonfigurować ważność reguł analizatora lub *diagnostyki*, w [pliku EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) lub w [menu żarówki](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu).

Analizatory można również skonfigurować w taki sposób, aby badali kod w czasie kompilacji i na żywo podczas pisania. Można skonfigurować zakres analizy kodu na żywo do wykonania tylko dla bieżącego dokumentu, wszystkie otwarte dokumenty lub całe rozwiązanie. Zobacz [jak to zrobić: Konfigurowanie zakresu analizy kodu na żywo](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Błędy i ostrzeżenia czasu kompilacji są wyświetlane tylko wtedy, gdy analizatory są zainstalowani jako pakiet NuGet. Wbudowane analizatory (na przykład IDE0067 i IDE0068) nigdy nie są uruchamiane podczas kompilacji.

## <a name="nuget-package-versus-vsix-extension"></a>Pakiet NuGet a rozszerzenie VSIX

Analizatory stron trzecich można instalować dla poszczególnych projektów za pośrednictwem pakietu NuGet. Niektóre z nich są również dostępne jako rozszerzenie programu Visual Studio, w takim przypadku mają zastosowanie do dowolnego rozwiązania, które jest otwierane w programie Visual Studio. Istnieją pewne kluczowe różnice między tymi dwiema metodami [instalacji analizatorów](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Zakres

Jeśli instalujesz analizatory jako rozszerzenie programu Visual Studio, są one stosowane na poziomie rozwiązania i we wszystkich wystąpieniach programu Visual Studio. Jeśli instalujesz analizatory jako pakiet NuGet, który jest preferowaną metodą, są one stosowane tylko do projektu, w którym zainstalowano pakiet NuGet. W środowiskach zespołu analizatory zainstalowane jako pakiety NuGet są w zakresie dla *wszystkich deweloperów* , którzy pracują nad tym projektem.

### <a name="build-errors"></a>Błędy kompilacji

Aby reguły były wymuszane w czasie kompilacji, w tym za pośrednictwem wiersza polecenia lub jako część kompilacji ciągłej integracji (CI), można wybrać jedną z następujących opcji:

- Utwórz projekt platformy .NET 5,0 zawierający domyślnie analizatory w zestawie SDK platformy .NET. Analiza kodu jest domyślnie włączona dla projektów przeznaczonych dla platformy .NET 5.0 lub nowszej. Można włączyć analizę kodu dla projektów przeznaczonych dla wcześniejszych wersji .NET przez ustawienie właściwości [EnableNETAnalyzers](https://docs.microsoft.com/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) na true.

- Zainstaluj analizatory jako pakiet NuGet. Ostrzeżenia i błędy analizatora nie są wyświetlane w raporcie kompilacji, jeśli analizatory są instalowane jako rozszerzenie.

Na poniższej ilustracji przedstawiono dane wyjściowe kompilacji wiersza polecenia z kompilowania projektu, który zawiera naruszenie reguły analizatora:

![Dane wyjściowe MSBuild z naruszeniem reguły](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Ważność reguły

Nie można skonfigurować ważności reguł z analizatorów, które zostały zainstalowane jako rozszerzenie programu Visual Studio. Aby skonfigurować [ważność reguły](../code-quality/use-roslyn-analyzers.md#configure-severity-levels), zainstaluj analizatory jako pakiet NuGet.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Instalowanie analizatorów kodu w programie Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Korzystanie z analizatorów kodu w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz też

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Napisz własny analizator kodu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK platformy kompilatora .NET](/dotnet/csharp/roslyn-sdk/)
