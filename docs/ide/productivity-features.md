---
title: Wskazówki dotyczące produktywności
ms.date: 2/21/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 620ad93c03e1a1b260ee14cb27093403f27648d7
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544305"
---
# <a name="productivity-tips-for-visual-studio"></a>Wskazówki dotyczące produktywności programu Visual Studio

W tym artykule omówiono wskazówki dotyczące funkcji programu Visual Studio, które ułatwiają szybsze i wydajniejsze pisanie, nawigowanie i debugowanie kodu.

Aby uzyskać informacje na temat przydatnych skrótów klawiaturowych, zobacz [Skróty zwiększające produktywność](../ide/productivity-shortcuts.md). Aby uzyskać pełną listę skrótów poleceń, zobacz [Domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="write-code"></a>Pisanie kodu

Pisz kod szybciej, korzystając z następujących funkcji.

- **Używaj poleceń convenience**. Program Visual Studio zawiera różne polecenia ułatwiające szybsze wykonywanie typowych zadań edycji. Na przykład można wybrać polecenie, aby łatwo zduplikować wiersz kodu bez konieczności kopiowania go, zmiany położenia kursora, a następnie wklejania go. Wybierz **pozycję Edytuj** > **duplikat** lub naciśnij **klawisze Ctrl**+**E**,**V**. Można również szybko rozwinąć lub umtraktować zaznaczenie tekstu, wybierając **pozycję Edytuj** > **zaawansowane** > **rozwiń zaznaczenie** lub **Edytuj** > **zaawansowane** > **zaznaczenie kontraktu**lub naciskając klawisz **Shift**+**Alt** + **=** lub **Shift**+**Alt**+**-**.

- **Użyj IntelliSense**. Po wprowadzeniu kodu w edytorze wyświetlane są informacje IntelliSense, takie jak Lista członków, Informacje o parametrach, Szybkie informacje, Pomoc podpisu i Pełne słowo. Funkcje te obsługują rozmyte dopasowanie tekstu; na przykład listy wyników dla członków listy zawierają nie tylko wpisy rozpoczynające się od wprowadzonych znaków, ale także wpisy zawierające kombinację znaków w dowolnym miejscu ich nazw. Aby uzyskać więcej informacji, zobacz [Korzystanie z programu IntelliSense](../ide/using-intellisense.md).

- **Zmieniaj automatyczne wstawianie opcji IntelliSense podczas wprowadzania kodu**. Przełączając intellisense do trybu sugestii, można określić, że opcje IntelliSense są wstawiane tylko wtedy, gdy jawnie je wybierzesz.

     Aby włączyć tryb sugestii, wybierz klawisze **Ctrl**+**Alt**+**Spacja** lub na pasku menu wybierz pozycję **Edytuj** > **tryb przełączania****intellisense** > .

- **Użyj fragmentów kodu**. Można użyć wbudowanych fragmentów kodu lub utworzyć własne fragmenty kodu.

     Aby wstawić fragment kodu, na pasku menu wybierz pozycję **Edytuj** > fragment kodu**IntelliSense** > **Insert** lub **Surround With**lub otwórz menu skrótów w pliku i wybierz pozycję **Snippet** > Fragment**wstawiania fragmentu** kodu lub **Surround With**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](../ide/code-snippets.md).

- **Napraw błędy kodu w linii**. Szybkie akcje umożliwiają łatwe refaktoryzowanie, generowanie lub modyfikowanie kodu za pomocą jednej akcji. Działania te można zastosować za pomocą ![ikony](media/screwdriver-icon.png) śrubokręta lub ![ikony żarówki Ikony](media/light-bulb-icon.png) żarówki lub naciskając klawisz **Alt**+**Enter** lub **Ctrl**+**.** gdy kursor znajduje się w odpowiednim wierszu kodu. Aby uzyskać więcej informacji, zobacz [Szybkie akcje.](quick-actions.md)

- **Pokaż i edytuj definicję elementu kodu**. Można szybko wyświetlić i edytować moduł, w którym zdefiniowano element kodu, taki jak element członkowski, zmienna lub lokalny.

    Aby otworzyć definicję w wyskakującym oknie, zaznacz element, a następnie wybierz klawisze **Alt**+**F12** lub otwórz menu skrótów dla elementu, a następnie wybierz polecenie **Definicja wglądu**. Aby otworzyć definicję w osobnym oknie kodu, otwórz menu skrótów dla elementu, a następnie wybierz pozycję **Przejdź do definicji**.

- **Użyj przykładowych aplikacji**. Tworzenie aplikacji można przyspieszyć, pobierając i instalując przykładowe aplikacje z [usługi Microsoft Developer Network.](https://code.msdn.microsoft.com/) Możesz również zapoznać się z określoną technologią lub koncepcją programowania, pobierając i eksplorując pakiet próbkowania dla tego obszaru.

## <a name="navigate-within-your-code"></a>Poruszanie się po kodzie

Można użyć różnych technik, aby szybciej znaleźć i przenieść do określonych lokalizacji w kodzie.

- **Zakładki wierszy kodu**. Zakładki umożliwiają szybkie przechodzenie do określonych wierszy kodu w pliku.

    Aby ustawić zakładkę, na pasku menu wybierz pozycję **Edytuj** > **zakładki Przełączanie** > **zakładki**. W oknie **Zakładki** można wyświetlić wszystkie zakładki rozwiązania. Aby uzyskać więcej informacji, zobacz [Ustawianie zakładek w kodzie](../ide/setting-bookmarks-in-code.md).

- **Wyszukiwanie definicji symboli w pliku**. Można wyszukiwać w ramach rozwiązania, aby zlokalizować definicje symboli i nazwy plików, ale wyniki wyszukiwania nie zawierają obszarów nazw ani zmiennych lokalnych.

   Aby uzyskać dostęp do tej funkcji, na pasku menu wybierz pozycję **Edytuj** > **nawiguj do**.

- **Przejrzyj ogólną strukturę kodu**. W **Eksploratorze rozwiązań**można wyszukiwać i przeglądać klasy oraz ich typy i elementy członkowskie w projektach. Można również wyszukiwać symbole, wyświetlać hierarchię wywołań metody, znajdować odniesienia do symboli i wykonywać inne zadania. Jeśli wybierzesz element kodu w **Eksploratorze rozwiązań,** skojarzony plik zostanie otwarty na karcie **Podgląd,** a kursor zostanie przeniesiony do elementu w pliku. Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md).

## <a name="find-items-faster"></a>Szybsze znajdowanie przedmiotów

Oprócz filtrowania zawartości okien narzędzi można przeszukiwać ide w poszukiwaniu poleceń, plików i opcji, aby wyświetlić tylko istotne informacje dotyczące bieżącego zadania.

- **Filtrowanie zawartości okien narzędzi**. Można wyszukiwać w obrębie zawartości wielu okien narzędzi, takich jak **Przybornik**, okno **Właściwości** i **Eksplorator rozwiązań,** ale wyświetla tylko elementy, których nazwy zawierają określone znaki.

- **Wyświetlaj tylko błędy, które chcesz rozwiązać**. Jeśli na pasku narzędzi Lista błędów zostanie wybrana przycisk **Filtruj,** można zmniejszyć liczbę błędów wyświetlanych w oknie **Lista błędów.** **Filter** Można wyświetlić tylko błędy w plikach, które są otwarte w edytorze, tylko błędy w bieżącym pliku lub tylko błędy w bieżącym projekcie. Można również wyszukać w oknie **Lista błędów,** aby znaleźć określone błędy.

- **Znajdź okna dialogowe, polecenia menu, opcje i inne**. W polu wyszukiwania wprowadź słowa kluczowe lub frazy elementów, które próbujesz znaleźć. Na przykład następujące opcje są wyświetlane po wprowadzeniu **nowego projektu:**

   ::: moniker range="vs-2017"

   ![Szybkie uruchamianie wyników dla "nowego projektu"](../ide/media/productivity_quicklaunch.png)

   **Szybkie uruchamianie** wyświetla łącza do tworzenia nowego projektu, dodawania nowego elementu do projektu oraz między innymi do strony **Projekty i rozwiązania** w oknie dialogowym **Opcje.** Wyniki wyszukiwania mogą również zawierać pliki projektu i okna narzędzi.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Wyniki wyszukiwania dla 'new project'](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Naciśnij **klawisz Ctrl**+**Q,** aby przejść bezpośrednio do pola wyszukiwania.

## <a name="debug-code"></a>Kod debugowania

Debugowanie może zużyć dużo czasu, ale poniższe wskazówki mogą pomóc przyspieszyć proces.

- **Przetestuj tę samą stronę, aplikację lub witrynę w różnych przeglądarkach.** Podczas debugowania kodu można łatwo przełączać się między zainstalowanymi przeglądarkami internetowymi, w tym [Inspektorem strony (Visual Studio),](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209)bez konieczności otwierania okna dialogowego **Przeglądaj za pomocą.** Za pomocą listy **Debugowania docelowego,** która znajduje się na pasku narzędzi **Standardowy** obok **przycisku Rozpocznij debugowanie,** można szybko sprawdzić, której przeglądarki używasz podczas debugowania lub wyświetlania stron.

    ![Wybieranie opcji debugowania przeglądarki internetowej](../ide/media/webbrowserdropdowntoolbar.png)

- **Ustaw tymczasowe punkty przerwania**. Można utworzyć tymczasowy punkt przerwania w bieżącym wierszu kodu i uruchomić debuger jednocześnie. Po naciśnięciu tego wiersza kodu debuger wchodzi w tryb przerwania. Aby uzyskać więcej informacji, zobacz [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

    Aby użyć tej funkcji, wybierz klawisze **Ctrl**+**F10** lub otwórz menu skrótów dla wiersza kodu, w którym chcesz przerwać, a następnie wybierz pozycję **Uruchom kursor**.

- **Przenieś punkt wykonywania podczas debugowania**. Można przenieść bieżący punkt wykonywania do innej sekcji kodu, a następnie ponownie debugowania z tego punktu. Ta technika jest przydatna, jeśli chcesz debugować sekcję kodu bez konieczności ponownego tworzenia wszystkich kroków, które są wymagane do osiągnięcia tej sekcji. Aby uzyskać więcej informacji, zobacz [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

     Aby przenieść punkt wykonania, przeciągnij żółty grot strzałki do lokalizacji, w której chcesz ustawić następną instrukcję w tym samym pliku źródłowym, a następnie wybierz klawisz **F5,** aby kontynuować debugowanie.

- **Przechwytywanie informacji o wartości dla zmiennych**. Można dodać DataTip do zmiennej w kodzie i przypiąć go, dzięki czemu można uzyskać dostęp do ostatniej znanej wartości zmiennej po zakończeniu debugowania. Aby uzyskać więcej informacji, zobacz [Wyświetlanie wartości danych w poradach dotyczących danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Aby dodać datatip, debuger musi być w trybie przerwania. Umieść kursor na zmiennej, a następnie wybierz przycisk pinezki na wyświetleniu etykietki danych. Po zatrzymaniu debugowania w pliku źródłowym obok wiersza kodu zawierającego zmienną pojawia się niebieska ikona pinezki. Jeśli wskażesz niebieski pin, pojawi się wartość zmiennej z ostatniej sesji debugowania.

- **Wyczyść okno Natychmiastowe**. Zawartość [okna Bezpośrednie](../ide/reference/immediate-window.md) można wymazać w czasie projektowania, `>cls` wprowadzając lub`>Edit.ClearAll`

     Aby uzyskać więcej informacji o dodatkowych poleceniach, zobacz [Aliasy poleceń programu Visual Studio](../ide/reference/visual-studio-command-aliases.md).

## <a name="access-visual-studio-tools"></a>Dostęp do narzędzi programu Visual Studio

Możesz szybko uzyskać dostęp do wiersza polecenia dewelopera lub innego narzędzia programu Visual Studio, jeśli przypiąć go do menu Start lub paska zadań.

::: moniker range="vs-2017"

1. W Eksploratorze Windows przejdź do *pozycji %ProgramData%\Microsoft\Windows\Menu Start\Programy\Visual Studio 2017\Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. W Eksploratorze Windows przejdź do *pozycji %ProgramData%\Microsoft\Windows\Menu Start\Programy\Visual Studio 2019\Visual Studio Tools*.

::: moniker-end

2. Kliknij prawym przyciskiem myszy lub otwórz menu kontekstowe **wiersza polecenia dewelopera,** a następnie wybierz pozycję **Przypnij do ekranu startowego** lub **Przypnij do paska zadań**.

## <a name="manage-files-toolbars-and-windows"></a>Zarządzanie plikami, paskami narzędzi i oknami

W dowolnym momencie, może być praca w wielu plikach kodu i przenoszenie między kilkoma oknami narzędzi podczas tworzenia aplikacji. Możesz zachować porządek, korzystając z następujących wskazówek:

- **Zachowaj pliki, których często używasz, są widoczne w edytorze**. Pliki można przypiąć po lewej stronie karty, tak aby były widoczne niezależnie od tego, ile plików jest otwartych w edytorze.

   Aby przypiąć plik, wybierz kartę pliku, a następnie wybierz przycisk **Przełącz stan pinu.**

- **Przenoszenie dokumentów i okien na inne monitory**. Jeśli podczas tworzenia aplikacji używasz więcej niż jednego monitora, możesz łatwiej pracować nad częściami aplikacji, przenosząc pliki otwarte w edytorze na inny monitor. Można również przenieść okna narzędzi, takie jak okna debugera, do innego monitora i tabulatora dokowania dokumentów i okien narzędzi razem, aby utworzyć "tratwy". Aby uzyskać więcej informacji, zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Można również łatwiej zarządzać plikami, tworząc inne wystąpienie **Eksploratora rozwiązań** i przenosząc je na inny monitor. Aby utworzyć inne wystąpienie **Eksploratora rozwiązań,** otwórz menu skrótów w **Eksploratorze rozwiązań,** a następnie wybierz pozycję **Widok Eksploratora nowych rozwiązań**.

- **Dostosuj czcionki wyświetlane w programie Visual Studio**. Można zmienić czcionkę, rozmiar i kolor używanego dla tekstu w IDE. Na przykład można dostosować kolor określonych elementów kodu w edytorze i czcionki ściany w oknach narzędzi lub w całej IDE. Aby uzyskać więcej informacji, zobacz [Jak: Zmienianie czcionek i kolorów](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) oraz [Jak: Zmienianie czcionek i kolorów w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz też

- [Wpis w blogu dotyczące porad i wskazówek dotyczących programu Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Jak: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Przewodnik: Tworzenie prostej aplikacji](../get-started/csharp/tutorial-wpf.md)
- [Porady i wskazówki związane z ułatwieniami dostępu](../ide/reference/accessibility-tips-and-tricks.md)
