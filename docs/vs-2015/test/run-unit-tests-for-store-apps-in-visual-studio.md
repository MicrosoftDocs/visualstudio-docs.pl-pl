---
title: Uruchamianie testów jednostkowych dla aplikacji Store
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 14
author: alexhomer1
ms.author: gewarren
manager: robinr
ms.openlocfilehash: 9496a41d3eadd91112579b54250a6022bd6484e5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050924"
---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Uruchamianie testów jednostkowych dla aplikacji Store w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób uruchamiania testów jednostkowych za pomocą Eksploratora testów w programie Microsoft Visual Studio

> [!NOTE]
>  W tematach w tej sekcji opisano funkcje programu Visual Studio Express for Windows 8. Visual Studio Community, Professional i Enterprise zapewniają dodatkowe funkcje testów jednostkowych.
>
> - Użyj dowolnego środowiska testów jednostkowych innych firm lub otwartego źródła został utworzony karty dodatku dla programu Microsoft Test Explorer. Można również analizować i wyświetlanie informacji o pokryciu kodu dla swoich testów.
>   -   Uruchom testy po każdej kompilacji. Można również użyć Microsoft Fakes framework izolacji dla kodu zarządzanego skoncentrować się testy na własny kod, zastępując kod testu systemu i innych firm funkcjonalność.
>
>   Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md) w bibliotece MSDN.

##  <a name="BKMK_In_this_topic"></a> W tym temacie
 [Framework testów jednostkowych i projekty testowe](#BKMK_Unit_test_frameworks_and_test_projects)

 [Uruchamianie testów w Eksploratorze testów](#BKMK_Running_tests_in_Test_Explorer)

- [Uruchamianie testów](#BKMK_Running_tests)

  [Wyświetlanie wyników testu](#BKMK_Viewing_test_results)

- [Wyświetlanie Szczegóły testu](#BKMK_Viewing_test_details)

- [Wyświetlanie kodu źródłowego metody badawczej](#BKMK_Viewing_the_source_code_of_a_test_method)

  [Organizowanie listy testów](#BKMK_Organizing_the_test_list)

- [Grupowanie testów](#BKMK_Grouping_tests)

- [Wyszukiwanie i filtrowanie listy testów](#BKMK_Searching_and_filtering_the_test_list)

  [Debugowanie testów jednostkowych](#BKMK_Debugging_unit_tests)

##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Framework testów jednostkowych i projekty testowe
 Visual Studio Express for Windows Store Apps zawiera struktur testów jednostek pochodzących od firmy Microsoft do zarządzanego i macierzystego kodu C++. Eksplorator testów może uruchamiać testy z wielu projektów testów w rozwiązaniu i z klas testowych, które są częścią projektów kodu produkcyjnego. Projekty testowe może być dowolną kombinacją języka Visual c++ lub środowiska wykonywania testów jednostkowych programu Visual C# i Visual Basic. Jeśli testowany kod jest przeznaczony dla .NET Framework, Projekt testowy można napisane w dowolnym języku .NET Framework, bez względu na język docelowy kodu. Natywnych projektów kodu C/C++ muszą być przetestowany przy użyciu struktury testowej jednostki C++.

##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Uruchamianie testów w Eksploratorze testów
 Podczas tworzenia projektu testowego, testy są wyświetlane w Eksploratorze testów. Eksplorator testów nie jest widoczny, wybierz opcję **testu** menu programu Visual Studio, wybierz **Windows**, a następnie wybierz **Eksplorator testów**.

 ![Eksplorator testów jednostkowych](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach domyślnych **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i  **Esty nieuruchamiane**. Można zmienić sposobu Eksplorator testów grupuje testy.

 Można przeprowadzić wiele prac wyszukiwania, organizowanie i Uruchamianie testów na pasku narzędzi Eksploratora testów.

 ![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute-toolbar.png "UTE_ToolBar")

###  <a name="BKMK_Running_tests"></a> Uruchamianie testów
 Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które można wybrać. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz **Uruchom wszystkie**.

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz **uruchamianie...**  a następnie wybierz grupę, w menu.

- Zaznacz poszczególne testy, które chcesz uruchomić, otwórz menu skrótów dla jednego z zaznaczonych testów, a następnie wybierz **Uruchom wybrane testy**.

  Pasek Powodzenie/niepowodzenie u góry okna Eksploratora testów jest animowany podczas działania testu. Po zakończeniu przebiegu testowego pasek Powodzenie/niepowodzenie zmienia kolor na zielony, jeśli wszystkie testy przekazane lub na czerwony, jeśli dowolny test nie powiodła się.

##  <a name="BKMK_Viewing_test_results"></a> Wyświetlanie wyników testu
 Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i **nie uruchomione Testy**. Uruchom Podsumowanie testu w dolnej części Eksploratora testów jest wyświetlane w okienku szczegółów.

###  <a name="BKMK_Viewing_test_details"></a> Wyświetlanie Szczegóły testu
 Aby wyświetlić szczegółowe informacje o poszczególnych testach, wybierz test.

 W okienku szczegółów są wyświetlane następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Czas trwania metody testowej.

  Jeśli test zakończy się niepowodzeniem, są wyświetlane również w okienku szczegółów:

- Komunikat zwracany przez strukturę testu jednostki dla testu.

- Ślad stosu w czasie testu nie powiodło się.

###  <a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Wyświetlanie kodu źródłowego metody badawczej
 Aby wyświetlić kod źródłowy metody testowej w edytorze programu Visual Studio, wybierz test, a następnie wybierz **Otwórz Test** w menu kontekstowym (klawiatura: F12).

##  <a name="BKMK_Organizing_the_test_list"></a> Organizowanie listy testów

###  <a name="BKMK_Grouping_tests"></a> Grupowanie testów
 Domyślnie program Test Explorer wyświetla testów jako węzły podrzędne **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i **testy nieuruchamiane**.

|||
|-|-|
|![Przycisk grupy Eksploratora testów](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Do grupowania testów przez czas potrzebny do wykonania je, otwórz **Group By** i wybierz polecenie **czas trwania**. Wybierz **wynik testu** Aby przełączyć się do oryginalnego grupowania.|

###  <a name="BKMK_Searching_and_filtering_the_test_list"></a> Wyszukiwanie i filtrowanie listy testów
 Jeśli masz dużą liczbę testów, można wpisać w polu wyszukiwania Eksploratora testów, aby filtrować listę według określonego ciągu. Filtr można ograniczyć do określonych typów ciągów, wybierając z listy filtrów przed wprowadź ciąg wyszukiwania.

 ![Wyszukaj filtr kategorii](../test/media/ute-searchfilter.png "UTE_SearchFilter")

##  <a name="BKMK_Debugging_unit_tests"></a> Debugowanie testów jednostkowych
 Eksplorator testów umożliwia uruchamianie sesji debugowania dla testów. Krokowe wykonywanie kodu za pomocą debugera programu Visual Studio bezproblemowe przejście i z powrotem między testami jednostek a testowanego projektu. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w metodach testów, które chcesz debugować.

   > [!NOTE]
   >  Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkich metodach testowych, które chcesz debugować.

2. W Eksploratorze testów Wybierz metody badania, a następnie wybierz **Debuguj wybrane testy** w menu skrótów.

   Aby uzyskać więcej informacji dotyczących debugera, zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).
