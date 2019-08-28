---
title: Ważność i pomijanie reguły analizatora
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5c5af5c98be92e52c356e0f20eaf437f66878690
ms.sourcegitcommit: 8a699df154464387f327691dce507d7c3d0e2aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060445"
---
# <a name="use-code-analyzers"></a>Korzystanie z analizatorów kodu

.NET Compiler Platform ("Roslyn") analizatory kodu analizują C# kod lub Visual Basic w trakcie pisania. Każda *Diagnostyka* lub reguła ma domyślną ważność i stan pomijania, który można zastąpić dla projektu. W tym artykule omówiono Ustawianie ważności reguły, korzystanie z zestawów reguł i pomijanie naruszeń.

## <a name="analyzers-in-solution-explorer"></a>Analizatory w Eksplorator rozwiązań

Można wykonać wiele czynności dostosowywania diagnostyki analizatora **Eksplorator rozwiązań**. Jeśli [instalujesz analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet, węzeł **analizatory** zostanie wyświetlony w węźle **odwołania** lub **zależności** w **Eksplorator rozwiązań**. W przypadku rozwinięcia analizatorów, a następnie rozszerzenia jednego z zestawów, zostanie wyświetlona cała Diagnostyka w zestawie.

![Węzeł analizatorów w Eksplorator rozwiązań](media/analyzers-expanded-in-solution-explorer.png)

Właściwości diagnostyki, w tym jej opis i domyślną ważność, można wyświetlić w oknie **Właściwości** . Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy regułę i wybierz pozycję **Właściwości**lub wybierz regułę, a następnie naciśnij klawisz **Alt**+**Enter**.

![Właściwości diagnostyczne w okno Właściwości](media/analyzer-diagnostic-properties.png)

Aby wyświetlić dokumentację online dla diagnostyki, kliknij prawym przyciskiem myszy diagnostykę i wybierz polecenie **Wyświetl pomoc**.

Ikony obok każdej diagnostyki w **Eksplorator rozwiązań** odpowiadają ikonom widocznym w zestawie reguł po otwarciu go w edytorze:

- "i" w okręgu wskazuje [ważność](#rule-severity) **informacji**
- "!" w trójkącie wskazuje [ważność](#rule-severity) **ostrzeżenia**
- Symbol "x" w okręgu wskazuje [ważność](#rule-severity) **błędu**
- "i" w okręgu w jasnym kolorze tła wskazuje [ważność](#rule-severity) **ukrycia**
- strzałka skierowana w dół w okręgu wskazuje, że Diagnostyka jest pomijana

![Ikony diagnostyki w Eksplorator rozwiązań](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Zestawy reguł

[Zestaw reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) to plik XML, który przechowuje ważność i stan pomijania dla poszczególnych diagnostyki.

> [!NOTE]
> Zestawy reguł mogą zawierać reguły zarówno z starszej analizy, jak i analizatorów kodu.

Aby edytować aktywny zestaw reguł w edytorze zestawu reguł, kliknij prawym przyciskiem myszy węzeł > **analizatory** **odwołań**w **Eksplorator rozwiązań** i wybierz **Otwórz aktywny zestaw reguł**. Jeśli po raz pierwszy edytujesz zestaw reguł, program Visual Studio tworzy kopię domyślnego pliku zestawu reguł, nazywa ją  *\<ProjectName >. zestaw*reguł i dodaje ją do projektu. Ten niestandardowy zestaw reguł jest również aktywnym zestawem reguł dla projektu.

Aby zmienić aktywny zestaw reguł dla projektu, przejdź do karty **Analiza kodu** właściwości projektu. Wybierz zestaw reguł z listy w obszarze **Uruchom ten zestaw reguł**. Aby otworzyć zestaw reguł, wybierz pozycję **Otwórz**.

> [!NOTE]
> Projekty .NET Core i .NET Standard nie obsługują poleceń menu dla zestawów reguł w **Eksplorator rozwiązań**, na przykład **Otwórz aktywny zestaw reguł**. Aby określić regułę niedomyślną dla projektu .NET Core lub .NET Standard, ręcznie [Dodaj właściwość **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) do pliku projektu. Nadal można skonfigurować reguły w ramach zestawu reguł w interfejsie użytkownika edytora zestawu reguł programu Visual Studio.

## <a name="rule-severity"></a>Ważność reguły

Można skonfigurować ważność reguł analizatora lub *diagnostyki*, jeśli [są instalowane analizatory](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet. W poniższej tabeli przedstawiono opcje ważności diagnostyki:


::: moniker range="vs-2019"
|Ważność|Zachowanie w czasie kompilacji|Zachowanie edytora|
|-|-|-|
|Błąd|Naruszenia są wyświetlane jako *Błędy* w **Lista błędów** i w danych wyjściowych kompilacji w wierszu polecenia i powodują niepowodzenie kompilacji.|Kod powodujący problemy jest podkreślony czerwoną falistej i oznaczony przez małe czerwone pole na pasku przewijania.|
|Ostrzeżenie|Naruszenia są wyświetlane jako *ostrzeżenia* w **Lista błędów** i w danych wyjściowych kompilacji wiersza polecenia, ale nie powodują awarii kompilacji.|Kod powodujący problemy jest podkreślony zieloną falistej i jest oznaczony małym zielonym polem na pasku przewijania.|
|Sugestia|Naruszenia są wyświetlane jako *komunikaty* w **Lista błędów**, a nie w danych wyjściowych kompilacji wiersza polecenia.|Kod powodujący problemy jest podkreślony szarym falistej i oznaczony przez małe szare pole na pasku przewijania.|
|Automatycznie|Niewidoczny dla użytkownika.|Niewidoczny dla użytkownika. Diagnostyka jest jednak raportowana w aparacie diagnostyki IDE.|
|Brak|Całkowicie pomijane.|Całkowicie pomijane.|
::: moniker-end

::: moniker range="< vs-2019"
|Ważność|Zachowanie w czasie kompilacji|Zachowanie edytora|
|-|-|-|
|Błąd|Naruszenia są wyświetlane jako *Błędy* w **Lista błędów** i w danych wyjściowych kompilacji w wierszu polecenia i powodują niepowodzenie kompilacji.|Kod powodujący problemy jest podkreślony czerwoną falistej i oznaczony przez małe czerwone pole na pasku przewijania.|
|Ostrzeżenie|Naruszenia są wyświetlane jako *ostrzeżenia* w **Lista błędów** i w danych wyjściowych kompilacji wiersza polecenia, ale nie powodują awarii kompilacji.|Kod powodujący problemy jest podkreślony zieloną falistej i jest oznaczony małym zielonym polem na pasku przewijania.|
|Informacje o|Naruszenia są wyświetlane jako *komunikaty* w **Lista błędów**, a nie w danych wyjściowych kompilacji wiersza polecenia.|Kod powodujący problemy jest podkreślony szarym falistej i oznaczony przez małe szare pole na pasku przewijania.|
|Hidden|Niewidoczny dla użytkownika.|Niewidoczny dla użytkownika. Diagnostyka jest jednak raportowana w aparacie diagnostyki IDE.|
|Brak|Całkowicie pomijane.|Całkowicie pomijane.|
::: moniker-end

Ponadto można zresetować ważność reguły przez ustawienie jej jako **domyślnej**. Każda Diagnostyka ma domyślną ważność, która może być widoczna w oknie **Właściwości** .

Poniższy zrzut ekranu przedstawia trzy różne naruszenia diagnostyki w edytorze kodu z trzema różnymi serwerami. Zwróć uwagę na kolor falistej, a także małe pole na pasku przewijania po prawej stronie.

![Błąd, ostrzeżenie i naruszenie informacji w edytorze kodu](media/diagnostics-severity-colors.png)

Poniższy zrzut ekranu przedstawia te same trzy naruszenia, które są wyświetlane w **Lista błędów**:

![Błąd, ostrzeżenie i naruszenie informacji w Lista błędów](media/diagnostics-severities-in-error-list.png)

Można zmienić ważność reguły z **Eksplorator rozwiązań**lub w  *\<pliku ProjectName >. zestawu reguł* , który jest dodawany do rozwiązania po zmianie ważności reguły w **Eksplorator rozwiązań**.

![Plik zestawu reguł w Eksplorator rozwiązań](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Ustaw ważność reguły na podstawie Eksplorator rozwiązań

1. W **Eksplorator rozwiązań**rozwiń węzeł > **analizatory** odwołań (**analizatory** **zależności** > dla projektów .NET Core).

1. Rozwiń zestaw, który zawiera regułę, dla której chcesz ustawić ważność.

1. Kliknij prawym przyciskiem myszy regułę, a następnie wybierz pozycję **Ustaw ważność zestawu reguł**. W menu rozwijanym wybierz jedną z opcji ważności.

   Ważność reguły jest zapisywana w pliku aktywnego zestawu reguł.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Ustaw ważność reguły w pliku zestawu reguł

1. Otwórz plik [zestawu reguł](analyzer-rule-sets.md) , klikając go dwukrotnie w **Eksplorator rozwiązań**, wybierając pozycję **Otwórz aktywny zestaw reguł** w menu rozwijanym prawym przyciskiem myszy węzła **analizatory** lub wybierając pozycję **Otwórz** na stronie właściwości **analizy kodu** dla projekt.

1. Przejdź do reguły, rozszerzając jej zawierający zestaw.

1. W kolumnie **Akcja** wybierz wartość, aby otworzyć listę rozwijaną, a następnie wybierz odpowiednią ważność z listy.

   ![Plik zestawu reguł otwarty w edytorze](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Pomiń naruszenia

Istnieje wiele sposobów pomijania naruszeń reguł:

- Z menu **Analizuj**

  Wybierz pozycję **Analizuj** > **analizę kodu uruchamiania i Pomiń aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami określane jako "określania poziomu odniesienia".

- Z **Eksplorator rozwiązań**

  Aby pominąć naruszenie w **Eksplorator rozwiązań**, ustaw ważność reguły na **Brak**.

- Z **edytora zestawu reguł**

  Aby pominąć naruszenie z edytora zestawu reguł, usuń zaznaczenie pola obok jego nazwy lub ustaw wartość **Brak**.

- Z **edytora kodu**

  Aby pominąć naruszenie z edytora kodu, umieść kursor w wierszu kodu z naruszeniem, a następnie naciśnij klawisz **Ctrl**+ **.** , aby otworzyć menu **szybkie akcje** . Wybierz pozycję **Pomiń CAXXXX** > **w elemencie Source/in**.

  ![Pomiń diagnostykę z menu szybkich akcji](media/suppress-diagnostic-from-editor.png)

- Z **Lista błędów**

  Można pominąć jedną lub wiele diagnostyki z **Lista błędów** , wybierając te, które mają zostać pominięte, a następnie klikając prawym przyciskiem myszy i wybierając pozycję **Pomiń** > **w pliku źródłowym/w plikach pomijania**.

  - W przypadku pominięcia **w źródle**zostanie otwarte okno dialogowe **Podgląd zmian** z podglądem C# [#pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) lub Visual Basic #Disable dyrektywie [ostrzegawczej](/dotnet/visual-basic/language-reference/directives/directives) , która jest dodawana do kodu źródłowego.

    ![Wersja zapoznawcza dodawania #pragma ostrzeżenie w pliku kodu](media/pragma-warning-preview.png)

  - W przypadku wybrania **w pliku pomijania**zostanie otwarte okno dialogowe **Podgląd zmian** i zostanie wyświetlony <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Podgląd atrybutu, który jest dodawany do globalnego pliku pominięć.

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
