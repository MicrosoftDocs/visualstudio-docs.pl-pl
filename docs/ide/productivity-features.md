---
title: Wskazówki dotyczące produktywności
ms.date: 2/21/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f351ffefae818beb1f51eaa41fbeea1eab81de16
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919476"
---
# <a name="productivity-tips-for-visual-studio"></a>Porady dotyczące wydajności dla programu Visual Studio

W tym artykule omówiono wskazówki dotyczące funkcji programu Visual Studio, które ułatwiają szybkie i wydajniejsze pisanie, nawigowanie i debugowanie kodu.

Aby uzyskać informacje na temat przydatnych skrótów klawiaturowych, zobacz [skróty](../ide/productivity-shortcuts.md)dotyczące produktywności. Aby uzyskać pełną listę skrótów poleceń, zobacz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="write-code"></a>Pisanie kodu

Pisz kod szybciej, korzystając z następujących funkcji.

- **Użyj poleceń wygody**. Program Visual Studio zawiera różne polecenia ułatwiające wykonywanie typowych zadań edycji szybciej. Na przykład można wybrać polecenie, aby łatwo zduplikować wiersz kodu bez konieczności jego kopiowania, zmiany położenia kursora, a następnie wklejenia. Wybierz **Edytuj** > **zduplikowane** lub naciśnij **Ctrl**+**E**,**V**. Możesz również szybko rozwijać lub zwijać zaznaczenie tekstu, wybierając pozycję **Edytuj** > **Zaawansowane** > **Rozwiń zaznaczenie** lub **Edytuj** > kontrakt**Zaawansowany** >  **Zaznaczenie**lub naciśnięcie klawisza **SHIFT**+**Alt** + **=** lub **SHIFT**+**Alt**.+ **-**

- **Korzystać z technologii IntelliSense**. Podczas wprowadzania kodu w edytorze, pojawi się informacje IntelliSense, takie jak lista członków, informacje o parametrach, szybkie informacje, pomoc podpisu i Dokończ wyraz. Funkcje te obsługują niepełne dopasowywanie tekstu. na przykład listy wyników dla List Members zawiera nie tylko wpisy, które rozpoczynają się od znaków czy zostały wprowadzone, ale także wpisy, które zawierają kombinacje znaków w dowolnym miejscu ich nazw. Aby uzyskać więcej informacji, zobacz [IntelliSense użyj](../ide/using-intellisense.md).

- **Zmień auto Wstawianie opcji IntelliSense podczas wpisywania kodu**. Przełączając IntelliSense do trybu sugestii, można określić, że opcje IntelliSense będą umieszczone tylko wtedy, gdy je samodzielnie wybierzesz.

     Aby włączyć tryb sugestia, wybierz opcję **Ctrl**+**Alt**+**spacja** kluczy lub na pasku menu wybierz **Edytuj**  >  **IntelliSense** > **Przełącz tryb uzupełniania**.

- **Używanie fragmentów kodu**. Możesz użyć wbudowanych fragmentów kodu lub utworzyć własne fragmenty kodu.

     Aby wstawić framgent kodu, na pasku menu wybierz **Edytuj** > **IntelliSense** > **Wstaw fragment kodu** lub **Otocz**, lub Otwórz menu skrótów w pliku i wybierz pozycję **fragment** > **Wstaw fragment kodu** lub **Otocz**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).

- **Rozwiązywanie błędów kodu w wierszu**. Szybkie akcje pozwalają na łatwe Refaktoryzacja, generowanie lub inny sposób modyfikować kodu za pomocą jednej akcji. Te akcje mogą być stosowane za pomocą śrubokręt ![ikonę śrubokręt](media/screwdriver-icon.png) lub żarówki ![ikoną żarówki](media/light-bulb-icon.png) ikony, lub naciskając **Alt** +  **Wprowadź** lub **Ctrl**+ **.** gdy kursor jest ustawiony na odpowiedni wiersz kodu. Zobacz [szybkie akcje](quick-actions.md) Aby uzyskać więcej informacji.

- **Pokaż i Edytuj definicję elementu kodu**. Można szybko wyświetlić i edytować ten moduł, w którym zdefiniowano element kodu, takich jak element członkowski, zmienna lub lokalnego lub.

    Aby otworzyć definicję w oknie podręcznym, zaznacz element, a następnie wybierz **Alt**+**F12** kluczy, lub Otwórz menu skrótów dla elementu, a następnie wybierz **wgląd Definicja**. Aby otworzyć definicję w oddzielnym oknie kodu, otwórz menu skrótów dla elementu, a następnie wybierz **przejdź do definicji**.

- **Użyj aplikacji przykładowych**. Można przyspieszyć opracowywanie aplikacji, pobierając i instalując aplikacje przykładowe od [sieci Microsoft Developer Network](https://code.msdn.microsoft.com/). Można także dowiesz się o określonej technologii lub koncepcji programowania, pobierając i przeglądając zestaw przykładów dotyczących danego obszaru.

## <a name="navigate-within-your-code"></a>Nawigowanie w kodzie

Aby znaleźć i Przenieś do określonych lokalizacji w kodzie szybciej, można użyć różnych technik przetwarzania.

- **Zakładki linii kodu**. Można użyć zakładek, aby szybko przechodzić do określonych wierszy kodu w pliku.

    Aby ustawić zakładki, na pasku menu, wybierz **Edytuj** > **zakładki** > **Przełącz zakładkę**. Możesz wyświetlać wszystkie zakładki dla rozwiązania w **zakładki** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie zakładek w kodzie](../ide/setting-bookmarks-in-code.md).

- **Wyszukaj definicje symbolu w pliku**. Możesz przeszukiwać rozwiązanie, aby zlokalizować definicje symboli i nazwy plików, ale wyniki wyszukiwania nie uwzględniają przestrzeni nazw lub zmiennych lokalnych.

   Aby skorzystać z tej funkcji, na pasku menu wybierz **Edytuj** > **przejdź do**.

- **Przeglądaj ogólną strukturę kodu**. W **Eksploratora rozwiązań**, możesz wyszukiwać i przeglądać klasy i ich typów i członków w projektach. Można również wyszukiwać symbole, wyświetlać hierarchię wywoływania metody, znajdować odwołania do symboli i wykonywać inne zadania. Jeśli wybierzesz element kodu w **Eksploratora rozwiązań**, skojarzony plik zostanie otwarty w **Podgląd** kartę, a kursor przeniesie się do elementu w pliku. Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md).

## <a name="find-items-faster"></a>Znajdź elementy szybciej

Możesz dodatkowo przeszukiwać środowisko IDE dla poleceń, plików i opcji, oprócz filtrowania zawartości okien narzędziowych, aby wyświetlić tylko informacje odnoszące się do bieżącego zadania.

- **Przefiltruj zawartość okna Narzędzie**. Możesz przeszukiwać zawartość wielu okien narzędziowych, takich jak **przybornika**, **właściwości** oknie i **Eksploratora rozwiązań**, ale Wyświetl tylko elementy, których nazwy zawiera znaki, które określisz.

- **Wyświetlenie tylko błędów, które mają adres**. Jeśli wybierzesz **filtru** znajdujący się na **lista błędów** narzędzi, można zmniejszyć liczbę błędów, które pojawiają się w **lista błędów** okna. Możesz wyświetlić tylko błędy w plikach, które są otwarte w edytorze, tylko błędy w bieżącym pliku lub tylko błędy w bieżącym projekcie. Można również wyszukiwać **lista błędów** okna, aby znaleźć określone błędy.

- **Znajdowanie okien dialogowych, poleceń menu, opcji i innych**. W polu wyszukiwania wprowadź słowa kluczowe lub frazy dla elementów, które próbujesz znaleźć. Na przykład następujące opcje są wyświetlane, jeśli wprowadzisz **Nowy projekt**:

   ::: moniker range="vs-2017"

   ![Szybkie uruchamianie wyniki "nowego projektu"](../ide/media/productivity_quicklaunch.png)

   Przycisk **szybkiego uruchamiania** wyświetla linki umożliwiające utworzenie nowego projektu, dodanie nowego elementu do projektu i strony **projekty i rozwiązania** w oknie dialogowym **Opcje** , między innymi. Wyniki wyszukiwania mogą również obejmować pliki projektu i okna narzędzi.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Wyniki wyszukiwania dla elementu "nowy projekt"](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Naciśnij klawisz **Ctrl**+**Q** , aby przejść bezpośrednio do pola wyszukiwania.

## <a name="debug-code"></a>Możliwe jest debugowanie kodu

Debugowanie może zajmować dużo czasu, ale poniższe porady mogą pomóc przyspieszyć proces.

- **Testowanie strony, aplikacji lub witryny w różnych przeglądarkach**. Podczas debugowania kodu można łatwo przełączać się między przeglądarkami zainstalowanych w sieci web, w tym [narzędzie Page Inspector (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209), bez konieczności otwierania **przeglądanie za pomocą** okno dialogowe. Możesz użyć **Debuguj element docelowy** listę, która znajduje się na **standardowa** pasku narzędzi obok pozycji **Rozpocznij debugowanie** przycisk, aby szybko sprawdzić, jakiej przeglądarki używasz podczas debugowania lub Wyświetlanie stron.

    ![Wybierz opcje debugowania w przeglądarce sieci web](../ide/media/webbrowserdropdowntoolbar.png)

- **Ustaw tymczasowe punkty przerwania**. Można utworzyć tymczasowy punkt przerwania w bieżącym wierszu kodu i jednocześnie uruchomić debuger. Po osiągnięciu tego wiersza kodu debuger przechodzi w tryb podziału. Aby uzyskać więcej informacji, zobacz [Nawiguj za pomocą kodu z debugerem](../debugger/navigating-through-code-with-the-debugger.md).

    Aby użyć tej funkcji, wybierz opcję **Ctrl**+**F10** kluczy lub Otwórz menu skrótów dla wiersza kodu, na którym chcesz przerwać, a następnie wybierz **Uruchom do kursora** .

- **Przenieś punkt wykonania podczas debugowania**. Można przenieść bieżący punkt wykonania do innej części kodu, a następnie ponownie uruchom debugowanie od tego momentu. Ta technika jest przydatna, jeśli chcesz debugować sekcję kodu bez konieczności ponownego przechodzenia przez wszystkie czynności, które są wymagane do uzyskania tej sekcji. Aby uzyskać więcej informacji, zobacz [Nawiguj za pomocą kodu z debugerem](../debugger/navigating-through-code-with-the-debugger.md).

     Aby przesunąć punkt wykonania, przeciągnij żółty grot do lokalizacji, w której chcesz ustawić następną instrukcję w tym samym pliku źródłowym, a następnie wybierz **F5** klawisz, aby kontynuować debugowanie.

- **Przechwytywanie informacji o wartości dla zmiennych**. Możesz dodać etykietki danych do zmiennej w kodzie i przypiąć go, aby umożliwić dostęp ostatniej znanej wartości zmiennej po zakończeniu debugowania. Aby uzyskać więcej informacji, zobacz [wyświetlanie wartości danych w poradach dotyczących](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Aby dodać etykietki danych, debuger musi być w trybie przerwania. Umieść kursor w zmiennej, a następnie wybierz przycisk szpilki na się DataTip. Po zatrzymaniu debugowania w pliku źródłowym obok wiersza kodu, który zawiera zmienną pojawia się niebieska ikona szpilki. Jeśli wskażesz niebieską zakładkę, pojawi się wartość zmiennej z ostatniej sesji debugowania.

- **Wyczyść okno bezpośrednie**. Możesz wymazać zawartość [bezpośrednim](../ide/reference/immediate-window.md) w czasie projektowania, wprowadzając `>cls` lub `>Edit.ClearAll`

     Aby uzyskać więcej informacji na temat dodatkowych poleceń, zobacz [Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

## <a name="access-visual-studio-tools"></a>Dostęp do narzędzi programu Visual Studio

Można szybko wyświetlić wiersz polecenia dla deweloperów lub innego narzędzia programu Visual Studio, jeśli przypniesz go do Start menu lub paska zadań.

::: moniker range="vs-2017"

1. W Eksploratorze Windows przejdź do *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. W Eksploratorze Windows przejdź do *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*.

::: moniker-end

2. Kliknij prawym przyciskiem myszy lub Otwórz menu kontekstowe dla **wiersz polecenia dla deweloperów**, a następnie wybierz **Przypnij do ekranu startowego** lub **Przypnij do paska zadań**.

## <a name="manage-files-toolbars-and-windows"></a>Zarządzanie plikami, paski narzędzi i systemu windows

W dowolnym momencie może być działa w wielu plikach kodów i poruszać się między kilkoma oknami narzędzi, jak utworzyć aplikację. Można organizować, korzystając z następujących wskazówek:

- **Zachowaj pliki, które są często używane widoczne w edytorze**. Możesz przypiąć pliki po lewej stronie karty, by pozostały widoczne niezależnie od tego, ile plików jest otwarty w edytorze.

   Aby przypiąć plik, wybierz kartę pliku, a następnie wybierz **Przełącz stan przypięcia** przycisku.

- **Przenoszenie dokumentów i okien na inne monitory**. Jeśli używasz więcej niż jednego monitora podczas opracowywania aplikacji, można pracować na porcjach aplikacji łatwiej, przenosząc pliki, które są otwarte w edytorze na inny monitor. Możesz również przesuwać, że okna narzędzi, takich jak okna debugera, do innego monitora i karty dokowanie okien dokumentu i narzędzi w celu utworzenia "tratwach". Aby uzyskać więcej informacji, zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Można również zarządzać plikami łatwiej, tworząc inną instancję **Eksploratora rozwiązań** i przenosząc ją na inny monitor. Aby utworzyć inną instancję programu **Eksploratora rozwiązań**, otwórz menu skrótów na liście **Eksploratora rozwiązań**, a następnie wybierz **nowy widok Eksploratora rozwiązań**.

- **Dostosowywanie czcionek, które są wyświetlane w programie Visual Studio**. Można zmienić krój czcionki, rozmiar i kolor, który jest używany dla tekstu w IDE. Na przykład możesz dostosować kolor elementów konkretnego kodu w edytorze i krój czcionki w narzędzie systemu windows lub w całej IDE. Aby uzyskać więcej informacji, zobacz [jak: Zmień czcionki i kolory](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) oraz [następujące instrukcje: Zmień czcionki i kolory w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz także

- [Domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Instrukcje: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Przewodnik: Tworzenie prostej aplikacji](../get-started/csharp/tutorial-wpf.md)
- [Ułatwienia dostępu, porady i wskazówki](../ide/reference/accessibility-tips-and-tricks.md)