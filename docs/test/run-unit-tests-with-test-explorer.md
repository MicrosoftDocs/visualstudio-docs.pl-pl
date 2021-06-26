---
title: Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów
description: Dowiedz się, jak uruchamiać testy za pomocą Eksploratora testów w Visual Studio. W tym temacie opisano sposób włączania automatycznych przebiegów testów po kompilacji, wyświetlania wyników testów, grupowania i filtrowania listy testów, tworzenia list odtwarzania i używania skrótów testowych.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 26dbed25f42f40614597075ad26c855398b56025
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925127"
---
# <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów

Użyj Eksploratora testów, aby uruchamiać testy jednostkowe z Visual Studio lub projektów testów jednostkowych innych firm. Eksplorator testów umożliwia również grupowanie testów w kategorie, filtrowanie listy testów oraz tworzenie, zapisywanie i uruchamianie list odtwarzania testów. Można również analizować pokrycie kodu i [debugować testy jednostkowe](../test/debug-unit-tests-with-test-explorer.md).

**Eksplorator testów** może uruchamiać testy z wielu projektów testowych w rozwiązaniu i z klas testowych, które są częścią projektów kodu produkcyjnego. Projekty testowe mogą używać różnych platform testów jednostkowych. Gdy testowy kod jest napisany dla programu .NET, projekt testowy może być napisany w dowolnym języku przeznaczonym dla programu .NET, niezależnie od języka kodu docelowego. Natywne projekty kodu C/C++ muszą być testowane przy użyciu struktury testów jednostkowych języka C++.

## <a name="build-your-test-project"></a>Tworzenie projektu testowego

Jeśli nie masz jeszcze projektu testowego w rozwiązaniu Visual Studio, musisz najpierw utworzyć i skompilować projekt testowy.

- [Wprowadzenie do testowania jednostkowego (.NET)](../test/getting-started-with-unit-testing.md)
- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)

Visual Studio obejmuje struktury testowania jednostkowego firmy Microsoft dla kodu zarządzanego i natywnego. Jednak Eksplorator testów może również uruchamiać dowolną platformę testów jednostkowych, w ramach których zaimplementowano adapter Eksploratora testów. Aby uzyskać więcej informacji na temat instalowania platform testów jednostkowych innych firm, zobacz Instalowanie platform testów [jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

## <a name="run-tests-in-test-explorer"></a>Uruchamianie testów w Eksploratorze testów

Podczas kompilowania projektu testowego testy są wyświetlane w Eksploratorze testów. Jeśli Eksplorator testów nie  jest widoczny, wybierz pozycję Testuj w menu Visual Studio, wybierz pozycję **Windows**, a następnie wybierz pozycję **Eksplorator testów** (lub naciśnij **klawisze Ctrl**  +  **E,** **T**).

::: moniker range="vs-2017"
![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Eksplorator testów](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Podczas uruchamiania, pisania i ponownego uruchamiania testów Eksplorator testów wyświetla wyniki w  domyślnych grupach testów nieudanych, testów pomyślnie przekazanych, pominiętych i nie **uruchamianych testów.** Możesz zmienić sposób grupować testy w Eksploratorze testów.
::: moniker-end
::: moniker range=">=vs-2019"
Podczas uruchamiania, pisania i ponownego uruchamiania testów Eksplorator testów wyświetla wyniki w domyślnej grupie **projektów,** przestrzeni **nazw** i **klasy**. Możesz zmienić sposób grupować testy w Eksploratorze testów.
::: moniker-end

Większość pracy można wykonać, znajdując, organizując i uruchamiając testy na pasku narzędzi **Eksploratora** testów.

::: moniker range="vs-2017"
![Uruchamianie testów z paska narzędzi Eksploratora testów](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Uruchamianie testów z paska narzędzi Eksploratora testów](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Uruchom testy

::: moniker range="vs-2017"
Możesz uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw wybranych testów. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz pozycję **Uruchom wszystko** (lub naciśnij **klawisze Ctrl** + **R,** **V**).

- Aby uruchomić wszystkie testy w grupie domyślnej, wybierz pozycję **Uruchom,** a następnie wybierz grupę z menu.

- Wybierz poszczególne testy, które chcesz uruchomić, otwórz menu dostępne po kliknięciu prawym przyciskiem myszy dla wybranego testu, a następnie wybierz polecenie Uruchom **wybrane** testy (lub naciśnij **klawisze Ctrl** + **R,** **T**).

- Jeśli poszczególne testy nie mają zależności uniemożliwiających ich uruchamianie w dowolnej kolejności, włącz równoległe wykonywanie testów za pomocą ![Zrzut ekranu przedstawiający przycisk przełączania Równoległe wykonywanie testu na pasku narzędzi Visual Studio Test Explorer. Po wybraniu tego przycisku testy będą uruchamiane równolegle.](../test/media/ute_parallelicon-small.png) na pasku narzędzi. Może to znacznie skrócić czas uruchamiania wszystkich testów.

Pasek **przebiegu/awarii w** górnej części okna **Eksplorator testów** jest animowany podczas uruchamiania testów. Po zakończeniu przebiegu testu pasek **przebiegu/awarii** zmieni kolor na zielony, jeśli wszystkie testy zakończyły się pomyślnie lub zmienią kolor na czerwony, jeśli którykolwiek test zakończył się niepowodzeniem.
::: moniker-end
::: moniker range=">=vs-2019"
Możesz uruchomić wszystkie testy w rozwiązaniu, wszystkie testy w grupie lub zestaw wybranych testów. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz ikonę Uruchom **wszystko** (lub naciśnij **klawisze Ctrl** + **R,** **V**).

- Aby uruchomić wszystkie testy w grupie  domyślnej, wybierz ikonę Uruchom, a następnie wybierz grupę z menu.

- Wybierz poszczególne testy, które chcesz uruchomić, otwórz menu dostępne po kliknięciu prawym przyciskiem myszy dla wybranego testu, a następnie wybierz polecenie Uruchom **wybrane** testy (lub naciśnij **klawisze Ctrl** + **R,** **T**).

- Jeśli poszczególne testy nie mają zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonywanie testów w menu ustawień paska narzędzi. Może to znacznie skrócić czas uruchamiania wszystkich testów.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Uruchamianie testów po każdej kompilacji
::: moniker range="vs-2017"
|Przycisk|Opis|
|-|-|
|![Uruchamianie po kompilacji](../test/media/ute_runafterbuild_btn.png)|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz pozycję **Testuj** w menu standardowym, a następnie wybierz pozycję Uruchom testy po **kompilacji** na pasku narzędzi **Eksploratora** testów.|

> [!NOTE]
> Uruchamianie testów jednostkowych po każdej kompilacji Visual Studio 2017 Enterprise lub Visual Studio 2019. W Visual Studio 2019 r. jest ona uwzględniona w wersji Community i Professional, a także Enterprise.
::: moniker-end
::: moniker range=">=vs-2019"
Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, otwórz ikonę ustawień na pasku narzędzi Eksploratora testów i wybierz pozycję **Uruchom testy po kompilacji.**
::: moniker-end

## <a name="view-test-results"></a>Wyświetlanie wyników testów

Podczas uruchamiania, pisania i ponownego uruchamiania testów Eksplorator testów wyświetla wyniki  w grupach testów nieudanych, testów pomyślnie przekazanych, pominiętych i nie **uruchamianych testów.** W okienku szczegółów w dolnej lub bocznej części Eksploratora testów jest wyświetlane podsumowanie uruchomienia testu.

### <a name="view-test-details"></a>Wyświetlanie szczegółów testu

Aby wyświetlić szczegóły pojedynczego testu, wybierz test.

::: moniker range="vs-2017"
![Szczegóły wykonywania testu](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Szczegóły wykonywania testu](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

W okienku szczegółów testu są wyświetlane następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Czas, który upłynął, jaki trwała metoda testowa.

Jeśli test zakończy się niepowodzeniem, w okienku szczegółów zostaną również wyświetlone:

- Komunikat zwrócony przez platformę testów jednostkowych dla testu.

- Ślad stosu w czasie, gdy test zakończył się niepowodzeniem.

### <a name="view-the-source-code-of-a-test-method"></a>Wyświetlanie kodu źródłowego metody testowej

Aby wyświetlić kod źródłowy metody testowej w edytorze Visual Studio, wybierz test, a następnie wybierz polecenie Otwórz **test** w menu prawym przyciskiem myszy (lub naciśnij **klawisz F12).**

## <a name="group-and-filter-the-test-list"></a>Grupowanie i filtrowanie listy testów

Eksplorator testów umożliwia grupowanie testów w wstępnie zdefiniowane kategorie. Większość platform testów jednostkowych uruchamianych w Eksploratorze testów umożliwia definiowanie własnych kategorii i par kategoria/wartość w celu grupowania testów. Możesz również filtrować listę testów, dopasowując ciągi do właściwości testu.

### <a name="group-tests-in-the-test-list"></a>Testy grupowe na liście testów

::: moniker range="vs-2017"
Aby zmienić sposób organizacji testów, wybierz strzałkę  w dół obok przycisku Grupuj według przycisku Grupa Eksplorator testów i ![ wybierz nowe kryteria ](../test/media/ute_groupby_btn.png) grupowania.

![Grupowanie testów według kategorii w Eksploratorze testów](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Eksplorator testów umożliwia grupowanie testów w hierarchię. Domyślne grupowanie hierarchii to **Projekt,** **Przestrzeń nazw**, a następnie **Klasa**. Aby zmienić sposób organizacji testów,  wybierz przycisk Grupuj według przycisku Grupa Eksploratora testów i ![ wybierz nowe kryteria ](../test/media/ute_groupby_btn.png) grupowania.

![Grupowanie testów według kategorii w Eksploratorze testów](../test/media/vs-2019/test-explorer-groupby-162.png)

Możesz zdefiniować własne poziomy hierarchii i  grupowania  według stanu, a następnie klasy, na przykład wybierając opcje Grupuj według w preferowanej kolejności.

![Zrzut ekranu przedstawiający Visual Studio testów z hierarchią testów w jednym okienku oraz menu Grupuj według w drugim z opcjami Klasa i Stan zaznaczone.](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Grupy Eksploratora testów

::: moniker range="vs-2017"
|Grupa|Opis|
|-|-----------------|
|**Czas trwania**|Grupuje test według czasu wykonywania: **Szybkie,** **Średnie** i **Powolne.**|
|**Wynik**|Grupuje testy według wyników wykonywania: **testy nieudane,** **testy pomijane,** **testy przekazane**.|
|**Cechy**|Grupowanie testuje według par kategorii/wartości, które definiujesz. Składnia określająca kategorie cech i wartości jest definiowana przez platformę testów jednostkowych.|
|**Project**|Grupy są testowe według nazwy projektów.|
::: moniker-end
::: moniker range=">=vs-2019"
|Grupa|Opis|
|-|-----------------|
|**Czas trwania**|Grupuje testy według czasu wykonywania: **Szybkie,** **Średnie** i **Powolne.**|
|**Stan**|Grupuje testy według wyników wykonywania: **testy nieudane,** **testy pominięte,** testy **przekazane,** **nie zostały uruchomione**|
|**Struktura docelowa** | Grupuje testy według struktury docelowej ich projektów |
|**Przestrzeń nazw**|Grupuje testy według zawierającej przestrzeni nazw.|
|**Project**|Grupuje testy według zawierającego projektu.|
|**Klasa**|Grupuje testy według zawierającej klasy.|
::: moniker-end

### <a name="traits"></a>Cechy

Cechą jest zazwyczaj para nazwa/wartość kategorii, ale może również być pojedynczą kategorią. Cechy można przypisać do metod, które są identyfikowane jako metoda testowa przez platformę testów jednostkowych. Na platformie testów jednostkowych można zdefiniować kategorie cech. Możesz dodać wartości do kategorii cech, aby zdefiniować własne pary nazwa/wartość kategorii. Składnia określająca kategorie cech i wartości jest definiowana przez platformę testów jednostkowych.

**Cechy w programie Microsoft Unit Testing Framework dla kodu zarządzanego**

W ramach struktury testów jednostkowych firmy Microsoft dla zarządzanych aplikacji należy zdefiniować parę nazwa/wartość cech w  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atrybutze. Ta platforma testowa zawiera również te wstępnie zdefiniowane cechy:

|Cecha|Opis|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategoria Właściciel jest definiowana przez platformę testów jednostkowych i wymaga podania wartości ciągu właściciela.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategoria Priorytet jest definiowana przez platformę testów jednostkowych i wymaga podania wartości całkowitej priorytetu.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atrybut TestCategory umożliwia określenie kategorii testu jednostkowego.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atrybut TestProperty umożliwia zdefiniowanie pary kategoria/wartość cech.|


**Cechy w programie Microsoft Unit Testing Framework dla języka C++**

Zobacz How to use the Microsoft Unit Testing Framework for C++ (Jak używać struktury [testowania jednostkowego firmy Microsoft dla języka C++).](how-to-use-microsoft-test-framework-for-cpp.md)

## <a name="create-custom-playlists"></a>Tworzenie niestandardowych list odtwarzania

::: moniker range="vs-2017"
Możesz utworzyć i zapisać listę testów, które chcesz uruchomić lub wyświetlić jako grupę. Po wybraniu listy odtwarzania testy na liście są wyświetlane w Eksploratorze testów. Test można dodać do więcej niż jednej listy odtwarzania, a wszystkie testy w projekcie będą dostępne po wybraniu domyślnej **listy odtwarzania Wszystkie testy.**

![Wybieranie listy odtwarzania](../test/media/ute_playlist.png)

**Aby utworzyć listę odtwarzania,** wybierz co najmniej jeden test w Eksploratorze testów. W menu prawym przyciskiem myszy wybierz polecenie Dodaj do **listy odtwarzania**  >  **NowyLista odtwarzania.** Zapisz plik pod nazwą i lokalizacją, które określisz w oknie dialogowym **Tworzenie nowej listy** odtwarzania.

**Aby dodać testy do listy odtwarzania,** wybierz co najmniej jeden test w Eksploratorze testów. W menu po kliknięciu prawym przyciskiem myszy wybierz pozycję Dodaj do listy **odtwarzania,** a następnie wybierz listę odtwarzania, do której chcesz dodać testy.

Aby otworzyć listę  **odtwarzania,** wybierz pozycję Testowa lista odtwarzania z menu usługi Visual Studio, a następnie wybierz listę ostatnio używanych list odtwarzania lub wybierz pozycję Otwórz listę odtwarzania, aby określić nazwę i lokalizację listy >   odtwarzania.

Jeśli poszczególne testy nie mają zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonywanie testów za pomocą ![Zrzut ekranu przedstawiający przycisk przełączania Równoległe wykonywanie testu na pasku Visual Studio Eksplorator testów.](../test/media/ute_parallelicon-small.png) na pasku narzędzi. Może to znacznie skrócić czas uruchamiania wszystkich testów.
::: moniker-end
::: moniker range=">=vs-2019"
Możesz utworzyć i zapisać listę testów, które chcesz uruchomić lub wyświetlić jako grupę. Po wybraniu listy odtwarzania testy na liście są wyświetlane na nowej karcie Eksplorator testów. Test można dodać do więcej niż jednej listy odtwarzania.

**Aby utworzyć listę odtwarzania,** wybierz co najmniej jeden test w Eksploratorze testów. W menu prawym przyciskiem myszy wybierz polecenie Dodaj do **listy odtwarzania Nowa lista**  >  **odtwarzania.**

![Tworzenie listy odtwarzania](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Lista odtwarzania zostanie otwarta na nowej karcie Eksplorator testów. Możesz użyć tej listy odtwarzania raz, a  następnie odrzucić ją lub kliknąć przycisk Zapisz na pasku narzędzi okna listy odtwarzania, a następnie wybrać nazwę i lokalizację, aby zapisać listę odtwarzania.

![Lista odtwarzania zostanie otwarta na osobnej karcie eksploratora testów](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

**Aby utworzyć listę odtwarzania,** wybierz co najmniej jeden test w Eksploratorze testów. Kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj do listy odtwarzania Nowa** lista  >  **odtwarzania.**

**Aby otworzyć listę odtwarzania,** wybierz ikonę listy odtwarzania na pasku narzędzi Visual Studio wybierz z menu wcześniej zapisany plik listy odtwarzania.

**Aby edytować listę odtwarzania,** możesz kliknąć prawym przyciskiem myszy dowolny test i użyć opcji menu, aby dodać listę odtwarzania lub usunąć ją z listy odtwarzania.

Począwszy od Visual Studio 2019 r. w wersji 16.7, możesz wybrać przycisk **Edytuj** na pasku narzędzi. Obok testów będą wyświetlane pola wyboru pokazujące, jakie testy są uwzględniane i wykluczone na liście odtwarzania. Edytuj grupy zgodnie z potrzebami.

![Przycisk Edytuj listę odtwarzania](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

Możesz również sprawdzić lub usunąć zaznaczenie pól grup nadrzędnych w hierarchii. Ta akcja powoduje utworzenie dynamicznej listy odtwarzania, która zawsze aktualizuje listę odtwarzania na podstawie testów, które znajdują się w tej grupie. Jeśli na przykład zaznaczysz znacznik wyboru obok klasy, dowolny test dodany z tej klasy stanie się częścią tej listy odtwarzania. Jeśli usuniesz test z tej klasy, zostanie on usunięty z listy odtwarzania. Aby dowiedzieć się więcej na temat reguł, zapisz listę odtwarzania za pomocą przycisku Zapisz na pasku narzędzi i otwierając plik *listy odtwarzania* utworzony na dysku. Ten plik zawiera listę wszystkich reguł i poszczególnych testów, które są listą odtwarzania.

![Plik XML listy odtwarzania](../test/media/vs-2019/test-explorer-playlist-xml-file.png)

Jeśli chcesz tworzyć listę odtwarzania cech, użyj następującego formatu dla msTest.
```xml
<Playlist Version="2.0">
    <Rule Name="Includes" Match="Any">
        <Property Name="Trait" Value="SchemaUpdateBasic" />
    </Rule>
</Playlist>
```

Użyj następującego formatu dla xUnit. Upewnij się, że między Twoim imieniem i nazwą znajduje się `TestCategory` `[Value]` spacja.
```xml
<Playlist Version="2.0">
  <Rule Name="Includes" Match="Any">
    <Rule Match="All">
      <Property Name="Solution" />
        <Rule Match="Any">
            <Property Name="Trait" Value="TestCategory [Value]" />
        </Rule>
    </Rule>
  </Rule>
</Playlist>
```

::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Kolumny Eksploratora testów

Grupy [są również](#test-explorer-groups) dostępne jako kolumny w Eksploratorze testów wraz z cechami, śladem stosu, komunikatem o błędzie i w pełni kwalifikowaną nazwą. Większość kolumn nie jest domyślnie widoczna i można dostosować wyświetlane kolumny oraz kolejność ich pojawiania się.

![Zrzut ekranu Visual Studio Eksploratora testów przedstawiający menu z wybranymi kolumnami i podmenu z wybranymi opcjami Czas trwania, Cechy i Komunikat o błędzie.](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtrowanie, sortowanie i ponowne rozmieszczanie kolumn testowych

Kolumny można filtrować, sortować i zmieniać ich rozmieszczenie.
* Aby filtrować według określonych cech, kliknij ikonę filtru w górnej części kolumny Traits (Cechy).

  ![Filtr kolumny](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Aby zmienić kolejność kolumn, kliknij nagłówek kolumny i przeciągnij go w lewo lub w prawo.

* Aby posortować kolumnę, kliknij nagłówek kolumny. Nie wszystkie kolumny można sortować. Możesz również sortować według kolumny pomocniczej, przytrzymując klawisz **Shift** i klikając dodatkowy nagłówek kolumny.

  ![Sortowanie kolumn](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Wyszukiwanie i filtrowanie listy testów

Filtry wyszukiwania Eksploratora testów mogą również ograniczać metody testowe w projektach, które są przeglądane i uruchamiane.

Po wpisaniu ciągu w polu wyszukiwania **Eksplorator testów** i wybraniu klawisza **Enter** lista testów jest filtrowana w celu wyświetlenia tylko tych testów, których w pełni kwalifikowane nazwy zawierają ciąg.

Aby filtrować według różnych kryteriów:

1. Otwórz listę rozwijaną po prawej stronie pola wyszukiwania.

2. Wybierz nowe kryteria.

3. Wprowadź wartość filtru między cudzysłowami. Jeśli chcesz wyszukać dokładne dopasowanie w ciągu zamiast zawierającego dopasowania, użyj znaku równości (=) zamiast dwukropka (:).

::: moniker range="vs-2017"
![Filtrowanie testów w Eksploratorze testów](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Filtrowanie testów w Eksploratorze testów](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> W wyszukiwaniach nie jest roz rozwrażliwa na literę i określony ciąg jest do każdej części wartości kryteriów.

::: moniker range="vs-2017"
|Kwalifikator|Opis|
|-|-----------------|
|**Cecha**|Wyszukuje zarówno kategorię cech, jak i wartość dla dopasowania. Składnia określająca kategorie cech i wartości jest definiowana przez platformę testów jednostkowych.|
|**Project**|Wyszukuje dopasowania w nazwach projektów testowych.|
|**Komunikat o błędzie**|Wyszukuje komunikaty o błędach zdefiniowane przez użytkownika zwrócone przez aserty, które zakończyły się niepowodzeniem, pod poszukiwaniu dopasowania.|
|**Ścieżka pliku**|Wyszukuje w pełni kwalifikowaną nazwę pliku testowych plików źródłowych pod poszukiwaniu dopasowania.|
|**W pełni kwalifikowana nazwa**|Wyszukuje w pełni kwalifikowaną nazwę testowych przestrzeni nazw, klas i metod pod poszukiwaniu dopasowania.|
|**Dane wyjściowe**|Wyszukuje zdefiniowane przez użytkownika komunikaty o błędach zapisywane w standardowych danych wyjściowych (stdout) lub błędzie standardowym (stderr). Składnia określająca komunikaty wyjściowe jest definiowana przez platformę testów jednostkowych.|
|**Wynik**|Wyszukuje nazwy kategorii Eksploratora testów pod poszukiwaniu dopasowania: Testy **nieudane,** **Testy pomijane,** **Testy przekazywane**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Kwalifikator|Opis|
|-|-----------------|
|**Stan**|Wyszukuje nazwy kategorii Eksploratora testów pod poszukiwaniu dopasowania: Testy **nieudane,** **Testy pomijane,** **Testy przekazywane**.|
|**Cechy**|Wyszukuje zarówno kategorię cech, jak i wartość dla dopasowania. Składnia określająca kategorie cech i wartości jest definiowana przez platformę testów jednostkowych.|
|**W pełni kwalifikowana nazwa**|Wyszukuje w pełni kwalifikowaną nazwę testowych przestrzeni nazw, klas i metod pod poszukiwaniu dopasowania.|
|**Project**|Wyszukuje dopasowania w nazwach projektów testowych.|
|**Struktura docelowa**|Wyszukuje nazwy kategorii Eksploratora testów pod poszukiwaniu dopasowania: Testy **nieudane,** **Testy pomijane,** **Testy przekazywane**.|
|**Przestrzeń nazw**|Wyszukuje dopasowania w testowych przestrzeniach nazw.|
|**Klasa**|Wyszukuje dopasowania w nazwach klas testów.|
::: moniker-end

Aby wykluczyć podzestaw wyników filtru, użyj następującej składni:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Na przykład funkcja zwraca wszystkie testy, które zawierają w nazwie wartość "MyClass", z wyjątkiem testów, które zawierają również w nazwie `FullName:"MyClass" - FullName:"PerfTest"` wartość "PerfTest".

### <a name="analyze-unit-test-code-coverage"></a>Analizowanie pokrycia kodu testu jednostkowego

Ilość kodu produktu, który jest faktycznie testowany przez testy jednostkowe, można określić przy użyciu narzędzia pokrycia kodu Visual Studio dostępnego w Visual Studio Enterprise edition. Pokrycie kodu można uruchomić dla wybranych testów lub wszystkich testów w rozwiązaniu.

Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu:

::: moniker range="vs-2017"

1. Wybierz **pozycję Test** (Testuj) na górnym pasku menu, a następnie wybierz pozycję Analyze code coverage **(Analizuj pokrycie kodu).**

2. Z menu podrzędnego wybierz jedno z następujących poleceń:

    - **Wybrane testy** uruchamiają metody testowe wybrane w Eksploratorze testów.

    - **Wszystkie testy** uruchamiają wszystkie metody testowe w rozwiązaniu.

::: moniker-end

::: moniker range=">=vs-2019"

* Kliknij prawym przyciskiem myszy w Eksploratorze testów i wybierz **pozycję Analizuj pokrycie kodu dla wybranych testów**

::: moniker-end

W **oknie Wyniki** pokrycia kodu jest wyświetlana wartość procentowa bloków kodu produktu, które były wykonywane według wiersza, funkcji, klasy, przestrzeni nazw i modułu.

Aby uzyskać więcej informacji, zobacz [Używanie pokrycia kodu do określania, ile kodu jest testowane.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="test-shortcuts"></a>Skróty testowe

Testy można uruchamiać z Eksploratora testów, klikając prawym przyciskiem myszy edytor kodu w teście i wybierając polecenie Uruchom **test** lub używając domyślnych skrótów [Eksploratora](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) testów w Visual Studio. Niektóre skróty są oparte na kontekście. Oznacza to, że uruchamiają lub [debugują testy](../test/debug-unit-tests-with-test-explorer.md) w zależności od tego, gdzie znajduje się kursor w edytorze kodu. Jeśli kursor znajduje się wewnątrz metody testowej, zostanie ona uruchomiona. Jeśli kursor znajduje się na poziomie klasy, wszystkie testy w tej klasie są uruchamiane. Jest to również takie samo dla poziomu przestrzeni nazw.

|Częste polecenia| Skróty klawiaturowe|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl** + **R,** **Ctrl** + **T**|
|TestExplorer.RunAllTestsInContext|**Ctrl** + **R,** **T**|
|TestExplorer.RunAllTests|**Ctrl** + **R,** **A**|
|TestExplorer.RepeatLastRun|**Ctrl** + **R,** **L**|

> [!NOTE]
> Nie można uruchomić testu w klasie abstrakcyjnej, ponieważ testy są definiowane tylko w klasach abstrakcyjnych, a nie w wystąpieniach. Aby uruchamiać testy w klasach abstrakcyjnych, utwórz klasę, która pochodzi od klasy abstrakcyjnej.

::: moniker range=">=vs-2019"
## <a name="test-audio-cue"></a>Testowanie sygnału dźwiękowego
Eksplorator testów może odtwarzać dźwięk po zakończeniu testu. Istnieją dwa dźwięki: jeden dźwięk wskazujący, że przebieg testu zakończył się pomyślnie ze wszystkimi testami zakończonymi powodzeniem, i drugi dźwięk wskazujący, że przebieg testu został ukończony z co najmniej jednym testem zakończonym niepowodzeniem. Te dźwięki można skonfigurować w domyślnym oknie dialogowym Windows 10 dźwięku. Ta funkcja jest dostępna od wersji Visual Studio 2019 Update 16.9 (wersja zapoznawcza 3).

1. Otwórz domyślne okno dialogowe Windows 10 dźwięku.
2. Przejdź do karty **Dźwięki.**
3. Znajdź **kategorię Microsoft Visual Studio.** Wybierz dźwięki **Przebieg testu zakończył się pomyślnie** lub Przebieg testu nie powiódł się, aby wybrać wstępnie ustawione dźwięki lub przejść do własnego pliku dźwiękowego.   
![Windows 10 dialogowe dźwięku](../test/media/default-windows-10-sound-dialog.png)

::: moniker-end
## <a name="see-also"></a>Zobacz też

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Debugowanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/debug-unit-tests-with-test-explorer.md)
- [Uruchamianie testu jednostkowego jako procesu 64-bitowego](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Eksplorator testów — często zadawane pytania](test-explorer-faq.md)
