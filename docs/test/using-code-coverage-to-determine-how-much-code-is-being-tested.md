---
title: Kod pokrycie testowania
ms.date: 09/18/2018
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
ms.openlocfilehash: a76b40e2a9848b0f80e755d15a9bd6e65fcf51da
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222912"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny obejmować lub pokrywać znaczną część kodu.

Analizy pokrycia kodu mogą dotyczyć zarówno kodów zarządzanych (CLI), jak i niezarządzanych (natywnych).

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

![Wyniki pokrycia kodu za pomocą kolorowania](../test/media/codecoverage1.png)

## <a name="requirements"></a>Wymagania

Funkcja pokrycia kodu jest dostępna tylko w programie Visual Studio Enterprise.

## <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Analizowanie pokrycia kodu w ramach testów jednostkowych w Eksploratorze testów

1. Na **testu** menu, wybierz **Analizuj pokrycie kodu**.

2. Aby zobaczyć, które wiersze zostały uruchomione, wybierz ![Pokaż ikona kolorowanie pokrycia kodu](../test/media/codecoverage-showcoloringicon.png) **Pokaż kolorowanie pokrycia kodu**.

   Aby zmienić kolory lub użyć pogrubionej czcionki, wybierz opcję **narzędzia** > **opcje** > **środowiska** > **czcionek i Kolory** > **Pokaż ustawienia dla: Edytor tekstu**. W obszarze **Wyświetle elementy**, Dopasuj pokrycie.

3. Jeśli wyniki wykażą niewielkie pokrycie, zbadaj części kodu, które nie są wykonywane, i napisz więcej testów, aby je pokryć. Zespoły deweloperów zazwyczaj dążą do około 80% pokrycia kodu. W niektórych sytuacjach dopuszczalne jest niższe zapotrzebowanie. Niższe zapotrzebowanie jest dopuszczalne np. tam, gdzie dany kod jest generowany na podstawie standardowego szablonu.

> [!TIP]
> - Upewnij się, że Optymalizacja kompilatora jest wyłączona.
> - Jeśli pracujesz z kodem niezarządzanym (natywna), należy użyć kompilacji debugowania
> - Upewnij się, że są generuje pliki .pdb (symbol) dla każdego zestawu.

Jeśli nie otrzymujesz oczekiwanych wyników, zobacz [Rozwiązywanie problemów z pokryciem kodu](../test/troubleshooting-code-coverage.md). Należy pamiętać uruchomić pokrycie kodu ponownie po jego aktualizacji. Wyniki pokrycia i kolorowanie kodu nie są automatycznie aktualizowane po zmodyfikowaniu kodu ani po uruchomieniu testów.

## <a name="report-in-blocks-or-lines"></a>Raport w blokach i wierszach

Pokrycie kodu jest liczone *bloków*. Blok jest fragmentem kodu z dokładnie jednym punktem wejścia i wyjścia.  Jeżeli przepływ kontroli programu przechodzi przez blok podczas przebiegu testu, ten blok jest zaliczany do pokrytych. To, ile razy użyto danego bloku, nie ma wpływu na wynik.

Mogą też istnieć wyniki wyświetlane w postaci wierszy, wybierając **Dodaj/Usuń kolumny** w nagłówku tabeli. Jeżeli przebieg testu sprawdził wszystkie bloki kodu w każdym jego wierszu, liczy się to jako jeden wiersz. W przypadku gdy wiersz zawiera bloki kodu, które były sprawdzane, oraz takie, które nie były, jest liczony jako wiersz częściowy.

Niektórzy użytkownicy preferują liczbę wierszy, ponieważ wartości procentowe ściślej odpowiadają rozmiarowi fragmentów, które widać w kodzie źródłowym. Duży blok obliczeń jest traktowany jako pojedynczy, nawet jeśli zajmuje wiele wierszy.

## <a name="manage-code-coverage-results"></a>Zarządzanie wynikami pokrycia kodu

**Wyniki pokrycia kodu** okna zazwyczaj zawiera wynik ostatniego uruchomienia. Wyniki będą się różnić, jeśli zmienisz ich dane lub za każdym razem uruchomisz tylko niektóre z testów.

Okno pokrycia kodu może służyć również do wyświetlania poprzednich wyników lub wyników uzyskanych na innych komputerach.

Można scalać wyniki kilku uruchomień, na przykład tych, które używają różnych danych testowych.

- **Aby wyświetlić poprzedni zestaw wyników**, wybierz go z menu rozwijanego. W menu pojawia się tymczasowa lista, która jest czyszczona po otwarciu nowego rozwiązania.

- **Aby wyświetlić wyniki z poprzedniej sesji**, wybierz **Importuj wyniki pokrycia kodu**, przejdź do **TestResults** folder w rozwiązaniu i zaimportuj *.coverage* pliku.

   Kolorowanie pokrycia może być nieprawidłowy, jeśli kod źródłowy zmienił się od *.coverage* został wygenerowany plik.

- **Aby wyniki były czytelne jak tekst**, wybierz **Eksportuj wyniki pokrycia kodu**. Spowoduje to wygenerowanie czytelny *.coveragexml* pliku, który może przetwarzać z innymi narzędziami lub łatwo wysłać pocztą.

- **Aby wysłać wyniki do kogoś innego**, albo wysłać *.coverage* pliku lub wyeksportowany *.coveragexml* pliku. Następnie można zaimportować plik. Jeśli mają one tę samą wersję kodu źródłowego, mogą odczytać kolorowanie pokrycia.

## <a name="merge-results-from-different-runs"></a>Scalanie wyników z różnych tras

W niektórych sytuacjach, w zależności od danych testowych, używane będą różne bloki w kodzie. W związku z tym można wykorzystać wyniki z różnych przebiegów testów.

Można na przykład założyć, że po uruchomieniu testu z wpisem „2” okaże się, że pokryto 50% określonej funkcji. Po uruchomieniu testu po raz drugi z wpisem "-2", zostanie wyświetlony w widoku, że pozostałe 50% funkcji jest objęty kolorowanie pokrycia. Teraz należy scalić wyniki z dwóch przebiegów testów, a raport i widok kolorowania pokrycia pokaże 100% pokrycia funkcji.

Użyj ![ikony dla przycisku scalania w oknie pokrycie kodu](../test/media/codecoverage-mergeicon.png) **Scal wyniki pokrycia kodu** w tym celu. Można wybrać dowolną kombinację ostatnich uruchomień lub zaimportowanych wyników. Aby połączyć wyeksportowane wyniki, należy je najpierw zaimportować.

Użyj **Eksportuj wyniki pokrycia kodu** zapisać wyniki operacji scalania.

### <a name="limitations-in-merging"></a>Ograniczenia w scalaniu

- W przypadku scalania danych pokrycia z różnych wersji kodu wyniki są wyświetlane oddzielnie i nie są połączone. Aby uzyskać w pełni połączone wyniki, należy zastosować tę samą kompilację kodu, zmieniając tylko dane testowe.

- W przypadku scalania pliku wyników, które zostały wyeksportowane, a następnie zaimportowane, wyniki można przeglądać tylko według wierszy, a nie bloków. Użyj **Dodaj/Usuń kolumny** polecenie, aby wyświetlić dane wiersza.

- W przypadku scalania wyników z testów programu ASP.NET wyniki dla oddzielnych testów są wyświetlane, ale nie są połączone. Dotyczy to tylko samych artefaktów ASP.NET: wyniki dla innych zestawów zostaną połączone.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Wykluczanie elementów z wyników pokrycia kodu

Można chcieć wykluczyć określone elementy w kodzie z oceny pokrycia, jeśli np. kod jest generowany na podstawie szablonu tekstu. Dodaj <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> atrybutu do żadnego z następujących elementów kodu: klasy, struktury, metoda, właściwość, metoda ustawiająca właściwości lub metody pobierającej, zdarzenia.

> [!TIP]
> Wykluczenie klasy nie wyklucza jej klas pochodnych.

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

`ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

`ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

- *ExclusionName* jest dowolną unikatową nazwą.

- *FunctionName* jest w pełni kwalifikowana nazwa funkcji. Może ona zawierać symbole wieloznaczne. Na przykład aby wykluczyć wszystkie funkcje klasy, należy napisać `MyNamespace::MyClass::*`

- *SourceFilePath* jest ścieżką lokalną lub UNC pliku .cpp. Może ona zawierać symbole wieloznaczne. Poniższy przykład wyłącza wszystkie pliki w określonym katalogu: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Miejsce wywołuje wyłączenie makr w globalnej przestrzeni nazw, nie w dowolnym obszarze nazw lub klasie.

- Można umieścić wyłączenia w pliku kodu testu jednostkowego lub w pliku kodu aplikacji.

- Wykluczenia muszą być skompilowane jako kod niezarządzany (natywny), przez ustawienie opcji kompilatora albo za pomocą `#pragma managed(off)`.

> [!NOTE]
> Aby wyłączyć funkcje w języku C + +/ CLI kodu, zastosuj atrybut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` do funkcji. To jest tak samo jak w języku C#.

### <a name="include-or-exclude-additional-elements"></a>Dołącz lub Wyklucz dodatkowe elementy

Analiza pokrycia kodu odbywa się tylko na zestawach, które są ładowane i dla których *.pdb* plik jest dostępny w tym samym katalogu co *.dll* lub *.exe* pliku. Dlatego w pewnych okolicznościach można rozszerzyć zbiór zestawów, włączony przez uzyskanie kopii odpowiednich *.pdb* plików.

Możesz skorzystać z większą kontrolę nad tym, którzy zespoły i elementy są zaznaczone dla analizy pokrycia kodu przez napisanie *.runsettings* pliku. Można np. wykluczyć zestawy określonego typu bez konieczności dodawania atrybutów do ich klas. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analiza pokrycia kodu w potokach platformy Azure

Podczas sprawdzania kodu testy uruchamiane na serwerze kompilacji oraz testy z innymi członkami zespołu. Jest to przydatne do analizy pokrycia kodu w potokach platformy Azure, aby uzyskać najbardziej aktualny i wszechstronny obraz pokrycia całego projektu. Zawiera także automatyczne testy systemu i inne zakodowane testy, których zwykle nie uruchamia na komputerach deweloperskich. Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych z kompilacjami](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analiza pokrycia kodu z poziomu wiersza polecenia

Aby uruchomić testy z wiersza polecenia, użyj *vstest.console.exe*. Pokrycie kodu jest opcją *vstest.console.exe* narzędzia.

1. Uruchom wiersz polecenia programisty dla programu Visual Studio:

   ::: moniker range="vs-2017"

   W Windows **Start** menu, wybierz **programu Visual Studio 2017** > **wiersz polecenia programisty dla programu VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   W Windows **Start** menu, wybierz **Visual Studio 2019** > **wiersz polecenia programisty dla programu VS 2019**.

   ::: moniker-end

2. W wierszu polecenia wpisz następujące polecenie:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Aby uzyskać więcej informacji, zobacz [opcje wiersza poleceń VSTest.Console.exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli nie widać wyników pokrycia kodu, [Rozwiązywanie problemów z pokryciem kodu](../test/troubleshooting-code-coverage.md) artykuł może pomóc.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Rozwiązywanie problemów z pokryciem kodu](../test/troubleshooting-code-coverage.md)
- [Kod testu jednostkowego](../test/unit-test-your-code.md)
