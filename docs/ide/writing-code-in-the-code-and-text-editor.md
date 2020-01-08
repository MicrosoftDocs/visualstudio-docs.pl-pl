---
title: Funkcje edytora kodu
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de209e0a940fe7f7c64644cea37de3762df0d643
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588554"
---
# <a name="features-of-the-code-editor"></a>Funkcje edytora kodu

Edytor programu Visual Studio zapewnia wiele funkcji, które ułatwiają zapis i zarządzanie nimi, tekstu i kodu. Można rozwijać i zwijać różne bloki kodu przy użyciu konturów. Więcej o kodzie można znaleźć za pomocą technologii IntelliSense, **przeglądarki obiektów**i hierarchii wywoływania. Kod można znaleźć przy użyciu funkcji, takich jak **przejdź do**, **przejdź do definicji**, i **Znajdź wszystkie odwołania**. Możesz wstawiać bloki kodu za pomocą wstawek kodu i może wygenerować kod, za pomocą funkcji, takich jak **Generowanie z użycia**. Jeśli nie korzystasz już z edytora programu Visual Studio, zobacz temat [uczenie się korzystania z edytora kodu](../get-started/tutorial-editor.md).

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [Edytor źródła (program Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor).

Możesz wyświetlić swój kod na wiele różnych sposobów. Domyślnie **Eksploratora rozwiązań** pokazuje kod zorganizowane w pliki. Możesz kliknąć **Widok klas** karta w dolnej części okna, aby wyświetlić kod uporządkowane według klasy.

Możesz wyszukiwać i zamieniać tekst w jednym lub wielu plikach. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md). Za używanie wyrażeń regularnych do znajdowania i zamieniania tekstu. Aby uzyskać więcej informacji, zobacz [używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Różne języki Visual Studio oferują różne zestawy funkcji, a w niektórych przypadkach funkcje zachowują się inaczej w różnych językach. Wiele z tych różnic jest określonych w opisach funkcji, ale aby uzyskać więcej informacji można zobaczyć sekcje o określonych językach programu Visual Studio.

## <a name="editor-features"></a>Funkcje edytora

|||
|-|-|
|Kolorowanie składni|Niektóre elementy składni kodu i pliki znaczników mają inny kolor pozwalający je odróżnić. Na przykład słowa kluczowe (takie jak `using` w języku C# i `Imports` w języku Visual Basic) są jednym kolorze, ale typy (takie jak `Console` i `Uri`) mają inny kolor. Inne elementy składni są także pokolorowane, takie jak ciągi literałów znaków i komentarze. C++ używa kolorów do rozróżniania między typami, wyliczeniami i makrami, między innymi tokenami.<br /><br /> Można zobaczyć domyślny kolor dla każdego typu i możesz zmienić kolor dowolnego elementu składni na [czcionki i kolory, środowisko, opcje, okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), które można otworzyć **narzędzia** menu.|
|Błąd i znaki ostrzegawcze|Dodaj kod i Skompiluj rozwiązanie, mogą być widoczne faliste podkreślenie () innego koloru (znane jako squiggles) lub (b) żarówki w kodzie. Czerwone symbole oznaczają błędy składni, niebieskie wskazuje błędy kompilatora, zielony oznacza ostrzeżenia i purpurowy oznacza innych rodzajów błędów. [Szybkie akcje](../ide/quick-actions.md) zasugerować poprawki dotyczące problemów, co bardzo ułatwia poprawki.<br /><br /> Możesz zobaczyć domyślny kolor dla każdego błędu i ostrzegawczy wężyk w **narzędzia** > **opcje** > **środowiska**  >   **Czcionki i kolory** okno dialogowe. Wyszukaj **błąd składniowy**, **błąd kompilatora**, **ostrzeżenie**, i **inny błąd**.|
|Parowanie nawiasów klamrowych|Gdy punkt wstawiania jest umieszczany na otwartym nawiasie klamrowym w pliku kodu, zarówno on jaki i nawias zamykający są wyróżnione. Ta funkcja zapewnia natychmiastowe informacje zwrotne zagubionych lub brakujących nawiasach klamrowych. Możesz włączyć parowanie nawiasów klamrowych lub wyłączyć za pomocą **automatycznego podkreślania ogranicznika** ustawienie (**narzędzia** > **opcje**  >   **Edytor tekstu**). Można zmienić kolor podświetlenia w **czcionki i kolory** ustawienie (**narzędzia** > **opcje** > **środowiska**). Wyszukaj **dopasowywanie nawiasów (Podświetl)** lub **parowanie nawiasów klamrowych (prostokąt)** .|
|Wizualizator struktury|Linii kropkowanej połączyć pasujące nawiasy klamrowe w plikach kodu, dzięki czemu łatwiej jest zobaczyć otwierający i zamykający nawias klamrowy pary. To pomoże Ci znaleźć kod w Twojej bazie kodu szybciej. Można włączyć te wiersze lub wyłączyć za pomocą **Pokaż wskazówki dotyczące struktury** w **wyświetlania** części **narzędzia** > **opcje**  >  **Edytora tekstów** > **ogólne** strony.|
|Numery wierszy|Numery wierszy mogą być wyświetlane na lewym marginesie w oknie Kod. Nie są wyświetlane domyślnie. Możesz włączyć tę opcję **Edytor tekstu wszystkie języki** ustawień (**narzędzia** > **opcje** > **edytora tekstów**  >  **Wszystkie języki**). Można wyświetlić numery wierszy dla poszczególnych języków programowania, zmieniając ustawienia w tych językach (**narzędzia** > **opcje** > **Edytor tekstu**   >   **\<języka >** ). Numery wierszy były drukowane, należy wybrać **dołączyć numery wierszy** w **drukowanie** okno dialogowe.|
|Śledzenie zmian|Kolor lewego marginesu pozwala na śledzenie zmiany wprowadzone w pliku. Zmiany wprowadzone przez użytkownika, ponieważ plik został otwarty, ale nie zostały zapisane, są oznaczane żółtym paskiem na lewym marginesie (znanych jako margines zaznaczania). Po zapisaniu zmian (ale przed zamknięciem pliku) pasek zmieni kolor na zielony. Jeśli po zapisaniu pliku cofniesz zmianę, pasek zmieni kolor na pomarańczowy. Aby włączyć tę funkcję i wyłączonym, zmień **śledzenie zmian** opcji **edytora tekstów** ustawień (**narzędzia** > **opcje**  >  **Edytora tekstów**).|
|Zaznaczanie tekstu i kodu|Można zaznaczyć tekst w standardowym trybie strumienia ciągłego lub w trybie okna, w którym są zaznaczasz prostokątny fragment tekstu, zamiast zestawu wierszy. Aby dokonać wyboru w trybie okna, naciśnij klawisze **Alt** podczas przeciągania myszy nad zaznaczeniem (lub naciśnij **Alt**+**Shift** +  **\<Strzałka >** ). Zaznaczenie obejmuje wszystkie znaki w obrębie prostokąta zdefiniowanego przez pierwszy znak i ostatni znak w zaznaczonym obszarze. Cokolwiek zostanie wpisane lub wklejone do zaznaczonego obszaru, zostanie wstawione w tym samym punkcie w każdym wierszu.|
|Powiększenie|Możesz można powiększać lub pomniejszać w dowolnym oknie kodu przez naciśnięcie i przytrzymanie **Ctrl** klucz i przesuwanie kółka przewijania na myszy (lub **Ctrl**+**Shift** + **.** Aby zwiększyć i **Ctrl**+**Shift**+ **,** zmniejszyć). Można również użyć **powiększenia** pole w lewym dolnym rogu okna kodu, aby ustawić procent powiększenia. Funkcja powiększenia nie działa w oknach narzędzi.|
|Pamięć wirtualna|Domyślnie wierszy w celu edytory programu Visual Studio za ostatnim znakiem, tak aby **Strzałka w prawo** klucza na końcu linii przenosił kursor do początku następnego wiersza. W niektórych innych edytorach wiersz nie kończy się za ostatnim znakiem i umieścić kursor gdziekolwiek w wierszu. Możesz włączyć wirtualną przestrzeń w edytorze w **narzędzia** > **opcje** > **edytora tekstów** > **wszystkie Języki** ustawienia. Należy pamiętać, że można włączyć opcję **wirtualną przestrzenią** lub **zawijanie**, ale nie oba jednocześnie.|
|Drukowanie|Możesz użyć opcji w **drukowanie** okno dialogowe, aby dołączyć numery wierszy lub ukryć zwinięte regiony kodu podczas drukowania pliku. W **ustawienia strony** okno dialogowe, również można wydrukować pełną ścieżkę i nazwę pliku, wybierając **nagłówek strony**.<br /><br /> Można ustawić opcje drukowania w kolorze w **narzędzia** > **opcje** > **środowiska** > **czcionek i Kolory** okno dialogowe. Wybierz **drukarki** w **Pokaż ustawienia dla** listy, aby dostosować drukowanie w kolorach. Można określić różne kolory do drukowania pliku, do edycji pliku.|
|Globalne operacje Cofnij i wykonaj ponownie|**Cofnij ostatnią akcję globalną** i **wykonaj ponownie ostatnią akcję globalną** polecenia na **Edytuj** menu cofnąć lub wykonują ponownie akcje globalne, które wpływają na wiele plików. Akcje globalne obejmują zmianę nazwy klasy lub przestrzeni nazw, wykonywanie operacji znajdowania i zamieniania w całym rozwiązaniu, refaktoryzację bazy danych lub każdą inną czynność, która zmieni wiele plików. Możesz zastosować globalne cofanie i wykonaj ponownie poleceń do akcji w bieżącej sesji programu Visual Studio, nawet po zamknięciu rozwiązania, w którym akcję zastosowano.|

## <a name="advanced-editing-features"></a>Zaawansowane funkcje edycji

Możesz znaleźć wiele zaawansowanych funkcji w **Edytuj** > **zaawansowane** menu na pasku narzędzi. Nie wszystkie te funkcje są dostępne dla wszystkich typów plików kodu.

|||
|-|-|
|Formatuj dokument|Ustawia właściwe wcięcia linii kodu i przenosi nawiasy klamrowe, aby rozdzielić linie w dokumencie.|
|Formatowanie zaznaczenia|Ustawia właściwe wcięcia linii kodu i przenosi nawiasy klamrowe, aby rozdzielić linie w zaznaczeniu.|
|Zmień spacje na tabulatory w zaznaczonych wierszach|Zmienia spacje wiodące na tabulatory, gdzie jest to odpowiednie.|
|Zmień tabulatory na spacje w zaznaczonych wierszach|Zmienia tabulatory wiodące na spacje. Jeśli chcesz przekonwertować wszystkie spacje w pliku na tabulacje (lub wszystkie tabulacje na spacje), możesz użyć `Edit.ConvertSpacesToTabs` i `Edit.ConvertTabsToSpaces` poleceń. Te polecenia nie są wyświetlane w menu programu Visual Studio, ale możesz je wywołać **szybki dostęp** okna lub okna poleceń.|
|Zmień litery na wielkie|Zmienia wszystkie znaki w zaznaczeniu na wielkie litery, lub jeśli nie zaznaczono żadnego fragmentu, zmienia znak w punkcie wstawiania na wielkie litery. Skrót: **Ctrl**+**SHIFT**+**U**.|
|Zmień litery na małe|Zmienia wszystkie znaki w zaznaczeniu na małe litery, lub jeśli nie zaznaczono żadnego fragmentu, zmienia znak w punkcie wstawiania na małe litery. Skrót: **Ctrl**+**U**.|
|Przesuń wybrane wiersze w górę|Przenosi wybrany wiersz w górę o jeden wiersz. Skrót: **Alt**+**Strzałka w górę**.|
|Przesuń wybrane wiersze w|Przenosi wybrany wiersz w dół o jeden wiersz. Skrót: **Alt**+**strzałkę w dół**.|
|Usuń biały znak poziome|Usuwa tabulatory lub spacje na końcu bieżącego wiersza. Skrót: **ctrl**+**K**, **Ctrl**+ **\\**|
|Wyświetl białe znaki|Wyświetla spacje jako kropki podniesione i tabulatory jako strzałki. Koniec pliku jest wyświetlany jako znacznik prostokątny. Jeśli **narzędzia** > **opcje** > **edytora tekstów** > **wszystkie języki**  >  **Zawijanie** > **Pokaż widoczne glify dla zawijania** jest zaznaczone, ten glif jest również wyświetlany.|
|Zawijanie wierszy|Powoduje, że wszystkie wiersze w dokumencie mają być wyświetlane w oknie kodu. Można włączać zawijanie wyrazów i Włącz w **Edytor tekstu wszystkie języki** ustawień (**narzędzia** > **opcje** > **Edytor tekstu**   >  **Wszystkie języki**).|
|Dodaj komentarz do zaznaczenia|Dodaje znaki komentarza do bieżącego wiersza lub zaznaczenia. Skrót: **ctrl**+**K**, **Ctrl**+**C**|
|Usuń komentarz z zaznaczenia|Usuwa znaki komentarza z bieżącego wiersza lub zaznaczenia. Skrót: **ctrl**+**K**, **Ctrl**+**U**|
|Zwiększ wcięcie wiersza|Dodaje znak tabulatora (lub równoważne spacje) do wybranych wierszy lub w bieżącym wierszu.|
|Zmniejsz wcięcie wiersza|Usuwa znak tabulatora (lub równoważne spacje) z wybranych wierszy lub w bieżącym wierszu.|
|Wybierz Tag|W dokumencie, który zawiera znaczniki (na przykład XML lub HTML) zaznacza znacznik.|
|Zaznacz zawartość tagu|W dokumencie, który zawiera znaczniki (na przykład XML lub HTML) zaznacza znaczniki.|

## <a name="navigate-and-find-code"></a>Nawigowanie i wyszukiwanie kodu

Można przenieść w edytorze kodu w kilku różnych sposobów, łącznie z poruszaniem się wstecz i przekazuje do poprzednich punktów wstawiania, wyświetlanie definicji typu lub elementu członkowskiego i przejście do określonej metody przy użyciu paska nawigacyjnego. Aby uzyskać więcej informacji, zobacz [Przechodzenie do kodu](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Znajdowanie odwołań w kodzie

Aby znaleźć, gdzie poszczególne elementy kodu są przywoływane w bazie kodu, możesz użyć polecenia **Znajdź wszystkie odwołania** lub naciśnij klawisz **SHIFT**+**F12**. Ponadto po kliknięciu typu lub elementu członkowskiego, **wyróżnianie odwołań** funkcja automatycznie wyróżnia wszystkie odwołania do tego typu lub elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).

## <a name="customize-the-editor"></a>Dopasowywanie edytora

Można udostępniać ustawienia programu Visual Studio innemu deweloperowi, ustawienia są zgodne z normą, lub przywrócić ustawienia domyślne programu Visual Studio przy użyciu zostały **Kreatora importowania i eksportowania ustawień** polecenie  **Narzędzia** menu. W **Kreatora importowania i eksportowania ustawień**, można zmienić wybranego ustawienia ogólne lub język i ustawienia specyficzne dla projektu.

Aby zdefiniować nowe klawisze dostępu lub ponownie zdefiniować istniejących klawisze dostępu, przejdź do **narzędzia** > **opcje** > **środowiska**  >  **Klawiatury**. Aby uzyskać więcej informacji o klawiszach dostępu, zobacz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Dla opcji edytora specyficznych dla języka JavaScript, zobacz [opcji edytora języka JavaScript](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Zobacz także

- [Edytor źródła (program Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Wprowadzenie do języka C++ w programie Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Wprowadzenie do języka C# i platformy ASP.NET w programie Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Rozpoczynanie pracy z językiem Python w programie Visual Studio](../ide/quickstart-python.md)
