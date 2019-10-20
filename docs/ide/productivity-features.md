---
title: Wskazówki dotyczące produktywności
ms.date: 2/21/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0ac256d9878df45404dc62f1080e12bb6e7f002
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666776"
---
# <a name="productivity-tips-for-visual-studio"></a>Porady dotyczące produktywności dla programu Visual Studio

W tym artykule omówiono wskazówki dotyczące funkcji programu Visual Studio, które ułatwiają szybkie i wydajniejsze pisanie, nawigowanie i debugowanie kodu.

Aby uzyskać informacje na temat przydatnych skrótów klawiaturowych, zobacz [Skróty dotyczące produktywności](../ide/productivity-shortcuts.md). Aby uzyskać pełną listę skrótów poleceń, zobacz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="write-code"></a>Napisz kod

Szybsze pisanie kodu przy użyciu następujących funkcji.

- **Używaj wygodnych poleceń**. Program Visual Studio zawiera różne polecenia ułatwiające szybsze wykonywanie typowych zadań edycji. Na przykład można wybrać polecenie, aby łatwo zduplikować wiersz kodu bez konieczności jego kopiowania, zmiany położenia kursora, a następnie wklejenia. Wybierz **edytuj**  > **Duplikuj** lub naciśnij **klawisze CTRL** +**E**,**V**. Możesz również szybko rozwijać lub zwijać zaznaczenie tekstu, wybierając opcję **edytuj**  > **Advanced**  > **Rozwiń zaznaczenie** lub **Edytuj**  > **zaawansowaną** pozycję  > **kontraktu**lub naciskając  **Shift** 1**alt** 3 **5** lub **SHIFT** 7**Alt** 9 **1**.

- **Użyj funkcji IntelliSense**. Podczas wprowadzania kodu w edytorze informacje o technologii IntelliSense, takie jak elementy członkowskie listy, informacje o parametrach, szybkie informacje, pomoc podpisu i pełny wyraz, pojawiają się. Funkcje te obsługują rozmyte dopasowywanie tekstu; na przykład listy wyników dla członków listy zawierają nie tylko wpisy, które zaczynają się od znaków wprowadzonych, ale także wpisy, które zawierają kombinację znaków w dowolnym miejscu nazwy. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md).

- **Zmień Autouzupełnianie opcji IntelliSense podczas wprowadzania kodu**. Przełączając funkcję IntelliSense do trybu sugestii, można określić, że opcje IntelliSense są wstawiane tylko wtedy, gdy użytkownik jawnie je wybiera.

     Aby włączyć tryb sugestii, wybierz klawisze **Ctrl** +**Alt** +**spacji** lub na pasku menu wybierz polecenie **Edytuj**  > **IntelliSense**  > **Przełącz tryb uzupełniania**.

- **Użyj fragmentów kodu**. Możesz użyć wbudowanych fragmentów kodu lub utworzyć własne fragmenty kodu.

     Aby wstawić fragment kodu, na pasku menu wybierz polecenie **edytuj**  > **IntelliSense**  > **Wstaw fragment kodu** lub **Otocz za pomocą**lub Otwórz menu skrótów w pliku i wybierz wstawka  > **Wstaw fragment kodu** lub  **Otocz przy użyciu**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).

- **Naprawianie błędów kodu w tekście**. Szybkie akcje umożliwiają łatwe refaktoryzację, generowanie lub modyfikowanie kodu przy użyciu jednej akcji. Te akcje można stosować przy użyciu ikony śrubokrętu ![Screwdriver ikona ](media/screwdriver-icon.png) lub żarówki ![Light ikonę żarówki ](media/light-bulb-icon.png) ikon lub naciskając klawisz **Alt** +**Enter** lub **Ctrl** + **.** gdy kursor znajduje się w odpowiednim wierszu kodu. Aby uzyskać więcej informacji, zobacz [szybkie akcje](quick-actions.md) .

- **Pokaż i Edytuj definicję elementu kodu**. Można szybko wyświetlać i edytować moduł, w którym zdefiniowano element kodu, taki jak element członkowski, zmienna lub wartość lokalna.

    Aby otworzyć definicję w oknie podręcznym, zaznacz element, a następnie wybierz klawisz **Alt** +**F12** klucze lub Otwórz menu skrótów dla elementu, a następnie wybierz polecenie **Podgląd definicji**. Aby otworzyć definicję w osobnym oknie kodu, otwórz menu skrótów dla elementu, a następnie wybierz **Przejdź do definicji**.

- **Korzystaj z przykładowych aplikacji**. Można przyspieszyć tworzenie aplikacji, pobierając i instalując przykładowe aplikacje z [sieci Microsoft Developer Network](https://code.msdn.microsoft.com/). Możesz również poznać konkretną technikę lub koncepcję programowania, pobierając i eksplorowanie przykładowego pakietu dla tego obszaru.

## <a name="navigate-within-your-code"></a>Nawigowanie w kodzie

Możesz użyć różnych technik, aby szybciej znajdować i przechodzić do określonych lokalizacji w kodzie.

- **Zakładki wierszy kodu**. Przy użyciu zakładek można szybko przechodzić do określonych wierszy kodu w pliku.

    Aby ustawić zakładkę, na pasku menu wybierz kolejno opcje **edytuj**  > **zakładki**  > **Przełącz zakładkę**. Wszystkie zakładki rozwiązania można wyświetlić w oknie **zakładek** . Aby uzyskać więcej informacji, zobacz [Ustawianie zakładek w kodzie](../ide/setting-bookmarks-in-code.md).

- **Wyszukaj definicje symboli w pliku**. Możesz wyszukać w rozwiązaniu, aby zlokalizować definicje symboli i nazwy plików, ale wyniki wyszukiwania nie obejmują przestrzeni nazw ani zmiennych lokalnych.

   Aby uzyskać dostęp do tej funkcji, na pasku menu wybierz polecenie **edytuj**  > **Przejdź do**.

- **Przeglądaj ogólną strukturę kodu**. W **Eksplorator rozwiązań**można wyszukiwać i przeglądać klasy oraz ich typy i członków w projektach. Możesz również wyszukiwać symbole, wyświetlać hierarchię wywołań metody, znajdować odwołania do symboli i wykonywać inne zadania. Jeśli wybierzesz element kodu w **Eksplorator rozwiązań**, skojarzony plik zostanie otwarty na karcie **podglądu** , a kursor zostanie przeniesiony do elementu w pliku. Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md).

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

   Naciśnij klawisz **Ctrl** +**Q** , aby przejść bezpośrednio do pola wyszukiwania.

## <a name="debug-code"></a>Debuguj kod

Debugowanie może zużywać dużo czasu, ale poniższe porady mogą pomóc przyspieszyć proces.

- **Przetestuj tę samą stronę, aplikację lub witrynę w różnych przeglądarkach**. Podczas debugowania kodu można łatwo przełączać się między zainstalowanymi przeglądarkami sieci Web, w tym [inspektorem stron (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209)bez konieczności otwierania okna dialogowego **przeglądanie za pomocą** . Możesz użyć listy **obiektów docelowych debugowania** , która znajduje się na **standardowym** pasku narzędzi obok przycisku **Rozpocznij debugowanie** , aby szybko sprawdzić, która przeglądarka jest używana podczas debugowania lub wyświetlania stron.

    ![Wybierz opcje debugowania przeglądarki sieci Web](../ide/media/webbrowserdropdowntoolbar.png)

- **Ustaw tymczasowe punkty przerwania**. Można utworzyć tymczasowy punkt przerwania w bieżącym wierszu kodu i uruchomić debuger jednocześnie. Po trafieniu tego wiersza kodu debuger przechodzi w tryb przerwania. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

    Aby użyć tej funkcji, wybierz klawisze **Ctrl** +**F10** lub Otwórz menu skrótów dla wiersza kodu, na którym chcesz przerwać, a następnie wybierz polecenie **Uruchom do kursora**.

- **Przenieś punkt wykonywania podczas debugowania**. Bieżący punkt wykonywania można przenieść do innej sekcji kodu, a następnie ponownie uruchomić debugowanie od tego momentu. Ta technika jest przydatna, jeśli chcesz debugować sekcję kodu bez konieczności ponownego tworzenia wszystkich kroków wymaganych w celu uzyskania dostępu do tej sekcji. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

     Aby przenieść punkt wykonywania, przeciągnij żółtą grot strzałki do lokalizacji, w której chcesz ustawić następną instrukcję w tym samym pliku źródłowym, a następnie wybierz klawisz **F5** , aby kontynuować debugowanie.

- **Przechwyć informacje o wartości dla zmiennych**. Można dodać etykietki danych do zmiennej w kodzie i przypiąć ją, aby można było uzyskać dostęp do ostatniej znanej wartości zmiennej po zakończeniu debugowania. Aby uzyskać więcej informacji, zobacz [Wyświetlanie wartości danych w etykietkach danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Aby dodać etykietki danych, debuger musi być w trybie przerwania. Umieść kursor na zmiennej, a następnie wybierz przycisk Przypnij na wyświetlonej etykietki danych. Po zatrzymaniu debugowania w pliku źródłowym obok wiersza kodu, który zawiera zmienną, pojawia się niebieska ikona pinezki. Jeśli wskażesz niebieski numer PIN, zostanie wyświetlona wartość zmiennej z ostatniej sesji debugowania.

- **Wyczyść okno bezpośrednie**. Możesz wymazać zawartość [okna bezpośredniego](../ide/reference/immediate-window.md) w czasie projektowania, wprowadzając `>cls` lub `>Edit.ClearAll`

     Aby uzyskać więcej informacji na temat dodatkowych poleceń, zobacz [Visual Studio — Aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

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

- **Zachowaj rzadko używane pliki w edytorze**. Możesz przypinać pliki do lewej strony z karty, aby były widoczne niezależnie od tego, ile plików jest otwartych w edytorze.

   Aby przypiąć plik, wybierz kartę plik, a następnie wybierz przycisk **Przełącz stan przypięcia** .

- **Przenieś dokumenty i okna do innych monitorów**. Jeśli używasz więcej niż jednego monitora podczas opracowywania aplikacji, możesz łatwiej pracować nad częściami aplikacji, przenosząc pliki, które są otwarte w edytorze, do innego monitora. Możesz również przenieść okna narzędzi, takie jak okna debugera, do innego monitora i Zadokuj okna dokumentów i narzędzi, aby utworzyć "tratwy". Aby uzyskać więcej informacji, zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Można również łatwiej zarządzać plikami, tworząc inne wystąpienie **Eksplorator rozwiązań** i przenosząc je do innego monitora. Aby utworzyć inne wystąpienie **Eksplorator rozwiązań**, otwórz menu skrótów w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Nowy widok Eksplorator rozwiązań**.

- **Dostosuj czcionki, które pojawiają się w programie Visual Studio**. Można zmienić krój, rozmiar i kolor czcionki używany dla tekstu w IDE. Na przykład można dostosować kolor określonych elementów kodu w edytorze i krój czcionki w oknach narzędzi lub w środowisku IDE. Aby uzyskać więcej informacji, zobacz [How to: Change Fonts and Colors](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) i [How to: Change Fonts and Colors in the Editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz także

- [Visual Studio — porady i wskazówki dotyczące wpisu w blogu](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Instrukcje: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Przewodnik: tworzenie prostej aplikacji](../get-started/csharp/tutorial-wpf.md)
- [Porady i wskazówki dotyczące ułatwień dostępu](../ide/reference/accessibility-tips-and-tricks.md)
