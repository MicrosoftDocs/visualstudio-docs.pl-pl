---
title: Funkcje edytora kodu
description: Dowiedz się więcej o funkcjach dostępnych w edytorze kodu w programie Visual Studio, aby ułatwić pisanie kodu i tekstu oraz zarządzanie nim.
ms.custom: SEO-VS-2020
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ec1b8f9d9ce44b494d1d9ad13e3dd46b88d0def5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960406"
---
# <a name="features-of-the-code-editor"></a>Funkcje edytora kodu

Edytor programu Visual Studio udostępnia wiele funkcji, które ułatwiają pisanie kodu i tekstu oraz zarządzanie nim. Możesz rozwijać i zwijać różne bloki kodu przy użyciu konspektu. Więcej informacji na temat kodu można uzyskać, korzystając z funkcji IntelliSense, **Przeglądarka obiektów** i hierarchii wywołań. Można znaleźć kod przy użyciu funkcji, takich jak **Przejdź do**, **Przejdź do definicji** i **Znajdź wszystkie odwołania**. Można wstawiać bloki kodu ze fragmentami kodu i generować kod przy użyciu funkcji, takich jak **generowanie na podstawie użycia**. Jeśli nie korzystasz już z edytora programu Visual Studio, zobacz temat [uczenie się korzystania z edytora kodu](../get-started/tutorial-editor.md).

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz temat [Edytor źródła (Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor).

Możesz wyświetlić swój kod na kilka różnych sposobów. Domyślnie **Eksplorator rozwiązań** pokazuje kod uporządkowany według plików. Możesz kliknąć kartę **Widok klasy** u dołu okna, aby wyświetlić kod zorganizowany według klas.

Można wyszukiwać i zamieniać tekst w jednym lub wielu plikach. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zamienianie tekstu](../ide/finding-and-replacing-text.md). Można używać wyrażeń regularnych do znajdowania i zastępowania tekstu. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Różne języki programu Visual Studio oferują różne zestawy funkcji, a w niektórych przypadkach funkcje działają inaczej w różnych językach. Wiele z tych różnic jest określonych w opisach funkcji, ale aby uzyskać więcej informacji, można zobaczyć sekcje w określonych językach programu Visual Studio.

## <a name="editor-features"></a>Funkcje edytora

|Cecha|Opis|
|-|-|
|Kolorowanie składni|Niektóre elementy składni plików Code i Markup są różne w różny sposób, aby je odróżnić. Na przykład słowa kluczowe (na przykład `using` w języku C# i `Imports` w Visual Basic) są jednym kolorem, ale typy (takie jak `Console` i `Uri` ) są kolejnymi kolorami. Inne elementy składni są również kolorowe, takie jak literały ciągów i komentarze. C++ używa koloru do rozróżniania typów, wyliczeń i makr, między innymi tokenami.<br /><br /> Możesz zobaczyć domyślny kolor dla każdego typu i zmienić kolor dla każdego określonego elementu składni w oknie [dialogowym czcionki i kolory, środowisko, opcje](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), które można otworzyć z menu **Narzędzia** .|
|Znaczniki błędów i ostrzeżeń|Podczas dodawania kodu i kompilowania rozwiązania, mogą pojawić się (a) różne kolorowe faliste podkreślenia (znane jako zygzaki) lub (b) żarówki pojawiające się w kodzie. W kolorze czerwonym są błędy składniowe, niebieskie oznacza błędy kompilatora, czerwone uwagi, a purpurowe oznaczają inne typy błędów. [Szybkie akcje](../ide/quick-actions.md) sugerują poprawki dotyczące problemów i ułatwiają stosowanie poprawki.<br /><br /> Dla każdego błędu i ostrzeżenia można zobaczyć kolor domyślny w oknie   >  dialogowym **Opcje** narzędzi  >    >  **czcionki i kolory** środowiska. Poszukaj **błędu składniowy**, **błędu kompilatora**, **ostrzeżenia** i **innego błędu**.|
|Dopasowywanie nawiasów klamrowych|Gdy punkt wstawiania zostanie umieszczony w otwartym nawiasie klamrowym w pliku kodu, zarówno, jak i zamykającego nawiasu klamrowego są wyróżnione. Ta funkcja umożliwia natychmiastowe przesłanie opinii na temat zagubionych lub brakujących nawiasów klamrowych. Możesz włączać lub wyłączać dopasowanie nawiasów klamrowych przy użyciu ustawienia **automatycznego wyróżniania ogranicznika** (**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**). Kolor wyróżnienia można zmienić w ustawieniu **czcionki i kolory** (**Narzędzia**  >  **Opcje**  >  **środowiska**). Poszukaj **pasującego nawiasu klamrowego (Podświetl)** lub **Dopasowywanie nawiasów klamrowych (prostokąt)**.|
|Wizualizator struktury|Linie kropkowane łączą pasujące nawiasy klamrowe w plikach kodu, co ułatwia wyświetlanie par otwierających i zamykających nawiasów klamrowych. Dzięki temu można szybciej znaleźć kod w bazie kodu. Te linie można włączać lub wyłączać za pomocą **wskazówek Pokaż strukturę** w sekcji **Wyświetlanie** w oknie   >  **Opcje** narzędzia  >  **Edytor tekstu**  >  **Ogólne** strony.|
|Numery wierszy|Numery wierszy mogą być wyświetlane na lewym marginesie okna kod. Domyślnie nie są wyświetlane. Tę opcję można włączyć na stronie ustawienia **Edytor tekstu wszystkie języki** (opcje **narzędzi**  >    >  **Edytor tekstu**  >  **wszystkie języki**). Możesz wyświetlić numery wierszy dla poszczególnych języków programowania, zmieniając ustawienia dla tych języków (opcje **Narzędzia**  >    >  **Edytor tekstu**  >  **\<language>** ). W przypadku numerów wierszy do drukowania należy wybrać opcję **Dołącz numery wierszy** w oknie dialogowym **Drukowanie** .|
|Śledzenie zmian|Kolor lewego marginesu umożliwia śledzenie zmian wprowadzonych w pliku. Zmiany wprowadzone od momentu otwarcia pliku, ale nie zostały zapisane, są oznaczane żółtym paskiem na lewym marginesie (znanym jako margines zaznaczenia). Po zapisaniu zmian (ale przed zamknięciem pliku) pasek zmieni kolor na zielony. W przypadku cofnięcia zmiany po zapisaniu pliku pasek zmieni kolor na pomarańczowy. Aby wyłączyć tę funkcję i włączyć ją, Zmień opcję **Śledź zmiany** w obszarze Ustawienia **edytora tekstu** (opcje **Narzędzia**  >    >  **Edytor tekstu**).|
|Zaznaczanie kodu i tekstu|Możesz zaznaczyć tekst w trybie standardowego ciągłego przesyłania strumieniowego lub w trybie Box, w którym można wybrać prostokątny fragment tekstu zamiast zestawu wierszy. Aby dokonać wyboru w trybie pola, naciśnij klawisz **Alt** podczas przesuwania wskaźnika myszy nad zaznaczeniem (lub naciśnij klawisz **Alt** + **SHIFT** + **\<arrow key>** ). Zaznaczenie zawiera wszystkie znaki w prostokącie zdefiniowanym przez pierwszy znak i ostatni znak w zaznaczeniu. Wszystkie wpisane lub wklejone do zaznaczonego obszaru są wstawiane w tym samym punkcie w każdym wierszu.|
|Zoom|Możesz powiększyć lub pomniejszyć w dowolnym oknie kodu, naciskając i przytrzymując klawisz **Ctrl** i przesuwając kółko przewijania na myszy (lub **Ctrl** + **SHIFT** + **.** Aby zwiększyć i **nacisnąć** + **klawisz Shift** + **,** aby zmniejszyć. Możesz również użyć pola **powiększenie** w lewym dolnym rogu okna kod, aby ustawić określony procent powiększenia. Funkcja zoom nie działa w oknach narzędzi.|
|Wirtualne miejsce|Domyślnie linie w edytorach programu Visual Studio kończą się po ostatnim znaku, dzięki czemu klawisz **Strzałka w prawo** na końcu linii przesuwa kursor na początek następnego wiersza. W niektórych innych edytorach linia nie kończy się po ostatnim znaku, a kursor można umieścić w dowolnym miejscu w wierszu. Możesz włączyć wirtualne miejsce w edytorze w **menu**  >  **Opcje** narzędzia  >  **Edytor tekstu**  >  **wszystkie języki** . Należy pamiętać, że można włączyć opcję **miejsce wirtualne** lub **Zawijanie słów**, ale nie oba.|
|Drukowanie|Możesz użyć opcji w oknie dialogowym **Drukuj** , aby uwzględnić numery wierszy lub ukryć zwinięte regiony kodu podczas drukowania pliku. W oknie dialogowym **Ustawienia strony** można również wydrukować pełną ścieżkę i nazwę pliku, wybierając pozycję **Nagłówek strony**.<br /><br /> Opcje drukowania koloru można ustawić w   >    >    >  oknie dialogowym Opcje narzędzi **czcionki i kolory** środowiska. Wybierz pozycję **drukarka** na liście **Pokaż ustawienia dla** , aby dostosować drukowanie kolorów. Można określić różne kolory do drukowania pliku, niż w przypadku edytowania pliku.|
|Globalne cofanie i ponowne wykonywanie|Polecenia **Cofnij ostatnią akcję globalną** i **Wykonaj ponownie ostatnią akcję globalną** w menu **Edytuj** Cofnij lub wykonaj ponownie działania globalne, które mają wpływ na wiele plików. Akcje globalne obejmują zmianę nazwy klasy lub przestrzeni nazw, wykonywanie operacji znajdowania i zamieniania w ramach rozwiązania, refaktoryzację bazy danych lub dowolną inną akcję, która zmienia wiele plików. Globalne polecenia Cofnij i wykonaj ponownie można zastosować do akcji w bieżącej sesji programu Visual Studio, nawet po zamknięciu rozwiązania, w którym została zastosowana akcja.|

## <a name="advanced-editing-features"></a>Zaawansowane funkcje edycji

Kilka zaawansowanych funkcji można znaleźć w menu **Edytuj**  >  **Zaawansowane** na pasku narzędzi. Nie wszystkie te funkcje są dostępne dla wszystkich typów plików kodu.

|Cecha|Opis|
|-|-|
|Formatuj dokument|Ustawia właściwe wcięcia linii kodu i przenosi nawiasy klamrowe w celu oddzielenia wierszy w dokumencie.|
|Formatowanie zaznaczenia|Ustawia właściwe wcięcia linii kodu i przenosi nawiasy klamrowe w celu oddzielenia wierszy w zaznaczeniu.|
|Na tabulatory wybrane wiersze|Zmienia początkowe spacje na tabulatory, gdzie są odpowiednie.|
|Tabulatory na wybrane wiersze|Zmienia wiodące tabulatory na spacje. Jeśli chcesz przekonwertować wszystkie spacje w pliku na tabulatory (lub wszystkie tabulatory na spacje), możesz użyć `Edit.ConvertSpacesToTabs` `Edit.ConvertTabsToSpaces` poleceń i. Te polecenia nie są wyświetlane w menu programu Visual Studio, ale można je wywoływać z okna **szybkiego dostępu** lub okna poleceń.|
|Zmień wielkie litery|Zmienia wszystkie znaki w zaznaczeniu na wielkie litery, lub jeśli nie ma zaznaczenia, zmienia znak w punkcie wstawiania na wielkie litery. Skrót: **Ctrl** + **SHIFT** + **U**.|
|Zmień na małe litery|Zmienia wszystkie znaki w zaznaczeniu na małe litery, lub jeśli nie ma zaznaczenia, zmienia znak w punkcie wstawiania na małe litery. Skrót: **Ctrl** + **U**.|
|Przesuń wybrane wiersze w górę|Przenosi zaznaczony wiersz o jeden wiersz w górę. Skrót: **Alt** + **Strzałka w górę**.|
|Przesuń wybrane wiersze w dół|Przenosi zaznaczony wiersz w dół o jeden wiersz w dół. Skrót: **Alt** + **Strzałka w dół**.|
|Usuń biały znak w poziomie|Usuwa tabulatory lub spacje na końcu bieżącego wiersza. Skrót: **Ctrl** + **K**, **Ctrl**+**\\**|
|Wyświetl biały znak|Wyświetla spacje jako punkty podniesione i tabulatory jako strzałki. Koniec pliku jest wyświetlany jako symbol prostokątny. Jeśli   >  **Opcje** narzędzi  >  **Edytor tekstu**  >  **wszystkie języki**  >  **zawijania wyrazów**  >  **Pokaż widoczne glify dla zawijania wierszy** jest zaznaczone, ten symbol jest również wyświetlany.|
|Zawijanie wierszy|Powoduje, że wszystkie wiersze w dokumencie będą widoczne w oknie kodu. Możesz włączyć zawijanie wierszy i włączyć je w oknie Ustawienia **edytora tekstu wszystkie języki** (  >  **Opcje** narzędzia  >  **Edytor tekstu**  >  **wszystkie języki**).|
|Zaznacz komentarz|Dodaje znaki komentarza do zaznaczenia lub bieżącego wiersza. Skrót: **Ctrl** + **K**, **Ctrl** + **C**|
|Usuń komentarz z zaznaczenia|Usuwa znaki komentarza z zaznaczenia lub bieżącego wiersza. Skrót: **Ctrl** + **K**, **Ctrl** + **U**|
|Zwiększ wcięcie wiersza|Dodaje tabulator (lub spacje) do wybranych wierszy lub w bieżącym wierszu.|
|Zmniejsz wcięcie wiersza|Usuwa tabulator (lub równoważne spacje) z wybranych wierszy lub z bieżącego wiersza.|
|Wybierz tag|W dokumencie zawierającym znaczniki (na przykład XML lub HTML), wybiera tag.|
|Wybierz zawartość tagów|W dokumencie, który zawiera znaczniki (na przykład XML lub HTML), wybiera zawartość.|

## <a name="navigate-and-find-code"></a>Nawigowanie i znajdowanie kodu

Można poruszać się w edytorze kodu na kilka różnych sposobów, w tym przechodzenie do tyłu i do poprzednich punktów wstawiania, Wyświetlanie definicji typu lub elementu członkowskiego, a następnie przechodzenie do określonej metody przy użyciu paska nawigacyjnego. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Znajdź odwołania w bazie kodu

Aby znaleźć, gdzie poszczególne elementy kodu są przywoływane w bazie kodu, możesz użyć polecenia **Znajdź wszystkie odwołania** lub naciśnij klawisz **SHIFT** + **F12**. Ponadto po kliknięciu typu lub elementu członkowskiego funkcja **wyróżniania odwołań** automatycznie Podświetla wszystkie odwołania do tego typu lub elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).

## <a name="customize-the-editor"></a>Dopasowywanie edytora

Ustawienia programu Visual Studio można udostępniać innym deweloperom, mieć ustawienia zgodne ze standardem lub powrócić do ustawień domyślnych programu Visual Studio za pomocą polecenia **Kreatora importowania i eksportowania ustawień** w menu **Narzędzia** . W **Kreatorze importowania i eksportowania ustawień** można zmienić wybrane ustawienia ogólne lub język i ustawienia specyficzne dla projektu.

Aby zdefiniować nowe klawisze skrótów lub przedefiniować istniejące klawisze skrótów, przejdź do pozycji **Narzędzia**  >  **Opcje**  >    >  **Klawiatura**. Aby uzyskać więcej informacji na temat klawiszy skrótów, zobacz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

W przypadku opcji edytora specyficznych dla języka JavaScript zobacz [Opcje edytora JavaScript](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Zobacz też

- [Edytor źródła (Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Wprowadzenie do języka C++ w programie Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Wprowadzenie do języka C# i ASP.NET w programie Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Wprowadzenie do języka Python w programie Visual Studio](../ide/quickstart-python.md)
