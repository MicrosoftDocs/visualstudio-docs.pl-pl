---
title: Ważność i pomijanie reguły analizatora
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6cd4d5517dae889387ec632df57c90485bd366b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649055"
---
# <a name="use-code-analyzers"></a>Korzystanie z analizatorów kodu

.NET Compiler Platform ("Roslyn") analizatory kodu analizują C# kod lub Visual Basic w trakcie pisania. Każda *Diagnostyka* lub reguła ma domyślną ważność i stan pomijania, który można zastąpić dla projektu. W tym artykule omówiono Ustawianie ważności reguły, korzystanie z zestawów reguł i pomijanie naruszeń.

## <a name="analyzers-in-solution-explorer"></a>Analizatory w Eksplorator rozwiązań

Można wykonać wiele czynności dostosowywania diagnostyki analizatora **Eksplorator rozwiązań**. Jeśli [instalujesz analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet, węzeł **analizatory** zostanie wyświetlony w węźle **odwołania** lub **zależności** w **Eksplorator rozwiązań**. W przypadku rozwinięcia **analizatorów, a**następnie rozszerzenia jednego z zestawów, zostanie wyświetlona cała Diagnostyka w zestawie.

![Węzeł analizatorów w Eksplorator rozwiązań](media/analyzers-expanded-in-solution-explorer.png)

Właściwości diagnostyki, w tym jej opis i domyślną ważność, można wyświetlić w oknie **Właściwości** . Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy regułę i wybierz pozycję **Właściwości**lub wybierz regułę, a następnie naciśnij klawisz **Alt** +**Enter**.

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
| Błąd | `error` | Naruszenia są wyświetlane jako *Błędy* w Lista błędów i w danych wyjściowych kompilacji w wierszu polecenia i powodują niepowodzenie kompilacji.| Kod powodujący problemy jest podkreślony czerwoną czerwoną ramką na pasku przewijania. |
| Ostrzeżenie | `warning` | Naruszenia są wyświetlane jako *ostrzeżenia* w Lista błędów i w danych wyjściowych kompilacji wiersza polecenia, ale nie powodują awarii kompilacji. | Kod powodujący problemy jest podkreślony zieloną, zieloną ramką na pasku przewijania. |
| Informacje o | `suggestion` | Naruszenia są wyświetlane jako *komunikaty* w Lista błędów, a nie w danych wyjściowych kompilacji wiersza polecenia. | Kod powodujący problemy jest podkreślony szarym i oznaczonym przez małe szare pole na pasku przewijania. |
| Hidden | `silent` | Niewidoczny dla użytkownika. | Niewidoczny dla użytkownika. Diagnostyka jest jednak raportowana w aparacie diagnostyki IDE. |
| Brak | `none` | Całkowicie pomijane. | Całkowicie pomijane. |
| Domyślny | `default` | Odnosi się do domyślnej wagi reguły. Aby określić, jaka jest wartość domyślna dla reguły, należy poszukać w okno Właściwości. | Odnosi się do domyślnej wagi reguły. |

Poniższy zrzut ekranu edytora kodu pokazuje trzy różne naruszenia z różnymi serwerami. Zwróć uwagę na kolor zygzaka i małego, kolorowego kwadratu na pasku przewijania po prawej stronie.

![Błąd, ostrzeżenie i naruszenie informacji w edytorze kodu](media/diagnostics-severity-colors.png)

Poniższy zrzut ekranu przedstawia te same trzy naruszenia, które są wyświetlane w Lista błędów:

![Błąd, ostrzeżenie i naruszenie informacji w Lista błędów](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Ustawianie ważności reguły w pliku EditorConfig

(Program Visual Studio 2019 w wersji 16,3 lub nowszej)

Ogólna składnia służąca do określania ważności reguły w pliku EditorConfig jest następująca:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Ustawienie ważności reguły w pliku EditorConfig ma pierwszeństwo przed ważnością ustawioną w zestawie reguł lub w Eksplorator rozwiązań. Ważność można skonfigurować [ręcznie](#manually-configure-rule-severity) w pliku EditorConfig lub [automatycznie](#automatically-configure-rule-severity) za pomocą żarówki, która pojawia się obok naruszenia.

#### <a name="manually-configure-rule-severity"></a>Ręcznie skonfiguruj ważność reguły

1. Jeśli nie masz jeszcze pliku EditorConfig dla projektu, [Dodaj go](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Dodaj wpis dla każdej reguły, która ma zostać skonfigurowana w ramach odpowiedniego rozszerzenia pliku. Na przykład, aby ustawić ważność [CA1822](ca1822.md) na `error` dla C# plików, wpis wygląda następująco:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> W przypadku analizatorów stylu kodu IDE można także skonfigurować je w pliku EditorConfig przy użyciu innej składni, na przykład `dotnet_style_qualification_for_field = false:suggestion`. Jeśli jednak ustawisz ważność przy użyciu składni `dotnet_diagnostic`, ma pierwszeństwo. Aby uzyskać więcej informacji, zobacz [konwencje językowe dla EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="automatically-configure-rule-severity"></a>Automatycznie Konfiguruj ważność reguły

Program Visual Studio zapewnia wygodny sposób konfigurowania ważności reguły z menu żarówki [szybkich działań](../ide/quick-actions.md) .

1. Po wystąpieniu naruszenia, umieść wskaźnik myszy nad naruszeniem w edytorze i otwórz menu żarówki. Lub umieść kursor w wierszu i naciśnij klawisz **Ctrl** + **.** (kropka).

2. W menu żarówki wybierz pozycję **Konfiguruj lub Pomiń problemy** > **skonfiguruj \<rule identyfikator > ważność**.

   ![Skonfiguruj ważność reguły z poziomu menu żarówki w programie Visual Studio](media/configure-rule-severity.png)

3. W tym miejscu wybierz jedną z opcji ważności.

   ![Skonfiguruj ważność reguły jako sugestię](media/configure-rule-severity-suggestion.png)

   Program Visual Studio dodaje wpis do pliku EditorConfig, aby skonfigurować regułę do żądanego poziomu, jak pokazano w polu podglądu.

   > [!TIP]
   > Jeśli nie masz jeszcze pliku EditorConfig w projekcie, program Visual Studio utworzy go dla Ciebie.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Ustaw ważność reguły na podstawie Eksplorator rozwiązań

1. W **Eksplorator rozwiązań**rozwiń węzeł **odwołania**  > **analizatory** (lub **zależności**  > **analizatory** dla projektów .NET Core).

1. Rozwiń zestaw, który zawiera regułę, dla której chcesz ustawić ważność.

1. Kliknij prawym przyciskiem myszy regułę, a następnie wybierz pozycję **Ustaw ważność zestawu reguł**. W menu rozwijanym wybierz jedną z opcji ważności.

   Ważność reguły jest zapisywana w pliku aktywnego zestawu reguł.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Ustaw ważność reguły w pliku zestawu reguł

![Plik zestawu reguł w Eksplorator rozwiązań](media/ruleset-in-solution-explorer.png)

1. Otwórz plik aktywnego zestawu reguł, klikając go dwukrotnie w **Eksplorator rozwiązań**, wybierając pozycję **Otwórz aktywny zestaw reguł** w menu rozwijanym prawym przyciskiem myszy węzła **odwołania**  > **analizatory** , lub wybierając pozycję **Otwórz** w kodzie.Strona właściwości analizy dla projektu.

   Jeśli po raz pierwszy edytujesz zestaw reguł, program Visual Studio tworzy kopię domyślnego pliku zestawu reguł, nazywa ją *\<projectname >. regułą*i dodaje ją do projektu. Ten niestandardowy zestaw reguł jest również aktywnym zestawem reguł dla projektu.

   > [!NOTE]
   > Projekty .NET Core i .NET Standard nie obsługują poleceń menu dla zestawów reguł w **Eksplorator rozwiązań**, na przykład **Otwórz aktywny zestaw reguł**. Aby określić regułę niedomyślną dla projektu .NET Core lub .NET Standard, ręcznie [Dodaj właściwość **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) do pliku projektu. Nadal można skonfigurować reguły w ramach zestawu reguł w interfejsie użytkownika edytora zestawu reguł programu Visual Studio.

1. Przejdź do reguły, rozszerzając jej zawierający zestaw.

1. W kolumnie **Akcja** wybierz wartość, aby otworzyć listę rozwijaną, a następnie wybierz odpowiednią ważność z listy.

   ![Plik zestawu reguł otwarty w edytorze](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Pomiń naruszenia

Istnieje wiele sposobów pomijania naruszeń reguł:

::: moniker range=">=vs-2019"

- W **pliku EditorConfig**

  Ustaw ważność na `none`, na przykład `dotnet_diagnostic.CA1822.severity = none`.

- Z menu **Analizuj**

  Wybierz pozycję **analizuj**  > **Kompiluj i Pomiń aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "określania poziomu odniesienia".

::: moniker-end

::: moniker range="vs-2017"

- Z menu **Analizuj**

  Wybierz pozycję **analizuj**  > **Uruchom analizę kodu i Pomiń aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "określania poziomu odniesienia".

::: moniker-end

- Z **Eksplorator rozwiązań**

  Ustaw ważność reguły na **Brak**.

- Z **edytora zestawu reguł**

  Usuń zaznaczenie pola obok jego nazwy lub ustaw opcję **Akcja** na **Brak**.

- Z **edytora kodu**

  Umieść kursor w wierszu kodu z naruszeniem, a następnie naciśnij klawisz **Ctrl** +**kropki (.)** , aby otworzyć menu **szybkie akcje** . Wybierz opcję **Pomijaj CAXXXX**  > **w pliku źródłowym/in**.

  ![Pomiń diagnostykę z menu szybkich akcji](media/suppress-diagnostic-from-editor.png)

- Z **Lista błędów**

  Wybierz reguły, które chcesz pominąć, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **pomiń**  > **w polu Źródło/w pliku**pominięć.

  - W przypadku pominięcia **w źródle**zostanie otwarte okno dialogowe **Podgląd zmian** z podglądem C# [#pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) lub Visual Basic #Disable dyrektywie [ostrzegawczej](/dotnet/visual-basic/language-reference/directives/directives) , która jest dodawana do kodu źródłowego.

    ![Wersja zapoznawcza dodawania #pragma ostrzeżenie w pliku kodu](media/pragma-warning-preview.png)

  - W przypadku wybrania **w pliku pomijania**zostanie otwarte okno dialogowe **Podgląd zmian** i zostanie wyświetlony podgląd atrybutu <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>, który zostanie dodany do globalnego pliku pominięć.

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
> Jeśli masz możliwość uruchomienia starszej analizy z poziomu wiersza polecenia, za pomocą *plik FxCopCmd. exe* lub za pośrednictwem MSBuild z flagą **RunCodeAnalysis** , Oto jak to zrobić za pomocą analizatorów kodu.

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
