---
title: Uruchamianie testów jednostkowych za pomocą Eksploratora testów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 56f2d4cb0b02cc661177a4f781a5c40db924ee2c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302104"
---
# <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystanie z Eksploratora testów do uruchamiania testów jednostkowych z programu Visual Studio lub projektów testów jednostkowych innych firm, grupowanie testów do kategorii, filtrowanie listy testów oraz tworzenie, zapisywanie i uruchamianie list odtwarzania testów. Można również debugować testy i analizować wydajność testów i pokrycie kodu.

## <a name="BKMK_Contents"></a>Contents
 [Framework testów jednostkowych i projekty testowe](#BKMK_Unit_test_frameworks_and_test_projects)

 [Uruchom testy w Eksploratorze testów](#BKMK_Run_tests_in_Test_Explorer)

 [Wyświetl wyniki testu](#BKMK_View_test_results)

 [Grupowanie i filtrowanie listy testów](#BKMK_Group_and_filter_the_test_list)

 [Tworzenie niestandardowych list odtwarzania](#BKMK_Create_custom_playlists)

 [Debuguj i Analizuj testy jednostkowe](#BKMK_Debug_and_analyze_unit_tests)

 [Zasoby zewnętrzne](#BKMK_External_resources)

## <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Framework testów jednostkowych i projekty testowe
 Program Visual Studio zawiera struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego i natywnego. Jednak w Eksploratorze testów można także uruchomić dowolną strukturę testów jednostkowych, która wdrożyła adapter programu Test Explorer. Aby uzyskać więcej informacji na temat instalowania platform testów jednostkowych innych firm, zobacz [Instalowanie platform testów jednostkowych](../test/install-third-party-unit-test-frameworks.md) innych firm

 Eksplorator testów może uruchamiać testy z wielu projektów testów w rozwiązaniu i z klas testowych, które są częścią projektów kodu produkcyjnego. Projekty testowe mogą korzystać z różnych platform testów jednostkowych. Gdy testowy kod jest zapisywana dla .NET Framework, projekt testowy można napisać w dowolnym języku, który również jest przeznaczony dla .NET Framework, niezależnie od języka kodu docelowego. Natywnych projektów kodu C/C++ muszą być przetestowany przy użyciu struktury testowej jednostki C++.

 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Run_tests_in_Test_Explorer"></a>Uruchom testy w Eksploratorze testów
 [Uruchom testy](#BKMK_Run_tests) **&#124;** [Uruchom testy po każdej kompilacji](#BKMK_Run_tests_after_every_build)

 Podczas tworzenia projektu testowego, testy są wyświetlane w Eksploratorze testów. Eksplorator testów nie jest widoczny, wybierz opcję **testu** menu programu Visual Studio, wybierz **Windows**, a następnie wybierz **Eksplorator testów**.

 ![Eksplorator testów jednostkowych](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach domyślnych **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i  **Esty nieuruchamiane**. Można zmienić sposobu Eksplorator testów grupuje testy.

 Na pasku narzędzi Eksploratora testów można wykonywać wiele prac znajdowania, organizowania i uruchamiania testów.

 ![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute-toolbar.png "UTE_ToolBar")

 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

### <a name="BKMK_Run_tests"></a>Uruchom testy
 Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które można wybrać. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz **Uruchom wszystkie**.

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz **uruchamianie...**  a następnie wybierz grupę, w menu.

- Wybierz pojedyncze testy, które chcesz uruchomić, otwórz menu kontekstowe dla wybranego testu, a następnie wybierz polecenie **Uruchom wybrane testy**.

- Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą przycisku przełączania ![&#95;wykonaj parallelicon&#45;mały](../test/media/ute-parallelicon-small.png "UTE_parallelicon — mały") przełącznik na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

  Pasek Powodzenie/niepowodzenie u góry okna Eksploratora testów jest animowany podczas działania testu. Po zakończeniu przebiegu testowego pasek Powodzenie/niepowodzenie zmienia kolor na zielony, jeśli wszystkie testy przekazane lub na czerwony, jeśli dowolny test nie powiodła się.

  ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

### <a name="BKMK_Run_tests_after_every_build"></a>Uruchom testy po każdej kompilacji

> [!WARNING]
> Uruchamianie testów jednostkowych po każdej kompilacji jest obsługiwane w Visual Studio Enterprise.

|||
|-|-|
|![Uruchom po kompilacji](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz **test** w menu Standard, a następnie wybierz polecenie **Uruchom testy po kompilacji** na pasku narzędzi Eksploratora testów.|

 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_View_test_results"></a>Wyświetl wyniki testu
 [Wyświetl szczegóły](#BKMK_View_test_details) **&#124;** testu [Wyświetl kod źródłowy metody testowej](#BKMK_View_the_source_code_of_a_test_method)

 Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i **nie uruchomione Testy**. Uruchom Podsumowanie testu w dolnej części Eksploratora testów jest wyświetlane w okienku szczegółów.

### <a name="BKMK_View_test_details"></a>Wyświetl szczegóły testu
 Aby wyświetlić szczegółowe informacje o poszczególnych testach, wybierz test.

 ![Szczegóły wykonania testu](../test/media/ute-testdetails.png "UTE_TestDetails")

 W okienku szczegółów są wyświetlane następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Czas trwania metody testowej.

  Jeśli test zakończy się niepowodzeniem, są wyświetlane również w okienku szczegółów:

- Komunikat zwracany przez strukturę testu jednostki dla testu.

- Ślad stosu w czasie testu nie powiodło się.

  ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

### <a name="BKMK_View_the_source_code_of_a_test_method"></a>Wyświetl kod źródłowy metody testowej
 Aby wyświetlić kod źródłowy dla metody testowej w edytorze programu Visual Studio, wybierz test, a następnie wybierz **Otwórz test** w menu kontekstowym (klawiatura: F12).

 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Group_and_filter_the_test_list"></a>Grupowanie i filtrowanie listy testów
 [Grupowanie list](#BKMK_Grouping_the_test_list) **&#124;** testów [według cech](#BKMK_Group_by_traits) **&#124;** [Wyszukiwanie i filtrowanie listy testów](#BKMK_Search_and_filter_the_test_list)

 Eksplorator testów umożliwia grupowanie testów w wstępnie zdefiniowanych kategoriach. Większość platform testów jednostkowych, które działają w Eksploratorze testów, umożliwiają definiowanie własnych kategorii i par kategorii/wartości w celu grupowania testów. Możesz również filtrować listę testów, dopasowując ciągi do właściwości testu.

### <a name="BKMK_Grouping_the_test_list"></a>Grupowanie listy testów
 Aby zmienić sposób, w jaki są zorganizowane testy, wybierz strzałkę w dół obok przycisku Grupuj **według** w ![Eksploratorze testów](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn") i wybierz nowe kryteria grupowania.

 ![Grupuj testy według kategorii w Eksploratorze testów](../test/media/ute-groupbycategory.png "UTE_GroupByCategory")

### <a name="test-explorer-groups"></a>Grupy Eksploratora testów

|Grupa|Opis|
|-----------|-----------------|
|**Czas trwania**|Testy grup według czasu wykonywania: **szybka**, **średnia**i **wolna**.|
|**Wynik**|Grupuje testy według wyników wykonywania: **testy zakończone niepomyślnie**, **testy pominięte**, **testy zakończone powodzeniem**.|
|**Cech**|Grupuje testy według par kategorii/wartości zdefiniowanych przez użytkownika. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.|
|{1&gt;Projekt&lt;1}|Grupuje testy według nazwy projektów.|

 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

### <a name="BKMK_Group_by_traits"></a>Grupuj według cech
 Cechą jest zazwyczaj para nazwa kategorii/wartość, ale może to być również jedna kategoria. Cechy mogą być przypisywane do metod, które są identyfikowane jako metoda testowa przez strukturę testów jednostkowych. Struktura testów jednostkowych może definiować kategorie cech. Możesz dodać wartości do kategorii cech, aby zdefiniować własne pary nazwa/wartość kategorii. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.

 **Cechy struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego**

 W środowisku testów jednostkowych firmy Microsoft dla aplikacji zarządzanych definiujesz parę nazwa/wartość w atrybucie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>. Struktura testowa zawiera również następujące wstępnie zdefiniowane cechy:

|Cecha|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategoria właściciela jest definiowana przez strukturę testów jednostkowych i wymaga podania wartości ciągu właściciela.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategoria priorytetu jest definiowana przez strukturę testów jednostkowych i wymaga podania wartości całkowitej priorytetu.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atrybut TestCategory umożliwia podanie kategorii bez wartości. Kategoria zdefiniowana przez atrybut TestCategory może być również kategorią atrybutu TestProperty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atrybut TestProperty umożliwia zdefiniowanie pary Category/wartość.|

 **Cechy struktury testów jednostkowych firmy Microsoft dlaC++**

 Aby zdefiniować cechę, użyj `TEST_METHOD_ATTRIBUTE` makra. Na przykład aby zdefiniować cechę o nazwie `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 Aby użyć określonej cechy w testach jednostki:

```
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>Makra atrybutów cech C++

|Macro|Opis|
|-----------|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Użyj makra test_method_attribute, aby zdefiniować cechę.|
|`TEST_OWNER(ownerAlias)`|Użyj wstępnie zdefiniowana cecha właściciela do określania właściciela metody badania.|
|`TEST_PRIORITY(priority)`|Użyj wstępnie zdefiniowanego cecha priorytetu jest używana do przypisywania względnych priorytetów do metod badania.|

 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

### <a name="BKMK_Search_and_filter_the_test_list"></a>Wyszukiwanie i filtrowanie listy testów
 Filtrów programu Test Explorer można użyć do ograniczenia metod testowych w projektach, które są wyświetlane i uruchamiane.

 Po wpisaniu ciągu w polu wyszukiwania Eksploratora testów i wybraniu klawisza ENTER lista testów jest filtrowana, aby wyświetlić tylko te testy, których w pełni kwalifikowane nazwy zawierają ciąg.

 Aby odfiltrować według innych kryteriów:

1. Otwórz listę rozwijaną z prawej strony pola wyszukiwania.

2. Wybierz nowe kryterium.

3. Wprowadź wartość filtru między znakami cudzysłowu.

   ![Filtruj testy w Eksploratorze testów](../test/media/ute-filtertestlist.png "UTE_FilterTestList")

> [!NOTE]
> Wyszukiwania są rozróżniane wielkości liter i pasują do określonego ciągu do dowolnej części wartości kryteriów.

|Kwalifikator|Opis|
|---------------|-----------------|
|**Cecha**|Wyszukuje dopasowania kategorii i wartości. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.|
|{1&gt;Projekt&lt;1}|Wyszukuje dopasowania w nazwach projektów testowych.|
|**Komunikat o błędzie**|Wyszukuje dopasowania w zdefiniowanych przez użytkownika komunikatach o błędach zwracanych przez nieudane potwierdzenia.|
|**Ścieżka pliku**|Wyszukuje dopasowania w w pełni kwalifikowanych nazwach plików źródłowych testów.|
|**W pełni kwalifikowana nazwa**|Wyszukuje dopasowania w w pełni kwalifikowanych nazwach plików przestrzeni nazw, klas i metod testowych.|
|**Output**|Wyszukuje komunikaty o błędach zdefiniowane przez użytkownika, które są zapisywane w standardowym wyjściu (stdout) lub w standardowym błędzie (stderr). Składnia służąca do określania komunikatów wyjściowych jest definiowana przez strukturę testów jednostkowych.|
|**Wynik**|Wyszukuje dopasowania w nazwach kategorii Eksploratora testów: **testy zakończone niepomyślnie**, **testy pominięte**, **testy zakończone powodzeniem**.|

 Aby wykluczyć podzestaw wyników filtru, należy użyć następującej składni:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

 Na przykład

```
FullName:"MyClass" - FullName:"PerfTest"
```

 zwraca wszystkie testy, które zawierają ciąg "MyClass" w nazwie, z wyjątkiem tych testów, które zawierają również ciąg "PerfTest" w nazwie.

 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Create_custom_playlists"></a>Tworzenie niestandardowych list odtwarzania
 Można utworzyć i zapisać listę testów, które chcesz uruchomić lub wyświetlić jako grupę. Po wybraniu listy odtwarzania testy na liście są wyświetlane w Eksploratorze testów. Test można dodać do więcej niż jednej listy odtwarzania, a wszystkie testy w projekcie są dostępne po wybraniu domyślnej listy odtwarzania **wszystkie testy** .

 ![Wybierz listę odtwarzania](../test/media/ute-playlist.png "UTE_Playlist")

 **Aby utworzyć listę odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu kontekstowym wybierz polecenie **Dodaj do listy odtwarzania**, **NewPlaylist**. Zapisz plik o nazwie i lokalizacji określonej w oknie dialogowym **Tworzenie nowej listy odtwarzania** .

 **Aby dodać testy do listy odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu kontekstowym wybierz polecenie **Dodaj do listy odtwarzania**, a następnie wybierz listę odtwarzania, do której chcesz dodać testy.

 **Aby otworzyć listę odtwarzania**, wybierz pozycję test, lista odtwarzania z menu programu Visual Studio, a następnie wybierz pozycję z listy ostatnio używanych list odtwarzania lub wybierz pozycję Otwórz listę odtwarzania, aby określić nazwę i lokalizację listy odtwarzania.

 Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą przycisku przełączania ![&#95;wykonaj parallelicon&#45;mały](../test/media/ute-parallelicon-small.png "UTE_parallelicon — mały") przełącznik na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Debug_and_analyze_unit_tests"></a>Debuguj i Analizuj testy jednostkowe
 [Debugowanie testów](#BKMK_Debug_unit_tests) **&#124;** jednostkowych [diagnozowanie problemów](#BKMK_Diagnose_test_method_performance_issues) **&#124;** z wydajnością [Analizowanie pokryciu kodu testu jednostkowego](#BKMK_Analyzeunit_test_code_coverage)

### <a name="BKMK_Debug_unit_tests"></a>Debuguj testy jednostkowe
 Eksplorator testów umożliwia uruchamianie sesji debugowania dla testów. Krokowe wykonywanie kodu za pomocą debugera programu Visual Studio bezproblemowe przejście i z powrotem między testami jednostek a testowanego projektu. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w metodach testów, które chcesz debugować.

   > [!NOTE]
   > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkich metodach testowych, które chcesz debugować.

2. W Eksploratorze testów wybierz metody testowe, a następnie wybierz **Debuguj wybrane testy** z menu kontekstowego.

   Aby uzyskać więcej informacji dotyczących debugera, zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

### <a name="BKMK_Diagnose_test_method_performance_issues"></a>Diagnozuj problemy z wydajnością metody testowej
 Aby zdiagnozować Dlaczego metoda testowa trwa zbyt wiele czasu, wybierz metodę w Eksploratorze testów, a następnie wybierz pozycję Profil w menu kontekstowym. Zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).

### <a name="BKMK_Analyzeunit_test_code_coverage"></a>Analizuj pokrycie kodu testu jednostkowego

> [!NOTE]
> Pokrycie kodu testu jednostkowego jest dostępne tylko w Visual Studio Enterprise.

 Można określić ilość kodu produktu, który jest faktycznie testowany przez testy jednostkowe za pomocą narzędzia pokrycia kodu w programie Visual Studio. Można uruchomić pokrycie kodów w wybranych testach albo we wszystkich testach w rozwiązaniu.

 Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu:

1. Wybierz pozycję **testy** w menu programu Visual Studio, a następnie wybierz polecenie **Analizuj pokrycie kodu**.

2. Wybierz jedno z następujących poleceń z podmenu:

   - **Wybrane testy** uruchamiają metody testowe, które zostały wybrane w Eksploratorze testów.

   - **Wszystkie testy** są uruchamiane ze wszystkich metod testowych w rozwiązaniu.

   Okno wyniki pokrycia kodu przedstawia wartość procentową bloków kodu produktu, które były wykonywane przez wiersz, funkcję, klasę, przestrzeń nazw i moduł.

   Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu w celu określenia, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_External_resources"></a>Zasoby zewnętrzne

### <a name="BKMK_Guidance"></a>Informator
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Zobacz też
 [Test jednostkowy kodu](../test/unit-test-your-code.md) [uruchamia test jednostkowy jako proces 64-bitowy](../test/run-a-unit-test-as-a-64-bit-process.md)
