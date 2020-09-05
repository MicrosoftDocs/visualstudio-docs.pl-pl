---
title: Ważność i pomijanie reguły analizatora
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
ms.openlocfilehash: ac5103b15cee6e44650d9b8aef6fdf755874b2d2
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2020
ms.locfileid: "89490290"
---
# <a name="use-code-analyzers"></a>Korzystanie z analizatorów kodu

.NET Compiler Platform ("Roslyn") analizatory kodu analizują kod C# lub Visual Basic podczas pisania. Każda *Diagnostyka* lub reguła ma domyślną ważność i stan pomijania, który można zastąpić dla projektu. W tym artykule omówiono Ustawianie ważności reguły, korzystanie z zestawów reguł i pomijanie naruszeń.

## <a name="analyzers-in-solution-explorer"></a>Analizatory w Eksplorator rozwiązań

Można wykonać wiele czynności dostosowywania diagnostyki analizatora **Eksplorator rozwiązań**. Jeśli [instalujesz analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet, węzeł **analizatory** zostanie wyświetlony w węźle **odwołania** lub **zależności** w **Eksplorator rozwiązań**. W przypadku rozwinięcia **analizatorów, a**następnie rozszerzenia jednego z zestawów, zostanie wyświetlona cała Diagnostyka w zestawie.

![Węzeł analizatorów w Eksplorator rozwiązań](media/analyzers-expanded-in-solution-explorer.png)

Właściwości diagnostyki, w tym jej opis i domyślną ważność, można wyświetlić w oknie **Właściwości** . Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy regułę i wybierz pozycję **Właściwości**lub wybierz regułę, a następnie naciśnij klawisz **Alt** + **Enter**.

![Właściwości diagnostyczne w okno Właściwości](media/analyzer-diagnostic-properties.png)

Aby wyświetlić dokumentację online dla diagnostyki, kliknij prawym przyciskiem myszy diagnostykę i wybierz polecenie **Wyświetl pomoc**.

Ikony obok każdej diagnostyki w **Eksplorator rozwiązań** odpowiadają ikonom widocznym w zestawie reguł po otwarciu go w edytorze:

- Symbol "x" w okręgu wskazuje [ważność](#rule-severity) **błędu**
- "!" w trójkącie wskazuje [ważność](#rule-severity) **ostrzeżenia**
- "i" w okręgu wskazuje [ważność](#rule-severity) **informacji**
- "i" w okręgu w jasnym kolorze tła wskazuje [ważność](#rule-severity) **ukrycia**
- strzałka skierowana w dół w okręgu wskazuje, że Diagnostyka jest pomijana

![Ikony diagnostyki w Eksplorator rozwiązań](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Ważność reguły

::: moniker range=">=vs-2019"

Można skonfigurować ważność reguł analizatora lub *diagnostyki*, jeśli [są instalowane analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet. Począwszy od programu Visual Studio 2019 w wersji 16,3, można skonfigurować ważność reguły [w pliku EditorConfig](#set-rule-severity-in-an-editorconfig-file). Możesz również zmienić ważność reguły [z Eksplorator rozwiązań](#set-rule-severity-from-solution-explorer) lub [w pliku zestawu reguł](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Można skonfigurować ważność reguł analizatora lub *diagnostyki*, jeśli [są instalowane analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet. Można zmienić ważność reguły [z Eksplorator rozwiązań](#set-rule-severity-from-solution-explorer) lub [w pliku zestawu reguł](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

W poniższej tabeli przedstawiono różne opcje ważności:

| Ważność (Eksplorator rozwiązań) | Ważność (plik EditorConfig) | Zachowanie w czasie kompilacji | Zachowanie edytora |
|-|-|-|
| Error | `error` | Naruszenia są wyświetlane jako *Błędy* w Lista błędów i w danych wyjściowych kompilacji w wierszu polecenia i powodują niepowodzenie kompilacji.| Kod powodujący problemy jest podkreślony czerwoną czerwoną ramką na pasku przewijania. |
| Ostrzeżenie | `warning` | Naruszenia są wyświetlane jako *ostrzeżenia* w Lista błędów i w danych wyjściowych kompilacji wiersza polecenia, ale nie powodują awarii kompilacji. | Kod powodujący problemy jest podkreślony zieloną, zieloną ramką na pasku przewijania. |
| Info | `suggestion` | Naruszenia są wyświetlane jako *komunikaty* w Lista błędów, a nie w danych wyjściowych kompilacji wiersza polecenia. | Kod powodujący problemy jest podkreślony szarym i oznaczonym przez małe szare pole na pasku przewijania. |
| Ukryty | `silent` | Niewidoczny dla użytkownika. | Niewidoczny dla użytkownika. Diagnostyka jest jednak raportowana w aparacie diagnostyki IDE. |
| Brak | `none` | Całkowicie pomijane. | Całkowicie pomijane. |
| Domyślny | `default` | Odnosi się do domyślnej wagi reguły. Aby określić, jaka jest wartość domyślna dla reguły, należy poszukać w okno Właściwości. | Odnosi się do domyślnej wagi reguły. |

Poniższy zrzut ekranu edytora kodu pokazuje trzy różne naruszenia z różnymi serwerami. Zwróć uwagę na kolor zygzaka i małego, kolorowego kwadratu na pasku przewijania po prawej stronie.

![Błąd, ostrzeżenie i naruszenie informacji w edytorze kodu](media/diagnostics-severity-colors.png)

Poniższy zrzut ekranu przedstawia te same trzy naruszenia, które są wyświetlane w Lista błędów:

![Błąd, ostrzeżenie i naruszenie informacji w Lista błędów](media/diagnostics-severities-in-error-list.png)

### <a name="hidden-severity-versus-none-severity"></a>Ważność wartości "Hidden" lub "Brak"

`Hidden` reguły ważności, które są domyślnie włączone, są inne niż reguły wyłączone lub `None` ważności na kilka sposobów.

- Jeśli jakakolwiek poprawka kodu została zarejestrowana dla `Hidden` reguły ważności, poprawka jest oferowana jako akcja refaktoryzacji kodu żarówki w programie Visual Studio, mimo że ukryta Diagnostyka nie jest widoczna dla użytkownika. Nie jest to przypadek dla wyłączonych `None` reguł ważności.
- `Hidden` reguły ważności mogą być konfigurowane zbiorczo według wpisów, które [ustawiają ważność reguły dla wielu reguł analizatora w pliku EditorConfig](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file). `None` nie można skonfigurować reguł ważności w ten sposób. Zamiast tego należy je skonfigurować przy użyciu wpisów, które [ustawiają ważność reguły w pliku EditorConfig dla każdego identyfikatora reguły](#set-rule-severity-in-an-editorconfig-file).

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Ustawianie ważności reguły w pliku EditorConfig

(Program Visual Studio 2019 w wersji 16,3 lub nowszej)

Można ustawić ważność ostrzeżeń kompilatora lub reguł analizatora w pliku EditorConfig o następującej składni:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Ustawienie ważności reguły w pliku EditorConfig ma pierwszeństwo przed ważnością ustawioną w zestawie reguł lub w Eksplorator rozwiązań. Ważność można skonfigurować [ręcznie](#manually-configure-rule-severity) w pliku EditorConfig lub [automatycznie](#automatically-configure-rule-severity) za pomocą żarówki, która pojawia się obok naruszenia.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Ustaw ważność reguły dla wielu reguł analizatora jednocześnie w pliku EditorConfig

(Program Visual Studio 2019 w wersji 16,5 lub nowszej)

Można ustawić ważność dla określonej kategorii reguł analizatora lub dla wszystkich reguł analizatora z pojedynczym wpisem w pliku EditorConfig.

- Ustaw ważność reguły dla kategorii reguł analizatora:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Ustaw ważność reguły dla wszystkich reguł analizatora:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Wpisy do konfigurowania wielu reguł analizatora jednocześnie dotyczą tylko reguł, które są *domyślnie włączone*. Reguły analizatora, które są oznaczone jako wyłączone domyślnie w pakiecie analizatora, muszą być włączone za pomocą wpisów jawnych `dotnet_diagnostic.<rule ID>.severity = <severity>` .

Jeśli masz wiele wpisów, które mają zastosowanie do określonego identyfikatora reguły, poniżej podano kolejność pierwszeństwa, aby wybrać odpowiedni wpis:

- Wpis ważności dla pojedynczej reguły według identyfikatora ma pierwszeństwo przed wpisem o ważności dla kategorii.
- Wpis ważności dla kategorii ma pierwszeństwo przed wpisem ważności dla wszystkich reguł analizatora.

Rozważmy następujący przykład EditorConfig, gdzie [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) ma kategorię "Performance":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

W poprzednim przykładzie wszystkie trzy wpisy mają zastosowanie do CA1822. Jednak przy użyciu określonych reguł pierwszeństwa, pierwszy wpis ważności oparty na identyfikatorze (w ramach identyfikatora reguły) w ciągu następnych wpisów. W tym przykładzie CA1822 będzie miał efektywną ważność "Error". Wszystkie pozostałe reguły z kategorią "Performance" będą mieć ważność "Warning". Wszystkie pozostałe reguły analizatora, które nie mają kategorii "Performance", będą mieć ważność "sugestia".

#### <a name="manually-configure-rule-severity"></a>Ręcznie skonfiguruj ważność reguły

1. Jeśli nie masz jeszcze pliku EditorConfig dla projektu, [Dodaj go](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Dodaj wpis dla każdej reguły, która ma zostać skonfigurowana w ramach odpowiedniego rozszerzenia pliku. Na przykład, aby ustawić ważność [CA1822](ca1822.md) dla `error` plików języka C#, wpis wygląda następująco:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> W przypadku analizatorów stylu kodu IDE można także skonfigurować je w pliku EditorConfig przy użyciu innej składni, na przykład `dotnet_style_qualification_for_field = false:suggestion` . Jednak ustawienie ważności przy użyciu `dotnet_diagnostic` składni ma pierwszeństwo. Aby uzyskać więcej informacji, zobacz [konwencje językowe dla EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Konwertuj istniejący plik zestawu reguł na plik EditorConfig

Począwszy od programu Visual Studio 2019 w wersji 16,5, pliki zestawu reguł są przestarzałe na rzecz pliku EditorConfig na potrzeby konfiguracji analizatora dla kodu zarządzanego. Większość narzędzi programu Visual Studio dla konfiguracji o ważności reguły analizatora została zaktualizowana tak, aby działała na plikach EditorConfig zamiast w plikach zestawu reguł. Pliki EditorConfig umożliwiają skonfigurowanie obu opcji odniesień i analizatorów reguł analizatora, w tym opcji stylu kodu IDE programu Visual Studio. Zdecydowanie zaleca się przekonwertowanie istniejącego pliku zestawu reguł do pliku EditorConfig. Zaleca się także zapisanie pliku EditorConfig w katalogu głównym repozytorium lub w folderze rozwiązania. Przy użyciu katalogu głównego repozytorium lub folderu rozwiązania upewnij się, że ustawienia ważności z tego pliku są automatycznie stosowane do całego repozytorium lub rozwiązania.

Istnieje kilka sposobów konwertowania istniejącego pliku zestawu reguł do pliku EditorConfig:

- Z edytora zestawu reguł w programie Visual Studio (wymaga programu Visual Studio 2019 16,5 lub nowszego). Jeśli projekt używa już określonego pliku zestawu reguł `CodeAnalysisRuleSet` , można go przekonwertować na odpowiedni plik EditorConfig z edytora zestawu reguł w programie Visual Studio.

    1. Kliknij dwukrotnie plik zestawu reguł w Eksplorator rozwiązań.

       Plik zestawu reguł powinien być otwarty w edytorze zestawu reguł. Powinien pojawić się **pasek informacyjny** , który można klikać u góry edytora zestawu reguł.

       ![Konwertuj zestaw reguł na plik EditorConfig w edytorze zestawu reguł](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Wybierz łącze do **paska** informacji.

       Powinno to spowodować otwarcie okna dialogowego **Zapisz jako** , które pozwala wybrać katalog, w którym chcesz wygenerować plik EditorConfig.

    3. Wybierz przycisk **Zapisz** , aby wygenerować plik EditorConfig.

       Wygenerowany EditorConfig powinien być otwarty w edytorze. Ponadto właściwość MSBuild jest `CodeAnalysisRuleSet` aktualizowana w pliku projektu, dzięki czemu nie odwołuje się już do oryginalnego pliku zestawu reguł.

- Za pomocą wiersza polecenia:

    1. Zainstaluj pakiet NuGet [Microsoft. CodeAnalysis. RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Wykonaj `RulesetToEditorconfigConverter.exe` z zainstalowanego pakietu, używając ścieżek do pliku zestawu reguł i pliku EditorConfig jako argumenty wiersza polecenia.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Oto przykładowy plik zestawu reguł do przekonwertowania:

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

Jest to konwertowany plik EditorConfig:

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

#### <a name="automatically-configure-rule-severity"></a>Automatycznie Konfiguruj ważność reguły

##### <a name="configure-from-light-bulb-menu"></a>Menu Konfiguruj z żarówki

Program Visual Studio zapewnia wygodny sposób konfigurowania ważności reguły z menu żarówki [szybkich działań](../ide/quick-actions.md) .

1. Po wystąpieniu naruszenia, umieść wskaźnik myszy nad naruszeniem w edytorze i otwórz menu żarówki. Lub umieść kursor w wierszu i naciśnij klawisz **Ctrl** + **.** (kropka).

2. W menu żarówki wybierz pozycję **Konfiguruj lub Pomiń problemy** > **Konfiguruj \<rule ID> ważność**.

   ![Skonfiguruj ważność reguły z poziomu menu żarówki w programie Visual Studio](media/configure-rule-severity.png)

3. Z tego miejsca wybierz jedną z opcji ważności.

   ![Skonfiguruj ważność reguły jako sugestię](media/configure-rule-severity-suggestion.png)

   Program Visual Studio dodaje wpis do pliku EditorConfig, aby skonfigurować regułę do żądanego poziomu, jak pokazano w polu podglądu.

   > [!TIP]
   > Jeśli nie masz jeszcze pliku EditorConfig w projekcie, program Visual Studio utworzy go dla Ciebie.

##### <a name="configure-from-error-list"></a>Konfiguruj z listy błędów

Program Visual Studio udostępnia również wygodny sposób konfigurowania ważności reguły z menu kontekstowego listy błędów.

1. Po wystąpieniu naruszenia, kliknij prawym przyciskiem myszy wpis Diagnostic na liście błędów.

2. Z menu kontekstowego wybierz pozycję **Ustaw ważność**.

   ![Konfigurowanie ważności reguły na podstawie listy błędów w programie Visual Studio](media/configure-rule-severity-error-list.png)

3. Z tego miejsca wybierz jedną z opcji ważności.

   Program Visual Studio dodaje wpis do pliku EditorConfig w celu skonfigurowania reguły na żądanym poziomie.

   > [!TIP]
   > Jeśli nie masz jeszcze pliku EditorConfig w projekcie, program Visual Studio utworzy go dla Ciebie.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Ustaw ważność reguły na podstawie Eksplorator rozwiązań

1. W Eksplorator rozwiązań rozwiń węzeł analizatory **odwołań**  >  **Analyzers** (lub **Dependencies**  >  **analizatory** zależności dla projektów .NET Core).

2. Rozwiń zestaw, który zawiera regułę, dla której chcesz ustawić ważność.

::: moniker range=">=vs-2019"
3. Kliknij prawym przyciskiem myszy regułę, a następnie wybierz pozycję **Ustaw ważność**. W menu kontekstowym wybierz jedną z opcji ważności.

   Program Visual Studio dodaje wpis do pliku EditorConfig w celu skonfigurowania reguły na żądanym poziomie. Jeśli projekt używa pliku zestawu reguł zamiast pliku EditorConfig, wpis ważności zostanie dodany do pliku zestawu reguł.

   > [!TIP]
   > Jeśli nie masz jeszcze pliku EditorConfig lub zestawu reguł w projekcie, program Visual Studio utworzy nowy plik EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Kliknij prawym przyciskiem myszy regułę, a następnie wybierz pozycję **Ustaw ważność zestawu reguł**. W menu kontekstowym wybierz jedną z opcji ważności.

   Ważność reguły jest zapisywana w pliku aktywnego zestawu reguł.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Ustaw ważność reguły w pliku zestawu reguł

![Plik zestawu reguł w Eksplorator rozwiązań](media/ruleset-in-solution-explorer.png)

1. Otwórz plik aktywnego zestawu reguł w jeden z następujących sposobów:

- W **Eksplorator rozwiązań**kliknij dwukrotnie plik, kliknij prawym przyciskiem myszy **References**  >  węzeł**analizatory** odwołań, a następnie wybierz **Otwórz aktywny zestaw reguł**.
- Na stronie właściwości **Analiza kodu** dla projektu wybierz pozycję **Otwórz** .

  Jeśli po raz pierwszy edytujesz zestaw reguł, program Visual Studio tworzy kopię domyślnego pliku zestawu reguł, nazywa go * \<projectname> . zestaw*reguł i dodaje go do projektu. Ten niestandardowy zestaw reguł jest również aktywnym zestawem reguł dla projektu.

   > [!NOTE]
   > Projekty .NET Core i .NET Standard nie obsługują poleceń menu dla zestawów reguł w **Eksplorator rozwiązań**, na przykład **Otwórz aktywny zestaw reguł**. Aby określić regułę niedomyślną dla projektu .NET Core lub .NET Standard, ręcznie [Dodaj właściwość **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) do pliku projektu. Nadal można skonfigurować reguły w ramach zestawu reguł w interfejsie użytkownika edytora zestawu reguł programu Visual Studio.

1. Przejdź do reguły, rozszerzając jej zawierający zestaw.

1. W kolumnie **Akcja** wybierz wartość, aby otworzyć listę rozwijaną, a następnie wybierz odpowiednią ważność z listy.

   ![Plik zestawu reguł otwarty w edytorze](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Konfigurowanie wygenerowanego kodu

Analizatory są uruchamiane na wszystkich plikach źródłowych w projekcie i zgłaszają naruszenia. Jednak te naruszenia nie są przydatne w przypadku generowanych plików kodu, takich jak pliki kodu generowane przez projektanta, tymczasowe pliki źródłowe generowane przez system kompilacji itp. Użytkownicy nie mogą ręcznie edytować tych plików i/lub nie mogą naprawianie naruszeń w tych typach plików generowanych przez narzędzia.

Domyślnie sterownik analizatora wykonujący analizy traktuje pliki z określoną nazwą, rozszerzeniem pliku lub automatycznie generowanym nagłówkiem plików jako pliki wygenerowanego kodu. Na przykład nazwa pliku kończąca się ciągiem `.designer.cs` lub `.generated.cs` jest uznawana za wygenerowany kod. Jednak te heurystyke mogą nie być w stanie zidentyfikować wszystkich niestandardowych plików kodu wygenerowanych w kodzie źródłowym użytkownika.

Począwszy od programu Visual Studio 2019 16,5, użytkownicy końcowi mogą konfigurować określone pliki i/lub foldery, które mają być traktowane jako kod wygenerowany w [pliku EditorConfig](https://editorconfig.org/). Wykonaj poniższe kroki, aby dodać taką konfigurację:

1. Jeśli nie masz jeszcze pliku EditorConfig dla projektu, [Dodaj go](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Dodaj `generated_code = true | false` wpis dla określonych plików i/lub folderów. Na przykład, aby traktować wszystkie pliki, których nazwy kończą się `.MyGenerated.cs` jako wygenerowany kod, wpis będzie następujący:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Pomiń naruszenia

Istnieje wiele sposobów pomijania naruszeń reguł:

::: moniker range=">=vs-2019"

- W **pliku EditorConfig**

  Ustaw wartość ważność na na `none` przykład `dotnet_diagnostic.CA1822.severity = none` .

- Z menu **Analizuj**

  Wybierz pozycję **Analizuj**  >  **kompilację i Pomiń aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "określania poziomu odniesienia".

::: moniker-end

::: moniker range="vs-2017"

- Z menu **Analizuj**

  Wybierz pozycję **Analizuj**  >  **analizę kodu uruchamiania i Pomiń aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "określania poziomu odniesienia".

::: moniker-end

- Z **Eksplorator rozwiązań**

  Ustaw ważność reguły na **Brak**.

- Z **edytora zestawu reguł**

  Wyczyść pole wyboru obok jego nazwy **lub ustaw wartość** **Brak**.

- Z **edytora kodu**

  Umieść kursor w wierszu kodu z naruszeniem, a następnie naciśnij klawisz **Ctrl** + **(.)** , aby otworzyć menu **szybkie akcje** . Wybierz pozycję **Pomiń CAXXXX**  >  **w elemencie Source/in**.

  ![Pomiń diagnostykę z menu szybkich akcji](media/suppress-diagnostic-from-editor.png)

- Z **Lista błędów**

  Wybierz reguły, które chcesz pominąć, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Pomiń**  >  **w polu Źródło/w pliku pomijania**.

  - W przypadku pominięcia **programu w obszarze Źródło**zostanie otwarte okno dialogowe **Podgląd zmian** , w którym jest wyświetlany podgląd [#pragma ostrzeżenia](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) lub Visual Basic [#Disable ostrzeżenie](/dotnet/visual-basic/language-reference/directives/directives) , który zostanie dodany do kodu źródłowego.

    ![Wersja zapoznawcza dodawania #pragma ostrzeżenie w pliku kodu](media/pragma-warning-preview.png)

  - W przypadku wybrania **w pliku pomijania**zostanie otwarte okno dialogowe **Podgląd zmian** i zostanie wyświetlony podgląd <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu, który jest dodawany do globalnego pliku pominięć.

    ![Wersja zapoznawcza dodawania atrybutu SuppressMessage do pliku pominięcia](media/preview-changes-in-suppression-file.png)

  W oknie dialogowym **Podgląd zmian** wybierz pozycję **Zastosuj**.

  > [!NOTE]
  > Jeśli nie widzisz opcji **pomijania** menu w **Eksplorator rozwiązań**, naruszenie może być możliwe z kompilacji, a nie analizy na żywo. **Lista błędów** wyświetla diagnostykę lub naruszenia reguł zarówno z analizy kodu na żywo, jak i do kompilacji. Ponieważ Diagnostyka kompilacji może być nieaktualna, na przykład Jeśli edytujesz kod w celu usunięcia naruszenia, ale nie został on ponownie skompilowany, nie można pominąć tej diagnostyki z **Lista błędów**. Diagnostyka z analizy na żywo lub technologia IntelliSense są zawsze aktualne z bieżącymi źródłami i można je pominąć z poziomu **Lista błędów**. Aby wykluczyć diagnostykę *kompilacji* z wybranej opcji, Przełącz filtr źródła **Lista błędów** z **kompilacja + IntelliSense** na **technologię IntelliSense**. Następnie wybierz diagnostykę, którą chcesz pominąć, i wykonaj instrukcje opisane wcześniej.
  >
  > ![Filtr źródła Lista błędów w programie Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Użycie wiersza polecenia

Podczas kompilowania projektu w wierszu polecenia naruszenia reguły pojawiają się w danych wyjściowych kompilacji w przypadku spełnienia następujących warunków:

- Analizatory są instalowane jako pakiet NuGet, a nie jako rozszerzenie VSIX.

- Co najmniej jedna reguła narusza kod projektu.

- [Ważność](#rule-severity) naruszonej reguły jest ustawiona na wartość **Ostrzeżenie**, w przypadku których naruszenia przypadków nie powodują niepowodzenia kompilacji lub **błąd**, w których wypadek naruszenia przypadku niepowodzenia kompilacji.

Szczegółowość danych wyjściowych kompilacji nie ma wpływu na to, czy są wyświetlane naruszenia reguł. Nawet z **cichą** szczegółowością, naruszenia reguł pojawiają się w danych wyjściowych kompilacji.

> [!TIP]
> Jeśli jesteś przyzwyczajony do uruchomienia starszej analizy z poziomu wiersza polecenia, za pomocą *FxCopCmd.exe* lub za pośrednictwem programu MSBuild z flagą **RunCodeAnalysis** , Oto jak to zrobić za pomocą analizatorów kodu.

Aby wyświetlić naruszenia analizatora w wierszu polecenia podczas kompilowania projektu przy użyciu programu MSBuild, uruchom polecenie podobne do tego:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Na poniższej ilustracji przedstawiono dane wyjściowe kompilacji wiersza polecenia z kompilowania projektu, który zawiera naruszenie reguły analizatora:

![Dane wyjściowe MSBuild z naruszeniem reguły](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projekty zależne

W projekcie .NET Core, jeśli dodasz odwołanie do projektu, który ma analizatory NuGet, te analizatory są automatycznie dodawane do projektu zależnego. Aby wyłączyć to zachowanie, na przykład jeśli projekt zależny jest projektem testowym jednostkowym, Oznacz pakiet NuGet jako prywatny w pliku *. csproj* lub *. vbproj* projektu, do którego istnieje odwołanie, ustawiając atrybut **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Zobacz także

- [Przegląd analizatorów kodu w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Prześlij usterkę analizatora kodu](https://github.com/dotnet/roslyn-analyzers/issues)
- [Korzystanie z zestawów reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Pomiń ostrzeżenia analizy kodu](../code-quality/in-source-suppression-overview.md)
