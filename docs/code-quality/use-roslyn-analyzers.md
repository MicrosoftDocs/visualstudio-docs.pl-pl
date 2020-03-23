---
title: Ważność i tłumienie reguły analizatora
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431413"
---
# <a name="use-code-analyzers"></a>Korzystanie z analizatorów kodu

Analizatory kodu platformy kompilatora platformy .NET ("Roslyn") analizują kod języka C# lub Visual Basic podczas pisania. Każda *diagnostyka* lub reguła ma domyślny stan ważności i tłumienia, który można nadpisać dla projektu. W tym artykule omówiono ważność reguły ustawiania, używania zestawów reguł i wygaszania naruszeń.

## <a name="analyzers-in-solution-explorer"></a>Analizatory w Eksploratorze rozwiązań

Można wykonać wiele dostosowywania diagnostyki analizatora z **Eksploratora rozwiązań**. Jeśli [instalujesz analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet, węzeł **Analizatory** pojawi się w węźle **Odwołania** lub **zależności** w **Eksploratorze rozwiązań.** Jeśli rozwiniesz **Analizatory**, a następnie rozwiń jeden z zestawów analizatora, zobaczysz wszystkie diagnostyki w zestawie.

![Węzeł analizatorów w Eksploratorze rozwiązań](media/analyzers-expanded-in-solution-explorer.png)

Można wyświetlić właściwości diagnostyki, w tym jej opis i ważność domyślną, w oknie **Właściwości.** Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy regułę i wybierz polecenie **Właściwości**lub zaznacz regułę, a następnie naciśnij klawisz **Alt**+**Enter**.

![Właściwości diagnostyczne w oknie Właściwości](media/analyzer-diagnostic-properties.png)

Aby wyświetlić dokumentację online dotyczącą diagnostyki, kliknij prawym przyciskiem myszy diagnostykę i wybierz pozycję **Wyświetl Pomoc**.

Ikony obok każdej diagnostyki w **Eksploratorze rozwiązań** odpowiadają ikonom widocznym w zestawie reguł po otwarciu go w edytorze:

- "x" w okręgu wskazuje [na ważność](#rule-severity) **błędu**
- "!" w trójkącie wskazuje na [ważność](#rule-severity) **ostrzeżenia**
- "i" w kole wskazuje na [ważność](#rule-severity) **informacji**
- litera "i" w okręgu na jasnym tle wskazuje **na** [ważność](#rule-severity)
- strzałka skierowana w dół w okręgu wskazuje, że diagnostyka jest wygaszony

![Ikony diagnostyki w Eksploratorze rozwiązań](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Ważność reguły

::: moniker range=">=vs-2019"

Można skonfigurować ważność reguł analizatora lub *diagnostyki*, jeśli [instalujesz analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet. Począwszy od programu Visual Studio 2019 w wersji 16.3, można skonfigurować ważność reguły [w pliku EditorConfig](#set-rule-severity-in-an-editorconfig-file). Ważność reguły można również zmienić [w Eksploratorze rozwiązań](#set-rule-severity-from-solution-explorer) lub [w pliku zestawu reguł](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Można skonfigurować ważność reguł analizatora lub *diagnostyki*, jeśli [instalujesz analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet. Ważność reguły można zmienić [w Eksploratorze rozwiązań](#set-rule-severity-from-solution-explorer) lub [w pliku zestawu reguł](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

W poniższej tabeli przedstawiono różne opcje ważności:

| Ważność (Eksplorator rozwiązań) | Ważność (plik EditorConfig) | Zachowanie w czasie kompilacji | Zachowanie edytora |
|-|-|-|
| Błąd | `error` | Naruszenia są wyświetlane jako błędy na liście *błędów* i w danych wyjściowych kompilacji wiersza polecenia i powodują niepowodzenie kompilacji.| Naruszający kod jest podkreślony czerwoną falistą i oznaczony małym czerwonym polem na pasku przewijania. |
| Ostrzeżenie | `warning` | Naruszenia są wyświetlane jako *ostrzeżenia* na liście błędów i w danych wyjściowych kompilacji wiersza polecenia, ale nie powodują awarii kompilacji. | Naruszający kod jest podkreślony zielonym squiggle i oznaczony małym zielonym polem na pasku przewijania. |
| Info | `suggestion` | Naruszenia są wyświetlane jako *komunikaty* na liście błędów, a nie w ogóle w danych wyjściowych kompilacji wiersza polecenia. | Naruszający kod jest podkreślony szarym squiggle i oznaczony małym szarym polem na pasku przewijania. |
| Ukryty | `silent` | Niewidoczne dla użytkownika. | Niewidoczne dla użytkownika. Diagnostyka jest jednak zgłaszana do aparatu diagnostycznego IDE. |
| Brak | `none` | Całkowicie stłumiony. | Całkowicie stłumiony. |
| Domyślne | `default` | Odpowiada domyślnej ważności reguły. Aby określić, jaka jest wartość domyślna reguły, poszukaj w oknie Właściwości. | Odpowiada domyślnej ważności reguły. |

Poniższy zrzut ekranu edytora kodu pokazuje trzy różne naruszenia o różnych ważnościach. Zwróć uwagę na kolor faliste i mały, kolorowy kwadrat na pasku przewijania po prawej stronie.

![Naruszenie błędów, ostrzeżeń i informacji w edytorze kodu](media/diagnostics-severity-colors.png)

Poniższy zrzut ekranu przedstawia te same trzy naruszenia, które pojawiają się na liście błędów:

![Naruszenie błędów, ostrzeżeń i informacji na liście błędów](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Ustawianie ważności reguły w pliku EditorConfig

(Visual Studio 2019 w wersji 16.3 i nowszej)

Ważność ostrzeżeń kompilatora lub reguł analizatora można ustawić w pliku EditorConfig z następującą składnią:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Ustawienie ważności reguły w pliku EditorConfig ma pierwszeństwo przed ważnością ustawioną w zestawie reguł lub w Eksploratorze rozwiązań. Ważność można [ręcznie](#manually-configure-rule-severity) skonfigurować w pliku EditorConfig lub [automatycznie](#automatically-configure-rule-severity) za pośrednictwem żarówki, która pojawia się obok naruszenia.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Ustawianie ważności reguł wielu reguł analizatora jednocześnie w pliku EditorConfig

(Visual Studio 2019 w wersji 16.5 i nowszej)

Można ustawić ważność dla określonej kategorii reguł analizatora lub dla wszystkich reguł analizatora z jednego wpisu w pliku EditorConfig.

- Ustaw ważność reguły dla kategorii reguł analizatora:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Ustaw ważność reguły dla wszystkich reguł analizatora:

`dotnet_analyzer_diagnostic.severity = <severity>`

Jeśli masz wiele wpisów, które mają zastosowanie do określonego identyfikatora reguły, poniżej znajduje się kolejność pierwszeństwa, aby wybrać odpowiedni wpis:

- Wpis ważności dla indywidualnej reguły według identyfikatora ma pierwszeństwo przed wpisem ważności dla kategorii.
- Wpis ważności dla kategorii ma pierwszeństwo przed wpisem ważności dla wszystkich reguł analizatora.

Rozważmy następujący przykład EditorConfig, gdzie [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) ma kategorię "Wydajność":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

W poprzednim przykładzie wszystkie trzy wpisy mają zastosowanie do ca1822. Jednak przy użyciu określonych reguł pierwszeństwa, pierwszy wpis ważności oparty na identyfikatorze reguły wygrywa nad kolejnymi wpisami. W tym przykładzie CA1822 będzie miał skuteczną ważność "błąd". Wszystkie pozostałe reguły z kategorią "Wydajność" będą miały ważność "ostrzeżenie". Wszystkie pozostałe reguły analizatora, które nie mają kategorii "Wydajność", będą miały ważność "sugestia".

#### <a name="manually-configure-rule-severity"></a>Ręczne konfigurowanie ważności reguły

1. Jeśli nie masz jeszcze pliku EditorConfig dla projektu, [dodaj jeden](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)plik .

2. Dodaj wpis dla każdej reguły, którą chcesz skonfigurować w ramach odpowiedniego rozszerzenia pliku. Na przykład, aby ustawić ważność dla [CA1822](ca1822.md) `error` dla plików Języka C#, wpis wygląda następująco:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> W przypadku analizatorów w stylu kodu IDE można je również skonfigurować w pliku EditorConfig przy użyciu innej składni, `dotnet_style_qualification_for_field = false:suggestion`na przykład . Jednak jeśli ustawisz ważność `dotnet_diagnostic` przy użyciu składni, ma pierwszeństwo. Aby uzyskać więcej informacji, zobacz [Konwencje języka dla EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Konwertowanie istniejącego pliku ruleset na plik EditorConfig

Począwszy od programu Visual Studio 2019 w wersji 16.5, pliki uszeprzonego są przestarzałe na rzecz pliku EditorConfig dla konfiguracji analizatora dla kodu zarządzanego. Większość narzędzi programu Visual Studio dla konfiguracji ważności reguły analizatora została zaktualizowana do pracy z plikami EditorConfig zamiast plików zestawu reguł. EditorConfig pliki umożliwiają skonfigurowanie zarówno ważności reguły analizatora i opcje analizatora, w tym opcje stylu kodu IDE programu Visual Studio. Zdecydowanie zaleca się przekonwertowanie istniejącego pliku zieć reguł na plik EditorConfig. Zaleca się również zapisanie pliku EditorConfig w katalogu głównym repozytorium lub w folderze rozwiązania. Korzystając z katalogu głównego repozytorium lub folderu rozwiązania, upewnij się, że ustawienia ważności z tego pliku są automatycznie stosowane odpowiednio do całego repozytorium lub rozwiązania.

Istnieje kilka sposobów konwersji istniejącego pliku rozstawu reguł na plik EditorConfig:

- Z Edytora reguł w programie Visual Studio (wymaga programu Visual Studio 2019 16.5 lub nowszego). Jeśli projekt używa już określonego pliku usterek jako jego `CodeAnalysisRuleSet`, można przekonwertować go na równoważny plik EditorConfig z Edytora reguł w programie Visual Studio.

    1. Kliknij dwukrotnie plik pliku zawierającego reguły w Eksploratorze rozwiązań.

       Plik ruleset powinien zostać otwarty w Edytorze reguł. W górnej części edytora zasad powinien zostać wyświetlony klikalny **pasek informacyjny.**

       ![Konwertuj plik reguł na EditorConfig w Edytorze reguł](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Kliknij** łącze paska informacyjnego.

       Powinno to otworzyć okno dialogowe **Zapisz jako,** które umożliwia wybranie katalogu, w którym chcesz wygenerować plik EditorConfig.

    3. **Kliknij** przycisk **Zapisz,** aby wygenerować plik EditorConfig.

       Wygenerowany EditorConfig powinien zostać otwarty w edytorze. Ponadto właściwość `CodeAnalysisRuleSet` MSBuild jest aktualizowana w pliku projektu, dzięki czemu nie odwołuje się już do oryginalnego pliku pliku pliku ruleset.

- Z wiersza polecenia:

    1. Zainstaluj pakiet NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Wykonywanie `RulesetToEditorconfigConverter.exe` z zainstalowanego pakietu ze ścieżkami do pliku zestawu reguł i pliku EditorConfig jako argumentami wiersza polecenia.

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

#### <a name="automatically-configure-rule-severity"></a>Automatyczne konfigurowanie ważności reguły

##### <a name="configure-from-light-bulb-menu"></a>Konfigurowanie z menu żarówki

Visual Studio zapewnia wygodny sposób konfigurowania ważności reguły z menu żarówki [Szybkie akcje.](../ide/quick-actions.md)

1. Po wystąpieniu naruszenia najedź kursorem na naruszenie w edytorze i otwórz menu żarówki. Możesz też umieścić kursor na linii i nacisnąć klawisz **Ctrl**+**.** (okres).

2. Z menu żarówki wybierz pozycję **Konfiguruj lub wyłącz problemy** > **Konfigurowanie \<identyfikatora reguły> ważności**.

   ![Konfigurowanie ważności reguły z menu żarówki w programie Visual Studio](media/configure-rule-severity.png)

3. W tym miejscu wybierz jedną z opcji ważności.

   ![Konfigurowanie ważności reguły jako sugestii](media/configure-rule-severity-suggestion.png)

   Visual Studio dodaje wpis do editorconfig pliku, aby skonfigurować regułę do żądanego poziomu, jak pokazano w polu podglądu.

   > [!TIP]
   > Jeśli nie masz jeszcze EditorConfig pliku w projekcie, Visual Studio tworzy jeden dla Ciebie.

##### <a name="configure-from-error-list"></a>Konfigurowanie z listy błędów

Visual Studio zapewnia również wygodny sposób konfigurowania ważności reguły z menu kontekstowego listy błędów.

1. Po wystąpieniu naruszenia kliknij prawym przyciskiem myszy wpis diagnostyczny na liście błędów.

2. Z menu kontekstowego wybierz polecenie **Ustaw ważność**.

   ![Konfigurowanie ważności reguły z listy błędów w programie Visual Studio](media/configure-rule-severity-error-list.png)

3. W tym miejscu wybierz jedną z opcji ważności.

   Visual Studio dodaje wpis do editorconfig pliku, aby skonfigurować regułę do żądanego poziomu.

   > [!TIP]
   > Jeśli nie masz jeszcze EditorConfig pliku w projekcie, Visual Studio tworzy jeden dla Ciebie.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Ustawianie ważności reguły w Eksploratorze rozwiązań

1. W Eksploratorze rozwiązań rozwiń**analizatory** **odwołań** > (lub**analizatory** **zależności** > dla projektów .NET Core).

2. Rozwiń zestaw zawierający regułę, dla której chcesz ustawić ważność.

::: moniker range=">=vs-2019"
3. Kliknij prawym przyciskiem myszy regułę i wybierz polecenie **Ustaw ważność**. W menu kontekstowym wybierz jedną z opcji ważności.

   Visual Studio dodaje wpis do editorconfig pliku, aby skonfigurować regułę do żądanego poziomu. Jeśli projekt używa pliku usiepów zamiast pliku EditorConfig, wpis ważności jest dodawany do pliku ruleset.

   > [!TIP]
   > Jeśli nie masz jeszcze EditorConfig plik lub plik ruleset w projekcie, Visual Studio tworzy nowy plik EditorConfig dla Ciebie.
::: moniker-end

::: moniker range="vs-2017"
3. Kliknij prawym przyciskiem myszy regułę i wybierz polecenie **Ustaw ważność zestawu reguł**. W menu kontekstowym wybierz jedną z opcji ważności.

   Ważność reguły jest zapisywana w aktywnym pliku zestawu reguł.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Ustawianie ważności reguły w pliku zestawu reguł

![Plik zestawu reguł w Eksploratorze rozwiązań](media/ruleset-in-solution-explorer.png)

1. Otwórz aktywny plik zestawu reguł, klikając go dwukrotnie w **Eksploratorze rozwiązań,** wybierając **polecenie Otwórz aktywny zestaw reguł** w menu prawym przyciskiem myszy **węzła Analizatory odwołań** > **Analyzers** lub wybierając **pozycję Otwórz** na stronie właściwości **Analiza kodu** dla projektu.

   Jeśli jest to pierwszy raz, gdy edytujesz zestaw reguł, program Visual Studio tworzy kopię domyślnego pliku zestawu reguł, nazywa go * \<projectname>.ruleset*i dodaje go do projektu. Ten niestandardowy zestaw reguł staje się również aktywnym zestawem reguł dla projektu.

   > [!NOTE]
   > Projekty .NET Core i .NET Standard nie obsługują poleceń menu dla zestawów reguł w **Eksploratorze rozwiązań,** na przykład **Otwórz aktywny zestaw reguł**. Aby określić nie domyślny zestaw reguł dla projektu .NET Core lub .NET Standard, należy ręcznie [dodać właściwość **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) do pliku projektu. Nadal można skonfigurować reguły w ramach zestawu reguł w interfejsie użytkownika edytora reguł programu Visual Studio.

1. Przejdź do reguły, rozwijając jej zestaw zawierający.

1. W kolumnie **Akcja** wybierz wartość, aby otworzyć listę rozwijaną, a następnie wybierz żądaną ważność z listy.

   ![Plik zestawu reguł otwarty w edytorze](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Pomijanie naruszeń

Istnieje wiele sposobów na pomijanie naruszeń reguł:

::: moniker range=">=vs-2019"

- W **pliku EditorConfig**

  Ustaw ważność `none`na , `dotnet_diagnostic.CA1822.severity = none`na przykład .

- Z menu **Analiza**

  Wybierz **pozycję Analizuj** > **kompilację i pomijaj aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "baselining".

::: moniker-end

::: moniker range="vs-2017"

- Z menu **Analiza**

  Wybierz **opcję Analizuj** > **analizę kodu przebiegu i pomiń aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "baselining".

::: moniker-end

- Z **Eksploratora rozwiązań**

  Ustaw ważność reguły na **Brak**.

- Z **edytora zestawów reguł**

  Wyezwuj pole wyboru obok jego nazwy lub ustaw **opcję Akcja** na **Brak**.

- Z **edytora kodu**

  Umieść kursor w wierszu kodu z naruszeniem i naciśnij klawisz **Ctrl**+**Period (.),** aby otworzyć menu **Szybkie akcje.** Wybierz **opcję Wygaszanie CAXXXX** > **w pliku tłumienia źródła/w .**

  ![Pomijanie diagnostyki z menu szybkich akcji](media/suppress-diagnostic-from-editor.png)

- Z **listy błędów**

  Zaznacz reguły, które chcesz pominąć, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Wygasij** > **w pliku pomijania źródła/w obszarze pomijania**.

  - Jeśli wygasniesz **w źródle,** zostanie otwarte okno dialogowe **Zmiany podglądu** i zostanie wyświetlony podgląd [ostrzeżenia #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) języka C# lub dyrektywy o ostrzeżeniu języka Visual Basic [#Disable,](/dotnet/visual-basic/language-reference/directives/directives) która jest dodana do kodu źródłowego.

    ![Podgląd dodawania ostrzeżenia #pragma w pliku kodu](media/pragma-warning-preview.png)

  - Jeśli wybierzesz **opcję W pliku pomijania,** zostanie otwarte <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> okno dialogowe Podgląd **zmian** i zostanie wyświetlony podgląd atrybutu dodanego do globalnego pliku wygaszania.

    ![Podgląd dodawania atrybutu SuppressMessage do pliku pomijania](media/preview-changes-in-suppression-file.png)

  W oknie **dialogowym Zmiany podglądu** wybierz pozycję **Zastosuj**.

  > [!NOTE]
  > Jeśli nie widzisz opcji **Menu Pomijanie** w **Eksploratorze rozwiązań,** naruszenie prawdopodobnie pochodzi z kompilacji, a nie analizy na żywo. **Lista błędów** wyświetla diagnostyki lub naruszenia reguły, z analizy kodu na żywo i kompilacji. Ponieważ diagnostyka kompilacji może być przestarzała, na przykład, jeśli edytowano kod, aby naprawić naruszenie, ale nie został przebudowany, nie można pominąć tych diagnostyki z **listy błędów**. Diagnostyka z analizy na żywo lub IntelliSense są zawsze aktualne z bieżącymi źródłami i mogą być pomijane z **listy błędów**. Aby wykluczyć *diagnostykę kompilacji* z wyboru, przełącz filtr **źródłowy listy błędów** z **Kompilacja + IntelliSense** na **IntelliSense Only**. Następnie wybierz diagnostykę, którą chcesz wygasić, i postępuj zgodnie z wcześniejszym opisem.
  >
  > ![Filtr źródła listy błędów w programie Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Użycie wiersza polecenia

Podczas tworzenia projektu w wierszu polecenia naruszenia reguł są wyświetlane w danych wyjściowych kompilacji, jeśli spełnione są następujące warunki:

- Analizatory są instalowane jako pakiet NuGet, a nie jako rozszerzenie VSIX.

- Jedna lub więcej reguł są naruszane w kodzie projektu.

- [Ważność](#rule-severity) naruszonej reguły jest ustawiona na **ostrzeżenie,** w którym to przypadku naruszenia nie powodują awarii **kompilacji**lub błąd , w którym to przypadku naruszenia powodują niepowodzenie kompilacji.

Szczegółowość danych wyjściowych kompilacji nie wpływa na to, czy są wyświetlane naruszenia reguły. Nawet w **przypadku cichej** szczegółowości naruszenia reguł pojawiają się w danych wyjściowych kompilacji.

> [!TIP]
> Jeśli jesteś przyzwyczajony do uruchamiania starszej analizy z wiersza polecenia, albo z *FxCopCmd.exe* lub za pośrednictwem msbuild z Flaga **RunCodeAnalysis,** oto jak to zrobić z analizatorów kodu.

Aby wyświetlić naruszenia analizatora w wierszu polecenia podczas tworzenia projektu przy użyciu msbuild, uruchom polecenie w ten sposób:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Na poniższej ilustracji przedstawiono dane wyjściowe kompilacji wiersza polecenia z tworzenia projektu, który zawiera naruszenie reguły analizatora:

![Wyjście MSBuild z naruszeniem reguły](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projekty zależne

W projekcie .NET Core, jeśli dodasz odwołanie do projektu, który ma analizatory NuGet, analizatory te są automatycznie dodawane do projektu zależnego. Aby wyłączyć to zachowanie, na przykład jeśli projekt zależny jest projektem testowym jednostkowym, oznacz pakiet NuGet jako prywatny w pliku *csproj* lub *.vbproj* projektu, do którego istnieje odwołanie, ustawiając atrybut **PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów kodu w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Prześlij błąd analizatora kodu](https://github.com/dotnet/roslyn-analyzers/issues)
- [Używanie zestawów reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Pomijanie ostrzeżeń o analizie kodu](../code-quality/in-source-suppression-overview.md)
