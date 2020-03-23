---
title: Testowanie pokrycia kodu
ms.date: 07/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dd6dde83720c6e6f37bd6827bb5d97526202aa7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585603"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny obejmować lub pokrywać znaczną część kodu.

Analizy pokrycia kodu mogą dotyczyć zarówno kodów zarządzanych (CLI), jak i niezarządzanych (natywnych).

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

::: moniker range="vs-2017"

![Wyniki pokrycia kodu z kolorowanki](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Wymagania

Funkcja pokrycia kodu jest dostępna tylko w programie Visual Studio Enterprise edition.

## <a name="analyze-code-coverage"></a>Analizowanie pokrycia kodu

::: moniker range="vs-2017"

1. W menu **Test** wybierz polecenie **Analizuj pokrycie kodu**.

::: moniker-end

::: moniker range=">=vs-2019"

1. W menu **Test** wybierz polecenie **Analizuj pokrycie kodu dla wszystkich testów**.

   ![Analizowanie menu pokrycia kodu w VS 2019](../test/media/vs-2019/analyze-code-coverage.png)

   Pokrycie kodu można również uruchomić w oknie narzędzia Eksploratora testów.

::: moniker-end

2. Po uruchomieniu testów, aby zobaczyć, które linie ![zostały uruchomione,](../test/media/codecoverage-showcoloringicon.png) wybierz opcję Pokaż pokrycie kodu Kolorowanie **ikona Pokaż pokrycie kodu kolorowanie** w **oknie Wyniki pokrycia kodu.** Domyślnie kod, który jest objęty testami jest wyróżniony na jasnoniebieski.

   > [!TIP]
   > Aby zmienić kolory lub użyć pogrubienia, wybierz pozycję**Opcje** >  **narzędzi** > **Czcionki środowiska** > **i Ustawienia** > pokaż kolory**dla: Edytor tekstu**. W obszarze **Elementy wyświetlania**dostosuj ustawienia elementów "Pokrycie", na przykład **Obszar pokrycia nie dotknął**.
   >
   > ![Czcionki i kolory pokrycia kodu](media/vs-2019/coverage-fonts-and-colors.png)

3. Jeśli wyniki wykażą niewielkie pokrycie, zbadaj części kodu, które nie są wykonywane, i napisz więcej testów, aby je pokryć. Zespoły deweloperów zazwyczaj dążą do około 80% pokrycia kodu. W niektórych sytuacjach dopuszczalne jest niższe zapotrzebowanie. Niższe zapotrzebowanie jest dopuszczalne np. tam, gdzie dany kod jest generowany na podstawie standardowego szablonu.

> [!TIP]
> - Wyłącz optymalizację kompilatora
> - Jeśli pracujesz z kodem niezarządzanym (natywnym), użyj kompilacji debugowania
> - Generowanie plików pdb (symbol) dla każdego złożenia

Jeśli nie uzyskasz oczekiwanych wyników, zobacz [Rozwiązywanie problemów z pokryciem kodu](../test/troubleshooting-code-coverage.md).

Nie zapomnij ponownie uruchomić pokrycia kodu po zaktualizowaniu kodu. Wyniki pokrycia i kolorowanie kodu nie są automatycznie aktualizowane po zmodyfikowaniu kodu ani po uruchomieniu testów.

## <a name="report-in-blocks-or-lines"></a>Raport w blokach lub wierszach

Pokrycie kodu jest liczone w *blokach*. Blok jest fragmentem kodu z dokładnie jednym punktem wejścia i wyjścia.  Jeśli przepływ sterowania programu przechodzi przez blok podczas przebiegu testowego, ten blok jest liczony jako objęty. To, ile razy użyto danego bloku, nie ma wpływu na wynik.

Wyniki można również wyświetlać w wierszach, wybierając pozycję **Dodaj/Usuń kolumny** w nagłówku tabeli. Niektórzy użytkownicy preferują liczbę wierszy, ponieważ wartości procentowe ściślej odpowiadają rozmiarowi fragmentów, które widać w kodzie źródłowym. Duży blok obliczeń jest traktowany jako pojedynczy, nawet jeśli zajmuje wiele wierszy.

> [!TIP]
> Wiersz kodu może zawierać więcej niż jeden blok kodu. Jeśli tak jest, a przebieg testu wykonuje wszystkie bloki kodu w wierszu, jest liczony jako jeden wiersz. Jeśli niektóre, ale nie wszystkie bloki kodu w wierszu są wykonywane, jest liczony jako wiersz częściowy.

## <a name="manage-code-coverage-results"></a>Zarządzanie wynikami pokrycia kodu

Okno **Wyniki pokrycia kodu** zwykle pokazuje wynik ostatniego uruchomienia. Wyniki będą się różnić, jeśli zmienisz ich dane lub za każdym razem uruchomisz tylko niektóre z testów.

Okno pokrycia kodu może służyć również do wyświetlania poprzednich wyników lub wyników uzyskanych na innych komputerach.

Można scalać wyniki kilku uruchomień, na przykład tych, które używają różnych danych testowych.

- **Aby wyświetlić poprzedni zestaw wyników,** wybierz go z menu rozwijanego. W menu pojawia się tymczasowa lista, która jest czyszczona po otwarciu nowego rozwiązania.

- **Aby wyświetlić wyniki z poprzedniej sesji,** wybierz pozycję **Importuj wyniki pokrycia kodu**, przejdź do folderu **TestResults** w rozwiązaniu i zaimportuj plik *.coverage.*

   Kolorowanie zapotrzebowania może być niepoprawne, jeśli kod źródłowy uległ zmianie od czasu wygenerowania pliku *.coverage.*

- **Aby wyniki były czytelne jako tekst,** wybierz pozycję **Wyniki pokrycia kodu eksportu**. Generuje czytelny plik *.coveragexml,* który można przetwarzać za pomocą innych narzędzi lub łatwo wysyłać pocztą.

- **Aby wysłać wyniki do innej osoby,** wyślij plik *.coverage* lub wyeksportowany plik *.coveragexml.* Następnie można zaimportować plik. Jeśli mają one tę samą wersję kodu źródłowego, mogą odczytać kolorowanie pokrycia.

## <a name="merge-results-from-different-runs"></a>Scalanie wyników z różnych przebiegów

W niektórych sytuacjach, w zależności od danych testowych, używane będą różne bloki w kodzie. W związku z tym można wykorzystać wyniki z różnych przebiegów testów.

Można na przykład założyć, że po uruchomieniu testu z wpisem „2” okaże się, że pokryto 50% określonej funkcji. Po uruchomieniu testu po raz drugi z wejściem "-2", widać w widoku kolorowania pokrycia, że pozostałe 50% funkcji jest objęte. Teraz należy scalić wyniki z dwóch przebiegów testów, a raport i widok kolorowania pokrycia pokaże 100% pokrycia funkcji.

Użyj ![przycisku Ikona do](../test/media/codecoverage-mergeicon.png) scalania w oknie Pokrycie kodu **Scal wyniki pokrycia kodu,** aby to zrobić. Można wybrać dowolną kombinację ostatnich uruchomień lub zaimportowanych wyników. Aby połączyć wyeksportowane wyniki, należy je najpierw zaimportować.

Użyj **wyników pokrycia kodu eksportu,** aby zapisać wyniki operacji scalania.

### <a name="limitations-in-merging"></a>Ograniczenia w scalaniu

- W przypadku scalania danych pokrycia z różnych wersji kodu wyniki są wyświetlane oddzielnie i nie są połączone. Aby uzyskać w pełni połączone wyniki, należy zastosować tę samą kompilację kodu, zmieniając tylko dane testowe.

- W przypadku scalania pliku wyników, które zostały wyeksportowane, a następnie zaimportowane, wyniki można przeglądać tylko według wierszy, a nie bloków. Użyj polecenia **Dodaj/Usuń kolumny,** aby wyświetlić dane linii.

- W przypadku scalania wyników z testów programu ASP.NET wyniki dla oddzielnych testów są wyświetlane, ale nie są połączone. Dotyczy to tylko samych artefaktów ASP.NET: wyniki dla innych zestawów zostaną połączone.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Wykluczanie elementów z wyników pokrycia kodu

Można chcieć wykluczyć określone elementy w kodzie z oceny pokrycia, jeśli np. kod jest generowany na podstawie szablonu tekstu. Dodaj <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> atrybut do dowolnego z następujących elementów kodu: class, struct, method, property, property setter or getter, event.

> [!TIP]
> Wyłączenie klasy nie wyklucza jej klas pochodnych.

Przykład:

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Wykluczanie elementów w natywnym kodzie C++

Aby wykluczyć niezarządzane (natywne) elementy kodu C++:

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Użyj następujących makr:

`ExcludeFromCodeCoverage(`*Nazwa nazwy wykluczeń* `, L"` *FunctionName*`");`

`ExcludeSourceFromCodeCoverage(`Ścieżka *źródła* *wykluczeń* `, L"``");`

- *ExclusionName* to dowolna unikatowa nazwa.

- *FunctionName* jest w pełni kwalifikowaną nazwą funkcji. Może ona zawierać symbole wieloznaczne. Na przykład, aby wykluczyć wszystkie funkcje klasy,`MyNamespace::MyClass::*`

- *SourceFilePath* jest lokalną ścieżką UNC pliku .cpp. Może ona zawierać symbole wieloznaczne. Poniższy przykład wyklucza wszystkie pliki w określonym katalogu:`\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Miejsce wywołuje wyłączenie makr w globalnej przestrzeni nazw, nie w dowolnym obszarze nazw lub klasie.

- Można umieścić wyłączenia w pliku kodu testu jednostkowego lub w pliku kodu aplikacji.

- Wykluczenia muszą być kompilowane jako kod niezarządzany (natywny), ustawiając `#pragma managed(off)`opcję kompilatora lub używając .

> [!NOTE]
> Aby wykluczyć funkcje w kodzie C++/CLI, zastosuj atrybut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` do funkcji. To jest tak samo jak w języku C#.

### <a name="include-or-exclude-additional-elements"></a>Uwzględnianie lub wykluczanie dodatkowych elementów

Analiza pokrycia kodu jest wykonywana tylko w zestawach, które są ładowane i dla których plik *.pdb* jest dostępny w tym samym katalogu co plik *.dll* lub *.exe.* W związku z tym w pewnych okolicznościach można rozszerzyć zestaw zestawów, który jest dołączony przez uzyskanie kopii odpowiednich plików *pdb.*

Można sprawować większą kontrolę nad tym, które zestawy i elementy są wybierane do analizy pokrycia kodu, pisząc plik *.runsettings.* Można np. wykluczyć zestawy określonego typu bez konieczności dodawania atrybutów do ich klas. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analizowanie pokrycia kodu w potokach platformy Azure

Po zaewidencjonowaniu kodu testy są uruchamiane na serwerze kompilacji wraz z testami innych członków zespołu. Jest to przydatne do analizowania pokrycia kodu w usłudze Azure Pipelines, aby uzyskać najbardziej aktualny i kompleksowy obraz pokrycia w całym projekcie. Obejmuje również zautomatyzowane testy systemu i inne zakodowane testy, które zwykle nie są uruchamiane na komputerach deweloperskich. Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych z kompilacjami](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analizowanie pokrycia kodu z wiersza polecenia

Aby uruchomić testy z wiersza polecenia, użyj *vstest.console.exe*. Pokrycie kodu jest opcją narzędzia *vstest.console.exe.*

1. Uruchom wiersz polecenia dewelopera dla programu Visual Studio:

   ::: moniker range="vs-2017"

   W menu **Start** systemu Windows wybierz polecenie Wiersz polecenia dewelopera **programu Visual Studio 2017** > **dla programu VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   W menu **Start** systemu Windows wybierz polecenie Wiersz polecenia dewelopera **programu Visual Studio 2019** > **dla programu VS 2019**.

   ::: moniker-end

2. W wierszu polecenia wpisz następujące polecenie:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Aby uzyskać więcej informacji, zobacz [opcje wiersza polecenia VSTest.Console.exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli nie widzisz wyników pokrycia kodu, artykuł [Rozwiązywanie problemów z pokryciem kodu](../test/troubleshooting-code-coverage.md) może Ci pomóc.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Rozwiązywanie problemów z pokryciem kodu](../test/troubleshooting-code-coverage.md)
- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
