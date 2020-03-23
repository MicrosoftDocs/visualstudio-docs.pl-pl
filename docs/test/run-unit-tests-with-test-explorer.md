---
title: Uruchamianie i debugowanie testów jednostkowych za pomocą Eksploratora testów
description: Dowiedz się, jak uruchamiać testy za pomocą Eksploratora testów w programie Visual Studio. W tym temacie opisano, jak włączyć automatyczne przebiegi testów po kompilacji, wyświetlić wyniki testów, zgrupować i filtrować listę testów, utworzyć listy odtwarzania, testy debugowania i użyć skrótów testowych.
ms.date: 07/29/2019
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b183c1939ed48351bc15dacff31c85af46286ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278515"
---
# <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów

Użyj Eksploratora testów, aby uruchomić testy jednostkowe z programu Visual Studio lub projektów testów jednostkowych innych firm. Eksploratora testów służy również do grupowania testów na kategorie, filtrowania listy testów oraz tworzenia, zapisywania i uruchamiania list odtwarzania testów. Można debugować testy i analizować wydajność testu i pokrycie kodu.

Visual Studio zawiera struktury testowania jednostkowego firmy Microsoft dla kodu zarządzanego i macierzystego. Jednak Eksplorator testów można również uruchomić dowolną strukturę testów jednostkowych, która zaimplementowała kartę Eksploratora testów. Aby uzyskać więcej informacji na temat instalowania struktur testów jednostkowych innych firm, zobacz [Instalowanie struktur testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

**Eksplorator testów** można uruchomić testy z wielu projektów testowych w rozwiązaniu i z klas testowych, które są częścią projektów kodu produkcyjnego. Projekty testowe można użyć różnych jednostek testów struktur. Gdy kod w ramach testu jest napisany dla .NET, projekt testowy można zapisać w dowolnym języku, który również jest przeznaczony dla .NET, niezależnie od języka kodu docelowego. Projekty kodu natywnego języka C/C++ muszą być testowane przy użyciu struktury testów jednostkowych języka C++. Aby uzyskać więcej informacji, zobacz [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Uruchamianie testów w Eksploratorze testów


Podczas tworzenia projektu testowego testy są wyświetlane w Eksploratorze testów. Jeśli Eksplorator testów nie jest widoczny, wybierz polecenie **Testuj** w menu programu Visual Studio, wybierz pozycję **Windows**, a następnie wybierz pozycję **Eksplorator testów**.


::: moniker range="vs-2017"
![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Eksplorator testów](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Podczas uruchamiania, zapisywania i ponownego uruchamiania testów Eksplorator testów wyświetla wyniki w domyślnych grupach **testów nieudanych,** **testów przeszłych,** **pominiętych testów** i nie **uruchamianych testów.** Można zmienić sposób, w jaki Eksplorator testów grupuje testy.
::: moniker-end
::: moniker range=">=vs-2019"
Podczas uruchamiania, zapisywania i ponownego uruchamiania testów Eksplorator testów wyświetla wyniki w domyślnej grupie **project,** **namespace**i **class**. Można zmienić sposób, w jaki Eksplorator testów grupuje testy.
::: moniker-end

Wiele pracy można wykonać w celu znajdowania, organizowania i uruchamiania testów z paska narzędzi **Eksploratora testów.**

::: moniker range="vs-2017"
![Uruchamianie testów z paska narzędzi Eksploratora testów](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Uruchamianie testów z paska narzędzi Eksploratora testów](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Uruchom testy

::: moniker range="vs-2017"
Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które można wybrać. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz pozycję **Uruchom wszystkie**.

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz pozycję **Uruchom,** a następnie wybierz grupę w menu.

- Wybierz poszczególne testy, które chcesz uruchomić, otwórz menu po kliknięciu prawym przyciskiem myszy dla wybranego testu, a następnie wybierz polecenie **Uruchom wybrane testy**.

- Jeśli poszczególne testy nie mają zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonanie testu za pomocą ![Ute&#95;równoległości&#45;małe](../test/media/ute_parallelicon-small.png) na pasku narzędzi. Może to znacznie skrócić czas pracy wszystkich testów.

Pasek **przebiegu/niepowodzenia** w górnej części okna **Eksploratora testów** jest animowany podczas uruchamiania testów. Po zakończeniu testu **pasek przebiegu/niepowodzenia** zmienia kolor na zielony, jeśli wszystkie testy przeszły lub zmienią kolor na czerwony, jeśli jakikolwiek test nie powiódł się.
::: moniker-end
::: moniker range=">=vs-2019"
Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw testów, które można wybrać. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz ikonę **Uruchom wszystko.**

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz ikonę **Uruchom,** a następnie wybierz grupę w menu.

- Wybierz poszczególne testy, które chcesz uruchomić, otwórz menu po kliknięciu prawym przyciskiem myszy dla wybranego testu, a następnie wybierz polecenie **Uruchom wybrane testy**.

- Jeśli poszczególne testy nie mają żadnych zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonanie testu w menu ustawień paska narzędzi. Może to znacznie skrócić czas pracy wszystkich testów.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Uruchamianie testów po każdej kompilacji
::: moniker range="vs-2017"
|Button|Opis|
|-|-|
|![Uruchom po kompilacji](../test/media/ute_runafterbuild_btn.png)|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz polecenie **Testuj** w standardowym menu, a następnie wybierz polecenie **Uruchom testy po kompilacji** na pasku narzędzi **Eksploratora testów.**|

> [!NOTE]
> Uruchamianie testów jednostkowych po każdej kompilacji wymaga programu Visual Studio 2017 Enterprise lub Visual Studio 2019. W programie Visual Studio 2019 jest on uwzględniony w community i professional, a także enterprise.
::: moniker-end
::: moniker range=">=vs-2019"
Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, otwórz ikonę ustawień na pasku narzędzi Eksploratora testów i wybierz pozycję **Uruchom testy po kompilacji**.
::: moniker-end

## <a name="view-test-results"></a>Wyświetlanie wyników testów

Podczas uruchamiania, pisania i ponownego uruchamiania testów Eksplorator testów wyświetla wyniki w grupach **testów nieudanych,** **testów przeszłych,** **pominiętych testów** i nie **uruchamianych testów.** Okienko szczegółów w dolnej lub bocznej części Eksploratora testów wyświetla podsumowanie przebiegu testu.

### <a name="view-test-details"></a>Wyświetlanie szczegółów testu

Aby wyświetlić szczegóły pojedynczego testu, wybierz test.

::: moniker range="vs-2017"
![Szczegóły wykonania testu](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Szczegóły wykonania testu](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

W okienku szczegółów testu są wyświetlane następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Upłynął czas, który metoda testowa miała do uruchomienia.

Jeśli test zakończy się niepowodzeniem, zostanie wyświetlone również okienko szczegółów:

- Komunikat zwrócony przez jednostkową platformę testową dla testu.

- Śledzenie stosu w czasie, gdy test nie powiódł się.

### <a name="view-the-source-code-of-a-test-method"></a>Wyświetlanie kodu źródłowego metody testowej

Aby wyświetlić kod źródłowy metody testowej w edytorze Visual Studio, wybierz test, a następnie wybierz polecenie **Otwórz test** w menu po kliknięciu prawym przyciskiem myszy (Klawiatura: **F12**).

## <a name="group-and-filter-the-test-list"></a>Grupowanie i filtrowanie listy testów

Eksplorator testów umożliwia grupowanie testów w wstępnie zdefiniowane kategorie. Większość struktur testów jednostkowych, które są uruchamiane w Eksploratorze testów, umożliwia definiowanie własnych kategorii i par kategorii/wartości w celu zgrupowania testów. Można również filtrować listę testów, dopasowując ciągi względem właściwości testu.

### <a name="group-tests-in-the-test-list"></a>Testy grupowe na liście testów

::: moniker range="vs-2017"
Aby zmienić sposób organizacji testów, wybierz strzałkę w ![dół obok](../test/media/ute_groupby_btn.png) przycisku **Grupuj według** przycisku Testowanie eksploratora i wybierz nowe kryteria grupowania.

![Grupowanie testów według kategorii w Eksploratorze testów](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Eksplorator testów umożliwia grupowanie testów w hierarchii. Domyślne grupowanie hierarchii to **Project**, **Namespace**, a następnie **Class**. Aby zmienić sposób organizacji testów, wybierz ![przycisk **Grupuj według** przycisku Testowanie eksploratora](../test/media/ute_groupby_btn.png) i wybierz nowe kryteria grupowania.

![Grupowanie testów według kategorii w Eksploratorze testów](../test/media/vs-2019/test-explorer-groupby-162.png)

Można zdefiniować własne poziomy hierarchii i grupy według **stanu,** a następnie **klasy,** na przykład wybierając opcję Grupuj według w preferowanej kolejności.

![Grupowanie według stanu, a następnie klasa](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Grupy Eksploratora testów

::: moniker range="vs-2017"
|Grupa|Opis|
|-|-----------------|
|**Czas trwania**|Grupy testują według czasu wykonania: **Szybki,** **Średni**i **Wolny.**|
|**Wynik**|Grupuje testy według wyników wykonania: **Testy nieudane,** **Testy pominięte**, **Testy przeszły**.|
|**Cechy**|Grupy testują według zdefiniowanych par kategorii/wartości. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.|
|**Project**|Grupy testują według nazwy projektów.|
::: moniker-end
::: moniker range=">=vs-2019"
|Grupa|Opis|
|-|-----------------|
|**Czas trwania**|Grupuje testy według czasu wykonania: **Szybki,** **Średni**i **Wolny.**|
|**Stan**|Grupuje testy według wyników wykonania: **Testy nieudane,** **Testy pominięte,** **Testy zrealizowane,** **Nie uruchamiane**|
|**Struktura docelowa** | Grupy testują w ramach, do ich projekty |
|**Namespace**|Grupuje testy według zawierającego obszaru nazw.|
|**Project**|Grupuje testy według projektu zawierającego.|
|**Klasa**|Grupy testów przez klasy zawierającej.|
::: moniker-end

### <a name="traits"></a>Cechy

Cecha jest zwykle parą nazwa/wartość kategorii, ale może być również pojedynczą kategorią. Cechy mogą być przypisane do metod, które są identyfikowane jako metoda testowa przez jednostkową platformę testową. Struktura testu jednostkowego może definiować kategorie cech. Można dodać wartości do kategorii cech, aby zdefiniować własne pary nazw/wartości kategorii. Składnia określająca kategorie i wartości cech jest definiowana przez strukturę testów jednostkowych.

**Cechy w ramach microsoft unit testing framework dla kodu zarządzanego**

W ramach testów jednostkowych firmy Microsoft dla aplikacji zarządzanych definiuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> się nazwę cechy / parę wartości w atrybucie. Struktura testów zawiera również te wstępnie zdefiniowane cechy:

|Cecha|Opis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Owner kategoria jest zdefiniowana przez platformę testów jednostkowych i wymaga podania wartości ciągu właściciela.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategoria Priorytet jest zdefiniowana przez platformę testów jednostkowych i wymaga podania wartości całkowitej priorytetu.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atrybut TestCategory umożliwia podanie kategorii bez wartości.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atrybut TestProperty umożliwia zdefiniowanie pary kategorii/wartości cech.|


**Cechy w ramach testów jednostkowych firmy Microsoft dla języka C++**

Zobacz [Jak używać programu Microsoft Unit Testing Framework dla języka C++](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Tworzenie niestandardowych list odtwarzania

::: moniker range="vs-2017"
Można utworzyć i zapisać listę testów, które mają być uruchamiane lub wyświetlane jako grupa. Po wybraniu listy odtwarzania testy na liście są wyświetlane w Eksploratorze testów. Możesz dodać test do więcej niż jednej listy odtwarzania, a wszystkie testy w projekcie są dostępne po wybraniu domyślnej listy odtwarzania **Wszystkie testy.**

![Wybieranie listy odtwarzania](../test/media/ute_playlist.png)

**Aby utworzyć listę odtwarzania,** wybierz jeden lub więcej testów w Eksploratorze testów. W menu prawym przyciskiem myszy wybierz polecenie **Dodaj do listy odtwarzania** > **NewPlaylist**. Zapisz plik o nazwie i lokalizacji określonej w oknie dialogowym **Tworzenie nowej listy odtwarzania.**

**Aby dodać testy do listy odtwarzania,** wybierz jeden lub więcej testów w Eksploratorze testów. W menu prawym przyciskiem myszy wybierz polecenie **Dodaj do listy odtwarzania,** a następnie wybierz listę odtwarzania, do której chcesz dodać testy.

**Aby otworzyć listę odtwarzania,** wybierz polecenie **Testuj** > **listę odtwarzania** z menu programu Visual Studio i wybierz z listy ostatnio używanych list odtwarzania lub wybierz pozycję Otwórz listę **odtwarzania,** aby określić nazwę i lokalizację listy odtwarzania.

Jeśli poszczególne testy nie mają zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonanie testu za pomocą ![Ute&#95;równoległości&#45;małe](../test/media/ute_parallelicon-small.png) na pasku narzędzi. Może to znacznie skrócić czas pracy wszystkich testów.
::: moniker-end
::: moniker range=">=vs-2019"
Można utworzyć i zapisać listę testów, które mają być uruchamiane lub wyświetlane jako grupa. Po wybraniu listy odtwarzania testy na liście są wyświetlane na nowej karcie Eksploratora testów. Test można dodać do więcej niż jednej listy odtwarzania.

**Aby utworzyć listę odtwarzania,** wybierz jeden lub więcej testów w Eksploratorze testów. W menu prawym przyciskiem myszy wybierz polecenie **Dodaj do listy odtwarzania** > **nowa lista odtwarzania**.

![Tworzenie listy odtwarzania](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Lista odtwarzania zostanie otwarta na nowej karcie Eksploratora testów. Możesz użyć tej listy odtwarzania raz, a następnie ją odrzucić lub kliknąć przycisk **Zapisz** na pasku narzędzi okna listy odtwarzania, a następnie wybrać nazwę i lokalizację, aby zapisać listę odtwarzania.

![Lista odtwarzania otwiera się w osobnej karcie eksploratora testów](../test/media/vs-2019/test-explorer-playlist-tab-16-2.png)

**Aby utworzyć listę odtwarzania,** wybierz jeden lub więcej testów w Eksploratorze testów. Kliknij prawym przyciskiem myszy i wybierz pozycję **Dodaj do listy odtwarzania** > **Nowa lista odtwarzania**.

**Aby otworzyć listę odtwarzania,** wybierz ikonę listy odtwarzania na pasku narzędzi Programu Visual Studio i wybierz z menu wcześniej zapisany plik listy odtwarzania.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Kolumny Eksploratora testów

[Grupy](#test-explorer-groups) są również dostępne jako kolumny w Eksploratorze testów, wraz z cechami, śledzeniem stosu, komunikatem o błędzie i w pełni kwalifikowaną nazwą. Większość kolumn nie jest domyślnie widoczna i można dostosować wyświetlane kolumny i kolejność ich pojawiania się.

![Grupowanie według stanu, a następnie klasa](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtrowanie, sortowanie i zmienianie rozmieszczenia kolumn testowych

Kolumny można filtrować, sortować i zmieniać.
* Aby odfiltrować do określonych cech, kliknij ikonę filtru u góry kolumny Cechy.

  ![Filtr kolumny](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Aby zmienić kolejność kolumn, kliknij nagłówek kolumny i przeciągnij go w lewo lub w prawo.

* Aby posortować kolumnę, kliknij nagłówek kolumny. Nie wszystkie kolumny można sortować. Można również sortować według kolumny pomocniczej, przytrzymując klawisz **Shift** i klikając dodatkowy nagłówek kolumny.

  ![Sortowanie kolumn](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Wyszukiwanie i filtrowanie listy testów

Można również użyć filtrów wyszukiwania Eksploratora testów, aby ograniczyć metody testowania w projektach, które można wyświetlić i uruchomić.

Po wpisaniu ciągu w polu wyszukiwania **Eksploratora testów** i **wybraniu**opcji Enter lista testów jest filtrowana w celu wyświetlenia tylko tych testów, których w pełni kwalifikowane nazwy zawierają ten ciąg.

Aby filtrować według różnych kryteriów:

1. Otwórz listę rozwijaną po prawej stronie pola wyszukiwania.

2. Wybierz nowe kryteria.

3. Wprowadź wartość filtru między cudzysłowami. Jeśli chcesz wyszukać dokładne dopasowanie na ciąg zamiast zawierającego dopasowania użyj znaku equals (=) zamiast dwukropka (:).

::: moniker range="vs-2017"
![Testy filtrów w Eksploratorze testów](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Testy filtrów w Eksploratorze testów](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Wyszukiwania są bez uwzględniania wielkości liter i odpowiadają określonej ciągu do dowolnej części wartości kryteriów.

::: moniker range="vs-2017"
|Kwalifikator|Opis|
|-|-----------------|
|**Cecha**|Przeszukuje zarówno kategorię cech, jak i wartość dopasowań. Składnia określająca kategorie i wartości cech są definiowane przez strukturę testów jednostkowych.|
|**Project**|Przeszukuje nazwy projektów testowych dla dopasowań.|
|**Komunikat o błędzie**|Przeszukuje komunikaty o błędach zdefiniowane przez użytkownika zwracane przez nieudane potwierdzenia dla dopasowań.|
|**Ścieżka pliku**|Przeszukuje w pełni kwalifikowaną nazwę pliku testowych plików źródłowych pod kątem dopasowań.|
|**W pełni kwalifikowana nazwa**|Przeszukuje w pełni kwalifikowaną nazwę testowych obszarów nazw, klas i metod dla dopasowań.|
|**Wyjście**|Przeszukuje komunikaty o błędach zdefiniowane przez użytkownika, które są zapisywane na standardowe dane wyjściowe (stdout) lub błąd standardowy (stderr). Składnia do określania komunikatów wyjściowych są definiowane przez platformę testu jednostkowego.|
|**Wynik**|Przeszukuje nazwy kategorii Eksploratora testów dla dopasowań: **Testy nieudane,** **Testy pominięte**, **Testy zdań**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Kwalifikator|Opis|
|-|-----------------|
|**Stan**|Przeszukuje nazwy kategorii Eksploratora testów dla dopasowań: **Testy nieudane,** **Testy pominięte**, **Testy zdań**.|
|**Cechy**|Przeszukuje zarówno kategorię cech, jak i wartość dopasowań. Składnia określająca kategorie i wartości cech są definiowane przez strukturę testów jednostkowych.|
|**W pełni kwalifikowana nazwa**|Przeszukuje w pełni kwalifikowaną nazwę testowych obszarów nazw, klas i metod dla dopasowań.|
|**Project**|Przeszukuje nazwy projektów testowych dla dopasowań.|
|**Struktura docelowa**|Przeszukuje nazwy kategorii Eksploratora testów dla dopasowań: **Testy nieudane,** **Testy pominięte**, **Testy zdań**.|
|**Namespace**|Przeszukuje obszary nazw testowych w poszukiwaniu dopasowań.|
|**Klasa**|Przeszukuje nazwy klas testowych dla dopasowań.|
::: moniker-end

Aby wykluczyć podzbiór wyników filtru, należy użyć następującej składni:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Na przykład `FullName:"MyClass" - FullName:"PerfTest"` zwraca wszystkie testy, które zawierają "MyClass" w ich nazwie, z wyjątkiem testów, które również zawierają "PerfTest" w ich nazwie.

## <a name="debug-and-analyze-unit-tests"></a>Debugowanie i analizowanie testów jednostkowych

Eksploratora testów służy do uruchamiania sesji debugowania dla testów. Krok po kroku kodu z debugerem visual studio bezproblemowo zabierze Cię tam iz powrotem między testów jednostkowych i projektu w ramach testu. Aby rozpocząć debugowanie:

1. W edytorze Visual Studio ustaw punkt przerwania w co najmniej jednej metod testowania, które chcesz debugować.

    > [!NOTE]
    > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustawić punkty przerwania we wszystkich metodach testowych, które chcesz debugować.

2. W Eksploratorze testów wybierz metody testowe, a następnie wybierz polecenie **Debugowanie wybranych testów** w menu po kliknięciu prawym przyciskiem myszy.

   Aby uzyskać więcej informacji na temat debugera, zobacz [Debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnozowanie problemów z wydajnością metody testowej

Aby zdiagnozować, dlaczego metoda testowa zajmuje zbyt dużo czasu, wybierz metodę w Eksploratorze testów, a następnie wybierz **polecenie Test wybrany profil** w menu po kliknięciu prawym przyciskiem myszy. Zobacz [raport profilowania instrumentacji](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).

### <a name="analyze-unit-test-code-coverage"></a>Analizowanie pokrycia kodu testu jednostkowego

Można określić ilość kodu produktu, który jest faktycznie testowany przez testy jednostkowe przy użyciu narzędzia pokrycia kodu programu Visual Studio, które jest dostępne w programie Visual Studio Enterprise edition. Pokrycie kodu można uruchomić w wybranych testach lub na wszystkich testach w rozwiązaniu.

Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu:

::: moniker range="vs-2017"

1. Wybierz **pozycję Testuj** na górnym pasku menu, a następnie wybierz pozycję **Analizuj pokrycie kodu**.

2. Wybierz jedno z następujących poleceń z podmenu:

    - **Wybrane testy** uruchamiają metody testowe wybrane w Eksploratorze testów.

    - **Wszystkie testy** uruchamia wszystkie metody testowania w rozwiązaniu.

::: moniker-end

::: moniker range=">=vs-2019"

* Kliknij prawym przyciskiem myszy Eksploratora testów i wybierz **pozycję Analizuj pokrycie kodu dla wybranych testów**

::: moniker-end

Okno **Wyniki pokrycia kodu** wyświetla procent bloków kodu produktu, które zostały wykonywane przez wiersz, funkcję, klasę, obszar nazw i moduł.

Aby uzyskać więcej informacji, zobacz [Użyj pokrycia kodu, aby określić, ile kodu jest testowany.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="test-shortcuts"></a>Skróty testowe

Testy można uruchomić z Eksploratora testów, klikając prawym przyciskiem myszy w edytorze kodu w teście i wybierając **uruchom test** lub używając [domyślnych skrótów Eksploratora testów](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) w programie Visual Studio. Niektóre skróty są oparte na kontekście. Oznacza to, że uruchamiają lub debugowania testów na podstawie, gdzie kursor znajduje się w edytorze kodu. Jeśli kursor znajduje się wewnątrz metody testowej, następnie uruchamia się tej metody testowej. Jeśli kursor znajduje się na poziomie klasy, wszystkie testy w tej klasie są uruchamiane. Jest to taka sama dla poziomu obszaru nazw, jak również.

|Częste polecenia| Skróty klawiaturowe|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl**+**R**, **Ctrl**+**T**|
|TestExplorer.RunAllTestsInContext|**Ctrl**+**R**, **T**|
|TestExplorer.RunAllTests|**Ctrl**+**R**, **A**|
|TestExplorer.RepeatLastRun|**Ctrl**+**R**, **L**|

> [!NOTE]
> Nie można uruchomić testu w klasie abstrakcyjnej, ponieważ testy są zdefiniowane tylko w klasach abstrakcyjnych i nie są tworzone. Aby uruchomić testy w klasach abstrakcyjnych, należy utworzyć klasę, która pochodzi od klasy abstrakcyjnej.

## <a name="see-also"></a>Zobacz też

- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
- [Uruchamianie testu jednostkowego jako procesu 64-bitowego](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
