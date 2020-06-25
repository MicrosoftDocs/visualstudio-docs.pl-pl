---
title: Uruchamianie i debugowanie testów jednostkowych za pomocą Eksploratora testów
description: Dowiedz się, jak uruchamiać testy za pomocą Eksploratora testów w programie Visual Studio. W tym temacie opisano sposób włączania automatycznych przebiegów testów po kompilacji, wyświetlania wyników testów, grupowania i filtrowania listy testów, tworzenia list odtwarzania, debugowania testów i używania skrótów testowych.
ms.date: 07/29/2019
ms.topic: how-to
f1_keywords:
- vs.unittesting.testexplorer.overview
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de463fbc941273bed9b949958b9463be6ea1fa3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285637"
---
# <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów

Użyj Eksploratora testów do uruchomienia testów jednostkowych z programu Visual Studio lub projektów testów jednostkowych innych firm. Za pomocą Eksploratora testów można także grupować testy w kategorie, filtrować listę testów oraz tworzyć, zapisywać i uruchamiać listy odtwarzania testów. Można debugować testy i analizować wydajność testów i pokrycie kodu.

Program Visual Studio zawiera struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego i natywnego. Jednak w Eksploratorze testów można także uruchomić dowolną strukturę testów jednostkowych, która wdrożyła adapter programu Test Explorer. Aby uzyskać więcej informacji na temat instalowania platform testów jednostkowych innych firm, zobacz [Instalowanie platform testów jednostkowych](../test/install-third-party-unit-test-frameworks.md) innych firm

**Eksplorator testów** może uruchamiać testy z wielu projektów testowych w rozwiązaniu i z klas testowych, które są częścią projektów kodu produkcyjnego. Projekty testowe mogą korzystać z różnych platform testów jednostkowych. Gdy testowy kod jest zapisywana dla platformy .NET, projekt testowy można napisać w dowolnym języku, który jest również przeznaczony dla platformy .NET, niezależnie od języka kodu docelowego. Natywne projekty kodu C/C++ muszą być testowane przy użyciu struktury testów jednostkowych języka C++. Aby uzyskać więcej informacji, zobacz [pisać testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Uruchom testy w Eksploratorze testów

Podczas [kompilowania projektu testowego](../test/getting-started-with-unit-testing.md), testy są wyświetlane w Eksploratorze testów. Jeśli Eksplorator testów nie jest widoczny, wybierz **Testuj** w menu programu Visual Studio, wybierz pozycję **Windows**, a następnie wybierz **Eksplorator testów**.

::: moniker range="vs-2017"
![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Eksplorator testów](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Podczas uruchamiania, zapisywania i ponownego uruchamiania testów, Eksplorator testów wyświetla wyniki w domyślnych grupach **testów zakończonych niepowodzeniem**, testy **zakończone pomyślnie**, **testy pominięte** i **testy nie są uruchamiane**. Można zmienić sposób, w jaki Eksplorator testów grupuje testy.
::: moniker-end
::: moniker range=">=vs-2019"
Podczas uruchamiania, zapisywania i ponownego uruchamiania testów, Eksplorator testów wyświetla wyniki w domyślnym grupowaniu **projektu**, **przestrzeni nazw**i **klasy**. Można zmienić sposób, w jaki Eksplorator testów grupuje testy.
::: moniker-end

Na pasku narzędzi **Eksploratora testów** można wykonywać wiele prac znajdowania, organizowania i uruchamiania testów.

::: moniker range="vs-2017"
![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Uruchom testy

::: moniker range="vs-2017"
Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które zostały wybrane. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz pozycję **Uruchom wszystkie**.

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz pozycję **Uruchom** , a następnie wybierz grupę w menu.

- Wybierz pojedyncze testy, które chcesz uruchomić, otwórz menu dostępne po kliknięciu prawym przyciskiem myszy, a następnie wybierz polecenie **Uruchom wybrane testy**.

- Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, należy włączyć równoległe wykonywanie testów przy użyciu ![Wykonaj&#95;parallelicon&#45;mały](../test/media/ute_parallelicon-small.png) przycisk przełączania na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.

**Pasek przekazywania/niepowodzenia** w górnej części okna **Eksploratora testów** jest animowany w miarę przebiegu testów. Po zakończeniu przebiegu testu **pasek powodzenia/niepowodzenia** zmieni kolor na zielony, jeśli wszystkie testy zakończyły się powodzeniem lub zmienią kolor na czerwony, jeśli którykolwiek z testów nie powiódł się.
::: moniker-end
::: moniker range=">=vs-2019"
Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które zostały wybrane. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz ikonę **Uruchom wszystko** .

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz ikonę Run ( **Uruchom** ), a następnie wybierz grupę w menu.

- Wybierz pojedyncze testy, które chcesz uruchomić, otwórz menu dostępne po kliknięciu prawym przyciskiem myszy, a następnie wybierz polecenie **Uruchom wybrane testy**.

- Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, Włącz równoległe wykonywanie testów w menu Ustawienia na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Uruchom testy po każdej kompilacji
::: moniker range="vs-2017"
|Przycisk|Opis|
|-|-|
|![Uruchom po kompilacji](../test/media/ute_runafterbuild_btn.png)|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz **test** w menu Standard, a następnie wybierz polecenie **Uruchom testy po kompilacji** na pasku narzędzi **Eksploratora testów** .|

> [!NOTE]
> Uruchamianie testów jednostkowych po każdej kompilacji wymaga programu Visual Studio 2017 Enterprise lub Visual Studio 2019. W programie Visual Studio 2019 jest on dostępny w społeczność i Professional oraz w przedsiębiorstwie.
::: moniker-end
::: moniker range=">=vs-2019"
Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, Otwórz ikonę ustawienia na pasku narzędzi Eksploratora testów i wybierz opcję **Uruchom testy po kompilacji**.
::: moniker-end

## <a name="view-test-results"></a>Wyświetl wyniki testu

Podczas uruchamiania, zapisywania i ponownego uruchamiania testów, Eksplorator testów wyświetla wyniki w grupach **testów zakończonych niepowodzeniem**, testy **zakończone pomyślnie**, testy **pominięte** i **testy nie są uruchamiane**. W okienku szczegółów u dołu lub stronie Eksploratora testów jest wyświetlane podsumowanie przebiegu testu.

### <a name="view-test-details"></a>Wyświetl szczegóły testu

Aby wyświetlić szczegóły poszczególnych testów, wybierz test.

::: moniker range="vs-2017"
![Szczegóły wykonania testu](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Szczegóły wykonania testu](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

W okienku Szczegóły testu są wyświetlane następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Czas, który upłynął do uruchomienia metody testowej.

Jeśli test nie powiedzie się, w okienku szczegółów zostanie również wyświetlony komunikat:

- Komunikat zwrócony przez strukturę testów jednostkowych dla testu.

- Ślad stosu w czasie testu nie powiódł się.

### <a name="view-the-source-code-of-a-test-method"></a>Wyświetl kod źródłowy metody testowej

Aby wyświetlić kod źródłowy dla metody testowej w edytorze programu Visual Studio, wybierz test, a następnie wybierz **Otwórz test** w menu rozwijanym prawym przyciskiem myszy (klawiatura: **F12**).

## <a name="group-and-filter-the-test-list"></a>Grupowanie i filtrowanie listy testów

Eksplorator testów umożliwia grupowanie testów w wstępnie zdefiniowanych kategoriach. Większość platform testów jednostkowych, które działają w Eksploratorze testów, umożliwiają definiowanie własnych kategorii i par kategorii/wartości w celu grupowania testów. Możesz również filtrować listę testów, dopasowując ciągi do właściwości testu.

### <a name="group-tests-in-the-test-list"></a>Grupuj testy na liście testów

::: moniker range="vs-2017"
Aby zmienić sposób, w jaki są zorganizowane testy, wybierz strzałkę w dół obok przycisku Grupuj **według** w ![ Eksploratorze testów ](../test/media/ute_groupby_btn.png) i wybierz nowe kryteria grupowania.

![Grupuj testy według kategorii w Eksploratorze testów](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Eksplorator testów pozwala grupować testy w hierarchię. Domyślnym grupowaniem hierarchii jest **projekt**, **przestrzeń nazw**, a następnie **Klasa**. Aby zmienić sposób organizowania testów, wybierz przycisk **Grupuj według** przycisk ![ Grupa Eksploratora testów ](../test/media/ute_groupby_btn.png) i wybierz nowe kryteria grupowania.

![Grupuj testy według kategorii w Eksploratorze testów](../test/media/vs-2019/test-explorer-groupby-162.png)

Można zdefiniować własne poziomy hierarchii i według **stanu** , a następnie **klasy** , na przykład wybierając pozycję Grupuj według opcji w preferowanej kolejności.

![Grupuj według stanu, a następnie klasy](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Grupy Eksploratora testów

::: moniker range="vs-2017"
|Grupa|Opis|
|-|-----------------|
|**Czas trwania**|Testy grup według czasu wykonywania: **szybka**, **średnia**i **wolna**.|
|**Wynik**|Grupuje testy według wyników wykonywania: **testy zakończone niepomyślnie**, **testy pominięte**, **testy zakończone powodzeniem**.|
|**Cech**|Grupuje testy według par kategorii/wartości zdefiniowanych przez użytkownika. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.|
|**Project**|Grupuje testy według nazwy projektów.|
::: moniker-end
::: moniker range=">=vs-2019"
|Grupa|Opis|
|-|-----------------|
|**Czas trwania**|Grupuje testy według czasu wykonywania: **szybka**, **średnia**i **wolna**.|
|**Stan**|Grupuje testy według wyników wykonywania: **testy zakończone niepomyślnie**, **testy pominięte**, **testy zakończone powodzeniem**, **nie uruchomiono**|
|**Struktura docelowa** | Grupuje testy według struktury obiektów docelowych projektów |
|**Przestrzeń nazw**|Grupuje testy według przestrzeni nazw zawierającej.|
|**Project**|Grupuje testy według projektu zawierającego.|
|**Klasa**|Grupuje testy według klasy zawierającej.|
::: moniker-end

### <a name="traits"></a>Cech

Cechą jest zazwyczaj para nazwa kategorii/wartość, ale może to być również jedna kategoria. Cechy mogą być przypisywane do metod, które są identyfikowane jako metoda testowa przez strukturę testów jednostkowych. Struktura testów jednostkowych może definiować kategorie cech. Możesz dodać wartości do kategorii cech, aby zdefiniować własne pary nazwa/wartość kategorii. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.

**Cechy struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego**

W środowisku testów jednostkowych firmy Microsoft dla zarządzanych aplikacji należy zdefiniować nazwę cechy/wartość pary w <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atrybucie. Struktura testowa zawiera również następujące wstępnie zdefiniowane cechy:

|Cecha|Opis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategoria właściciela jest definiowana przez strukturę testów jednostkowych i wymaga podania wartości ciągu właściciela.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategoria priorytetu jest definiowana przez strukturę testów jednostkowych i wymaga podania wartości całkowitej priorytetu.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atrybut TestCategory umożliwia podanie kategorii bez wartości.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atrybut TestProperty umożliwia zdefiniowanie pary Category/wartość.|


**Cechy struktury testów jednostkowych firmy Microsoft dla języka C++**

Zobacz [, jak używać struktury testów jednostkowych firmy Microsoft dla języka C++](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Tworzenie niestandardowych list odtwarzania

::: moniker range="vs-2017"
Można utworzyć i zapisać listę testów, które chcesz uruchomić lub wyświetlić jako grupę. Po wybraniu listy odtwarzania testy z listy są wyświetlane w Eksploratorze testów. Test można dodać do więcej niż jednej listy odtwarzania, a wszystkie testy w projekcie są dostępne po wybraniu domyślnej listy odtwarzania **wszystkie testy** .

![Wybierz listę odtwarzania](../test/media/ute_playlist.png)

**Aby utworzyć listę odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu po kliknięciu prawym przyciskiem myszy wybierz polecenie **Dodaj do listy odtwarzania**  >  **NewPlaylist**. Zapisz plik o nazwie i lokalizacji określonej w oknie dialogowym **Tworzenie nowej listy odtwarzania** .

**Aby dodać testy do listy odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu po kliknięciu prawym przyciskiem myszy wybierz polecenie **Dodaj do listy odtwarzania**, a następnie wybierz listę odtwarzania, do której chcesz dodać testy.

**Aby otworzyć listę odtwarzania**, wybierz pozycję **Testuj** > **listę odtwarzania** z menu programu Visual Studio, a następnie wybierz pozycję z listy ostatnio używanych list odtwarzania lub wybierz pozycję **Otwórz listę odtwarzania** , aby określić nazwę i lokalizację listy odtwarzania.

Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, należy włączyć równoległe wykonywanie testów przy użyciu ![Wykonaj&#95;parallelicon&#45;mały](../test/media/ute_parallelicon-small.png) przycisk przełączania na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.
::: moniker-end
::: moniker range=">=vs-2019"
Można utworzyć i zapisać listę testów, które chcesz uruchomić lub wyświetlić jako grupę. Po wybraniu listy odtwarzania testy z listy są wyświetlane na nowej karcie programu Test Explorer. Test można dodać do więcej niż jednej listy odtwarzania.

**Aby utworzyć listę odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu po kliknięciu prawym przyciskiem myszy wybierz polecenie **Dodaj do listy odtwarzania**  >  **Nowa lista odtwarzania**.

![Tworzenie listy odtwarzania](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Lista odtwarzania zostanie otwarta na nowej karcie programu Test Explorer. Możesz użyć tej listy odtwarzania raz, a następnie odrzucić ją. Możesz też kliknąć przycisk **Zapisz** na pasku narzędzi okna listy odtwarzania, a następnie wybrać nazwę i lokalizację, aby zapisać listę odtwarzania.

![Lista odtwarzania zostanie otwarta na osobnej karcie Eksploratora testów](../test/media/vs-2019/test-explorer-playlist-tab-16-2.png)

**Aby utworzyć listę odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. Kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj do listy odtwarzania**  >  **Nowa lista odtwarzania**.

**Aby otworzyć listę odtwarzania**, wybierz ikonę listy odtwarzania na pasku narzędzi programu Visual Studio i wybierz wcześniej zapisany plik listy odtwarzania z menu.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Kolumny Eksploratora testów

[Grupy](#test-explorer-groups) są również dostępne jako kolumny w Eksploratorze testów oraz cechy, ślad stosu, komunikat o błędzie i w pełni kwalifikowana nazwa. Większość kolumn nie jest domyślnie widoczna i można dostosować wyświetlane kolumny oraz kolejność ich wyświetlania.

![Grupuj według stanu, a następnie klasy](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtrowanie, sortowanie i zmiana rozmieszczenia kolumn testowych

Kolumny można filtrować, sortować i zmieniać ich kolejność.
* Aby odfiltrować do określonych cech, kliknij ikonę filtru w górnej części kolumny cechy.

  ![Filtr kolumn](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Aby zmienić kolejność kolumn, kliknij nagłówek kolumny i przeciągnij go w lewo lub w prawo.

* Aby posortować kolumnę, kliknij nagłówek kolumny. Nie wszystkie kolumny można sortować. Możesz również sortować według pomocniczej kolumny, przytrzymując klawisz **SHIFT** i klikając nagłówek dodatkowej kolumny.

  ![Sortowanie kolumn](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Wyszukiwanie i filtrowanie listy testów

Możesz również użyć filtrów wyszukiwania programu Test Explorer, aby ograniczyć metody testowe w projektach, które są wyświetlane i uruchamiane.

Po wpisaniu ciągu w polu wyszukiwania **Eksploratora testów** i wybraniu **klawisza ENTER**lista testów jest filtrowana, aby wyświetlić tylko te testy, których w pełni kwalifikowane nazwy zawierają ciąg.

Aby odfiltrować według innych kryteriów:

1. Otwórz listę rozwijaną z prawej strony pola wyszukiwania.

2. Wybierz nowe kryterium.

3. Wprowadź wartość filtru między znakami cudzysłowu. Jeśli chcesz wyszukać dokładne dopasowanie w ciągu, a nie zawierającej dopasowania, użyj znaku równości (=) zamiast dwukropka (:).

::: moniker range="vs-2017"
![Filtruj testy w Eksploratorze testów](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Filtruj testy w Eksploratorze testów](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Wyszukiwania są rozróżniane wielkości liter i pasują do określonego ciągu do dowolnej części wartości kryteriów.

::: moniker range="vs-2017"
|Kwalifikator|Opis|
|-|-----------------|
|**Cecha**|Wyszukuje dopasowania kategorii i wartości. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.|
|**Project**|Wyszukuje dopasowania w nazwach projektów testowych.|
|**Komunikat o błędzie**|Wyszukuje dopasowania w zdefiniowanych przez użytkownika komunikatach o błędach zwracanych przez nieudane potwierdzenia.|
|**Ścieżka pliku**|Wyszukuje dopasowania w w pełni kwalifikowanych nazwach plików źródłowych testów.|
|**W pełni kwalifikowana nazwa**|Przeszukuje w pełni kwalifikowaną nazwę testowanych przestrzeni nazw, klas i metod w celu dopasowania.|
|**Dane wyjściowe**|Wyszukuje komunikaty o błędach zdefiniowane przez użytkownika, które są zapisywane w standardowym wyjściu (stdout) lub w standardowym błędzie (stderr). Składnia służąca do określania komunikatów wyjściowych jest definiowana przez strukturę testów jednostkowych.|
|**Wynik**|Wyszukuje dopasowania w nazwach kategorii Eksploratora testów: **testy zakończone niepomyślnie**, **testy pominięte**, **testy zakończone powodzeniem**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Kwalifikator|Opis|
|-|-----------------|
|**Stan**|Wyszukuje dopasowania w nazwach kategorii Eksploratora testów: **testy zakończone niepomyślnie**, **testy pominięte**, **testy zakończone powodzeniem**.|
|**Cech**|Wyszukuje dopasowania kategorii i wartości. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.|
|**W pełni kwalifikowana nazwa**|Przeszukuje w pełni kwalifikowaną nazwę testowanych przestrzeni nazw, klas i metod w celu dopasowania.|
|**Project**|Wyszukuje dopasowania w nazwach projektów testowych.|
|**Struktura docelowa**|Wyszukuje dopasowania w nazwach kategorii Eksploratora testów: **testy zakończone niepomyślnie**, **testy pominięte**, **testy zakończone powodzeniem**.|
|**Przestrzeń nazw**|Wyszukuje dopasowania w przestrzeniach nazw testów.|
|**Klasa**|Wyszukuje dopasowania w nazwach klas testowych.|
::: moniker-end

Aby wykluczyć podzestaw wyników filtru, należy użyć następującej składni:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Na przykład `FullName:"MyClass" - FullName:"PerfTest"` zwraca wszystkie testy, które zawierają ciąg "MyClass" w nazwie, z wyjątkiem testów, które zawierają również ciąg "PerfTest" w nazwie.

## <a name="debug-and-analyze-unit-tests"></a>Debuguj i Analizuj testy jednostkowe

Możesz użyć Eksploratora testów, aby rozpocząć sesję debugowania dla testów. Przechodzenie przez kod za pomocą debugera programu Visual Studio bezproblemowo przeprowadzi Cię z powrotem między testami jednostkowymi i badanym projektem. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w co najmniej jednej metodzie testowej, która ma być debugowana.

    > [!NOTE]
    > Ponieważ metody testowe mogą być uruchamiane w dowolnej kolejności, należy ustawić punkty przerwania we wszystkich metodach testowych, które mają być debugowane.

2. W Eksploratorze testów wybierz metody testowe, a następnie wybierz **Debuguj wybrane testy** w menu po kliknięciu prawym przyciskiem myszy.

   Aby uzyskać więcej informacji o debugerze, zobacz [debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnozuj problemy z wydajnością metody testowej

Aby zdiagnozować Dlaczego metoda testowa trwa zbyt wiele czasu, wybierz metodę w Eksploratorze testów, a następnie wybierz pozycję **profil wybrany test** w menu po kliknięciu prawym przyciskiem myszy. Zobacz [raport profilowania Instrumentacji](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).

### <a name="analyze-unit-test-code-coverage"></a>Analizuj pokrycie kodu testu jednostkowego

Można określić ilość kodu produktu, który jest faktycznie testowany przez testy jednostkowe za pomocą narzędzia pokrycia kodu w programie Visual Studio dostępnego w wersji Visual Studio Enterprise. Można uruchomić pokrycie kodu dla wybranych testów lub wszystkich testów w rozwiązaniu.

Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu:

::: moniker range="vs-2017"

1. Wybierz **test** na górnym pasku menu, a następnie wybierz polecenie **Analizuj pokrycie kodu**.

2. Wybierz jedno z następujących poleceń z podmenu:

    - **Wybrane testy** uruchamiają metody testowe, które zostały wybrane w Eksploratorze testów.

    - **Wszystkie testy** są uruchamiane ze wszystkich metod testowych w rozwiązaniu.

::: moniker-end

::: moniker range=">=vs-2019"

* Kliknij prawym przyciskiem myszy w Eksploratorze testów i wybierz polecenie **Analizuj pokrycie kodu dla wybranych testów**

::: moniker-end

Okno **wyniki pokrycia kodu** przedstawia wartość procentową bloków kodu produktu, które były wykonywane przez wiersz, funkcję, klasę, przestrzeń nazw i moduł.

Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu w celu określenia, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Skróty testowe

Testy można uruchomić z poziomu Eksploratora testów, klikając prawym przyciskiem myszy w edytorze kodu na test i wybierając polecenie **Uruchom test** lub używając domyślnych [skrótów Eksploratora testów](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) w programie Visual Studio. Niektóre skróty są oparte na kontekście. Oznacza to, że uruchamiają lub debugują testy w zależności od tego, gdzie znajduje się kursor w edytorze kodu. Jeśli kursor znajduje się wewnątrz metody testowej, ta metoda testowa jest uruchamiana. Jeśli kursor znajduje się na poziomie klasy, wszystkie testy w tej klasie są uruchamiane. Jest to taka sama dla poziomu przestrzeni nazw.

|Częste polecenia| Skróty klawiaturowe|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl** + **R**, **Ctrl** + **T**|
|TestExplorer.RunAllTestsInContext|**Ctrl** + **R**, **T**|
|TestExplorer.RunAllTests|**Ctrl** + **R**, **A**|
|TestExplorer.RepeatLastRun|**Ctrl** + **R**, **L**|

> [!NOTE]
> Nie można uruchomić testu w klasie abstrakcyjnej, ponieważ testy są zdefiniowane tylko w klasach abstrakcyjnych i nie są tworzone. Aby uruchomić testy w klasach abstrakcyjnych, należy utworzyć klasę, która dziedziczy z klasy abstrakcyjnej.

## <a name="see-also"></a>Zobacz też

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Uruchamianie testu jednostkowego jako procesu 64-bitowego](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
