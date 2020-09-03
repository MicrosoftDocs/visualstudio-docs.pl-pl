---
title: Pisanie kodu w edytorze kodu i tekstu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa647d8a8d52588481d18347cb3400141978bd20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548034"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Pisanie kodu w edytorze kodu i tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Edytor programu Visual Studio udostępnia wiele funkcji, które ułatwiają pisanie kodu i zarządzanie nim. Możesz rozwijać i zwijać różne bloki kodu przy użyciu konspektu. Możesz dowiedzieć się więcej o kodzie, którego używasz, korzystając z funkcji IntelliSense, **Przeglądarka obiektów**i hierarchii wywołań. Możesz nawigować wewnątrz kodu przy użyciu funkcji, takich jak **Przejdź do**, **Przejdź do definicji**i **Znajdź wszystkie odwołania**. Można wstawiać bloki kodu ze fragmentami kodu i generować kod przy użyciu funkcji, takich jak **generowanie na podstawie użycia**. Jeśli Edytor programu Visual Studio 2015 nigdy nie był wcześniej używany, zobacz [Edytowanie kodu](https://www.visualstudio.com/features/ide-vs) , aby uzyskać szybki przegląd.

 Możesz wyświetlić swój kod na kilka różnych sposobów. Aby wyświetlić widok klasy rozwiązania, możesz otworzyć okno **Widok klasy** lub rozwinąć węzły w **Eksplorator rozwiązań** w obszarze plików klas.

 Można wyszukiwać i zamieniać tekst dla jednego lub wielu plików. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md). W przypadku używania wyrażeń regularnych należy zauważyć, że funkcja Znajdź i Zamień teraz używa wyrażeń regularnych programu .NET. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Różne języki programu Visual Studio oferują różne zestawy funkcji, a w niektórych przypadkach funkcje działają inaczej w różnych językach. Wiele z tych różnic jest określonych w opisach funkcji, ale aby uzyskać więcej informacji, można zobaczyć sekcje w określonych językach programu Visual Studio.

> [!IMPORTANT]
> Wersja programu Visual Studio i używane ustawienia mogą mieć wpływ na funkcje w środowisku IDE. Mogą się one różnić od tych opisanych w tym temacie.

## <a name="editor-features"></a>Funkcje edytora

|Cechy|Opis|
|-|-|
|Kolorowanie składni|Niektóre elementy składni plików Code i Markup są różne w różny sposób, aby je odróżnić. Na przykład słowa kluczowe (na przykład `using` w języku C# i `Imports` w Visual Basic) są jednym kolorem, ale typy (takie jak `Console` i `Uri` ) są kolejnymi kolorami. Inne elementy składni są również kolorowe, takie jak literały ciągów i komentarze. C++ używa koloru do rozróżniania typów, wyliczeń i makr, między innymi tokenami.<br /><br /> Możesz zobaczyć domyślny kolor dla każdego typu i zmienić kolor dla każdego określonego elementu składni w oknie [dialogowym czcionki i kolory, środowisko, opcje](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), które można otworzyć z menu **Narzędzia** .|
|Znaczniki błędów i ostrzeżeń|Podczas dodawania kodu i kompilowania rozwiązania, mogą pojawić się (a) różne kolorowe faliste podkreślenia (znane jako zygzaki) lub (b) żarówki pojawiające się w kodzie. W kolorze czerwonym są błędy składniowe, niebieskie oznacza błędy kompilatora, czerwone uwagi, a purpurowe oznaczają inne typy błędów. [Żarówki](../ide/perform-quick-actions-with-light-bulbs.md) sugerują poprawki dotyczące problemów i ułatwiają stosowanie poprawki.<br /><br /> W oknie dialogowym **Narzędzia/Opcje/środowisko/czcionki i kolory** można zobaczyć domyślny kolor poszczególnych błędów i ostrzeżeń. Poszukaj **błędu składniowy**, **błędu kompilatora**, **ostrzeżenia**i **innego błędu**.|
|Dopasowywanie nawiasów klamrowych|Gdy punkt wstawiania zostanie umieszczony w otwartym nawiasie klamrowym w pliku kodu, zarówno, jak i zamykającego nawiasu klamrowego są wyróżnione. Ta funkcja umożliwia natychmiastowe przesłanie opinii na temat zagubionych lub brakujących nawiasów klamrowych. Można włączać lub wyłączać dopasowanie nawiasów klamrowych przy użyciu ustawienia **automatycznego wyróżniania ogranicznika** (**Narzędzia/Opcje/Edytor tekstu**). Możesz zmienić kolor podświetlenia w ustawieniu **czcionki i kolory** (**Narzędzia/Opcje/środowisko**). Poszukaj **pasującego nawiasu klamrowego (Podświetl)** lub **Dopasowywanie nawiasów klamrowych (prostokąt)**.|
|Numery wierszy|Numery wierszy mogą być wyświetlane na lewym marginesie okna kod. Domyślnie nie są wyświetlane. Tę opcję można włączyć w ustawieniach **Edytor tekstu wszystkie języki** (**Narzędzia/Opcje/Edytor tekstu/wszystkie języki**). Możesz wyświetlić numery wierszy dla poszczególnych języków programowania, zmieniając ustawienia dla tych języków (**Narzędzia/Opcje/Edytor tekstu/ \<language> **). W przypadku numerów wierszy do drukowania należy wybrać opcję Dołącz numery wierszy w oknie dialogowym **Drukowanie** .|
|Śledzenie zmian|Kolor lewego marginesu umożliwia śledzenie zmian wprowadzonych w pliku. Zmiany wprowadzone od momentu otwarcia pliku, ale nie zostały zapisane, są oznaczane żółtym paskiem na lewym marginesie (znanym jako margines zaznaczenia). Po zapisaniu zmian (ale przed zamknięciem pliku) pasek zmieni kolor na zielony. W przypadku cofnięcia zmiany po zapisaniu pliku pasek zmieni kolor na pomarańczowy. Aby wyłączyć tę funkcję i włączyć ją, Zmień opcję **Śledź zmiany** w ustawieniach **edytora tekstu** (**Narzędzia/Opcje/Edytor tekstu**).|
|Zaznaczanie kodu i tekstu|Możesz zaznaczyć tekst w trybie standardowego ciągłego przesyłania strumieniowego lub w trybie Box, w którym można wybrać prostokątny fragment tekstu zamiast zestawu wierszy. Aby dokonać wyboru w trybie pola, naciśnij klawisz ALT podczas przeciągania wskaźnika myszy nad zaznaczeniem (lub naciśnij klawisze ALT + SHIFT + \<arrow key> ). Zaznaczenie zawiera wszystkie znaki w prostokącie zdefiniowanym przez pierwszy znak i ostatni znak w zaznaczeniu. Wszystkie wpisane lub wklejone do zaznaczonego obszaru są wstawiane w tym samym punkcie w każdym wierszu.|
|Zoom|Możesz powiększyć lub pomniejszyć w dowolnym oknie kodu, naciskając i przytrzymując klawisz CTRL i przesuwając kółko przewijania na myszy (lub CTRL + SHIFT +). Aby zwiększyć i nacisnąć klawisze CTRL + SHIFT +, aby zmniejszyć. Możesz również użyć pola powiększenie w lewym dolnym rogu okna kod, aby ustawić określony procent powiększenia. Funkcja zoom nie działa w oknach narzędzi.|
|Wirtualne miejsce|Domyślnie linie w edytorach programu Visual Studio kończą się po ostatnim znaku, dzięki czemu klawisz Strzałka w prawo na końcu linii przesuwa kursor na początek następnego wiersza. W niektórych innych edytorach linia nie kończy się po ostatnim znaku, a kursor można umieścić w dowolnym miejscu w wierszu. Możesz włączyć wirtualne miejsce w edytorze w ustawieniach **Narzędzia/Opcje/Edytor tekstu/wszystkie języki** . Należy pamiętać, że można włączyć opcję **miejsce wirtualne** lub **Zawijanie słów**, ale nie oba.|
|Drukowanie|Możesz użyć opcji w oknie dialogowym **Drukuj** , aby uwzględnić numery wierszy lub ukryć zwinięte regiony kodu podczas drukowania pliku. W oknie dialogowym **Ustawienia strony** można również wydrukować pełną ścieżkę i nazwę pliku, wybierając pozycję **Nagłówek strony**.<br /><br /> Opcje drukowania kolorów można ustawić w oknie dialogowym **Narzędzia/Opcje/środowisko/czcionki i kolory** . Wybierz pozycję **drukarka** na liście **Pokaż ustawienia dla** , aby dostosować drukowanie kolorów. Można określić różne kolory do drukowania pliku, niż w przypadku edytowania pliku.|
|Globalne cofanie i ponowne wykonywanie|Polecenia **Cofnij ostatnią akcję globalną** i **Wykonaj ponownie ostatnią akcję globalną** w menu **Edytuj** Cofnij lub wykonaj ponownie działania globalne, które mają wpływ na wiele plików. Akcje globalne obejmują zmianę nazwy klasy lub przestrzeni nazw, wykonywanie operacji znajdowania i zamieniania w ramach rozwiązania, refaktoryzację bazy danych lub dowolną inną akcję, która zmienia wiele plików. Globalne polecenia Cofnij i wykonaj ponownie można zastosować do akcji w bieżącej sesji programu Visual Studio, nawet po zamknięciu rozwiązania, w którym została zastosowana akcja.|

## <a name="advanced-editing-features"></a>Zaawansowane funkcje edycji
 Kilka zaawansowanych funkcji można znaleźć w podmenu **Edytuj/zaawansowane** . Nie wszystkie te funkcje są dostępne dla wszystkich typów plików kodu.

|Cechy|Opis|
|-|-|
|Formatuj dokument|Ustawia właściwe wcięcia linii kodu i przenosi nawiasy klamrowe w celu oddzielenia wierszy w dokumencie.|
|Formatowanie zaznaczenia|Ustawia właściwe wcięcia linii kodu i przenosi nawiasy klamrowe w celu oddzielenia wierszy w zaznaczeniu.|
|Na tabulatory wybrane wiersze|Zmienia początkowe spacje na tabulatory, gdzie są odpowiednie.|
|Tabulatory na wybrane wiersze|Zmienia wiodące tabulatory na spacje. Jeśli chcesz przekonwertować wszystkie spacje w pliku na tabulatory (lub wszystkie tabulatory na spacje), możesz użyć `Edit.ConvertSpacesToTabs` `Edit.ConvertTabsToSpaces` poleceń i. Te polecenia nie są wyświetlane w menu programu Visual Studio, ale można je wywoływać z okna szybkiego dostępu lub okna poleceń.|
|Zmień wielkie litery|Zmienia wszystkie znaki w zaznaczeniu na wielkie litery, lub jeśli nie ma zaznaczenia, zmienia znak w punkcie wstawiania na wielkie litery.|
|Zmień na małe litery|Zmienia wszystkie znaki w zaznaczeniu na małe litery, lub jeśli nie ma zaznaczenia, zmienia znak w punkcie wstawiania na małe litery.|
|Sprawdź poprawność dokumentu|Sprawdza poprawność plików kodu JScript.|
|Usuń biały znak w poziomie|Usuwa tabulatory lub spacje na końcu bieżącego wiersza.|
|Wyświetl biały znak|Wyświetla spacje jako punkty podniesione i tabulatory jako strzałki. Koniec pliku jest wyświetlany jako symbol prostokątny. Jeśli zaznaczone są **Narzędzia/Opcje/Edytor tekstu/wszystkie języki/zawijanie wyrazów/Pokaż widoczne glify dla zawijania wierszy** , ten symbol jest również wyświetlany.|
|Zawijanie wierszy|Powoduje, że wszystkie wiersze w dokumencie będą widoczne w oknie kodu. Możesz włączyć zawijanie wierszy i włączyć je w oknie Edytor tekstu wszystkie języki (**Narzędzia/Opcje/Edytor tekstu/wszystkie języki**).|
|Usuń komentarz z zaznaczenia|Dodaje znaki komentarza do zaznaczenia lub bieżącego wiersza.|
|Zaznacz komentarz|Usuwa znaki komentarza z zaznaczenia lub bieżącego wiersza.|
|Zwiększ wcięcie wiersza|Dodaje tabulator (lub spacje) do wybranych wierszy lub w bieżącym wierszu.|
|Zmniejsz wcięcie wiersza|Usuwa tabulator (lub równoważne spacje) z wybranych wierszy lub z bieżącego wiersza.|
|Wybierz tag|W dokumencie zawierającym znaczniki (na przykład XML lub HTML), wybiera tag.|
|Wybierz zawartość tagów|W dokumencie, który zawiera znaczniki (na przykład XML lub HTML), wybiera zawartość.|

## <a name="navigate-in-the-code-window"></a>Nawigowanie w oknie kod
 Możesz poruszać się w dokumencie na kilka różnych sposobów. Oprócz standardowych operacji można użyć przycisków **Nawiguj wstecz** (lub CTRL + minus) i **Przejdź do przodu** (Ctrl + Shift + minus) na pasku narzędzi, aby przenieść punkt wstawiania do poprzednich lokalizacji lub wrócić do nowszych lokalizacji w aktywnym dokumencie. Przyciski te zachowują ostatnie 20 lokalizacji punktu wstawiania.

 ![Przyciski nawigacji do przodu i do tyłu](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")

 Możesz również użyć rozszerzonego paska przewijania w oknie kodu, aby uzyskać wgląd w swój kod w oczy. W trybie mapy można zobaczyć podglądy kodu podczas przesuwania kursora w górę i w dół paska przewijania, aby uzyskać więcej informacji, zobacz [How to: Tracking The Code, dostosowując pasek przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

 Następujące polecenia są metodami nawigacji specyficznymi dla kodu:

|Polecenie|Opis|
|-|-|
|Przejdź do \<line number>|(**Edytuj/przejdź do** lub CTRL + G): przenosi do określonego numeru wiersza w aktywnym dokumencie.|
|Przejdź do|(**Edytuj/Nawiguj do** lub CTRL +,): znajduje symbol lub plik w aktywnym rozwiązaniu. Ułatwia wybór dobrego zestawu pasujących wyników zapytania. Słowa kluczowe, które są zawarte w symbolu, można wyszukiwać przy użyciu znaków notacji CamelCase i podkreślenia, aby podzielić symbol na słowa kluczowe.|
|Znajdź wszystkie odwołania|(menu kontekstowe): znajduje wszystkie odwołania do wybranego elementu w rozwiązaniu.|
|Przejdź do definicji|(menu kontekstowe lub F12): znajduje definicję wybranego elementu.|
|Podejrzyj definicję|(menu kontekstowe lub Alt + F12): znajduje definicję wybranego elementu i wyświetla go w oknie podręcznym. Aby uzyskać więcej informacji, zobacz [How to: wyświetlanie i edytowanie kodu za pomocą definicji wglądu (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|
|Next, metoda, poprzednia Metoda|(**Edycja/Następna Metoda, poprzednia Metoda**) W Visual Basic pliki kodu Użyj tych poleceń, aby przenieść punkt wstawiania do różnych metod.|
|Wyróżnianie odwołań|Gdy klikniesz symbol w kodzie źródłowym, wszystkie wystąpienia tego symbolu zostaną wyróżnione w dokumencie. Wyróżnione symbole mogą zawierać deklaracje i odwołania, a wiele innych symboli, które będą zwracać **wszystkie odwołania** . Obejmują one nazwy klas, obiektów, zmiennych, metod i właściwości. W kodzie Visual Basic są również wyróżnione słowa kluczowe dla wielu struktur kontroli. Aby przejść do następnego lub poprzedniego wyróżnionego symbolu, naciśnij klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę. Możesz zmienić kolor wyróżnienia w obszarze **Narzędzia/Opcje/środowisko/czcionki i kolory/wyróżnione odwołanie.**|
|Znajdź informacje związane z kodem|W edytorze kodu można znaleźć informacje o konkretnym kodzie, takie jak zmiany i osoby, które wprowadziły te zmiany, odwołania, błędy, elementy robocze, przeglądy kodu i stan testu jednostkowego. CodeLens działa jak w przypadku wyświetlania głowic w przypadku używania Visual Studio Enterprise z Team Foundation Server. Zobacz [Znajdowanie zmian w kodzie i innych historii](../ide/find-code-changes-and-other-history-with-codelens.md).|

 Możesz również użyć **paska nawigacyjnego**, czyli dwóch pól listy rozwijanej wyświetlanych u góry okna kod, aby nawigować w pliku kodu. Ten pasek umożliwia przejście bezpośrednio do określonego typu lub do jednego z elementów członkowskich w ramach typu. Pasek nawigacyjny pojawia się z plikami kodu Visual Basic, C# i C++.

 Aby ukryć pasek nawigacyjny, Zmień opcję **pasek nawigacyjny** w ustawieniach Edytor tekstu wszystkie języki (**Narzędzia/Opcje/Edytor tekstu/wszystkie języki**lub można zmienić ustawienia dla poszczególnych języków). Możesz nawigować w polach listy rozwijanej w następujący sposób:

- Aby przenieść fokus z okna kod na pasek nawigacyjny, naciśnij kombinację klawiszy skrótu CTRL + F2.

- Aby zwrócić fokus z paska nawigacyjnego do okna kodu, naciśnij klawisz ESC.

- Aby przenieść fokus z elementu do elementu na pasku nawigacyjnym, naciśnij klawisz TAB.

- Aby wybrać element paska nawigacyjnego, który ma fokus, i powrócić do środowiska IDE, naciśnij klawisz ENTER.

- Aby przejść do klasy lub typu, kliknij jej nazwę w lewym menu rozwijanym.

- Aby przejść bezpośrednio do procedury w klasie, kliknij procedurę na liście rozwijanej po prawej stronie.

  W klasie częściowej elementy członkowskie zdefiniowane poza bieżącym plikiem kodu mogą być wyszarzone.

## <a name="find-code-using-navigate-to"></a>Znajdź kod przy użyciu przejdź do
Polecenie "przejdź do" programu Visual Studio umożliwia skoncentrowane wyszukiwanie kodu w celu ułatwienia szybkiego znajdowania określonych elementów w plikach kodu, ścieżkach plików i symbolach kodu. W przeciwieństwie do innych wyszukiwania tekstu, takich jak Znajdź lub Znajdź w plikach, przejdź do obszaru wyszukiwania, aby ograniczyć jego wyszukiwanie do obszarów, w których faktycznie przebywa kod, takich jak pliki, formularze i moduły kodu. Na przykład jeśli szukasz ciągu w aplikacji sieci Web ASP.NET przy użyciu funkcji Znajdź lub Znajdź w plikach w całym rozwiązaniu, możesz uzyskać kilka trafień, w tym wystąpienia ciągu w uwagach do kodu. Korzystając z przechodzenia do, można jednak uzyskać tylko jedną funkcję, ignorując wszystkie wystąpienia ciągu w uwagach do kodu.

### <a name="navigate-code-using-navigate-to"></a>Nawigowanie po kodzie przy użyciu przejdź do

1. Otwórz rozwiązanie lub folder w programie Visual Studio.
1. W menu głównym wybierz polecenie **Edytuj**, **Przejdź do**lub naciśnij **klawisze CTRL +,**.

    Małe pole tekstowe pojawia się w górnym rogu edytora kodu.
1. W polu tekstowym wprowadź nazwę elementu kodu, który ma zostać znaleziony.

    ![Przejdź do okna](../ide/media/vside-navigatetowindow.png "Przejdź do okna")

    Podczas pisania, wyniki pojawiają się na liście rozwijanej poniżej pola tekstowego.
1. Aby przejść do elementu, wybierz go z listy.

### <a name="filter-your-search"></a>Filtrowanie wyszukiwania

Aby ograniczyć wyszukiwanie tylko do symboli, należy poprzedzić przechodzenie do zapytania za pomocą znaku " \@ ". Na przykład, jeśli szukasz `@application` , przejdź do wyświetlania, na przykład, tylko klasy, które mają wyraz "aplikacja".

Jeśli używasz notacji CamelCase wielkości liter w kodzie, możesz znaleźć elementy kodu szybciej, wprowadzając tylko wielkie litery nazwy elementu kodu. Na przykład jeśli kod zawiera składnik o nazwie, można `ViewSwitcher` go znaleźć, wprowadzając tylko wielkie litery nazwy ( `"VS"` ) w oknie przechodzenie do.

![Przejdź do okna — wyszukiwanie przy użyciu wersalików](../ide/media/vside-capitalsearch.png "Przejdź do okna — wyszukiwanie przy użyciu wersalików")

Ta funkcja jest szczególnie przydatna, jeśli kod ma długie nazwy.

## <a name="customize-the-editor"></a>Dostosowywanie edytora
 **Importowanie i eksportowanie ustawień**: można udostępniać ustawienia innym deweloperom, mieć ustawienia zgodne ze standardem lub powrócić do ustawień domyślnych programu Visual Studio za pomocą **Kreatora importowania i eksportowania ustawień** w menu **Narzędzia** . Można zmienić ustawienia ogólne lub język i ustawienia specyficzne dla projektu.

 **Mapowanie klawiatury**: można zdefiniować nowe klawisze skrótów lub ponownie zdefiniować istniejące w ustawieniach narzędzia/opcje/środowisko/klawiatura. Aby uzyskać więcej informacji na temat klawiszy skrótów, zobacz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Aby uzyskać informacje na temat opcji edytora specyficznych dla języka, zobacz następujące tematy:

- [Ustawienia Visual Basic](https://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)

- [Używanie środowiska programistycznego Visual Studio dla języka C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)

- [Opcje, Edytor tekstów, JavaScript, Formatowanie](../ide/reference/options-text-editor-javascript-formatting.md)

## <a name="in-this-section"></a>W tej sekcji

- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)

- [Kodowania i podziały wierszy](../ide/encodings-and-line-breaks.md)

- [Tworzenie konspektu](../ide/outlining.md)

- [Refaktoryzacja](../ide/refactoring-in-visual-studio.md)

- [Porady dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)

- [Dopasowywanie edytora](../ide/customizing-the-editor.md)

- [Instrukcje: Śledzenie kodu przez dostosowania paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)

- [Porady: Podgląd i edycja kodu za pomocą definicji wglądu (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

- [Szybkie wykonywanie akcji dzięki żarówkom](../ide/perform-quick-actions-with-light-bulbs.md)

- [Fragmenty kodu](../ide/code-snippets.md)

- [Korzystanie z przybornika](../ide/using-the-toolbox.md)

- [Wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md)

- [Ustawianie zakładek w kodzie](../ide/setting-bookmarks-in-code.md)

- [Korzystanie z listy zadań](../ide/using-the-task-list.md)

- [Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)

## <a name="see-also"></a>Zobacz też
 [Visual Studio IDE](../ide/visual-studio-ide.md)
