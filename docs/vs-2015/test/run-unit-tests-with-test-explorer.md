---
title: Uruchamianie testów jednostkowych w Eksploratorze testów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 29
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9541180ba8740cdc12a038f81c4ef74d47fcc1aa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446234"
---
# <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eksplorator testów umożliwia uruchamianie testów jednostkowych z Visual Studio lub projektów testów jednostkowych innych firm, grupowanie testów w kategorie, filtrowanie listy testów, tworzenie, zapisywanie i uruchamianie list odtwarzania testów. Możesz również debugować testy i analizowanie testów wydajność i pokrycie kodu.  
  
## <a name="BKMK_Contents"></a> Zawartość  
 [Framework testów jednostkowych i projekty testowe](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Uruchom testy w Eksploratorze testów](#BKMK_Run_tests_in_Test_Explorer)  
  
 [Wyświetlanie wyników testu](#BKMK_View_test_results)  
  
 [Grupuj i Filtruj listę testów](#BKMK_Group_and_filter_the_test_list)  
  
 [Utwórz niestandardowe listy odtwarzania](#BKMK_Create_custom_playlists)  
  
 [Debugowanie i analizowanie testów jednostkowych](#BKMK_Debug_and_analyze_unit_tests)  
  
 [Zasoby zewnętrzne](#BKMK_External_resources)  
  
## <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Framework testów jednostkowych i projekty testowe  
 Program Visual Studio obejmuje struktur testowania jednostek pochodzących od firmy Microsoft dla kodu zarządzanego i natywnego. Jednak Test Explorer można również uruchomić dowolnej jednostki struktury testów, które ma zaimplementowany adapter programu Test Explorer. Aby uzyskać więcej informacji na temat Instalowanie platform testów jednostkowych innych firm, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)  
  
 Eksplorator testów może uruchamiać testy z wielu projektów testów w rozwiązaniu i z klas testowych, które są częścią projektów kodu produkcyjnego. Projekty testów mogą używać innych struktur testów jednostek. Jeśli testowany kod jest przeznaczony dla .NET Framework, Projekt testowy można napisać tak w dowolnym języku, który również jest przeznaczony dla .NET Framework, bez względu na język docelowy kodu. Natywnych projektów kodu C/C++ muszą być przetestowany przy użyciu struktury testowej jednostki C++.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="BKMK_Run_tests_in_Test_Explorer"></a> Uruchom testy w Eksploratorze testów  
 [Uruchom testy](#BKMK_Run_tests) **&#124;** [uruchamiania testów po każdej kompilacji](#BKMK_Run_tests_after_every_build)  
  
 Podczas tworzenia projektu testowego, testy są wyświetlane w Eksploratorze testów. Eksplorator testów nie jest widoczny, wybierz opcję **testu** menu programu Visual Studio, wybierz **Windows**, a następnie wybierz **Eksplorator testów**.  
  
 ![Eksplorator testów jednostkowych](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach domyślnych **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i  **Esty nieuruchamiane**. Można zmienić sposobu Eksplorator testów grupuje testy.  
  
 Można przeprowadzić wiele prac wyszukiwania, organizowanie i Uruchamianie testów na pasku narzędzi Eksploratora testów.  
  
 ![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute-toolbar.png "UTE_ToolBar")  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
### <a name="BKMK_Run_tests"></a> Uruchom testy  
 Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które można wybrać. Wykonaj jedną z następujących czynności:  
  
- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz **Uruchom wszystkie**.  
  
- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz **uruchamianie...**  a następnie wybierz grupę, w menu.  
  
- Zaznacz poszczególne testy, które chcesz uruchomić, otwórz menu kontekstowe dla jednego z zaznaczonych testów, a następnie wybierz **Uruchom wybrane testy**.  
  
- Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małych](../test/media/ute-parallelicon-small.png "małych UTE_parallelicon") Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.  
  
  Pasek Powodzenie/niepowodzenie u góry okna Eksploratora testów jest animowany podczas działania testu. Po zakończeniu przebiegu testowego pasek Powodzenie/niepowodzenie zmienia kolor na zielony, jeśli wszystkie testy przekazane lub na czerwony, jeśli dowolny test nie powiodła się.  
  
  ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
### <a name="BKMK_Run_tests_after_every_build"></a> Uruchamianie testów po każdej kompilacji  
  
> [!WARNING]
> Uruchamianie testów jednostek po każdej kompilacji jest obsługiwane w programie Visual Studio Enterprise.  
  
|||  
|-|-|  
|![Uruchom po kompilacji](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz **testu** w menu standardowym, a następnie wybierz **Uruchom testy po kompilacji** na pasku narzędzi Eksploratora testów.|  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="BKMK_View_test_results"></a> Wyświetlanie wyników testu  
 [Wyświetl szczegóły testu](#BKMK_View_test_details) **&#124;** [wyświetlić kodu źródłowego metody badawczej](#BKMK_View_the_source_code_of_a_test_method)  
  
 Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i **nie uruchomione Testy**. Uruchom Podsumowanie testu w dolnej części Eksploratora testów jest wyświetlane w okienku szczegółów.  
  
### <a name="BKMK_View_test_details"></a> Pokaż szczegóły testu  
 Aby wyświetlić szczegółowe informacje o poszczególnych testach, wybierz test.  
  
 ![Szczegóły wykonywania testu](../test/media/ute-testdetails.png "UTE_TestDetails")  
  
 W okienku szczegółów są wyświetlane następujące informacje:  
  
- Nazwa pliku źródłowego i numer wiersza metody testowej.  
  
- Stan testu.  
  
- Czas trwania metody testowej.  
  
  Jeśli test zakończy się niepowodzeniem, są wyświetlane również w okienku szczegółów:  
  
- Komunikat zwracany przez strukturę testu jednostki dla testu.  
  
- Ślad stosu w czasie testu nie powiodło się.  
  
  ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
### <a name="BKMK_View_the_source_code_of_a_test_method"></a> Wyświetlanie kodu źródłowego metody badawczej  
 Aby wyświetlić kod źródłowy metody testowej w edytorze programu Visual Studio, wybierz test, a następnie wybierz **Otwórz Test** w menu kontekstowym (klawiatura: F12).  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="BKMK_Group_and_filter_the_test_list"></a> Grupuj i Filtruj listę testów  
 [Grupowanie listy testów](#BKMK_Grouping_the_test_list) **&#124;** [Grupuj według cech](#BKMK_Group_by_traits) **&#124;** [wyszukiwania i filtrowania listy testów](#BKMK_Search_and_filter_the_test_list)  
  
 Eksplorator testów umożliwia grupowanie testów we wstępnie zdefiniowanych kategorii. Większość struktur testów jednostek, które działają w eksplorerze testu, można zdefiniować własne kategorie i kategorię/wartość pary do grupowania testu. Można również filtrować listę testów, za pomocą dopasowywania ciągów do właściwości testów.  
  
### <a name="BKMK_Grouping_the_test_list"></a> Grupowanie listy testów  
 Aby zmienić sposób zorganizowania testów, wybierz strzałkę w dół **Group By** przycisk ![przycisk grupy Eksploratora testów](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn") i wybierz pozycję nowe grupowania kryteria.  
  
 ![Grupuj testy według kategorii w Eksploratorze testów](../test/media/ute-groupbycategory.png "UTE_GroupByCategory")  
  
### <a name="test-explorer-groups"></a>Grupy Eksploratora testów  
  
|Grupa|Opis|  
|-----------|-----------------|  
|**Czas trwania**|Grupuje testy według czasu wykonywania: **Szybkie**, **średni**, i **powolne**.|  
|**Wynik**|Grupy testy według wyników wykonania: **Testy zakończone niepowodzeniem**, **testy pominięte**, **przeszedł testy**.|  
|**Cechy**|Grupuje testy według par kategoria/wartość, należy zdefiniować. Składnia określająca kategorie i wartości cech jest zdefiniowana przez strukturę testu jednostki.|  
|**Project**|Grupuje testy według nazw projektów.|  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
### <a name="BKMK_Group_by_traits"></a> Grupowanie według cech  
 Cecha jest zazwyczaj pary nazwa/wartość kategorii, ale może też być jednej kategorii. Cechy mogą być przypisane do metod, które są identyfikowane jako metoda testowa przez strukturę testu jednostki. Struktura testu jednostkowego może określać kategorie cech. Można dodać wartości do kategorii cech w celu zdefiniowania własnych par nazwa/wartość kategorii. Składnia określająca kategorie i wartości cech jest zdefiniowana przez strukturę testu jednostki.  
  
 **Cechy w Microsoft testowania jednostkowego dla zarządzanego kodu**  
  
 W środowisko testów jednostkowych Microsoft dla zarządzanych aplikacji, można zdefiniować nazwę cechy / wartość pary w <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atrybutu. Struktura testu zawiera również następujące cechy wstępnie zdefiniowane:  
  
|Cechy|Opis|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategoria właściciel jest zdefiniowana przez strukturę testów jednostek i wymaga podania wartości ciągu właściciela.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategoria priorytet jest zdefiniowana przez strukturę testów jednostek i wymaga podania wartości całkowitej priorytetu.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atrybut TestCategory umożliwia podanie kategorii bez wartości. Kategoria określona przez atrybut TestCategory może być również kategorii atrybut TestProperty.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atrybut TestProperty pozwala na zdefiniowanie pary kategoria/wartość cechy.|  
  
 **Cechy w Microsoft testowania jednostkowego dla języka C++**  
  
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
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
### <a name="BKMK_Search_and_filter_the_test_list"></a> Wyszukiwanie i filtrowanie listy testów  
 Filtry Test Explorer służy do ograniczenia metod testowych w swoich projektach, które możesz wyświetlać i uruchamiać.  
  
 Gdy wpisz ciąg w polu wyszukiwania Eksploratora testów i wybierz klawisz ENTER, lista testów jest filtrowany w celu wyświetlenia tylko te testy, których w pełni kwalifikowane nazwy zawierają ciąg znaków.  
  
 Aby filtrować według różnych kryteriów:  
  
1. Otwieranie listy rozwijanej z prawej strony pola wyszukiwania.  
  
2. Wybierz nowe kryterium.  
  
3. Wprowadź wartość filtru między znakami cudzysłowu.  
  
   ![Filtruje testy w Eksploratorze testów](../test/media/ute-filtertestlist.png "UTE_FilterTestList")  
  
> [!NOTE]
> Wyszukiwanie jest rozróżniana wielkość liter i jest zgodny z ciągiem określonym w dowolnej części wartości kryterium.  
  
|Kwalifikator|Opis|  
|---------------|-----------------|  
|**Cechy**|Wyszukuje zarówno w kategoriach cech, jak i wartość dopasowania. Składnia określająca kategorie i wartości cech są definiowane przez strukturę testu jednostki.|  
|**Project**|Wyszukuje dopasowania w nazwach projektów testów.|  
|**Komunikat o błędzie**|Wyszukiwanie komunikatów o błędach zdefiniowane przez użytkownika zwracanych przez nieudane potwierdzenia dopasowań.|  
|**Ścieżka pliku**|Wyszukuje dopasowania WE w pełni kwalifikowanej nazwy pliku źródłowych plików testowych.|  
|**W pełni kwalifikowana nazwa**|Wyszukuje dopasowania WE w pełni kwalifikowanej nazwy pliku testu w przestrzeni nazw, klas i metod.|  
|**Output**|Przeszukuje zdefiniowane przez użytkownika komunikaty o błędach, które są zapisywane do wyjścia standardowego (stdout) lub błędzie standardowym (stderr). Składnia określająca komunikaty wyjściowe są definiowane przez strukturę testu jednostki.|  
|**Wynik**|Wyszukuje dopasowania w nazwach kategorii Eksploratora testów: **Testy zakończone niepowodzeniem**, **testy pominięte**, **przeszedł testy**.|  
  
 Aby wykluczyć podzbiór wyników filtrowania, należy użyć następującej składni:  
  
```  
FilterName:"Criteria" -FilterName:"SubsetCriteria"  
```  
  
 Na przykład  
  
```  
FullName:"MyClass" - FullName:"PerfTest"  
```  
  
 Zwraca wszystkie testy, które zawierają "MyClass" w swojej nazwie, z wyjątkiem tych, które również zawierać "ciąg PerfTest" w nazwie.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="BKMK_Create_custom_playlists"></a> Utwórz niestandardowe listy odtwarzania  
 Można utworzyć i zapisać listę testów, które chcesz przeprowadzić lub zobaczyć jako grupę. Po wybraniu listy odtwarzania, testy na liście są wyświetlane Eksploratora testów. Test można dodać do więcej niż jednej listy odtwarzania, a wszystkie testy w projekcie są dostępne po wybraniu opcji domyślnej **wszystkie testy** listy odtwarzania.  
  
 ![Wybierz listę odtwarzania](../test/media/ute-playlist.png "UTE_Playlist")  
  
 **Aby utworzyć listę odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu kontekstowym wybierz **Dodaj do listy odtwarzania**, **NewPlaylist**. Zapisz plik o nazwie i lokalizacji, którą określasz w **Tworzenie nowej listy odtwarzania** okno dialogowe.  
  
 **Aby dodać testy do listy odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu kontekstowym wybierz **Dodaj do listy odtwarzania**, a następnie wybierz listę odtwarzania, który chcesz dodać testy.  
  
 **Aby otworzyć listę odtwarzania**, wybierz opcję Testuj, lista odtwarzania z menu programu Visual Studio i wybierz opcję z listy niedawno używanych list odtwarzania lub wybierz polecenie Otwórz listę, aby określić nazwę i lokalizację listy odtwarzania.  
  
 Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małych](../test/media/ute-parallelicon-small.png "małych UTE_parallelicon") Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="BKMK_Debug_and_analyze_unit_tests"></a> Debugowanie i analizowanie testów jednostkowych  
 [Debuguj testy jednostkowe](#BKMK_Debug_unit_tests) **&#124;** [diagnozowanie problemów z wydajnością metoda testu](#BKMK_Diagnose_test_method_performance_issues) **&#124;** [Analizuj pokrycie kodu testu jednostkowego](#BKMK_Analyzeunit_test_code_coverage)  
  
### <a name="BKMK_Debug_unit_tests"></a> Debuguj testy jednostkowe  
 Eksplorator testów umożliwia uruchamianie sesji debugowania dla testów. Krokowe wykonywanie kodu za pomocą debugera programu Visual Studio bezproblemowe przejście i z powrotem między testami jednostek a testowanego projektu. Aby rozpocząć debugowanie:  
  
1. W edytorze programu Visual Studio Ustaw punkt przerwania w metodach testów, które chcesz debugować.  
  
   > [!NOTE]
   > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkich metodach testowych, które chcesz debugować.  
  
2. W Eksploratorze testów Wybierz metody badania, a następnie wybierz **Debuguj wybrane testy** w menu kontekstowym.  
  
   Aby uzyskać więcej informacji dotyczących debugera, zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
### <a name="BKMK_Diagnose_test_method_performance_issues"></a> Diagnozowanie problemów z wydajnością metoda testu  
 Aby zdiagnozować, dlaczego metoda testowa zajmuje zbyt dużo czasu, należy wybrać metodę w Eksploratorze testów, a następnie wybierz profil z menu kontekstowego. Zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).  
  
### <a name="BKMK_Analyzeunit_test_code_coverage"></a> Analizuj pokrycie kodu testu jednostkowego  
  
> [!NOTE]
> Pokrycie kodu testu jednostkowego jest dostępna tylko w programie Visual Studio Enterprise.  
  
 Można określić liczbę kodów produktu, który jest aktualnie testowany przez nasze testy jednostkowe za pomocą narzędzia pokrycia kodu programu Visual Studio. Można uruchomić pokrycie kodów w wybranych testach albo we wszystkich testach w rozwiązaniu.  
  
 Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu:  
  
1. Wybierz **testy** menu programu Visual Studio, a następnie wybierz **analiza pokrycia kodu**.  
  
2. Wybierz jedną z następujących poleceń z podmenu:  
  
   - **Wybrane testy** uruchamia metody testowe wybrane w Eksploratorze testów.  
  
   - **Wszystkie testy** uruchamia metody testowe w rozwiązaniu.  
  
   Okno wyniki pokrycia kodu Wyświetla procent bloków kodu produktu, które były wykonywane przez wiersz, funkcji, klasy, przestrzeni nazw i moduł.  
  
   Aby uzyskać więcej informacji, zobacz [przy użyciu pokrycia kodu, aby określić, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="BKMK_External_resources"></a> Zasoby zewnętrzne  
  
### <a name="BKMK_Guidance"></a> Wskazówki dotyczące  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie jednostek kodu](../test/unit-test-your-code.md)   
 [Uruchamianie testu jednostkowego jako procesu 64-bitowego](../test/run-a-unit-test-as-a-64-bit-process.md)
