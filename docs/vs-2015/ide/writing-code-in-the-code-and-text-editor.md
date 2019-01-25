---
title: Pisanie kodu w edytorze kodu i tekstu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 62efe11b7c640e228a3b4120259facec3b6f9d4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794244"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Pisanie kodu w edytorze kodu i tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Edytor programu Visual Studio zapewnia wiele funkcji, które ułatwiają umożliwia pisanie kodu i zarządzanie. Można rozwijać i zwijać różne bloki kodu przy użyciu konturów. Dowiedz się więcej o kod, używając za pomocą funkcji IntelliSense, **przeglądarki obiektów**i hierarchii wywoływania. Możesz nawigować wewnątrz kodu przy użyciu funkcji, takich jak **przejdź do**, **przejdź do definicji**, i **Znajdź wszystkie odwołania**. Możesz wstawiać bloki kodu za pomocą wstawek kodu i może wygenerować kod, za pomocą funkcji, takich jak **Generowanie z użycia**. Jeśli po raz pierwszy używasz edytora programu Visual Studio 2015 przed, zobacz [edycji kodu](https://www.visualstudio.com/features/ide-vs) Aby uzyskać szybki przegląd.  

 Możesz wyświetlić swój kod na wiele różnych sposobów. Aby wyświetlić widok klasy dla rozwiązania, możesz otworzyć **Widok klas** okna lub rozwinąć węzły w **Eksploratora rozwiązań** w plikach klas.  

 Możesz wyszukiwać i zamieniać tekst w jednym lub wielu plikach. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md). Jeśli używasz wyrażeń regularnych, należy pamiętać, że znajdowanie i zamienianie teraz używać w wyrażeniach regularnych programu .NET. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 Różne języki Visual Studio oferują różne zestawy funkcji, a w niektórych przypadkach funkcje zachowują się inaczej w różnych językach. Wiele z tych różnic jest określonych w opisach funkcji, ale aby uzyskać więcej informacji można zobaczyć sekcje o określonych językach programu Visual Studio.  

> [!IMPORTANT]
>  Wersja Visual Studio i ustawienia, którego używasz może mieć wpływ na funkcje w IDE. Mogą się różnić od tych opisanych w tym temacie.  

## <a name="editor-features"></a>Funkcje edytora  

|||  
|-|-|  
|Kolorowanie składni|Niektóre elementy składni kodu i pliki znaczników mają inny kolor pozwalający je odróżnić. Na przykład słowa kluczowe (takie jak `using` w języku C# i `Imports` w języku Visual Basic) są jednym kolorze, ale typy (takie jak `Console` i `Uri`) mają inny kolor. Inne elementy składni są także pokolorowane, takie jak ciągi literałów znaków i komentarze. C++ używa kolorów do rozróżniania między typami, wyliczeniami i makrami, między innymi tokenami.<br /><br /> Można zobaczyć domyślny kolor dla każdego typu i możesz zmienić kolor dowolnego elementu składni na [czcionki i kolory, środowisko, opcje, okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), które można otworzyć **narzędzia** menu.|  
|Błąd i znaki ostrzegawcze|Dodaj kod i Skompiluj rozwiązanie, mogą być widoczne faliste podkreślenie () innego koloru (znane jako squiggles) lub (b) żarówki w kodzie. Czerwone symbole oznaczają błędy składni, niebieskie wskazuje błędy kompilatora, zielony oznacza ostrzeżenia i purpurowy oznacza innych rodzajów błędów. [Żarówki](../ide/perform-quick-actions-with-light-bulbs.md) zasugerować poprawki dotyczące problemów, co bardzo ułatwia poprawki.<br /><br /> Możesz zobaczyć domyślny kolor dla każdego błędu i ostrzegawczy wężyk w **narzędzia/Opcje/środowisko/czcionki i kolory** okno dialogowe. Wyszukaj **błąd składniowy**, **błąd kompilatora**, **ostrzeżenie**, i **inny błąd**.|  
|Parowanie nawiasów klamrowych|Gdy punkt wstawiania jest umieszczany na otwartym nawiasie klamrowym w pliku kodu, zarówno on jaki i nawias zamykający są wyróżnione. Ta funkcja zapewnia natychmiastowe informacje zwrotne zagubionych lub brakujących nawiasach klamrowych. Możesz włączyć parowanie nawiasów klamrowych lub wyłączyć za pomocą **automatycznego podkreślania ogranicznika** ustawienie (**narzędzia/Opcje/Edytor tekstu**). Można zmienić kolor podświetlenia w **czcionki i kolory** ustawienie (**narzędzia/Opcje/środowisko**). Wyszukaj **dopasowywanie nawiasów (Podświetl)** lub **parowanie nawiasów klamrowych (prostokąt)**.|  
|Numery wierszy|Numery wierszy mogą być wyświetlane na lewym marginesie w oknie Kod. Nie są wyświetlane domyślnie. Możesz włączyć tę opcję **Edytor tekstu wszystkie języki** ustawień (**języków/wszystkie języki narzędzia/Opcje/edytor**). Można wyświetlić numery wierszy dla poszczególnych języków programowania, zmieniając ustawienia w tych językach (**narzędzia / Opcje / Edytor tekstu /\<języka >**). Numery wierszy były drukowane, należy zaznaczyć Dołącz numery wierszy w **drukowanie** okno dialogowe.|  
|Śledzenie zmian|Kolor lewego marginesu pozwala na śledzenie zmiany wprowadzone w pliku. Zmiany wprowadzone przez użytkownika, ponieważ plik został otwarty, ale nie zostały zapisane, są oznaczane żółtym paskiem na lewym marginesie (znanych jako margines zaznaczania). Po zapisaniu zmian (ale przed zamknięciem pliku) pasek zmieni kolor na zielony. Jeśli po zapisaniu pliku cofniesz zmianę, pasek zmieni kolor na pomarańczowy. Aby włączyć tę funkcję i wyłączonym, zmień **śledzenie zmian** opcji **edytora tekstów** ustawień (**narzędzia/Opcje/Edytor tekstu**).|  
|Zaznaczanie tekstu i kodu|Można zaznaczyć tekst w standardowym trybie strumienia ciągłego lub w trybie okna, w którym są zaznaczasz prostokątny fragment tekstu, zamiast zestawu wierszy. Aby dokonać wyboru w trybie okna, naciśnij ALT podczas przeciągania myszy nad zaznaczeniem (lub naciśnij klawisze ALT + SHIFT + \<Strzałka >). Zaznaczenie obejmuje wszystkie znaki w obrębie prostokąta zdefiniowanego przez pierwszy znak i ostatni znak w zaznaczonym obszarze. Cokolwiek zostanie wpisane lub wklejone do zaznaczonego obszaru, zostanie wstawione w tym samym punkcie w każdym wierszu.|  
|Powiększenie|Możesz można powiększać lub pomniejszać w dowolnym oknie kodu przez naciśnięcie i przytrzymanie klawisza CTRL i przesuwanie kółka przewijania na myszy (lub CTRL + SHIFT +. Aby zwiększyć i CTRL + SHIFT +, aby zmniejszyć). Można również użyć pola powiększenia w lewym dolnym rogu okna kodu, można ustawić procent powiększenia. Funkcja powiększenia nie działa w oknach narzędzi.|  
|Pamięć wirtualna|Domyślnie linie w edytorach Visual Studio kończy za ostatnim znakiem, tak aby klawisz Strzałka w prawo na końcu linii przenosił kursor do początku następnego wiersza. W niektórych innych edytorach wiersz nie kończy się za ostatnim znakiem i umieścić kursor gdziekolwiek w wierszu. Możesz włączyć wirtualną przestrzeń w edytorze w **języków/wszystkie języki narzędzia/Opcje/edytor** ustawienia. Należy pamiętać, że można włączyć opcję **wirtualną przestrzenią** lub **zawijanie**, ale nie oba jednocześnie.|  
|Drukowanie|Możesz użyć opcji w **drukowanie** okno dialogowe, aby dołączyć numery wierszy lub ukryć zwinięte regiony kodu podczas drukowania pliku. W **ustawienia strony** okno dialogowe, również można wydrukować pełną ścieżkę i nazwę pliku, wybierając **nagłówek strony**.<br /><br /> Można ustawić opcje drukowania w kolorze w **narzędzia/Opcje/środowisko/czcionki i kolory** okno dialogowe. Wybierz **drukarki** w **Pokaż ustawienia dla** listy, aby dostosować drukowanie w kolorach. Można określić różne kolory do drukowania pliku, do edycji pliku.|  
|Globalne operacje Cofnij i wykonaj ponownie|**Cofnij ostatnią akcję globalną** i **wykonaj ponownie ostatnią akcję globalną** polecenia na **Edytuj** menu cofnąć lub wykonują ponownie akcje globalne, które wpływają na wiele plików. Akcje globalne obejmują zmianę nazwy klasy lub przestrzeni nazw, wykonywanie operacji znajdowania i zamieniania w całym rozwiązaniu, refaktoryzację bazy danych lub każdą inną czynność, która zmieni wiele plików. Możesz zastosować globalne cofanie i wykonaj ponownie poleceń do akcji w bieżącej sesji programu Visual Studio, nawet po zamknięciu rozwiązania, w którym akcję zastosowano.|  

## <a name="advanced-editing-features"></a>Zaawansowane funkcje edycji  
 Możesz znaleźć wiele zaawansowanych funkcji w **Edycja/zaawansowane** podmenu. Nie wszystkie te funkcje są dostępne dla wszystkich typów plików kodu.  

|||  
|-|-|  
|Formatuj dokument|Ustawia właściwe wcięcia linii kodu i przenosi nawiasy klamrowe, aby rozdzielić linie w dokumencie.|  
|Formatuj zaznaczenie|Ustawia właściwe wcięcia linii kodu i przenosi nawiasy klamrowe, aby rozdzielić linie w zaznaczeniu.|  
|Zmień spacje na tabulatory w zaznaczonych wierszach|Zmienia spacje wiodące na tabulatory, gdzie jest to odpowiednie.|  
|Zmień tabulatory na spacje w zaznaczonych wierszach|Zmienia tabulatory wiodące na spacje. Jeśli chcesz przekonwertować wszystkie spacje w pliku na tabulacje (lub wszystkie tabulacje na spacje), możesz użyć `Edit.ConvertSpacesToTabs` i `Edit.ConvertTabsToSpaces` poleceń. Te polecenia nie są wyświetlane w menu programu Visual Studio, ale można je wywoływać z okna Szybki dostęp lub okna poleceń.|  
|Zmień litery na wielkie|Zmienia wszystkie znaki w zaznaczeniu na wielkie litery, lub jeśli nie zaznaczono żadnego fragmentu, zmienia znak w punkcie wstawiania na wielkie litery.|  
|Zmień litery na małe|Zmienia wszystkie znaki w zaznaczeniu na małe litery, lub jeśli nie zaznaczono żadnego fragmentu, zmienia znak w punkcie wstawiania na małe litery.|  
|Sprawdź poprawność dokumentu|Sprawdza poprawność plików kodu języka JScript.|  
|Usuń biały znak poziome|Usuwa tabulatory lub spacje na końcu bieżącego wiersza.|  
|Wyświetl białe znaki|Wyświetla spacje jako kropki podniesione i tabulatory jako strzałki. Koniec pliku jest wyświetlany jako znacznik prostokątny. Jeśli **narzędzia/Opcje/Edytor Edytor języki/zawijanie wierszy/Pokaż widoczne glify dla zawijania** jest zaznaczone, ten glif jest również wyświetlany.|  
|Zawijanie wyrazów|Powoduje, że wszystkie wiersze w dokumencie mają być wyświetlane w oknie kodu. Włącz zawijanie wyrazów i Włącz w ustawieniach Edytor tekstu wszystkie języki (**narzędzia/Opcje/Edytor tekstu/wszystkie języki**).|  
|Usuń komentarz z zaznaczenia|Dodaje znaki komentarza do bieżącego wiersza lub zaznaczenia.|  
|Dodaj komentarz do zaznaczenia|Usuwa znaki komentarza z bieżącego wiersza lub zaznaczenia.|  
|Zwiększ wcięcie wiersza|Dodaje znak tabulatora (lub równoważne spacje) do wybranych wierszy lub w bieżącym wierszu.|  
|Zmniejsz wcięcie wiersza|Usuwa znak tabulatora (lub równoważne spacje) z wybranych wierszy lub w bieżącym wierszu.|  
|Wybierz Tag|W dokumencie, który zawiera znaczniki (na przykład XML lub HTML) zaznacza znacznik.|  
|Zaznacz zawartość tagu|W dokumencie, który zawiera znaczniki (na przykład XML lub HTML) zaznacza znaczniki.|  

## <a name="navigate-in-the-code-window"></a>Nawigowanie w oknie kodu  
 Może się zmieniają położenie w dokumencie na kilka różnych sposobów. Oprócz standardowych operacji można użyć **Nawiguj wstecz** (lub CTRL + MINUS) i **Nawiguj do przodu** (CTRL + SHIFT + MINUS) do poprzedniego punktu przycisków na pasku narzędzi, aby przenieść wstawiania lokalizacji lub powrócić do nowszych lokalizacji w aktywnym dokumencie. Przyciski te zachowują ostatnich 20 lokalizacji.  

 ![Kierunek przód- tył przyciski nawigacyjne](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")  

 Można również użyć rozszerzonego paska przewijania w oknie kodu można pobrać z lotu ptaka kodu. W trybie mapy, zobacz wersje zapoznawcze kodu, gdy kursor Przenieś w górę i w dół na pasku przewijania, aby uzyskać więcej informacji, zobacz [jak: Śledzenie kodu przez dostosowania paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

 Następujące polecenia są metodami nawigacji specyficznymi dla kodu:  

|||  
|-|-|  
|Przejdź do \<numer wiersza >|(**Edytuj/przejdź do** lub CTRL + G): Przenieś do wiersza o podanym numerze w aktywnym dokumencie.|  
|Przejdź do|(**Edytuj/przejdź do** lub CTRL +): Znajdzie symbol lub pliku w aktywnym rozwiązaniu. Pomaga wybrać dobry zestaw pasujących wyników z zapytania. Można wyszukiwać słowa kluczowe, które są zawarte w symbolu przy użyciu pisane i podkreślenia znaków do podziału symbolu na słowa kluczowe.|  
|Znajdź wszystkie odwołania|(menu kontekstowe): Znajduje wszystkie odwołania do wybranego elementu w rozwiązaniu.|  
|Przejdź do definicji|(menu kontekstowe lub F12): Znajdzie definicję zaznaczonego elementu.|  
|Zobacz definicję|(menu kontekstowe lub Alt + F12): Znajdzie definicję zaznaczonego elementu i wyświetla go w oknie podręcznym. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie i edytowanie kodu za pomocą polecenia Zobacz definicję (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|  
|Następna metoda, Poprzednia metoda|(**Edytuj/Następna metoda, Poprzednia metoda**) plików kodu w języku Visual Basic, użyj tych poleceń, aby przenieść wstawiania wskaż różnych metod.|  
|Wyróżnianie odwołań|Po kliknięciu symbolu w kodzie źródłowym, wszystkie wystąpienia tego symbolu zostaną wyróżnione w dokumencie. Wyróżnione symbole mogą zawierać oświadczenia i odwołania i wiele innych symboli, które **Znajdź wszystkie odwołania** zwróci. Należą do nich nazwy klas, obiektów, zmiennych, metod i właściwości. W kodzie języka Visual Basic słowa kluczowe dla wielu struktur sterowania są również wyróżnione. Aby przejść do następnego lub poprzedniego wyróżnionego symbolu, naciśnij klawisz Strzałka CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę Strzałka. Można zmienić kolor podświetlenia w **narzędzia/Opcje/środowisko/czcionki i kolory/wyróżnione odwołanie.**|  
|Znajdź informacje związane z kodem|Można znaleźć informacje dotyczące konkretnego kodu, takich jak zmian i kto wprowadził te zmiany, odwołania, usterki, elementy robocze, przeglądy kodu i jednostki stan testu w przypadku korzystania z witryny CodeLens w edytorze kodu. CodeLens działa jak ekran projekcyjny, gdy używasz programu Visual Studio Enterprise z programem Team Foundation Server. Zobacz [znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md).|  

 Można również użyć **pasek nawigacyjny**, który, dwa pola listy rozwijanej wyświetlane u góry okna kodu, aby przejść w pliku kodu. Pasek ten pozwala przejść bezpośrednio do określonego typu lub jeden z członków w ramach danego typu. Pasek nawigacyjny pojawia się za pomocą Visual Basic, C# i pliki kodu C++.  

 Aby ukryć pasek nawigacyjny, należy zmienić **pasek nawigacyjny** opcję w ustawieniach Edytor tekstu wszystkie języki (**języków/wszystkie języki narzędzia/Opcje/edytor**, lub zmienić ustawienia dla poszczególnych języków). Nawigacja w oknach list rozwijanych w następujący sposób:  

- Aby przenieść fokus z okna kodu do paska nawigacji, naciśnij kombinację klawiszy skrótu CTRL + F2.  

- Aby zabrać fokus z paska nawigacji do okna kodu, naciśnij klawisz ESC.  

- Aby przenieść fokus z pozycji na pozycję na pasku nawigacyjnym, naciśnij klawisz TAB.  

- Aby zaznaczyć element paska nawigacji, który ma fokus i powrócić do IDE, naciśnij klawisz ENTER  

- Aby przejść do klasy lub typu, kliknij jej nazwę w lewym menu rozwijanym.  

- Aby przejść bezpośrednio do procedury w klasie, kliknij procedurę w prawym menu rozwijanym.  

  W częściowej klasie mogą być wyszarzone elementy członkowskie zdefiniowane poza bieżącym plikiem kodu.  

## <a name="find-code-using-navigate-to"></a>Znajdowanie kodu za pomocą przejdź do
Visual Studio "Przejdź do" polecenie powoduje ukierunkowane wyszukiwanie kodu, aby ułatwić szybkie znajdowanie określonych elementów w plikach kodu, ścieżki do plików i symbole, kod. W przeciwieństwie do innych tekst wyszukiwania, takie jak znaleźć lub Znajdź w plikach przejdź do ogranicza wyszukiwanie do obszarów, w którym przebywa rzeczywisty kod, takich jak pliki, formularze i modułów kodu. Na przykład jeśli wyszukasz ciąg w ASP.NET sieci web aplikacji za pomocą Znajdź lub Znajdź w plikach w całego rozwiązania, możesz otrzymać kilka trafień, w tym wystąpienia ciągu w kodzie uwagi. Za pomocą, przejdź do, jednak możesz tylko otrzymać jednej funkcji, ignorując wszystkie wystąpienia ciągu w kodzie uwagi.

### <a name="navigate-code-using-navigate-to"></a>Przechodzenie do kodu za pomocą przejdź do

1. Otwórz rozwiązanie lub folder w programie Visual Studio.
1. W menu głównym wybierz **Edytuj**, **przejdź do**, lub naciśnij **CTRL +,**.

    Pole tekstowe małych pojawia się w prawym górnym rogu edytora kodu.
1. W polu tekstowym wprowadź nazwę elementu kodu, który ma zostać odnaleziona.

    ![Przejdź do okna](../ide/media/vside-navigatetowindow.png "przejdź do okna")

    Podczas wpisywania, wyniki są wyświetlane na liście rozwijanej poniżej pola tekstowego.
1. Aby przejść do elementu, wybierz go na liście.


### <a name="filter-your-search"></a>Przefiltruj wyszukiwanie

Aby ograniczyć wyszukiwanie, tak aby tylko kod symbole, należy poprzedzić przejdź do zapytania przy użyciu "@" znaków. Na przykład, jeśli wyszukasz `@application`, przejdź do Wyświetla, na przykład tylko klasy, które zawierają słowo "aplikacja" w ich.

Jeśli używasz camelcase w kodzie, szybciej znaleźć elementy kodu, wprowadzając tylko wielkimi literami nazwa elementu kodu. Na przykład, jeśli kod ma składnik o nazwie `ViewSwitcher`, możesz go znaleźć, wprowadzając tylko wielkimi literami nazwę (`"VS"`) przejdź do okna.

![Przejdź do okna — Wyszukiwanie za pomocą literami](../ide/media/vside-capitalsearch.png "przejdź do okna — Wyszukiwanie za pomocą literami")

Ta funkcja jest szczególnie przydatne, jeśli kod ma długich nazwach.

## <a name="customize-the-editor"></a>Dopasowywanie edytora  
 **Import i eksport ustawień**: Można udostępnić ustawienia innemu deweloperowi, ustawienia są zgodne z normą, lub przywrócić ustawienia domyślne programu Visual Studio przy użyciu zostały **Kreatora importowania i eksportowania ustawień** na **narzędzia** menu. Możesz zmienić ustawienia ogólne lub język i ustawienia specyficzne dla projektu.  

 **Mapowanie klawiatury**: Można zdefiniować nowe klawisze dostępu lub zmienić definicje istniejących w ustawieniach narzędzia/Opcje/środowisko/klawiatura. Aby uzyskać więcej informacji o klawiszach dostępu, zobacz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

 Aby uzyskać informacje o opcjach edytora specyficznych dla języka zobacz następujące tematy:  

-   [Ustawienia języka Visual Basic](http://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)  

-   [Używanie środowiska programistycznego Visual Studio dla C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)  

-   [Opcje, Edytor tekstów, JavaScript, Formatowanie](../ide/reference/options-text-editor-javascript-formatting.md)  

## <a name="in-this-section"></a>W tej sekcji  

-   [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)  

-   [Kodowania i znaki podziału wiersza](../ide/encodings-and-line-breaks.md)  

-   [Obramowanie](../ide/outlining.md)  

-   [Refaktoryzacja](../ide/refactoring-in-visual-studio.md)  

-   [Wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)  

-   [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)  

-   [Dostosowywanie edytora](../ide/customizing-the-editor.md)  

-   [Instrukcje: Śledzenie kodu przez dostosowania paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)  

-   [Instrukcje: Wyświetlanie i edytowanie kodu za pomocą polecenia Zobacz definicję (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  

-   [Szybkie wykonywanie akcji dzięki żarówkom](../ide/perform-quick-actions-with-light-bulbs.md)  

-   [Fragmenty kodu](../ide/code-snippets.md)  

-   [Korzystanie z przybornika](../ide/using-the-toolbox.md)  

-   [Wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md)  

-   [Ustawianie zakładek w kodzie](../ide/setting-bookmarks-in-code.md)  

-   [Korzystanie z listy zadań](../ide/using-the-task-list.md)  

-   [Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)  

## <a name="see-also"></a>Zobacz też  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
