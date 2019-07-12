---
title: Ważność reguły analizator i pomijania
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
ms.openlocfilehash: d4b5ad6ca824e6c7091c6c508b51c2d51501b2fd
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821528"
---
# <a name="use-roslyn-analyzers"></a>Używanie analizatorów Roslyn

Reguły analizatora platformie kompilatora .NET ("Roslyn"), lub *diagnostyki*, analizowanie kodu C# lub Visual Basic podczas wpisywania. Każdy Diagnostyka ma domyślne ważności i pomijania stanu, który może zostać zastąpiona w projekcie. W tym artykule opisano ustawienia reguły ważności, korzystanie z zestawów reguł i pomijanie naruszenia.

## <a name="analyzers-in-solution-explorer"></a>Analizatory w Eksploratorze rozwiązań

Można wykonać wiele dostosowania Diagnostyka analyzer z **Eksploratora rozwiązań**. Jeśli użytkownik [instalowanie analizatorów](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet **analizatory** pojawia się pod węzłem **odwołania** lub **zależności** węzła w  **Eksplorator rozwiązań**. Po rozwinięciu **analizatory**i następnie rozwiń jedno ze zestawy analizatora, zobaczysz wszystkie diagnostyki w zestawie.

![Węzeł analizatory w Eksploratorze rozwiązań](media/analyzers-expanded-in-solution-explorer.png)

Możesz wyświetlić właściwości danych diagnostycznych, w tym jego opis i domyślna ważność w **właściwości** okna. Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy reguły, a następnie wybierz **właściwości**, lub wybierz regułę, a następnie naciśnij klawisz **Alt**+**Enter**.

![Właściwości diagnostyczne w oknie właściwości](media/analyzer-diagnostic-properties.png)

Aby wyświetlić dokumentację online dla diagnostyki, kliknij prawym przyciskiem myszy na diagnostyczne, a następnie wybierz **Wyświetl Pomoc**.

Ikony obok każdego Diagnostyka w **Eksploratora rozwiązań** odnoszą się do tych ikon, zostanie wyświetlony w regule ustawić po otwarciu w edytorze:

- "i" w okręgu wskazuje [ważność](#rule-severity) z **informacji**
- "!" w trójkąt wskazuje [ważność](#rule-severity) z **ostrzeżenie**
- "x" w okręgu wskazuje [ważność](#rule-severity) z **błąd**
- Wskazuje "i" w okręgu na tle jasnego [ważność](#rule-severity) z **ukryty**
- strzałkę skierowaną w dół w okręgu wskazuje, czy pomijane jest diagnostyczne

![Ikony diagnostyki w oknie Eksploratora rozwiązań](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Zestawy reguł

A [zestaw reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) jest plikiem XML, który zapisuje stan ważność i pomijania poszczególnych diagnostyki.

> [!NOTE]
> Zestawy reguł mogą zawierać reguły z analizy kodu statycznego (plik binarny) i analizatorów Roslyn.

Aby edytować aktywny zestaw reguł w z edytora zestawu reguł, kliknij prawym przyciskiem myszy **odwołania** > **analizatory** w węźle **Eksploratora rozwiązań** i wybierz **Otwórz aktywny zestaw reguł**. Jeśli po raz pierwszy, edycji zestawu reguł, Visual Studio tworzy kopię domyślną regułę pliku zestawu, nadaje mu  *\<nazwa_projektu > .ruleset*i dodaje go do projektu. Ten niestandardowy zestaw reguł, również stanie się aktywny zestaw reguł dla projektu.

Aby zmienić aktywny zestaw reguł dla projektu, przejdź do **analizy kodu** karcie we właściwościach projektu. Wybierz regułę, ustaw na liście w obszarze **Uruchom ten zestaw reguł**. Aby otworzyć zestaw reguł, wybierz **Otwórz**.

> [!NOTE]
> Dla zestawów reguł projektach .NET core i .NET Standard nie obsługują polecenia menu **Eksploratora rozwiązań**, na przykład **otwórz aktywny zestaw reguł**. Aby określić inny niż domyślny zestaw reguł dla projektu .NET Core lub .NET Standard, ręcznie [Dodaj **CodeAnalysisRuleSet** właściwość](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) do pliku projektu. Nadal można skonfigurować reguły w ramach zestawu reguł w programie Visual Studio czy interfejs użytkownika edytora zestawu reguł.

## <a name="rule-severity"></a>Ważność reguły

Można skonfigurować ważność reguły analizatora lub *diagnostyki*, jeśli użytkownik [instalowanie analizatorów](../code-quality/install-roslyn-analyzers.md) jako pakiet NuGet. W poniższej tabeli przedstawiono opcje ważność diagnostyki:

|Ważność|Zachowanie w czasie kompilacji|Zachowanie edytora|
|-|-|-|
|Błąd|Naruszeń są traktowane jako *błędy* w **lista błędów** w wiersza polecenia dane wyjściowe kompilacji i powodować niepowodzenia kompilacji.|Naruszeń kodu jest podkreślony z czerwonym falista i oznaczone czerwoną otoczkę małych na pasku przewijania.|
|Ostrzeżenie|Naruszeń są traktowane jako *ostrzeżenia* w **lista błędów** w wiersza polecenia dane wyjściowe kompilacji, ale nie powoduje niepowodzenia kompilacji.|Naruszeń kodu jest podkreślony z zielonym falista i oznaczone przez małe zielone pole na pasku przewijania.|
|Informacje o|Naruszeń są traktowane jako *wiadomości* w **lista błędów**i w ogóle nie będzie w danych wyjściowych kompilacji z wiersza polecenia.|Naruszeń kodu jest podkreślony szaro falista i oznaczone przez małe pole szarym pasku przewijania.|
|Hidden|Non widoczny dla użytkownika.|Non widoczny dla użytkownika. Diagnostyka jest zgłaszany do aparatu diagnostyki IDE, jednak.|
|Brak|Całkowicie pominąć.|Całkowicie pominąć.|

Ponadto użytkownik może "Resetuj" ważność reguły, ustawiając go na **domyślne**. Każdy Diagnostyka ma domyślna ważność, którą można wyświetlić w **właściwości** okna.

Poniższy zrzut ekranu przedstawia trzy różne naruszeń diagnostycznych w edytorze kodu z trzema różnymi poziomami ważności. Zwróć uwagę, kolor falista, jak małe pole po prawej stronie na pasku przewijania.

![Błąd, ostrzeżenie i informacje o naruszenie w edytorze kodu](media/diagnostics-severity-colors.png)

Poniższy zrzut ekranu przedstawia tych samych trzech naruszeń, w jakiej występują w **lista błędów**:

![Naruszenie błędu, ostrzeżenia i informacje o liście błędów](media/diagnostics-severities-in-error-list.png)

Możesz zmienić ważność reguły z **Eksploratora rozwiązań**, lub w ramach  *\<nazwa_projektu > .ruleset* pliku, który jest dodawany do rozwiązania, po zmianie ważność reguły w  **Eksplorator rozwiązań**.

![Pliku zestawu reguł w oknie Eksploratora rozwiązań](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Ustaw ważność reguły za pomocą Eksploratora rozwiązań

1. W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** > **analizatory** (**zależności**  >  **Analizatory** dla projektów .NET Core).

1. Rozwiń węzeł zestawu, który zawiera regułę, którą chcesz ustawić ważność.

1. Kliknij prawym przyciskiem myszy, reguły i wybierz pozycję **Ustaw ważność zestawu reguł**. W menu wysuwanego wybierz jedną z opcji ważności.

   Ważność reguły są zapisywane w pliku zestawu reguł active.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Ustaw ważność reguły w pliku zestawu reguł

1. Otwórz [zestaw reguł](analyzer-rule-sets.md) pliku przez dwukrotne kliknięcie go w **Eksploratora rozwiązań**, wybierając opcję **otwórz aktywny zestaw reguł** w menu kliknij prawym przyciskiem myszy **analizatory** węzła, lub wybierając **Otwórz** na **analizy kodu** strony właściwości dla projektu.

1. Przejdź do reguły, rozwijając jego zawierające zestaw.

1. W **akcji** kolumn, wybierz wartość do otwierania listy rozwijanej i wybierz żądany poziom zagrożenia z listy.

   ![Otwórz w edytorze pliku zestawu reguł](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Pomiń naruszenia

Istnieje wiele sposobów, aby pominąć naruszeń reguł:

- Z **analizy** menu

  Wybierz **analizy** > **Uruchom analizę kodu i Pomiń aktywne problemy** na pasku menu, aby pominąć wszystkie bieżące naruszenia. Jest to czasami nazywane "określania poziomu odniesienia".

- Z **Eksploratora rozwiązań**

  Aby pominąć naruszenie w **Eksploratora rozwiązań**, Ustaw ważność reguły **Brak**.

- Z **edytorze zestawu reguł**

  Aby pominąć to naruszenie z edytora zestawu reguł, usuń zaznaczenie pola obok jego nazwy lub ustaw **akcji** do **Brak**.

- Z **Edytor kodu**

  Aby pominąć naruszenie zasad w edytorze kodu, umieść kursor w wierszu kodu za pomocą naruszenie, a następnie naciśnij klawisz **Ctrl**+ **.** Aby otworzyć **szybkie akcje** menu. Wybierz **Pomiń CAXXXX** > **w źródle/w pliku pominięć**.

  ![Pomiń diagnostyki w menu Szybkie akcje](media/suppress-diagnostic-from-editor.png)

- Z **lista błędów**

  Można pominąć Diagnostyka jednej lub wielu z **lista błędów** , wybierając do pominięcia, a następnie kliknij prawym przyciskiem myszy i wybierając **Pomiń** > **Source/In w Pliku pominięć**.

  - Jeśli zostanie pominięty **w źródłowej**, **podgląd zmian** okno dialogowe otwiera i pokazuje jego podgląd C# [ostrzeżenie #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) lub Visual Basic [#Disable Ostrzeżenie](/dotnet/visual-basic/language-reference/directives/directives) dyrektywę, który zostanie dodany do kodu źródłowego.

    ![Dodawanie ostrzeżenie #pragma w pliku kodu w wersji zapoznawczej](media/pragma-warning-preview.png)

  - Jeśli wybierzesz **w pliku pominięć**, **podgląd zmian** okno dialogowe otwiera i pokazuje jego podgląd <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybut, który jest dodawany do pliku pominięć globalnych.

    ![Dodawanie atrybutu SuppressMessage do pliku pominięć w wersji zapoznawczej](media/preview-changes-in-suppression-file.png)

  W **podgląd zmian** okno dialogowe, wybierz opcję **Zastosuj**.

  > [!NOTE]
  > Jeśli nie widzisz **Pomiń** opcji menu w **Eksploratora rozwiązań**, naruszenia prawdopodobnie pochodzi z kompilacji i analizy nie na żywo. **Lista błędów** Wyświetla diagnostyki lub reguła naruszeń z obu analizy kodu na żywo i kompilacji. Ponieważ diagnostyki kompilacji mogą być nieaktualne, na przykład, jeśli zakończeniu edycji kodu, aby naprawić naruszenie, ale nie został ponownie skompilowany, nie można ukryć te Diagnostyka z **lista błędów**. Diagnostyka z analizy na żywo lub funkcja IntelliSense, są zawsze aktualne z bieżącego źródła i można pominąć z **lista błędów**. Aby wykluczyć *kompilacji* diagnostyki z zaznaczenia, Przełącz **lista błędów** Filtr źródła z **kompilacja + IntelliSense** do **Intellisense tylko**. Następnie wybierz diagnostyki, które chcesz pominąć i postępować zgodnie z opisem w poprzedniej sekcji.
  >
  > ![Filtr źródła listy błędów w programie Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Użycie wiersza polecenia

Podczas tworzenia projektu w wierszu polecenia, naruszenia reguły są wyświetlane w danych wyjściowych kompilacji, jeśli są spełnione następujące warunki:

- Analizatory są instalowane jako pakiet Nuget, a nie jako rozszerzenia VSIX.

- Co najmniej jedną regułę naruszenia kodu projektu.

- [Ważność](#rule-severity) naruszono reguły jest ustawiona jako **ostrzeżenie**, w którym to przypadku naruszeń nie powodują kompilacji, która ma zakończyć się niepowodzeniem, lub **błąd**, w którym to przypadku naruszeń spowodować błąd kompilacji.

Nie wpływa na poziom szczegółowości danych wyjściowych kompilacji, czy naruszenia reguły są wyświetlane. Nawet w przypadku **cichy** poziom szczegółowości, naruszenia reguły są wyświetlane w danych wyjściowych kompilacji.

> [!TIP]
> Użytkownicy przyzwyczajeni do uruchomionego statycznej analizy kodu w wierszu polecenia, za pomocą *FxCopCmd.exe* lub przez program msbuild z **RunCodeAnalysis** Flaga, Oto jak to zrobić za pomocą analizatorów Roslyn.

Aby wyświetlić naruszeń analizator, w wierszu polecenia podczas kompilowania projektu przy użyciu programu msbuild, uruchom polecenie następująco:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Na poniższej ilustracji przedstawiono dane wyjściowe kompilacji wiersza polecenia, od tworzenia projektu, który zawiera naruszenie reguły analizatora:

![Naruszenie reguły danych wyjściowych programu MSBuild](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projekty zależne

W projekcie platformy .NET Core Jeśli dodasz odwołanie do projektu, który ma analizatorów NuGet te analizatory są automatycznie dodawane do projektu zależnego zbyt. Aby wyłączyć to zachowanie, na przykład jeśli projekt zależny jest projekt testu jednostkowego oznaczyć pakietu NuGet jako prywatne w ramach *.csproj* lub *.vbproj* pliku przywoływanego projektu, ustawiając **PrivateAssets** atrybutu:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów Roslyn w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Prześlij usterkę analizatora Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Korzystanie z zestawów reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Pomijanie ostrzeżeń analizy kodu](../code-quality/in-source-suppression-overview.md)
