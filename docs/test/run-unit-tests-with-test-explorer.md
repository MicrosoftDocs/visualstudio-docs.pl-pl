---
title: Uruchamianie i debugowanie testów jednostkowych w Eksploratorze testów
description: Dowiedz się, jak uruchomić testy z użyciem Eksplorator testów w programie Visual Studio. W tym temacie opisano, jak włączyć automatyczne testy po kompilacji, wyświetlić wyniki testów, grupy i filtrowanie listy testów, tworzenie listy odtwarzania, Debuguj testy i skróty testu.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa24dedd776a0866d5de23fbacd31b32c2d55145
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55956548"
---
# <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów

Użyj **Eksploratora testów** do uruchamiania testów jednostkowych z Visual Studio lub projektów testów jednostkowych innych firm. Można również użyć **Eksploratora testów** do grupowania testów w kategorie, filtrowanie listy testów, tworzenie, zapisywanie i uruchamianie list odtwarzania testów. Możliwe jest debugowanie testów i analizowanie testów wydajność i pokrycie kodu.

Program Visual Studio obejmuje struktur testowania jednostek pochodzących od firmy Microsoft dla kodu zarządzanego i natywnego. Jednak **Eksploratora testów** można również uruchomić dowolnej jednostki struktury testów, które ma zaimplementowany adapter programu Test Explorer. Aby uzyskać więcej informacji na temat Instalowanie platform testów jednostkowych innych firm, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

**Eksplorator testów** można uruchomić testy z wielu projektów testów w rozwiązaniu i z klas testowych, które są częścią projektów kodu produkcyjnego. Projekty testów mogą używać innych struktur testów jednostek. Jeśli testowany kod jest przeznaczony dla .NET Framework, Projekt testowy można napisać tak w dowolnym języku, który również jest przeznaczony dla .NET Framework, bez względu na język docelowy kodu. Natywnych projektów kodu C/C++ muszą być przetestowany przy użyciu struktury testowej jednostki C++. Aby uzyskać więcej informacji, zobacz [pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Uruchom testy w Eksploratorze testów

Podczas tworzenia projektu testowego, testy są wyświetlane w Eksploratorze testów. Eksplorator testów nie jest widoczny, wybierz opcję **testu** menu programu Visual Studio, wybierz **Windows**, a następnie wybierz **Eksplorator testów**.

![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)

Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach domyślnych **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i  **Esty nieuruchamiane**. Można zmienić sposobu Eksplorator testów grupuje testy.

Można przeprowadzić wiele prac wyszukiwania, organizowanie i Uruchamianie testów z **Eksplorator testów** paska narzędzi.

![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute_toolbar.png)

### <a name="run-tests"></a>Uruchom testy

Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które można wybrać. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz **Uruchom wszystkie**.

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz **Uruchom** a następnie wybierz grupę, w menu.

- Zaznacz poszczególne testy, które chcesz uruchomić, otwórz menu kontekstowe dla jednego z zaznaczonych testów, a następnie wybierz **Uruchom wybrane testy**.

- Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małe](../test/media/ute_parallelicon-small.png) Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

**Pasek Powodzenie/niepowodzenie** w górnej części **Eksplorator testów** okna jest animowany podczas uruchamiania testów. Po zakończeniu przebiegu testu **pasek Powodzenie/niepowodzenie** zmieni kolor na zielony, jeśli wszystkie testy Zakończono powodzeniem lub na czerwony, jeśli dowolny test nie powiodła się.

### <a name="run-tests-after-every-build"></a>Uruchamianie testów po każdej kompilacji

|Przycisk|Opis|
|-|-|
|![Uruchom po kompilacji](../test/media/ute_runafterbuild_btn.png)|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz **testu** w menu standardowym, a następnie wybierz **Uruchom testy po kompilacji** na **Eksplorator testów** paska narzędzi.|

> [!NOTE]
> Uruchamianie testów jednostek po każdej kompilacji wymaga programu Visual Studio Enterprise edition.

## <a name="view-test-results"></a>Wyświetlanie wyników testu

Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **testy pominięte** i **nie uruchomione Testy**. Uruchom Podsumowanie testu w dolnej części Eksploratora testów jest wyświetlane w okienku szczegółów.

### <a name="view-test-details"></a>Pokaż szczegóły testu

Aby wyświetlić szczegółowe informacje o poszczególnych testach, wybierz test.

![Szczegóły wykonywania testu](../test/media/ute_testdetails.png)

W okienku szczegółów są wyświetlane następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Czas trwania metody testowej.

Jeśli test zakończy się niepowodzeniem, są wyświetlane również w okienku szczegółów:

- Komunikat zwracany przez strukturę testu jednostki dla testu.

- Ślad stosu w czasie testu nie powiodło się.

### <a name="view-the-source-code-of-a-test-method"></a>Wyświetlanie kodu źródłowego metody badawczej

Aby wyświetlić kod źródłowy metody testowej w edytorze programu Visual Studio, wybierz test, a następnie wybierz **Otwórz Test** w menu kliknij prawym przyciskiem myszy (klawiatury: **F12**).

## <a name="group-and-filter-the-test-list"></a>Grupuj i Filtruj listę testów

Eksplorator testów umożliwia grupowanie testów we wstępnie zdefiniowanych kategorii. Większość struktur testów jednostek, które działają w eksplorerze testu, można zdefiniować własne kategorie i kategorię/wartość pary do grupowania testu. Można również filtrować listę testów, za pomocą dopasowywania ciągów do właściwości testów.

### <a name="group-tests-in-the-test-list"></a>Grupa testów na liście testów

Aby zmienić sposób zorganizowania testów, wybierz strzałkę w dół **Group By** przycisk ![przycisk grupy Eksploratora testów](../test/media/ute_groupby_btn.png) i wybierz nowe kryteria grupowania.

![Grupa testów według kategorii w Eksploratorze testów](../test/media/ute_groupbycategory.png)

### <a name="test-explorer-groups"></a>Grupy Eksploratora testów

|Grupa|Opis|
|-|-----------------|
|**Czas trwania**|Grupuje testy według czasu wykonywania: **Szybkie**, **średni**, i **powolne**.|
|**Wynik**|Grupy testy według wyników wykonania: **Testy zakończone niepowodzeniem**, **testy pominięte**, **przeszedł testy**.|
|**Cechy**|Grupuje testy według par kategoria/wartość, należy zdefiniować. Składnia określająca kategorie i wartości cech jest zdefiniowana przez strukturę testu jednostki.|
|**Project**|Grupuje testy według nazw projektów.|

### <a name="group-by-traits"></a>Grupowanie według cech

Cecha jest zazwyczaj pary nazwa/wartość kategorii, ale może też być jednej kategorii. Cechy mogą być przypisane do metod, które są identyfikowane jako metoda testowa przez strukturę testu jednostki. Struktura testu jednostkowego może określać kategorie cech. Można dodać wartości do kategorii cech w celu zdefiniowania własnych par nazwa/wartość kategorii. Składnia określająca kategorie i wartości cech jest zdefiniowana przez strukturę testu jednostki.

**Cechy w Microsoft testowania jednostkowego dla zarządzanego kodu**

W środowisko testów jednostkowych Microsoft dla zarządzanych aplikacji, można zdefiniować nazwę cechy / wartość pary w <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atrybutu. Struktura testu zawiera również następujące cechy wstępnie zdefiniowane:

|Cechy|Opis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategoria właściciel jest zdefiniowana przez strukturę testów jednostek i wymaga podania wartości ciągu właściciela.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategoria priorytet jest zdefiniowana przez strukturę testów jednostek i wymaga podania wartości całkowitej priorytetu.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atrybut TestCategory umożliwia podanie kategorii bez wartości. Kategoria określona przez atrybut TestCategory może być również kategorii atrybut TestProperty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atrybut TestProperty pozwala na zdefiniowanie pary kategoria/wartość cechy.|

**Cechy w Microsoft testowania jednostkowego dla języka C++**

 Zobacz [sposób używania szablonu testów jednostkowych firmy Microsoft dla języka C++](how-to-use-microsoft-test-framework-for-cpp.md).

### <a name="search-and-filter-the-test-list"></a>Wyszukiwanie i filtrowanie listy testów

Filtry Test Explorer służy do ograniczenia metod testowych w swoich projektach, które możesz wyświetlać i uruchamiać.

Po wpisaniu ciągu w **Eksploratora testów** pole wyszukiwania i wybierz polecenie **Enter**, listy testów jest filtrowany w celu wyświetlenia tylko te testy, których w pełni kwalifikowane nazwy zawierają ciąg znaków.

Aby filtrować według różnych kryteriów:

1. Otwieranie listy rozwijanej z prawej strony pola wyszukiwania.

2. Wybierz nowe kryterium.

3. Wprowadź wartość filtru między znakami cudzysłowu.

![Filtruje testy w Eksploratorze testów](../test/media/ute_filtertestlist.png)

> [!NOTE]
> Wyszukiwanie jest rozróżniana wielkość liter i jest zgodny z ciągiem określonym w dowolnej części wartości kryterium.

|Kwalifikator|Opis|
|-|-----------------|
|**Cechy**|Wyszukuje zarówno w kategoriach cech, jak i wartość dopasowania. Składnia określająca kategorie i wartości cech są definiowane przez strukturę testu jednostki.|
|**Project**|Wyszukuje dopasowania w nazwach projektów testów.|
|**Komunikat o błędzie**|Wyszukiwanie komunikatów o błędach zdefiniowane przez użytkownika zwracanych przez nieudane potwierdzenia dopasowań.|
|**Ścieżka pliku**|Wyszukuje dopasowania WE w pełni kwalifikowanej nazwy pliku źródłowych plików testowych.|
|**W pełni kwalifikowana nazwa**|Wyszukuje dopasowania WE w pełni kwalifikowanej nazwy pliku testu w przestrzeni nazw, klas i metod.|
|**Output**|Przeszukuje zdefiniowane przez użytkownika komunikaty o błędach, które są zapisywane do wyjścia standardowego (stdout) lub błędzie standardowym (stderr). Składnia określająca komunikaty wyjściowe są definiowane przez strukturę testu jednostki.|
|**Wynik**|Wyszukuje dopasowania w nazwach kategorii Eksploratora testów: **Testy zakończone niepowodzeniem**, **testy pominięte**, **przeszedł testy**.|

Aby wykluczyć podzbiór wyników filtrowania, należy użyć następującej składni:

```cpp
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Na przykład `FullName:"MyClass" - FullName:"PerfTest"` zwraca wszystkie testy, które zawierają "MyClass" w nazwie, chyba że testy, które również zawierać "ciąg PerfTest" w nazwie.

## <a name="create-custom-playlists"></a>Utwórz niestandardowe listy odtwarzania

Można utworzyć i zapisać listę testów, które chcesz przeprowadzić lub zobaczyć jako grupę. Po wybraniu listy odtwarzania, testy na liście są wyświetlane w Eksploratorze testów. Test można dodać do więcej niż jednej listy odtwarzania, a wszystkie testy w projekcie są dostępne po wybraniu opcji domyślnej **wszystkie testy** listy odtwarzania.

![Wybierz listę odtwarzania](../test/media/ute_playlist.png)

**Aby utworzyć listę odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu kliknij prawym przyciskiem myszy, wybierz **Dodaj do listy odtwarzania** > **NewPlaylist**. Zapisz plik o nazwie i lokalizacji, którą określasz w **Tworzenie nowej listy odtwarzania** okno dialogowe.

**Aby dodać testy do listy odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu kliknij prawym przyciskiem myszy, wybierz **Dodaj do listy odtwarzania**, a następnie wybierz listę odtwarzania, który chcesz dodać testy.

**Aby otworzyć listę odtwarzania**, wybierz **testu** > **listy odtwarzania** z menu programu Visual Studio, a następnie wybierz z listy niedawno używanych list odtwarzania lub wybierz **Otwórz Lista odtwarzania** Aby określić nazwę i lokalizację listy odtwarzania.

Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małe](../test/media/ute_parallelicon-small.png) Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

## <a name="debug-and-analyze-unit-tests"></a>Debugowanie i analizowanie testów jednostkowych

Eksplorator testów umożliwia uruchamianie sesji debugowania dla testów. Krokowe wykonywanie kodu za pomocą debugera programu Visual Studio bezproblemowe przejście i z powrotem między testami jednostek a testowanego projektu. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w metodach testów, które chcesz debugować.

    > [!NOTE]
    > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkich metodach testowych, które chcesz debugować.

2. W Eksploratorze testów Wybierz metody badania, a następnie wybierz **Debuguj wybrane testy** w menu kliknij prawym przyciskiem myszy.

   Aby uzyskać więcej informacji dotyczących debugera, zobacz [debugowania w programie Visual Studio](../debugger/debugger-feature-tour.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnozowanie problemów z wydajnością metoda testu

Aby zdiagnozować, dlaczego metoda testowa zajmuje zbyt dużo czasu, wybierz metodę w Eksploratorze testów, a następnie wybierz **profilu** w menu kliknij prawym przyciskiem myszy. Zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Analizuj pokrycie kodu testu jednostkowego

Można określić liczbę kodów produktu, który jest aktualnie testowany przez nasze testy jednostkowe za pomocą narzędzia pokrycia kodu programu Visual Studio. Można uruchomić pokrycie kodów w wybranych testach albo we wszystkich testach w rozwiązaniu.

Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu:

1. Wybierz **testy** menu programu Visual Studio, a następnie wybierz **analiza pokrycia kodu**.

2. Wybierz jedną z następujących poleceń z podmenu:

    - **Wybrane testy** uruchamia metody testowe wybrane w Eksploratorze testów.

    - **Wszystkie testy** uruchamia metody testowe w rozwiązaniu.

**Wyniki pokrycia kodu** okno wyświetla procent bloków kodu produktu, które były wykonywane przez wiersz, funkcji, klasy, przestrzeni nazw i moduł.

Aby uzyskać więcej informacji, zobacz [użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Skróty testu

Testy mogą być uruchamiane z **Eksploratora testów**, klikając prawym przyciskiem myszy w edytorze kodu dla testu i wybierając polecenie **Uruchom test**, lub przy użyciu domyślnej [skróty programu Test Explorer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) w Program Visual Studio. Niektóre skróty są oparte na kontekście. Oznacza to, uruchomić lub debugować testy, w oparciu o którym kursor w edytorze kodu. Jeśli kursor znajduje się wewnątrz metody testowej, następnie, metoda przebiegów testów. Jeśli kursor znajduje się na poziomie klasy, a następnie uruchom wszystkie testy w tej klasie. Jest taka sama dla danego poziomu przestrzeni nazw.

|Częste odzyskiwanie pamięci poleceń| Skróty klawiaturowe|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl**+**R**, **Ctrl**+**T**|
|TestExplorer.RunAllTestsInContext|**Ctrl**+**R**, **T**|

> [!NOTE]
> Nie można uruchomić testu w klasie abstrakcyjnej, ponieważ testy są tylko zdefiniowane w klasy abstrakcyjne i nie jest uruchomiony. Aby uruchomić testy z klasy abstrakcyjne, należy utworzyć klasę, która pochodzi z klasy abstrakcyjnej.

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)
- [Uruchamianie testu jednostkowego jako procesu 64-bitowego](../test/run-a-unit-test-as-a-64-bit-process.md)
