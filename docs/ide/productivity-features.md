---
title: Przewodnik po produktywności
description: Poznaj skróty klawiaturowe i funkcje produktywności w programie Visual Studio, które mogą pomóc efektywnie napisać kod, debugować kod i obsłużyć błędy.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 01367d821ffc74de0e9d087bfe52680508fad9e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951163"
---
# <a name="productivity-guide-for-visual-studio"></a>Przewodnik dotyczący produktywności dla programu Visual Studio

Jeśli chcesz zaoszczędzić czas podczas pisania kodu, jesteś w odpowiednim miejscu. Ten przewodnik dotyczący wydajności zawiera wskazówki, które mogą pomóc Ci rozpocząć pracę z programem Visual Studio, napisać kod, debugować kod, obsłużyć błędy i używać skrótów klawiaturowych &mdash; wszystkich na jednej stronie.

Aby uzyskać informacje na temat przydatnych skrótów klawiaturowych, zobacz [Skróty dotyczące produktywności](../ide/productivity-shortcuts.md). Aby uzyskać pełną listę skrótów poleceń, zobacz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="get-started"></a>Rozpoczęcie pracy

Oszczędź czas przeszukiwanie stosów za pomocą menu, szybko wyszukując potrzebne elementy, w tym polecenia, ustawienia, dokumentację i opcje instalacji. Zobacz skróty klawiaturowe dla poleceń znajdujących się w wynikach wyszukiwania w programie Visual Studio, dzięki czemu można je łatwo znają. 

- **Symulacja kodu za pomocą listy zadań**. Jeśli nie masz wystarczającej ilości wymaganych do ukończenia fragmentu kodu, użyj Lista zadań do śledzenia komentarzy do kodu, które używają tokenów, takich jak `TODO` i `HACK` , lub tokenów niestandardowych, oraz do zarządzania skrótami, które przenoszą bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Aby uzyskać więcej informacji, zobacz [Korzystanie z Lista zadań](../ide/using-the-task-list.md).

- **Użyj Eksplorator rozwiązań skrótów**. Jeśli dopiero zaczynasz w programie Visual Studio, te skróty będą w pełni przydatne i zaoszczędzić czas podczas przygotowywania nowej bazy kodu. Aby zapoznać się z pełną listą skrótów, zobacz [domyślne skróty klawiaturowe w programie Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL).

- **[Identyfikowanie i Dostosowywanie skrótów klawiaturowych w programie Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)**. Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Można zawsze znaleźć i zmienić skrót klawiaturowy w oknie dialogowym Opcje.

- **Zwiększ dostępność programu Visual Studio**. Program Visual Studio ma wbudowane funkcje ułatwień dostępu, które są zgodne z czytnikami ekranu i innymi technologiami pomocniczymi. Zobacz [porady dotyczące ułatwień dostępu i wskazówki dla programu Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) , aby zapoznać się z pełną listą dostępnych funkcji. 

- **Zapoznaj się z cyklem życia produktu i obsługą programu Visual Studio**. Aby uzyskać informacje na temat pobierania aktualizacji dla programu Visual Studio, opcji pomocy technicznej dla klientów korporacyjnych i profesjonalnych, obsługi starszych wersji programu Visual Studio i składników, które nie są objęte obsługą programu Visual Studio, zobacz [cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing). 

- **Instalowanie pakietów NuGet i zarządzanie nimi w programie Visual Studio**. Interfejs użytkownika Menedżera pakietów NuGet w programie Visual Studio w systemie Windows umożliwia łatwe instalowanie, Odinstalowywanie i aktualizowanie pakietów NuGet w projektach i rozwiązaniach. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietów i zarządzanie nimi w programie Visual Studio przy użyciu Menedżera pakietów NuGet](/nuget/consume-packages/install-use-packages-visual-studio).

## <a name="write-code"></a>Pisanie kodu

Szybsze pisanie kodu przy użyciu następujących funkcji.

- **Używaj wygodnych poleceń**. Program Visual Studio zawiera różne polecenia ułatwiające szybsze wykonywanie typowych zadań edycji. Na przykład można wybrać polecenie, aby łatwo zduplikować wiersz kodu bez konieczności jego kopiowania, zmiany położenia kursora, a następnie wklejenia. Wybierz pozycję **Edytuj**  >  **duplikat** lub naciśnij **klawisze CTRL** + **E**,**V**. Możesz również szybko rozwijać lub zwijać zaznaczenie tekstu, wybierając opcję **Edytuj**  >  **Zaawansowane**  >  **Rozszerzanie zaznaczenia** lub **Edytuj**  >  **zaawansowaną**  >  **umowę wyboru** lub naciskając klawisze **SHIFT** + **Alt** + **=** lub **SHIFT** + **Alt** + **-** .

- **Użyj funkcji IntelliSense**. Podczas wprowadzania kodu w edytorze informacje o technologii IntelliSense, takie jak elementy członkowskie listy, informacje o parametrach, szybkie informacje, pomoc podpisu i pełny wyraz, pojawiają się. Funkcje te obsługują rozmyte dopasowywanie tekstu; na przykład listy wyników dla członków listy zawierają nie tylko wpisy, które zaczynają się od znaków wprowadzonych, ale także wpisy, które zawierają kombinację znaków w dowolnym miejscu nazwy. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md).

- **Zmień Autouzupełnianie opcji IntelliSense podczas wprowadzania kodu**. Przełączając funkcję IntelliSense do trybu sugestii, można określić, że opcje IntelliSense są wstawiane tylko wtedy, gdy użytkownik jawnie je wybiera.

     Aby włączyć tryb sugestii, wybierz **kombinację klawiszy CTRL** + **Alt**/ +  lub na pasku menu wybierz polecenie **Edytuj**  >    >  **Tryb uzupełniania** funkcji IntelliSense.

- **Użyj fragmentów kodu**. Możesz użyć wbudowanych fragmentów kodu lub utworzyć własne fragmenty kodu.

     Aby wstawić fragment kodu, na pasku menu wybierz **Edycja**  >  **IntelliSense**  >  **Wstaw fragment kodu** lub **Otocz za pomocą** lub Otwórz menu skrótów w pliku, a następnie wybierz   >  **Wstaw fragment kodu** lub **Otocz za pomocą**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).

- **Naprawianie błędów kodu w tekście**. Szybkie akcje umożliwiają łatwe refaktoryzację, generowanie lub modyfikowanie kodu przy użyciu jednej akcji. Te akcje mogą być stosowane przy użyciu ikony śrubokręta śrubokrętka lub żarówki ikona żarówki ![ ](media/screwdriver-icon.png) ![ ](media/light-bulb-icon.png) lub przez naciśnięcie klawisza **Alt** + **Enter** lub **Ctrl** + **.** gdy kursor znajduje się w odpowiednim wierszu kodu. Aby uzyskać więcej informacji, zobacz [szybkie akcje](quick-actions.md) .

- **Pokaż i Edytuj definicję elementu kodu**. Można szybko wyświetlać i edytować moduł, w którym zdefiniowano element kodu, taki jak element członkowski, zmienna lub wartość lokalna.

    Aby otworzyć definicję w oknie podręcznym, zaznacz element, a następnie wybierz klawisze **Alt** + **F12** lub Otwórz menu skrótów dla elementu, a następnie wybierz polecenie **Podgląd definicji**. Aby otworzyć definicję w osobnym oknie kodu, otwórz menu skrótów dla elementu, a następnie wybierz **Przejdź do definicji**.

- **Korzystaj z przykładowych aplikacji**. Można przyspieszyć tworzenie aplikacji, pobierając i instalując przykładowe aplikacje z [sieci Microsoft Developer Network](https://code.msdn.microsoft.com/). Możesz również poznać konkretną technikę lub koncepcję programowania, pobierając i eksplorowanie przykładowego pakietu dla tego obszaru.

- **Zmień formatowanie nawiasów klamrowych z formatowaniem/nowym wierszem**. Strona Opcje **formatowania**  służy do ustawiania opcji formatowania kodu w edytorze kodu, w tym nowych wierszy. Aby uzyskać więcej informacji na temat używania tego ustawienia w języku C#, zobacz [Opcje okno dialogowe: Edytor tekstu > C# > stylu kodu > formatowanie](../ide/reference/options-text-editor-csharp-formatting.md). W przypadku języka C++ zapoznaj się z tematem [Ustawianie preferencji kodowania języka C++ w programie Visual Studio](/cpp/ide/how-to-set-preferences). W przypadku języka Python zobacz [Formatowanie kodu](../python/formatting-python-code.md)w języku Python.

- **Zmień wcięcie przy użyciu kart**. Użyj niestandardowych ustawień edytora, które są dostosowane do poszczególnych baz kodu, aby wymusić spójne style kodowania dla wielu deweloperów pracujących nad tym samym projektem w różnych edytorach i środowisk IDE. Upewnij się, że cały zespół jest zgodny z tymi samymi konwencjami językowymi, konwencjami nazewnictwa i regułami formatowania. Ponieważ te ustawienia niestandardowe są przenośne i podróżują z kodem, można wymusić style kodowania nawet poza programem Visual Studio. Aby uzyskać więcej informacji, zobacz [Opcje, Edytor tekstu, wszystkie języki, karty](../ide/reference/options-text-editor-all-languages-tabs.md#tabs).

## <a name="navigate-within-your-code-and-the-ide"></a>Nawigowanie w kodzie i IDE

Możesz użyć różnych technik, aby szybciej znajdować i przechodzić do określonych lokalizacji w kodzie. Możesz również zmienić układ okna programu Visual Studio w oparciu o Twoje preferencje. 

- **Zakładki wierszy kodu**. Przy użyciu zakładek można szybko przechodzić do określonych wierszy kodu w pliku.

    Aby ustawić zakładkę, na pasku menu wybierz pozycję **Edytuj**  >  **zakładki**  >  **Przełącz zakładkę**. Wszystkie zakładki rozwiązania można wyświetlić w oknie **zakładek** . Aby uzyskać więcej informacji, zobacz [Ustawianie zakładek w kodzie](../ide/setting-bookmarks-in-code.md).

- **Wyszukaj definicje symboli w pliku**. Możesz wyszukać w rozwiązaniu, aby zlokalizować definicje symboli i nazwy plików, ale wyniki wyszukiwania nie obejmują przestrzeni nazw ani zmiennych lokalnych.

   Aby uzyskać dostęp do tej funkcji, na pasku menu wybierz pozycję **Edytuj**  >  **Przejdź do**.

- **Przeglądaj ogólną strukturę kodu**. W **Eksplorator rozwiązań** można wyszukiwać i przeglądać klasy oraz ich typy i członków w projektach. Możesz również wyszukiwać symbole, wyświetlać hierarchię wywołań metody, znajdować odwołania do symboli i wykonywać inne zadania. Jeśli wybierzesz element kodu w **Eksplorator rozwiązań**, skojarzony plik zostanie otwarty na karcie **podglądu** , a kursor zostanie przeniesiony do elementu w pliku. Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md).

- **Przejdź do lokalizacji w pliku z trybem mapowania**. Tryb mapy Wyświetla linie kodu w miniaturach na pasku przewijania. Aby uzyskać więcej informacji o tym trybie wyświetlania, zobacz [How to: Dostosowywanie paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode).

- **Zapoznaj się ze strukturą kodu za pomocą mapy kodu**. Mapy kodu mogą ułatwić wizualizację zależności w kodzie i zobaczyć, jak dopasowuje się do siebie bez odczytywania plików i wierszy kodu. Aby uzyskać więcej informacji, zobacz [Mapowanie zależności za pomocą map kodu](../modeling/map-dependencies-across-your-solutions.md).

- **Zobacz często używane pliki, edytując/przejdź do ostatniego pliku**. Użyj poleceń przejdź do w programie Visual Studio, aby przeprowadzić skoncentrowane wyszukiwanie kodu, aby ułatwić szybkie znajdowanie określonych elementów. Aby uzyskać szczegółowe instrukcje, zobacz [Znajdowanie kodu przy użyciu przejdź do poleceń](../ide/go-to.md).

- **Przenieś [okno właściwości](../ide/reference/properties-window.md) po prawej stronie**. Jeśli szukasz bardziej znanego układu okna, możesz przenieść okno Właściwości w programie Visual Studio, naciskając klawisz **F4**.

## <a name="find-items-faster"></a>Szybsze znajdowanie elementów

Oprócz filtrowania zawartości okien narzędzi można przeszukiwać w środowisku IDE, aby wyświetlić tylko odpowiednie informacje dotyczące bieżącego zadania.

- **Filtrowanie zawartości okien narzędzi**. Można wyszukiwać zawartość wielu okien narzędzi, takich jak **Przybornik**, okno **Właściwości** i **Eksplorator rozwiązań**, ale wyświetlane są tylko elementy, których nazwy zawierają określone znaki.

- **Wyświetl tylko błędy, które chcesz rozwiązać**. Jeśli wybierzesz przycisk **Filtr** na pasku narzędzi **Lista błędów** , możesz zmniejszyć liczbę błędów, które pojawiają się w oknie **Lista błędów** . Można wyświetlić tylko błędy w plikach, które są otwarte w edytorze, tylko błędy w bieżącym pliku lub tylko błędy w bieżącym projekcie. Możesz również wyszukać w oknie **Lista błędów** , aby znaleźć konkretne błędy.

- **Znajdowanie okien dialogowych, poleceń menu, opcji i innych**. W polu wyszukiwania wprowadź słowa kluczowe lub frazy dla elementów, które próbujesz znaleźć. Na przykład następujące opcje są wyświetlane, jeśli wprowadzisz **Nowy projekt**:

   ::: moniker range="vs-2017"

   ![Wyniki szybkiego uruchamiania dla "nowy projekt"](../ide/media/productivity_quicklaunch.png)

   Przycisk **szybkiego uruchamiania** wyświetla linki umożliwiające utworzenie nowego projektu, dodanie nowego elementu do projektu i strony **projekty i rozwiązania** w oknie dialogowym **Opcje** , między innymi. Wyniki wyszukiwania mogą również obejmować pliki projektu i okna narzędzi.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Wyniki wyszukiwania dla elementu "nowy projekt"](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Naciśnij klawisz **Ctrl** + **Q** , aby przejść bezpośrednio do pola wyszukiwania.

## <a name="debug-code"></a>Debugowanie kodu

Debugowanie może zużywać dużo czasu, ale poniższe porady mogą pomóc przyspieszyć proces.

- **Użyj narzędzi debugera programu Visual Studio**. W kontekście programu Visual Studio, gdy *debugujesz aplikację*, zazwyczaj oznacza to, że aplikacja jest uruchamiana w trybie debugera. Debuger zapewnia wiele sposobów, aby sprawdzić, co Twój kod działa podczas jego działania. Aby zapoznać się z przewodnikiem Rozpoczynanie pracy [, zobacz najpierw debuger programu Visual Studio](../debugger/debugger-feature-tour.md) . 

- **Przetestuj tę samą stronę, aplikację lub witrynę w różnych przeglądarkach**. Podczas debugowania kodu można łatwo przełączać się między zainstalowanymi przeglądarkami sieci Web, w tym [inspektorem stron (Visual Studio)](/previous-versions/hh974728(v=vs.140))bez konieczności otwierania okna dialogowego **przeglądanie za pomocą** . Możesz użyć listy **obiektów docelowych debugowania** , która znajduje się na **standardowym** pasku narzędzi obok przycisku **Rozpocznij debugowanie** , aby szybko sprawdzić, która przeglądarka jest używana podczas debugowania lub wyświetlania stron.

    ![Wybierz opcje debugowania przeglądarki sieci Web](../ide/media/webbrowserdropdowntoolbar.png)

- **Ustaw tymczasowe punkty przerwania**. Można utworzyć tymczasowy punkt przerwania w bieżącym wierszu kodu i uruchomić debuger jednocześnie. Po trafieniu tego wiersza kodu debuger przechodzi w tryb przerwania. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

    Aby użyć tej funkcji, wybierz klawisze **Ctrl** + **F10** lub Otwórz menu skrótów dla wiersza kodu, na którym chcesz przerwać, a następnie wybierz polecenie **Uruchom do kursora**.

- **Przenieś punkt wykonywania podczas debugowania**. Bieżący punkt wykonywania można przenieść do innej sekcji kodu, a następnie ponownie uruchomić debugowanie od tego momentu. Ta technika jest przydatna, jeśli chcesz debugować sekcję kodu bez konieczności ponownego tworzenia wszystkich kroków wymaganych w celu uzyskania dostępu do tej sekcji. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

     Aby przenieść punkt wykonywania, przeciągnij żółtą grot strzałki do lokalizacji, w której chcesz ustawić następną instrukcję w tym samym pliku źródłowym, a następnie wybierz klawisz **F5** , aby kontynuować debugowanie.

- **Przechwyć informacje o wartości dla zmiennych**. Można dodać etykietki danych do zmiennej w kodzie i przypiąć ją, aby można było uzyskać dostęp do ostatniej znanej wartości zmiennej po zakończeniu debugowania. Aby uzyskać więcej informacji, zobacz [Wyświetlanie wartości danych w etykietkach danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Aby dodać etykietki danych, debuger musi być w trybie przerwania. Umieść kursor na zmiennej, a następnie wybierz przycisk Przypnij na wyświetlonej etykietki danych. Po zatrzymaniu debugowania w pliku źródłowym obok wiersza kodu, który zawiera zmienną, pojawia się niebieska ikona pinezki. Jeśli wskażesz niebieski numer PIN, zostanie wyświetlona wartość zmiennej z ostatniej sesji debugowania.

- **Wyczyść okno bezpośrednie**. Możesz wymazać zawartość [okna bezpośredniego](../ide/reference/immediate-window.md) w czasie projektowania, wprowadzając `>cls` lub `>Edit.ClearAll`

     Aby uzyskać więcej informacji na temat dodatkowych poleceń, zobacz [Visual Studio — Aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

- **[Znajdź zmiany w kodzie i inne historyczne z CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)**. Usługa CodeLens umożliwia skoncentrowanie się na pracy w czasie, gdy dowiesz się, co się stało z kodem &mdash; bez opuszczania edytora. Można znaleźć odwołania do fragmentu kodu, zmiany w kodzie, połączone błędy, elementy robocze, przeglądy kodu i testy jednostkowe.

- **Użyj Live Share do debugowania w czasie rzeczywistym z innymi osobami**. Rozszerzenie Live Share umożliwia wspólne edytowanie i debugowanie z innymi osobami w czasie rzeczywistym, niezależnie od używanych języków programowania lub typów tworzonych aplikacji. Aby uzyskać więcej informacji, zobacz [co to jest Visual Studio Live Share?](/visualstudio/liveshare/)

- **Użyj okna interaktywnego, aby napisać i przetestować mały kod**. Program Visual Studio udostępnia interaktywne okno odczytu-Szacuj-Print-Loop (REPL), które umożliwia wprowadzanie dowolnego kodu i wyświetlanie wyników natychmiastowych. Ten sposób kodowania pomaga uczyć się i eksperymentować z interfejsami API i bibliotekami oraz interaktywnie opracowywać kod roboczy do uwzględnienia w projektach. W przypadku języka Python zobacz [Working with Interactive Window języka Python](../python/python-interactive-repl-in-visual-studio.md). Funkcja interaktywnego okna jest również dostępna dla języka C#. 

## <a name="access-visual-studio-tools"></a>Uzyskaj dostęp do narzędzi programu Visual Studio

Po przypięciu do menu Start lub paska zadań można szybko uzyskać dostęp do wiersz polecenia dla deweloperów lub innego narzędzia Visual Studio.

::: moniker range="vs-2017"

1. W Eksploratorze Windows przejdź do *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. W Eksploratorze Windows przejdź do *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*.

::: moniker-end

2. Kliknij prawym przyciskiem myszy lub Otwórz menu kontekstowe dla **wiersz polecenia dla deweloperów**, a następnie wybierz pozycję **Przypnij do** **paska zadań**.

## <a name="manage-files-toolbars-and-windows"></a>Zarządzanie plikami, paskami narzędzi i oknami

W dowolnym momencie możesz pracować w wielu plikach kodu i poruszać się po kilku oknach narzędzi podczas opracowywania aplikacji. Można organizować, korzystając z następujących wskazówek:

- **Zachowaj rzadko używane pliki w edytorze**. Możesz przypinać pliki do lewej strony karty, aby były widoczne niezależnie od tego, ile plików jest otwartych w edytorze.

   Aby przypiąć plik, wybierz kartę plik, a następnie wybierz przycisk **Przełącz stan przypięcia** .

- **Przenieś dokumenty i okna do innych monitorów**. Jeśli używasz więcej niż jednego monitora podczas opracowywania aplikacji, możesz łatwiej pracować nad częściami aplikacji, przenosząc pliki, które są otwarte w edytorze, do innego monitora. Możesz również przenieść okna narzędzi, takie jak okna debugera, do innego monitora i Zadokuj okna dokumentów i narzędzi, aby utworzyć "tratwy". Aby uzyskać więcej informacji, zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Można również łatwiej zarządzać plikami, tworząc inne wystąpienie **Eksplorator rozwiązań** i przenosząc je do innego monitora. Aby utworzyć inne wystąpienie **Eksplorator rozwiązań**, otwórz menu skrótów w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Nowy widok Eksplorator rozwiązań**.

- **Dostosuj czcionki, które pojawiają się w programie Visual Studio**. Można zmienić krój, rozmiar i kolor czcionki używany dla tekstu w IDE. Na przykład można dostosować kolor określonych elementów kodu w edytorze i krój czcionki w oknach narzędzi lub w środowisku IDE. Aby uzyskać więcej informacji, zobacz [How to: Change Fonts and Colors](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) i [How to: Change Fonts and Colors in the Editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz też

- [Visual Studio — porady i wskazówki dotyczące wpisu w blogu](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Instrukcje: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Przewodnik: tworzenie prostej aplikacji](../get-started/csharp/tutorial-wpf.md)
- [Porady i wskazówki związane z ułatwieniami dostępu](../ide/reference/accessibility-tips-and-tricks.md)