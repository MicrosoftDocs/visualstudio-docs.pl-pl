---
title: Uruchamianie testów jednostkowych dla aplikacji ze sklepu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 14
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b70e3a24cd4cb05dc1a28ff855498496f5665ddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542860"
---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Uruchamianie testów jednostkowych dla aplikacji ze sklepu w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób uruchamiania testów jednostkowych za pomocą Eksploratora testów w Microsoft Visual Studio

> [!NOTE]
> W tematach w tej sekcji opisano funkcjonalność Visual Studio Express dla systemu Windows 8. Program Visual Studio Community, Enterprise i Professional udostępnia dodatkowe funkcje do testowania jednostkowego.
>
> - Użyj platformy testów jednostkowych innej firmy lub Open Source, która utworzyła adapter dodatku dla programu Microsoft Test Explorer. Możesz również analizować i wyświetlać informacje o pokryciu kodu dla testów.
>   - Uruchom testy po każdej kompilacji. Można również użyć sztucznych produktów firmy Microsoft, struktury izolacji dla kodu zarządzanego, aby skoncentrować testy na własnym kodzie poprzez podstawianie kodu testowego dla systemu i funkcji innych firm.
>
>   Aby uzyskać więcej informacji, zobacz [testowanie jednostkowe kodu](../test/unit-test-your-code.md) w bibliotece MSDN.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 [Struktury testów jednostkowych i projekty testowe](#BKMK_Unit_test_frameworks_and_test_projects)

 [Uruchamianie testów w Eksploratorze testów](#BKMK_Running_tests_in_Test_Explorer)

- [Uruchamianie testów](#BKMK_Running_tests)

  [Wyświetlanie wyników testu](#BKMK_Viewing_test_results)

- [Wyświetlanie szczegółów testu](#BKMK_Viewing_test_details)

- [Wyświetlanie kodu źródłowego metody testowej](#BKMK_Viewing_the_source_code_of_a_test_method)

  [Organizowanie listy testów](#BKMK_Organizing_the_test_list)

- [Grupowanie testów](#BKMK_Grouping_tests)

- [Wyszukiwanie i filtrowanie listy testów](#BKMK_Searching_and_filtering_the_test_list)

  [Debugowanie testów jednostkowych](#BKMK_Debugging_unit_tests)

## <a name="unit-test-frameworks-and-test-projects"></a><a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Struktury testów jednostkowych i projekty testowe
 Visual Studio Express dla aplikacji ze sklepu Windows obejmuje platformy testów jednostkowych firmy Microsoft dla kodu zarządzanego i natywnego języka C++. Eksplorator testów może uruchamiać testy z wielu projektów testowych w rozwiązaniu i z klas testowych, które są częścią projektów kodu produkcyjnego. Projekty testowe mogą być dowolną kombinacją Visual C++ lub struktury testów jednostkowych w języku Visual C# i Visual Basic. Gdy testowy kod jest zapisywana dla .NET Framework, projekt testowy można napisać w dowolnym języku .NET Framework, niezależnie od języka kodu docelowego. Natywne projekty kodu C/C++ muszą być testowane przy użyciu struktury testów jednostkowych języka C++.

## <a name="running-tests-in-test-explorer"></a><a name="BKMK_Running_tests_in_Test_Explorer"></a> Uruchamianie testów w Eksploratorze testów
 Podczas kompilowania projektu testowego, testy są wyświetlane w Eksploratorze testów. Jeśli Eksplorator testów nie jest widoczny, wybierz **Testuj** w menu programu Visual Studio, wybierz pozycję **Windows**, a następnie wybierz **Eksplorator testów**.

 ![Eksplorator testów jednostkowych](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Podczas uruchamiania, zapisywania i ponownego uruchamiania testów, Eksplorator testów wyświetla wyniki w domyślnych grupach **testów zakończonych niepowodzeniem**, testy **zakończone pomyślnie**, **testy pominięte** i **testy nie są uruchamiane**. Można zmienić sposób, w jaki Eksplorator testów grupuje testy.

 Na pasku narzędzi Eksploratora testów można wykonywać wiele zadań znajdowania, organizowania i uruchamiania testów.

 ![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute-toolbar.png "UTE_ToolBar")

### <a name="running-tests"></a><a name="BKMK_Running_tests"></a> Uruchamianie testów
 Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które zostały wybrane. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz pozycję **Uruchom wszystkie**.

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz pozycję **Uruchom...** , a następnie wybierz grupę w menu.

- Wybierz pojedyncze testy, które chcesz uruchomić, otwórz menu skrótów dla wybranego testu, a następnie wybierz polecenie **Uruchom wybrane testy**.

  Pasek przekazywania/niepowodzenia w górnej części okna Eksploratora testów jest animowany w miarę przebiegu testów. Po zakończeniu przebiegu testu pasek powodzenia/niepowodzenia zmieni kolor na zielony, jeśli wszystkie testy zakończyły się powodzeniem lub zmienią kolor na czerwony, jeśli którykolwiek z testów nie powiódł się.

## <a name="viewing-test-results"></a><a name="BKMK_Viewing_test_results"></a> Wyświetlanie wyników testu
 Podczas uruchamiania, zapisywania i ponownego uruchamiania testów, Eksplorator testów wyświetla wyniki w grupach **testów zakończonych niepowodzeniem**, testy **zakończone pomyślnie**, testy **pominięte** i **testy nie są uruchamiane**. W okienku szczegółów u dołu Eksploratora testów jest wyświetlane podsumowanie przebiegu testu.

### <a name="viewing-test-details"></a><a name="BKMK_Viewing_test_details"></a> Wyświetlanie szczegółów testu
 Aby wyświetlić szczegóły poszczególnych testów, wybierz test.

 W okienku Szczegóły testu są wyświetlane następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Czas, który upłynął do uruchomienia metody testowej.

  Jeśli test nie powiedzie się, w okienku szczegółów zostanie również wyświetlony komunikat:

- Komunikat zwrócony przez strukturę testów jednostkowych dla testu.

- Ślad stosu w czasie testu nie powiódł się.

### <a name="viewing-the-source-code-of-a-test-method"></a><a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Wyświetlanie kodu źródłowego metody testowej
 Aby wyświetlić kod źródłowy dla metody testowej w edytorze programu Visual Studio, wybierz test, a następnie wybierz **Otwórz test** w menu skrótów (klawiatura: F12).

## <a name="organizing-the-test-list"></a><a name="BKMK_Organizing_the_test_list"></a> Organizowanie listy testów

### <a name="grouping-tests"></a><a name="BKMK_Grouping_tests"></a> Grupowanie testów
 Domyślnie Eksplorator testów wyświetla testy jako węzły podrzędne **testów zakończonych niepowodzeniem**, **testy zakończone pomyślnie**, **testy pominięte** i testy **nie są uruchamiane**.

|Obraz|Opis|
|-|-|
|![Przycisk grupy Eksploratora testów](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Aby zgrupować testy według czasu potrzebnego na ich wykonanie, Otwórz listę **Grupuj według** i wybierz pozycję **czas trwania**. Wybierz pozycję **wynik testu** , aby przełączyć się do oryginalnego grupowania.|

### <a name="searching-and-filtering-the-test-list"></a><a name="BKMK_Searching_and_filtering_the_test_list"></a> Wyszukiwanie i filtrowanie listy testów
 Jeśli masz dużą liczbę testów, możesz wpisać w polu wyszukiwania Eksploratora testów, aby odfiltrować listę według określonego ciągu. Można ograniczyć filtr do określonych typów ciągów, wybierając z listy filtrów przed wprowadzeniem ciągu wyszukiwania.

 ![Kategorie filtrów wyszukiwania](../test/media/ute-searchfilter.png "UTE_SearchFilter")

## <a name="debugging-unit-tests"></a><a name="BKMK_Debugging_unit_tests"></a> Debugowanie testów jednostkowych
 Możesz użyć Eksploratora testów, aby rozpocząć sesję debugowania dla testów. Przechodzenie przez kod za pomocą debugera programu Visual Studio bezproblemowo przeprowadzi Cię z powrotem między testami jednostkowymi i badanym projektem. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w co najmniej jednej metodzie testowej, która ma być debugowana.

   > [!NOTE]
   > Ponieważ metody testowe mogą być uruchamiane w dowolnej kolejności, należy ustawić punkty przerwania we wszystkich metodach testowych, które mają być debugowane.

2. W Eksploratorze testów wybierz metody testowe, a następnie wybierz **Debuguj wybrane testy** w menu skrótów.

   Aby uzyskać więcej informacji o debugerze, zobacz [debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md).
