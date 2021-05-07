---
title: Analiza kodu przy użyciu analizatorów Roslyn
ms.date: 09/01/2020
description: Zapoznaj się z analizą kodu źródłowego w Visual Studio. Dowiedz się więcej o poprawkach kodu oraz różnych typach analizatorów i poziomach ważności.
ms.custom: SEO-VS-2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c3a7192ac55dc4138746e3e1e1abe4eaa6928395
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798339"
---
# <a name="overview-of-source-code-analysis"></a>Omówienie analizy kodu źródłowego

.NET Compiler Platform (Roslyn) Analyzers (Analizatory Roslyn) sprawdzają kod języka C# lub Visual Basic pod Visual Basic stylu, jakości, konserwacji, projektu i innych problemów. Ta inspekcja lub analiza odbywa się w czasie projektowania we wszystkich otwartych plikach.

Analizatory można podzielić na następujące grupy:

- [Analizatory](/dotnet/fundamentals/code-analysis/code-style-rule-options?preserve-view=true&view=vs-2019#convention-categories) stylu kodu są wbudowane w Visual Studio. Identyfikator diagnostyczny (czyli kod) dla tych analizatorów ma format IDExxxx, na przykład IDE0067. Preferencje można skonfigurować na stronie [opcji edytora tekstów](../ide/code-styles-and-code-cleanup.md) lub w pliku [EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options). Począwszy od programu .NET 5.0 analizatory stylu kodu są dołączone do zestawu .NET SDK i mogą być ściśle wymuszane jako ostrzeżenia lub błędy kompilacji. Aby uzyskać więcej informacji, zobacz [tutaj](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis).

- [Analizatory](/dotnet/fundamentals/code-analysis/quality-rules/index) jakości kodu są teraz dołączone do zestawu .NET 5 SDK i domyślnie włączone. Identyfikator diagnostyczny lub kod dla tych analizatorów ma format CAxxxx, na przykład CA1822. Aby uzyskać więcej informacji, zobacz [Overview of .NET code quality analysis (Omówienie analizy jakości kodu .NET).](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis)

- Analizatory innych firm można zainstalować jako pakiet NuGet lub Visual Studio rozszerzenia. Analizatory innych firm, takie jak [StyleCop,](https://www.nuget.org/packages/StyleCop.Analyzers/) [Roslynator,](https://www.nuget.org/packages/Roslynator.Analyzers/) [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)i [Sonar Analyzer.](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="severity-levels-of-analyzers"></a>Poziomy ważności analizatorów

Każdy analizator ma jeden z następujących poziomów ważności:

| Ważność (Eksplorator rozwiązań) | Ważność (plik EditorConfig) | Zachowanie w czasie kompilacji | Zachowanie edytora |
|-|-|-|
| Błąd | `error` | Naruszenia są wyświetlane jako *Błędy* na liście błędów i w danych wyjściowych kompilacji wiersza polecenia i powodują niepowodzenie kompilacji.| Obrażający kod jest podkreślony czerwonym zygmkiem i oznaczony małym czerwonym polem na pasku przewijania. |
| Ostrzeżenie | `warning` | Naruszenia są wyświetlane *jako ostrzeżenia* na liście błędów i w danych wyjściowych kompilacji wiersza polecenia, ale nie powodują awarii kompilacji. | Obrażający kod jest podkreślony zielonym zygmkiem i oznaczony małym zielonym polem na pasku przewijania. |
| Info | `suggestion` | Naruszenia są wyświetlane *jako Komunikaty* na liście błędów, a w ogóle nie w danych wyjściowych kompilacji wiersza polecenia. | Obrażający kod jest podkreślony szarym zygmkiem i oznaczony małym szarym polem na pasku przewijania. |
| Ukryty | `silent` | Nie jest widoczny dla użytkownika. | Nie jest widoczny dla użytkownika. Diagnostyka jest jednak zgłaszana do aparatu diagnostycznego IDE. |
| Brak | `none` | Całkowicie pominięte. | Całkowicie pominięte. |
| Domyślne | `default` | Odpowiada domyślnej ważności reguły. Aby określić, jaka jest wartość domyślna reguły, poszukaj w okno Właściwości. | Odpowiada domyślnej ważności reguły. |

Jeśli analizator znajdzie naruszenia reguł, zostaną one zgłoszone w edytorze  kodu (jako zygym pod kodem naruszającym kod) i w oknie Lista błędów.

![Naruszenie analizatora w oknie Lista błędów](../code-quality/media/code-analysis-error-list.png)

Naruszenia analizatora zgłoszone na liście błędów są zgodne z [ustawieniem poziomu](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) ważności reguły. Naruszenia analizatora są również wyświetlane w edytorze kodu jako zygmki pod kodem, który jest odejmowany. Na poniższej ilustracji przedstawiono trzy naruszenia: jeden błąd (czerwony zygmki), jedno ostrzeżenie (zielony zygieł) i jedna &mdash; sugestia (trzy szare kropki):

![Zygniał w edytorze kodu w Visual Studio](media/diagnostics-severity-colors.png)

Wiele reguł analizatora lub *diagnostyki* ma  co najmniej jedną skojarzoną poprawki kodu, które można zastosować w celu skorygowania naruszenia reguły. Poprawki kodu są wyświetlane w menu ikony żarówki wraz z innymi typami [szybkich akcji.](../ide/quick-actions.md) Aby uzyskać informacje o tych poprawkach kodu, zobacz [Typowe szybkie akcje](../ide/quick-actions.md).

![Naruszenie analizatora i poprawka kodu szybkiej akcji](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Konfigurowanie poziomów ważności analizatora

Ważność reguł analizatora lub diagnostyki można skonfigurować w pliku [EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) lub w [menu żarówki](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu).

Analizatory można również skonfigurować do inspekcji kodu w czasie kompilacji i na żywo podczas wpisywania. Zakres analizy kodu na żywo można skonfigurować do wykonywania tylko dla bieżącego dokumentu, wszystkich otwartych dokumentów lub całego rozwiązania. Zobacz [Jak skonfigurować zakres analizy kodu na żywo](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Błędy i ostrzeżenia czasu kompilacji z analizatorów kodu są wyświetlane tylko wtedy, gdy analizatory są zainstalowane jako pakiet NuGet. Wbudowane analizatory (na przykład IDE0067 i IDE0068) nigdy nie są uruchamiane podczas kompilacji.

## <a name="nuget-package-versus-vsix-extension"></a>Pakiet NuGet a rozszerzenie VSIX

Analizatory innych firm można instalować dla każdego projektu za pośrednictwem pakietu NuGet. Niektóre są również dostępne jako rozszerzenie Visual Studio, w którym to przypadku mają zastosowanie do dowolnego rozwiązania otwartego w Visual Studio. Istnieją pewne kluczowe różnice w zachowaniu między tymi dwiema metodami [instalowania analizatorów](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Zakres

Jeśli zainstalujesz analizatory jako Visual Studio, będą one stosowane na poziomie rozwiązania i do wszystkich wystąpień Visual Studio. Jeśli zainstalujesz analizatory jako pakiet NuGet, który jest preferowaną metodą, będą one stosowane tylko do projektu, w którym został zainstalowany pakiet NuGet. W środowiskach zespołowych analizatory zainstalowane jako pakiety NuGet znajdują się w zakresie dla *wszystkich* deweloperów, którzy pracują nad tym projektem.

### <a name="build-errors"></a>Błędy kompilacji

Aby reguły były wymuszane w czasie kompilacji, w tym za pośrednictwem wiersza polecenia lub w ramach kompilacji ciągłej integracji (CI), można wybrać jedną z następujących opcji:

- Utwórz projekt .NET 5.0, który domyślnie zawiera analizatory w zestawie .NET SDK. Analiza kodu jest domyślnie włączona dla projektów przeznaczonych dla platformy .NET 5.0 lub nowszej. Analizę kodu można włączyć dla projektów docelowych wcześniejszych wersji programu .NET, ustawiając właściwość [EnableNETAnalyzers na](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) wartość true.

- Zainstaluj analizatory jako pakiet NuGet. Ostrzeżenia i błędy analizatora nie są wyświetlane w raporcie kompilacji, jeśli zainstalujesz analizatory jako rozszerzenie.

Na poniższej ilustracji przedstawiono dane wyjściowe kompilacji wiersza polecenia z kompilacji projektu zawierającego naruszenie reguły analizatora:

![Dane wyjściowe programu MSBuild z naruszeniem reguły](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Ważność reguły

Nie można skonfigurować ważności reguł z analizatorów, które zostały zainstalowane jako Visual Studio rozszerzenia. Aby skonfigurować [ważność reguły,](../code-quality/use-roslyn-analyzers.md#configure-severity-levels)zainstaluj analizatory jako pakiet NuGet.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Instalowanie analizatorów kodu w programie Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Używanie analizatorów kodu w Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz też

- [Analizatory — często zadawane pytania](analyzers-faq.yml)
- [Pisanie własnego analizatora kodu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK platformy kompilatora .NET](/dotnet/csharp/roslyn-sdk/)