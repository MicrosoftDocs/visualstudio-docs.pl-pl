---
title: Korzystanie z pokrycia kodu do określania, jaka część kodu jest testowana | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- code coverage
ms.assetid: 800fc739-acd2-4242-84cb-1d83b4d82cf9
caps.latest.revision: 38
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee281e2cabcbce4f950188465163769caae7b2bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657243"
---
# <a name="using-code-coverage-to-determine-how-much-code-is-being-tested"></a>Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny obejmować lub pokrywać znaczną część kodu.

 Analizy pokrycia kodu mogą dotyczyć zarówno kodów zarządzanych (CLI), jak i niezarządzanych (natywnych).

 Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

 ![Wyniki pokrycia kodu z kolorami](../test/media/codecoverage1.png "CodeCoverage1")

 **Requirements**

- Visual Studio Enterprise

### <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Analizowanie pokrycia kodu w ramach testów jednostkowych w Eksploratorze testów

1. W menu **test** wybierz polecenie **Analizuj pokrycie kodu**.

2. Aby zobaczyć, które wiersze zostały uruchomione, wybierz ![ikonę Pokaż kolorowanie pokrycia kodu](../test/media/codecoverage-showcoloringicon.png "CodeCoverage — ShowColoringIcon").**Pokaż kolorowanie pokrycia kodu**.

     Aby zmienić kolory lub użyć pogrubienia, wybierz **Narzędzia**, **Opcje**, **środowisko**, **czcionki i kolory**, **Pokaż ustawienia dla edytora tekstu**. W obszarze **Wyświetl elementy**Dostosuj elementy pokrycia.

3. Jeśli wyniki wykażą niewielkie pokrycie, zbadaj części kodu, które nie są wykonywane, i napisz więcej testów, aby je pokryć. Zespoły deweloperów zazwyczaj dążą do około 80% pokrycia kodu. W niektórych sytuacjach dopuszczalne jest niższe zapotrzebowanie. Niższe zapotrzebowanie jest dopuszczalne np. tam, gdzie dany kod jest generowany na podstawie standardowego szablonu.

> [!TIP]
> Aby uzyskać dokładne wyniki:
>
> - Upewnij się, że optymalizacja kompilatora jest wyłączona.
>
>   Pracując z kodem niezarządzanym (natywnym), należy użyć kompilacji debugowania.
>   - Upewnij się, że pliki .pdb (symbol) są generowane dla każdego zestawu.
>
>   Jeśli nie otrzymujesz oczekiwanych wyników, zobacz temat [Rozwiązywanie problemów z kodem](../test/troubleshooting-code-coverage.md). . Nie można zapominać o ponownym uruchomieniu pokrycia kodu po jego aktualizacji. Wyniki pokrycia i kolorowanie kodu nie są automatycznie aktualizowane po zmodyfikowaniu kodu ani po uruchomieniu testów.

## <a name="reporting-in-blocks-or-lines"></a>Raportowanie w blokach i wierszach
 Pokrycie kodu jest zliczane w *blokach*. Blok jest fragmentem kodu z dokładnie jednym punktem wejścia i wyjścia.  Jeżeli przepływ kontroli programu przechodzi przez blok podczas przebiegu testu, blok jest zaliczany do pokrytych. To, ile razy użyto danego bloku, nie ma wpływu na wynik.

 Wyniki można także wyświetlić w obszarze wiersze, wybierając pozycję **Dodaj/Usuń kolumny** w nagłówku tabeli. Jeżeli przebieg testu sprawdził wszystkie bloki kodu w każdym jego wierszu, liczy się to jako jeden wiersz. W przypadku gdy wiersz zawiera bloki kodu, które były sprawdzane, oraz takie, które nie były, jest liczony jako wiersz częściowy.

 Niektórzy użytkownicy preferują liczbę wierszy, ponieważ wartości procentowe ściślej odpowiadają rozmiarowi fragmentów, które widać w kodzie źródłowym. Duży blok obliczeń jest traktowany jako pojedynczy, nawet jeśli zajmuje wiele wierszy.

## <a name="managing-code-coverage-results"></a>Zarządzanie wynikami pokrycia kodu
 Okno Wyniki pokrycia kodu zwykle przedstawia najnowszy wynik uruchomionych testów. Wyniki będą się różnić, jeśli zmienisz ich dane lub za każdym razem uruchomisz tylko niektóre z testów.

 Okno pokrycia kodu może służyć również do wyświetlania poprzednich wyników lub wyników uzyskanych na innych komputerach.

 Można scalać wyniki kilku uruchomień, na przykład tych, które używają różnych danych testowych.

- **Aby wyświetlić poprzedni zestaw wyników**, wybierz go z menu rozwijanego. W menu pojawia się tymczasowa lista, która jest czyszczona po otwarciu nowego rozwiązania.

- **Aby wyświetlić wyniki z poprzedniej sesji**, wybierz pozycję **Importuj wyniki pokrycia kodu**, przejdź do folderu TestResults w rozwiązaniu i zaimportuj plik. coverage.

     Kolorowanie pokrycia może być niepoprawne, jeśli kod źródłowy zmienił się od czasu wygenerowania pliku .coverage.

- **Aby wyniki były odczytywane jako tekst**, wybierz opcję **Eksportuj wyniki pokrycia kodu**. Spowoduje to wygenerowanie pliku .coveragexml, który można odczytać. Można go też przetwarzać z innymi narzędziami lub łatwo wysłać pocztą.

- **Aby wysłać wyniki do kogoś innego**, Wyślij plik. coverage lub wyeksportowany plik. COVERAGEXML. Następnie można zaimportować plik. Jeśli mają one tę samą wersję kodu źródłowego, mogą odczytać kolorowanie pokrycia.

## <a name="merging-results-from-different-runs"></a>Scalanie wyników z różnych tras
 W niektórych sytuacjach, w zależności od danych testowych, używane będą różne bloki w kodzie. W związku z tym można wykorzystać wyniki z różnych przebiegów testów.

 Można na przykład założyć, że po uruchomieniu testu z wpisem „2” okaże się, że pokryto 50% określonej funkcji. Po uruchomieniu testu po raz drugi z wpisem „-2” widoczne kolorowanie pokrycia obejmie pozostałe 50% funkcji. Teraz należy scalić wyniki z dwóch przebiegów testów, a raport i widok kolorowania pokrycia pokaże 100% pokrycia funkcji.

 Użyj ![ikony przycisku Scal w oknie pokrycie kodu](../test/media/codecoverage-mergeicon.png "CodeCoverage — MergeIcon")**Scal wyniki pokrycia kodu** , aby to zrobić. Można wybrać dowolną kombinację ostatnich uruchomień lub zaimportowanych wyników. Aby połączyć wyeksportowane wyniki, należy je najpierw zaimportować.

 Użyj **Eksportuj wyniki pokrycia kodu** , aby zapisać wyniki operacji scalania.

### <a name="limitations-in-merging"></a>Ograniczenia w scalaniu

- W przypadku scalania danych pokrycia z różnych wersji kodu wyniki są wyświetlane oddzielnie i nie są połączone. Aby uzyskać w pełni połączone wyniki, należy zastosować tę samą kompilację kodu, zmieniając tylko dane testowe.

- W przypadku scalania pliku wyników, które zostały wyeksportowane, a następnie zaimportowane, wyniki można przeglądać tylko według wierszy, a nie bloków. Użyj polecenia **Dodaj/Usuń kolumny** , aby wyświetlić dane wiersza.

- W przypadku scalania wyników z testów programu ASP.NET wyniki dla oddzielnych testów są wyświetlane, ale nie są połączone. Dotyczy to tylko samych artefaktów ASP.NET: wyniki dla innych zestawów zostaną połączone.

## <a name="excluding-elements-from-the-code-coverage-results"></a>Wykluczanie elementów z wyników pokrycia kodu
 Można chcieć wykluczyć określone elementy w kodzie z oceny pokrycia, jeśli np. kod jest generowany na podstawie szablonu tekstu. Dodaj `System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverage` atrybutu do dowolnego z następujących elementów kodu: Klasa, struktura, metoda, właściwość, Metoda ustawiająca lub metoda pobierająca, zdarzenie. Należy zauważyć, że wykluczenie klasy nie wyklucza jej klas pochodnych.

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

```cpp#
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

### <a name="excluding-elements-in-native-c-code"></a>Wykluczanie elementów w Natywnym kodzie C++
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

 `ExcludeFromCodeCoverage(` *wykluczenianame* `, L"` *funkcjaname* `");`

 `ExcludeSourceFromCodeCoverage(` *wykluczenia* `, L"` *sourcefilepath* `");`

- *Wykluczname* jest dowolną unikatową nazwą.

- *FunctionName* jest w pełni kwalifikowaną nazwą funkcji. Może ona zawierać symbole wieloznaczne. Na przykład, aby wykluczyć wszystkie funkcje klasy, `MyNamespace::MyClass::*` zapisu

- *Sourcefilepath* to lokalna lub UNC Ścieżka do pliku. cpp. Może ona zawierać symbole wieloznaczne. Poniższy przykład wyklucza wszystkie pliki w określonym katalogu: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Miejsce wywołuje wyłączenie makr w globalnej przestrzeni nazw, nie w dowolnym obszarze nazw lub klasie.

- Można umieścić wyłączenia w pliku kodu testu jednostkowego lub w pliku kodu aplikacji.

- Wykluczenia muszą być kompilowane jako kod niezarządzany (natywny) przez ustawienie opcji kompilatora lub przy użyciu `#pragma managed(off)`.

> [!NOTE]
> Aby wykluczyć funkcje w C++kodzie/CLI, zastosuj atrybut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` do funkcji. To jest tak samo jak w języku C#.

### <a name="including-or-excluding-additional-elements"></a>Włączanie lub wyłączanie dodatkowych elementów
 Analizy pokrycia kodu są wykonywane tylko na zestawach, które są ładowane i dla których plik .pdb jest dostępny w tym samym katalogu co plik .exe lub .dll. Dlatego w pewnych okolicznościach można rozszerzyć zbiór zestawów, włączony przez uzyskanie kopii odpowiednich plików .pdb.

 Można zwiększyć kontrolę nad tym, które zespoły i elementy są zaznaczone dla analizy pokrycia kodu przez napisanie pliku .runsettings. Można np. wykluczyć zestawy określonego typu bez konieczności dodawania atrybutów do ich klas. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="analyzing-code-coverage-in-the-build-service"></a>Analizowanie pokrycia kodu w usłudze kompilacji
 Podczas sprawdzania kodu testy będą uruchamiane na serwerze kompilacji, razem z innymi testami pozostałych członków zespołu. (Jeśli jeszcze tego nie zrobiono, zobacz [Uruchamianie testów w procesie kompilacji](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)). Warto analizować pokrycie kodu w usłudze kompilacji, ponieważ zapewnia to najbardziej aktualne i kompleksowe zdjęcie pokrycia w całym projekcie. Zawiera także automatyczne testy systemu i inne zakodowane testy, których zwykle nie uruchamia się na komputerach deweloperskich.

1. W Team Explorer Otwórz **kompilacje**, a następnie Dodaj lub Edytuj definicję kompilacji.

2. Na stronie **proces** rozwiń węzeł **testy automatyczne**, **Źródło testów**, **Parametry uruchomieniowe**. Ustaw **Typ pliku parametrów uruchomieniowych** na **włączony pokrycie kodu**.

    Jeśli masz więcej niż jedną definicję źródła testów, powtórz ten krok dla każdej z nich.

   - <em>Ale nie istnieje pole o nazwie **typu pliku parametrów uruchomieniowych</em>* . *

      W obszarze **testy automatyczne**wybierz pozycję **zestaw testowy** i wybierz przycisk wielokropka **[...]** na końcu wiersza. W oknie dialogowym **Dodawanie/edytowanie przebiegu testu** w obszarze moduł uruchamiający **testy**wybierz pozycję **Visual Studio Test Runner**.

   ![Ustawianie definicji kompilacji dla pokrycia kodu](../test/media/codecoverage-plaincc.png "CodeCoverage — plainCC")

   Po uruchomieniu kompilacji wyniki pokrycia kodu są dołączane do przebiegu testowego i pojawiają się w podsumowaniu kompilacji.

## <a name="analyzing-code-coverage-in-a-command-line"></a>Analizowanie pokrycia kodu w wierszu polecenia
 Aby uruchomić testy z wiersza polecenia, należy użyć narzędzia vstest.console.exe. Pokrycie kodu jest opcją tego narzędzia. Aby uzyskać więcej informacji, zobacz [Opcje wiersza polecenia VSTest. Console. exe](https://msdn.microsoft.com/library/52e1689d-b1a8-4589-bd98-99a55acd0a11).

1. Uruchom wiersz polecenia programisty dla programu Visual Studio:

     W menu **Start** systemu Windows wybierz kolejno pozycje **wszystkie programy**, **Microsoft Visual Studio**, **Visual Studio Tools**i **wiersz polecenia dla deweloperów**.

2. Uruchom:

     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage`

## <a name="troubleshooting"></a>Rozwiązywanie problemów
 Jeśli nie widzisz wyników pokrycia kodu, zobacz temat [Rozwiązywanie problemów z kodem](../test/troubleshooting-code-coverage.md).

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="guidance"></a>Wskazówki
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md) [Rozwiązywanie problemów z](../test/troubleshooting-code-coverage.md) [jednostką pokrycia kodu testowanie kodu](../test/unit-test-your-code.md)
