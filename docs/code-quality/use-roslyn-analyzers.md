---
title: Konfiguracja analizatora
ms.date: 05/10/2021
description: Dowiedz się, jak dostosować reguły analizatora Roslyn. Zobacz, jak dostosować ważność analizatora, pominąć naruszenia i wyznaczyć pliki jako wygenerowany kod.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 36a9f1651a4aef7742b6bf52f8691f6ae8f9c616
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973385"
---
# <a name="overview"></a>Omówienie

Każda reguła lub  diagnostyka analizatora Roslyn ma domyślną ważność i stan pomijania, który można nadpisać i dostosować dla projektu. Ten artykuł obejmuje ustawianie ważności analizatora i pomijanie naruszeń analizatora.

## <a name="configure-severity-levels"></a>Konfigurowanie poziomów ważności

::: moniker range=">=vs-2019"

Począwszy od Visual Studio 2019 r. w wersji 16.3, można skonfigurować ważność reguł analizatora lub diagnostyki *w* pliku [EditorConfig](#set-rule-severity-in-an-editorconfig-file)z [menu](#set-rule-severity-from-the-light-bulb-menu)żarówki i z listy błędów.

::: moniker-end

::: moniker range="vs-2017"

Jeśli zainstalujesz analizatory jako pakiet NuGet, [](../code-quality/install-roslyn-analyzers.md) możesz skonfigurować ważność reguł analizatora lub diagnostyki . Ważność reguły można zmienić [z](#set-rule-severity-from-solution-explorer) Eksplorator rozwiązań lub [w pliku zestawu reguł](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

W poniższej tabeli przedstawiono różne opcje ważności:

| Ważność (Eksplorator rozwiązań) | Ważność (plik EditorConfig) | Zachowanie w czasie kompilacji | Zachowanie edytora |
|-|-|-|
| Błąd | `error` | Naruszenia są wyświetlane jako *Błędy* na liście błędów i w danych wyjściowych kompilacji wiersza polecenia i powodują niepowodzenie kompilacji.| Obrażający kod jest podkreślony czerwoną zygmającą linią i oznaczony małym czerwonym polem na pasku przewijania. |
| Ostrzeżenie | `warning` | Naruszenia są wyświetlane jako *Ostrzeżenia* na liście błędów i w danych wyjściowych kompilacji wiersza polecenia, ale nie powodują błędów kompilacji. | Obrażający kod jest podkreślony zielonym zygmki i oznaczony małym zielonym polem na pasku przewijania. |
| Info | `suggestion` | Naruszenia są wyświetlane *jako Komunikaty* na liście błędów, a w ogóle nie w danych wyjściowych kompilacji wiersza polecenia. | Obrażający kod jest podkreślony szarym zygmki i oznaczony małym szarym polem na pasku przewijania. |
| Ukryty | `silent` | Nie jest widoczny dla użytkownika. | Nie jest widoczny dla użytkownika. Diagnostyka jest jednak zgłaszana do aparatu diagnostycznego ŚRODOWISKA IDE. |
| Brak | `none` | Całkowicie pominięte. | Całkowicie pominięte. |
| Domyślne | `default` | Odpowiada domyślnej ważności reguły. Aby określić, jaka jest wartość domyślna dla reguły, poszukaj w okno Właściwości. | Odpowiada domyślnej ważności reguły. |

Jeśli analizator znajdzie naruszenia reguł, zostaną one zgłoszone w edytorze  kodu (jako zygym pod kodem naruszającym kod) i w oknie Lista błędów.

Naruszenia analizatora zgłoszone na liście błędów są zgodne z [ustawieniem poziomu](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) ważności reguły. Naruszenia analizatora są również wyświetlane w edytorze kodu jako zygmki pod kodem. Na poniższej ilustracji przedstawiono trzy naruszenia: jeden błąd (czerwony zygmki), jedno ostrzeżenie &mdash; (zielony zygmki) i jedna sugestia (trzy szare kropki):

![Zygki w edytorze kodu w Visual Studio](media/diagnostics-severity-colors.png)

Poniższy zrzut ekranu przedstawia te same trzy naruszenia, które są wyświetlane na liście błędów:

![Naruszenie błędów, ostrzeżeń i informacji na liście błędów](media/diagnostics-severities-in-error-list.png)

Wiele reguł analizatora lub *diagnostyki* ma co najmniej jedną skojarzoną poprawek *kodu,* które można zastosować w celu skorygowania naruszenia reguły. Poprawki kodu są wyświetlane w menu ikony żarówki wraz z innymi typami [szybkich akcji.](../ide/quick-actions.md) Aby uzyskać informacje o tych poprawkach kodu, zobacz [Typowe szybkie akcje](../ide/quick-actions.md).

![Naruszenie analizatora i poprawka kodu szybkiej akcji](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>Ważność "Ukryte" a ważność "Brak"

`Hidden` Reguły ważności, które są domyślnie włączone, różnią się od wyłączonych lub `None` reguł ważności na kilka sposobów.

- Jeśli jakakolwiek poprawka kodu została zarejestrowana dla reguły ważności, ta poprawka jest oferowana jako akcja refaktoryzacji kodu żarówki w programie Visual Studio, nawet jeśli ukryta diagnostyka nie jest widoczna dla `Hidden` użytkownika. Nie dotyczy to wyłączonych `None` reguł ważności.
- `Hidden` Reguły ważności można skonfigurować zbiorczo przez wpisy, które ustawiają ważność reguły wielu reguł analizatora [jednocześnie w pliku EditorConfig](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file). `None` nie można skonfigurować w ten sposób reguł ważności. Zamiast tego należy je skonfigurować za pomocą wpisów, które ustawiają ważność reguły w [pliku EditorConfig dla każdego identyfikatora reguły](#set-rule-severity-in-an-editorconfig-file).

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Ustawianie ważności reguły w pliku EditorConfig

(Visual Studio 2019 w wersji 16.3 lub nowszej)

Ważność ostrzeżeń kompilatora lub reguł analizatora można ustawić w pliku EditorConfig przy użyciu następującej składni:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Ustawianie ważności reguły w pliku EditorConfig ma pierwszeństwo przed ważnością ustawioną w zestawie reguł lub w Eksplorator rozwiązań. Ważność [można skonfigurować](#manually-configure-rule-severity-in-an-editorconfig-file) ręcznie w pliku EditorConfig lub automatycznie [za](#set-rule-severity-from-the-light-bulb-menu) pomocą żarówki wyświetlanej obok naruszenia.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Ustawianie ważności reguły dla wielu reguł analizatora jednocześnie w pliku EditorConfig

(Visual Studio 2019 w wersji 16.5 lub nowszej)

Można ustawić ważność dla określonej kategorii reguł analizatora lub dla wszystkich reguł analizatora z jednym wpisem w pliku EditorConfig.

- Ustaw ważność reguły dla kategorii reguł analizatora:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Ustaw ważność reguły dla wszystkich reguł analizatora:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Wpisy służące do konfigurowania wielu reguł analizatora jednocześnie mają zastosowanie tylko do reguł, które *są domyślnie włączone.* Reguły analizatora, które są domyślnie oznaczone jako wyłączone w pakiecie analizatora, muszą być włączone za pośrednictwem jawnych `dotnet_diagnostic.<rule ID>.severity = <severity>` wpisów.

Jeśli masz wiele wpisów, które mają zastosowanie do określonego identyfikatora reguły, pierwszeństwo ma kolejność wyboru odpowiedniego wpisu:

- Wpis ważności dla poszczególnych reguł według identyfikatora ma pierwszeństwo przed wpisem ważności dla kategorii.
- Wpis ważności dla kategorii ma pierwszeństwo przed wpisem ważności dla wszystkich reguł analizatora.

Rozważmy następujący przykład editorconfig, gdzie [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) ma kategorię "Wydajność":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

W poprzednim przykładzie wszystkie trzy wpisy mają zastosowanie do CA1822. Jednak przy użyciu określonych reguł pierwszeństwa, pierwszy wpis ważności na podstawie identyfikatora reguły przejmuje następne wpisy. W tym przykładzie CA1822 będzie miał efektywną ważność "błąd". Wszystkie pozostałe reguły z kategorią "Wydajność" będą mieć ważność "ostrzeżenie". Wszystkie pozostałe reguły analizatora, które nie mają kategorii "Wydajność", będą mieć ważność "sugestia".

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Ręczne konfigurowanie ważności reguły w pliku EditorConfig

1. Jeśli nie masz jeszcze pliku EditorConfig dla projektu, [dodaj jeden .](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Dodaj wpis dla każdej reguły, którą chcesz skonfigurować, w ramach odpowiedniego rozszerzenia pliku. Na przykład, aby ustawić ważność [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) dla plików `error` języka C#, wpis wygląda następująco:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> W przypadku analizatorów stylu kodu IDE można je również skonfigurować w pliku EditorConfig przy użyciu innej składni, na przykład `dotnet_style_qualification_for_field = false:suggestion` . Jeśli jednak ustawisz ważność przy użyciu `dotnet_diagnostic` składni , ma ona pierwszeństwo. Aby uzyskać więcej informacji, zobacz [Language conventions for EditorConfig (Konwencje języka dla pliku EditorConfig).](/dotnet/fundamentals/code-analysis/style-rules/language-rules)

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Ustawianie ważności reguły z menu żarówki

Visual Studio udostępnia wygodny sposób konfigurowania ważności reguły z menu [żarówki Szybkie](../ide/quick-actions.md) akcje.

1. Po naruszeniu zatrzymaj wskaźnik myszy na zygmłonie naruszenia w edytorze i otwórz menu żarówki. Możesz też umieścić kursor w wierszu i nacisnąć **klawisz Ctrl** + **.** (okres).

2. W menu żarówki wybierz pozycję Konfiguruj **lub Pomiń problemy** > **Skonfiguruj \<rule ID> ważność.**

   ![Konfigurowanie ważności reguły z menu żarówki w menu Visual Studio](media/configure-rule-severity.png)

3. W tym miejscu wybierz jedną z opcji ważności.

   ![Skonfiguruj ważność reguły jako sugestię](media/configure-rule-severity-suggestion.png)

   Visual Studio dodaje wpis do pliku EditorConfig w celu skonfigurowania reguły na żądany poziom, jak pokazano w oknie podglądu.

   > [!TIP]
   > Jeśli nie masz jeszcze pliku EditorConfig w projekcie, Visual Studio go dla Ciebie.

### <a name="set-rule-severity-from-the-error-list-window"></a>Ustawianie ważności reguły w oknie Lista błędów

Visual Studio również wygodny sposób konfigurowania ważności reguły z menu kontekstowego listy błędów.

1. Po naruszeniu kliknij prawym przyciskiem myszy wpis diagnostyki na liście błędów.

2. Z menu kontekstowego wybierz pozycję **Ustaw ważność**.

   ![Konfigurowanie ważności reguły na liście błędów w Visual Studio](media/configure-rule-severity-error-list.png)

3. W tym miejscu wybierz jedną z opcji ważności.

   Visual Studio dodaje wpis do pliku EditorConfig, aby skonfigurować regułę na żądany poziom.

   > [!TIP]
   > Jeśli nie masz jeszcze pliku EditorConfig w projekcie, Visual Studio go dla Ciebie.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Ustawianie ważności reguły z Eksplorator rozwiązań

Większość dostosowywania diagnostyki analizatora można wykonać z **Eksplorator rozwiązań**. Jeśli [zainstalujesz analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet, węzeł  **Analizatory** pojawi się w węźle Odwołania lub Zależności w **Eksplorator rozwiązań**.  Jeśli **rozwiniesz pozycję Analizatory,** a następnie rozwiniesz jeden z zestawów analizatorów, zobaczysz całą diagnostykę w zestawie.

![Węzeł Analizatory w Eksplorator rozwiązań](media/analyzers-expanded-in-solution-explorer.png)

Właściwości diagnostyki, w tym jej opis i domyślną ważność, można wyświetlić w **oknie** Właściwości. Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy regułę i wybierz pozycję **Właściwości** lub wybierz regułę, a następnie naciśnij **klawisz Alt** + **Enter**.

![Właściwości diagnostyczne w okno Właściwości](media/analyzer-diagnostic-properties.png)

Aby wyświetlić dokumentację online dotyczącą diagnostyki, kliknij prawym przyciskiem myszy diagnostykę i wybierz **polecenie Wyświetl pomoc.**

Ikony obok każdej diagnostyki w **Eksplorator rozwiązań** odpowiadają ikonom wyświetlonym w zestawie reguł po otwarciu go w edytorze:

- znak "x" w okręgu wskazuje [ważność](#configure-severity-levels) **błędu**
- "!" w trójkątie wskazuje [ważność](#configure-severity-levels) **Ostrzeżenie**
- "i" w okręgu wskazuje [ważność](#configure-severity-levels) **informacji**
- "i" w okręgu na jasnym tle wskazuje [ważność](#configure-severity-levels) **Ukryte**
- Strzałka skierowana w dół w okręgu wskazuje, że diagnostyka jest pomijana

![Ikony diagnostyki w Eksplorator rozwiązań](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Konwertowanie istniejącego pliku ruleset na plik EditorConfig

Począwszy od Visual Studio 2019 r. w wersji 16.5, pliki grupy reguł są przestarzałe na rzecz pliku EditorConfig dla konfiguracji analizatora dla kodu zarządzanego. Większość narzędzi Visual Studio dla konfiguracji ważności reguły analizatora została zaktualizowana do pracy z plikami EditorConfig zamiast plikami zestawu reguł. Pliki EditorConfig umożliwiają skonfigurowanie ważności reguł analizatora i opcji analizatora, w tym Visual Studio stylu kodu IDE. Zdecydowanie zaleca się przekonwertowanie istniejącego pliku ruleset na plik EditorConfig. Zaleca się również zapisanie pliku EditorConfig w katalogu głównym swojego repo lub w folderze rozwiązania. Korzystając z katalogu głównego swojego repo lub folderu rozwiązania, upewnij się, że ustawienia ważności z tego pliku są automatycznie stosowane odpowiednio do całego repo lub rozwiązania.

Istnieje kilka sposobów konwertowania istniejącego pliku grupy reguł na plik EditorConfig:

- W Edytorze reguł w Visual Studio (wymaga Visual Studio 2019 16.5 lub nowszego). Jeśli projekt używa już określonego pliku grupy reguł jako pliku , można przekonwertować go na równoważny plik EditorConfig z edytora reguł w `CodeAnalysisRuleSet` Visual Studio.

    1. Kliknij dwukrotnie plik z Eksplorator rozwiązań.

       Plik ruleset powinien zostać otwarty w Edytorze reguł. W górnej części edytora **grupy** reguł powinien zostać wyświetlony klikalny pasek informacyjny.

       ![Konwertowanie grupy reguł na plik EditorConfig w edytorze reguł](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Wybierz **link do paska** informacji.

       Powinno zostać otwarte okno **dialogowe Zapisz** jako, w którym można wybrać katalog, w którym chcesz wygenerować plik EditorConfig.

    3. Wybierz przycisk **Zapisz,** aby wygenerować plik EditorConfig.

       Wygenerowany plik EditorConfig powinien zostać otwarty w edytorze. Ponadto właściwość MSBuild jest aktualizowana w pliku projektu, dzięki czemu nie odwołuje się już do `CodeAnalysisRuleSet` oryginalnego pliku ruleset.

- Za pomocą wiersza polecenia:

    1. Zainstaluj pakiet NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter)

    2. Wykonaj polecenie z zainstalowanego pakietu ze ścieżkami do pliku zestawu reguł i pliku `RulesetToEditorconfigConverter.exe` EditorConfig jako argumenty wiersza polecenia.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Oto przykładowy plik ruleset do konwersji:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Oto przekonwertowany plik EditorConfig:

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Ustawianie ważności reguły z Eksplorator rozwiązań

1. W Eksplorator rozwiązań rozwiń pozycję  >  **Analizatory odwołań** (lub **Analizatory**  >  **zależności dla** projektów .NET Core).

2. Rozwiń zestaw zawierający regułę, dla której chcesz ustawić ważność.

::: moniker range=">=vs-2019"
3. Kliknij prawym przyciskiem myszy regułę i wybierz **polecenie Ustaw ważność**. W menu kontekstowym wybierz jedną z opcji ważności.

   Visual Studio dodaje wpis do pliku EditorConfig, aby skonfigurować regułę na żądany poziom. Jeśli projekt używa pliku ruleset zamiast pliku EditorConfig, wpis ważności jest dodawany do pliku grupy reguł.

   > [!TIP]
   > Jeśli nie masz jeszcze pliku EditorConfig lub pliku ruleset w projekcie, Visual Studio utworzy nowy plik EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Kliknij prawym przyciskiem myszy regułę i wybierz **polecenie Ustaw ważność zestawu reguł.** W menu kontekstowym wybierz jedną z opcji ważności.

   Ważność reguły jest zapisywana w aktywnym pliku zestawu reguł.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Ustawianie ważności reguły w pliku zestawu reguł

![Plik zestawu reguł w Eksplorator rozwiązań](media/ruleset-in-solution-explorer.png)

1. Otwórz aktywny plik zestawu reguł na jeden z następujących sposobów:

- W **Eksplorator rozwiązań** kliknij dwukrotnie plik, kliknij prawym przyciskiem myszy węzeł   >  **Analizatory** odwołań, a następnie wybierz polecenie Otwórz aktywny **zestaw reguł.**
- Na stronie **Code Analysis** projektu wybierz pozycję **Otwórz** .

  Jeśli edytujesz zestaw reguł po raz pierwszy, program Visual Studio kopię domyślnego pliku zestawu reguł, nadaje jej nazwę *\<projectname> .ruleset* i dodaje ją do projektu. Ten niestandardowy zestaw reguł staje się również aktywnym zestawem reguł dla projektu.

   > [!NOTE]
   > Projekty .NET Core i .NET Standard nie obsługują poleceń menu dla zestawów reguł w **programie Eksplorator rozwiązań**, na przykład Otwórz **aktywny zestaw reguł.** Aby określić zestaw reguł innych niż domyślne dla projektu .NET Core lub .NET Standard, ręcznie dodaj właściwość [ **CodeAnalysisRuleSet**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) do pliku projektu. Nadal można skonfigurować reguły w zestawie reguł w interfejsie użytkownika Visual Studio zestawu reguł.

1. Przejdź do reguły, rozwijając jej zawierający zestaw.

1. W kolumnie **Akcja** wybierz wartość , aby otworzyć listę rozwijaną, a następnie wybierz z listy odpowiednią ważność.

   ![Plik zestawu reguł otwarty w edytorze](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Konfigurowanie wygenerowanego kodu

Analizatory są uruchamiane na wszystkich plikach źródłowych w projekcie i raportują naruszenia na nich. Jednak te naruszenia nie są przydatne w przypadku wygenerowanych plików kodu, takich jak pliki kodu wygenerowane przez projektanta, tymczasowe pliki źródłowe generowane przez system kompilacji itp. Użytkownicy nie mogą ręcznie edytować tych plików i/lub nie są zaniepokojeni naprawianiem naruszeń w tego rodzaju plikach generowanych przez narzędzia.

Domyślnie analizatory wykonujące sterownik analizatora traktują pliki z określoną nazwą, rozszerzeniem pliku lub automatycznie wygenerowanym nagłówkiem pliku jako wygenerowane pliki kodu. Na przykład nazwa pliku kończąca się na `.designer.cs` lub jest uznawana za `.generated.cs` wygenerowany kod. Jednak te heurystyczne mogą nie być w stanie zidentyfikować wszystkich niestandardowych plików kodu wygenerowanego w kodzie źródłowym użytkownika.

Począwszy od Visual Studio 2019 16.5, użytkownicy końcowi mogą skonfigurować określone pliki i/lub foldery tak, aby były traktowane jako wygenerowany kod w pliku [EditorConfig.](https://editorconfig.org/) Wykonaj poniższe kroki, aby dodać taką konfigurację:

1. Jeśli nie masz jeszcze pliku EditorConfig dla projektu, [dodaj jeden .](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Dodaj `generated_code = true | false` wpis dla określonych plików i/lub folderów. Aby na przykład traktować wszystkie pliki, których nazwa kończy się na jako `.MyGenerated.cs` wygenerowany kod, wpis będzie następujący:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Pomijanie naruszeń

Naruszenia reguł można pominąć przy użyciu różnych metod. Aby uzyskać więcej informacji, zobacz [Pomijanie naruszeń analizy kodu](../code-quality/in-source-suppression-overview.md).

## <a name="command-line-usage"></a>Użycie wiersza polecenia

Podczas kompilowania projektu w wierszu polecenia naruszenia reguł są wyświetlane w danych wyjściowych kompilacji, jeśli zostaną spełnione następujące warunki:

- Analizatory są instalowane z zestawem .NET SDK lub jako pakiet NuGet, a nie jako rozszerzenie VSIX.

  W przypadku analizatorów zainstalowanych przy użyciu zestawu .NET SDK może być konieczne [włączenie analizatorów](../code-quality/install-net-analyzers.md). W przypadku stylów kodu można również [wymuszać style kodu](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) podczas kompilacji, ustawiając właściwość programu MSBuild.

- W kodzie projektu naruszono co najmniej jedną regułę.

- Ważność naruszonej reguły jest ustawiona na ostrzeżenie **,** w takim przypadku naruszenia nie powodują błędu kompilacji lub błędu **,** w którym to przypadku naruszenia powodują niepowodzenie kompilacji. [](#configure-severity-levels)

Szczegółowość danych wyjściowych kompilacji nie ma wpływu na to, czy są wyświetlane naruszenia reguł. Nawet przy **cichym** poziomem szczegółowości naruszenia reguł pojawiają się w danych wyjściowych kompilacji.

> [!TIP]
> Jeśli już wiesz, jak uruchamiać starszą analizę z wiersza polecenia za pomocą narzędziaFxCopCmd.exelub za pośrednictwem programu *msbuild* z flagą **RunCodeAnalysis,** oto jak to zrobić za pomocą analizatorów kodu.

Aby zobaczyć naruszenia analizatora w wierszu polecenia podczas kompilowania projektu przy użyciu programu msbuild, uruchom polecenie w ten sposób:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Na poniższej ilustracji przedstawiono dane wyjściowe kompilacji wiersza polecenia z kompilacji projektu zawierającego naruszenie reguły analizatora:

![Dane wyjściowe programu MSBuild z naruszeniem reguły](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projekty zależne

Jeśli w projekcie .NET Core dodasz odwołanie do projektu, który ma analizatory NuGet, te analizatory również zostaną automatycznie dodane do projektu zależnego. Aby wyłączyć to zachowanie, na przykład jeśli projekt zależny jest projektem testu jednostkowego, oznacz pakiet NuGet jako prywatny w pliku *csproj* lub *vbproj* przywoływzanych projektów, ustawiając atrybut **PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów kodu w Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Prześlij usterkę analizatora kodu](https://github.com/dotnet/roslyn-analyzers/issues)
- [Korzystanie z zestawów reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Pomijanie ostrzeżeń analizy kodu](../code-quality/in-source-suppression-overview.md)
- [Opcje konfiguracji analizy kodu (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
