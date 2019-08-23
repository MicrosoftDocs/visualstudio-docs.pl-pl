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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6aa9cb62bc0ae956a85acd75d1a9615a2283133
ms.sourcegitcommit: f42b5318c5c93e2b5ecff44f408fab8bcdfb193d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69976777"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny obejmować lub pokrywać znaczną część kodu.

Analizy pokrycia kodu mogą dotyczyć zarówno kodów zarządzanych (CLI), jak i niezarządzanych (natywnych).

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

![Wyniki pokrycia kodu za pomocą kolorowania](../test/media/codecoverage1.png)

## <a name="requirements"></a>Wymagania

Funkcja pokrycia kodu jest dostępna tylko w wersji Visual Studio Enterprise.

## <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Analizowanie pokrycia kodu w ramach testów jednostkowych w Eksploratorze testów

::: moniker range="vs-2017"
1. W menu **test** wybierz polecenie **Analizuj pokrycie kodu**.
::: moniker-end
::: moniker range=">=vs-2019"
1. W **Eksploratorze testów**wybierz polecenie **Analizuj pokrycie kodu** z menu **uruchamiania** .
::: moniker-end

2. Aby zobaczyć, które wiersze zostały uruchomione, wybierz ![ikonę](../test/media/codecoverage-showcoloringicon.png) Pokaż kolorowanie pokrycia kodu. **Pokaż kolorowanie pokrycia kodu**.

   Aby zmienić kolory lub użyć pogrubienia, wybierz**Opcje** >  **Narzędzia** > **czcionki i kolory** >  ****środowiska** > Pokaż ustawienia dla: Edytor**tekstu. W obszarze **Wyświetl elementy**Dostosuj elementy pokrycia.

3. Jeśli wyniki wykażą niewielkie pokrycie, zbadaj części kodu, które nie są wykonywane, i napisz więcej testów, aby je pokryć. Zespoły deweloperów zazwyczaj dążą do około 80% pokrycia kodu. W niektórych sytuacjach dopuszczalne jest niższe zapotrzebowanie. Niższe zapotrzebowanie jest dopuszczalne np. tam, gdzie dany kod jest generowany na podstawie standardowego szablonu.

> [!TIP]
> - Upewnij się, że optymalizacja kompilatora jest wyłączona
> - Jeśli pracujesz z kodem niezarządzanym (natywnym), użyj kompilacji debugowania
> - Upewnij się, że generowane są pliki PDB (symbol) dla każdego zestawu

Jeśli nie otrzymujesz oczekiwanych wyników, zobacz [Rozwiązywanie problemów z pokryciem kodu](../test/troubleshooting-code-coverage.md). Nie zapomnij ponownie uruchomić pokrycia kodu po zaktualizowaniu kodu. Wyniki pokrycia i kolorowanie kodu nie są automatycznie aktualizowane po zmodyfikowaniu kodu ani po uruchomieniu testów.

## <a name="report-in-blocks-or-lines"></a>Raport w blokach lub wierszach

Pokrycie kodu jest zliczane w *blokach*. Blok jest fragmentem kodu z dokładnie jednym punktem wejścia i wyjścia.  Jeśli przepływ sterowania programu przechodzi przez blok podczas przebiegu testowego, ten blok jest traktowany jako pokryty. To, ile razy użyto danego bloku, nie ma wpływu na wynik.

Wyniki można także wyświetlić w obszarze wiersze, wybierając pozycję **Dodaj/Usuń kolumny** w nagłówku tabeli. Niektórzy użytkownicy preferują liczbę wierszy, ponieważ wartości procentowe ściślej odpowiadają rozmiarowi fragmentów, które widać w kodzie źródłowym. Duży blok obliczeń jest traktowany jako pojedynczy, nawet jeśli zajmuje wiele wierszy.

> [!TIP]
> Wiersz kodu może zawierać więcej niż jeden blok kodu. W takim przypadku, a przebieg testu sprawdza wszystkie bloki kodu w wierszu, jest liczony jako jeden wiersz. Jeśli niektóre bloki kodu w wierszu, ale nie są wykonywane, są zliczane jako linia częściowa.

## <a name="manage-code-coverage-results"></a>Zarządzanie wynikami pokrycia kodu

Okno **wyniki pokrycia kodu** zwykle pokazuje wynik ostatniego uruchomienia. Wyniki będą się różnić, jeśli zmienisz ich dane lub za każdym razem uruchomisz tylko niektóre z testów.

Okno pokrycia kodu może służyć również do wyświetlania poprzednich wyników lub wyników uzyskanych na innych komputerach.

Można scalać wyniki kilku uruchomień, na przykład tych, które używają różnych danych testowych.

- **Aby wyświetlić poprzedni zestaw wyników**, wybierz go z menu rozwijanego. W menu pojawia się tymczasowa lista, która jest czyszczona po otwarciu nowego rozwiązania.

- **Aby wyświetlić wyniki z poprzedniej sesji**, wybierz pozycję **Importuj wyniki pokrycia kodu**, przejdź do folderu **TestResults** w rozwiązaniu i zaimportuj plik *. coverage* .

   Kolorowanie pokrycia może być niepoprawne, jeśli kod źródłowy został zmieniony od czasu wygenerowania pliku *pokrycia* .

- **Aby wyniki były odczytywane jako tekst**, wybierz opcję **Eksportuj wyniki pokrycia kodu**. Spowoduje to wygenerowanie pliku *COVERAGEXML* , który można przetworzyć przy użyciu innych narzędzi lub łatwo wysyłać pocztą.

- **Aby wysłać wyniki do kogoś innego**, Wyślij plik *. coverage* lub wyeksportowany plik *. COVERAGEXML* . Następnie można zaimportować plik. Jeśli mają one tę samą wersję kodu źródłowego, mogą odczytać kolorowanie pokrycia.

## <a name="merge-results-from-different-runs"></a>Scalanie wyników z różnych uruchomień

W niektórych sytuacjach, w zależności od danych testowych, używane będą różne bloki w kodzie. W związku z tym można wykorzystać wyniki z różnych przebiegów testów.

Można na przykład założyć, że po uruchomieniu testu z wpisem „2” okaże się, że pokryto 50% określonej funkcji. Gdy uruchamiasz test po raz drugi z danymi wejściowymi "-2", zobaczysz w widoku kolorowanie pokrycia, że podano pozostałe 50% funkcji. Teraz należy scalić wyniki z dwóch przebiegów testów, a raport i widok kolorowania pokrycia pokaże 100% pokrycia funkcji.

Użyj ![ikony przycisku Scal w oknie](../test/media/codecoverage-mergeicon.png) pokrycie kodu **Scal wyniki pokrycia kodu** , aby to zrobić. Można wybrać dowolną kombinację ostatnich uruchomień lub zaimportowanych wyników. Aby połączyć wyeksportowane wyniki, należy je najpierw zaimportować.

Użyj **Eksportuj wyniki pokrycia kodu** , aby zapisać wyniki operacji scalania.

### <a name="limitations-in-merging"></a>Ograniczenia w scalaniu

- W przypadku scalania danych pokrycia z różnych wersji kodu wyniki są wyświetlane oddzielnie i nie są połączone. Aby uzyskać w pełni połączone wyniki, należy zastosować tę samą kompilację kodu, zmieniając tylko dane testowe.

- W przypadku scalania pliku wyników, które zostały wyeksportowane, a następnie zaimportowane, wyniki można przeglądać tylko według wierszy, a nie bloków. Użyj polecenia **Dodaj/Usuń kolumny** , aby wyświetlić dane wiersza.

- W przypadku scalania wyników z testów programu ASP.NET wyniki dla oddzielnych testów są wyświetlane, ale nie są połączone. Dotyczy to tylko samych artefaktów ASP.NET: wyniki dla innych zestawów zostaną połączone.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Wyklucz elementy z wyników pokrycia kodu

Można chcieć wykluczyć określone elementy w kodzie z oceny pokrycia, jeśli np. kod jest generowany na podstawie szablonu tekstu. <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> Dodaj atrybut do dowolnego z następujących elementów kodu: Klasa, struktura, metoda, właściwość, Metoda ustawiająca lub metoda pobierająca, zdarzenie.

> [!TIP]
> Wyłączenie klasy nie wyklucza jej klas pochodnych.

Na przykład:

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

### <a name="exclude-elements-in-native-c-code"></a>Wyklucz elementy w C++ kodzie natywnym

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

`ExcludeFromCodeCoverage(` Wykluczname `, L"` *Funkcjaname*`");`

`ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

- Wykluczname jest dowolną unikatową nazwą.

- *FunctionName* jest w pełni kwalifikowaną nazwą funkcji. Może ona zawierać symbole wieloznaczne. Na przykład, aby wykluczyć wszystkie funkcje klasy, należy napisać`MyNamespace::MyClass::*`

- *Sourcefilepath* to lokalna lub UNC Ścieżka do pliku. cpp. Może ona zawierać symbole wieloznaczne. Poniższy przykład wyklucza wszystkie pliki w określonym katalogu:`\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Miejsce wywołuje wyłączenie makr w globalnej przestrzeni nazw, nie w dowolnym obszarze nazw lub klasie.

- Można umieścić wyłączenia w pliku kodu testu jednostkowego lub w pliku kodu aplikacji.

- Wykluczenia muszą być kompilowane jako kod niezarządzany (natywny) przez ustawienie opcji kompilatora lub przy użyciu polecenia `#pragma managed(off)`.

> [!NOTE]
> Aby wykluczyć funkcje w C++kodzie/CLI, zastosuj atrybut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` do funkcji. To jest tak samo jak w języku C#.

### <a name="include-or-exclude-additional-elements"></a>Dołącz lub Wyklucz dodatkowe elementy

Analiza pokrycia kodu jest wykonywana tylko na zestawach, które są ładowane i dla których plik *. pdb* jest dostępny w tym samym katalogu, w którym znajduje się plik *. dll* lub *. exe* . W związku z tym w pewnych okolicznościach można rozciągnąć zestaw zestawów, które są dołączone przez pobranie kopii odpowiednich plików *. pdb* .

Można wykonać większą kontrolę nad tym, które zestawy i elementy są wybrane do analizy pokrycia kodu, pisząc plik *. runsettings* . Można np. wykluczyć zestawy określonego typu bez konieczności dodawania atrybutów do ich klas. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analizowanie pokrycia kodu w Azure Pipelines

Podczas ewidencjonowania kodu testy są uruchamiane na serwerze kompilacji wraz z testami z innych członków zespołu. Warto analizować pokrycie kodu w Azure Pipelines, aby uzyskać najbardziej aktualne i kompleksowe zdjęcie pokrycia w całym projekcie. Zawiera również zautomatyzowane testy systemowe i inne kodowane testy, które zwykle nie są uruchamiane na maszynach deweloperskich. Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych wraz z kompilacjami](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analizowanie pokrycia kodu z wiersza polecenia

Aby uruchomić testy z wiersza polecenia, należy użyć *VSTest. Console. exe*. Pokrycie kodu jest opcją narzędzia *VSTest. Console. exe* .

1. Uruchom wiersz polecenia dla deweloperów dla programu Visual Studio:

   ::: moniker range="vs-2017"

   W menu **Start** systemu Windows wybierz pozycję **Visual Studio 2017** > **wiersz polecenia dla deweloperów dla programu vs 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   W menu **Start** systemu Windows wybierz pozycję **Visual Studio 2019** > **wiersz polecenia dla deweloperów dla programu vs 2019**.

   ::: moniker-end

2. W wierszu polecenia wpisz następujące polecenie:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Aby uzyskać więcej informacji, zobacz [Opcje wiersza polecenia VSTest. Console. exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli nie widzisz wyników pokrycia kodu, artykuł [Rozwiązywanie problemów z kodem](../test/troubleshooting-code-coverage.md) może Ci pomóc.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Rozwiązywanie problemów z pokryciem kodu](../test/troubleshooting-code-coverage.md)
- [Kod testu jednostkowego](../test/unit-test-your-code.md)
