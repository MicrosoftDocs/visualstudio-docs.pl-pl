---
title: Wskazówki dotyczące produktywności | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 096de590d49f5d09614bb9149ae6e5218f2ab7ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785690"
---
# <a name="productivity-tips-for-visual-studio"></a>Visual Studio — wskazówki dotyczące produktywności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wykorzystując te porady, możesz można szybciej i wydajniej zapisu, przejść i debugowania kodu w programie Visual Studio. Aby uzyskać więcej informacji na temat typowych skrótów klawiaturowych, zobacz [porady i wskazówki](../ide/tips-and-tricks-for-visual-studio.md). Aby uzyskać bardziej szczegółowy wykaz zobacz [określenie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) i [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Ten temat zawiera następujące sekcje:

 [Uzyskiwanie dostępu do narzędzi programu Visual Studio](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)

 [Pisanie kodu](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)

 [Poruszanie się w obrębie kodu](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)

 [Szybsze znajdowanie elementów](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)

 [Debugowanie kodu](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)

 [Zarządzanie plikami, paski narzędzi i Windows](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)

##  <a name="BKMK_Access"></a> Uzyskiwanie dostępu do narzędzi programu Visual Studio
 Można łatwiej uzyskać dostęp wiersz polecenia dla deweloperów lub innego narzędzia, gdy możesz przypiąć do paska zadań lub ekranu startowego.

1.  Na ekranie startowym wpisz `Visual Studio Tools`, a następnie naciśnij klawisz Enter.

2.  W **Eksploratora plików**, otwórz menu skrótów dla elementu, który chcesz:

    -   Powiadomienia związane z kompilacją

    -   Debugowalny Menedżer pakietów

    -   Wiersz polecenia programisty dla VS2013

    -   Microsoft Feedback Client 2013

    -   VS2013 ARM Cross Tools wiersza polecenia

    -   VS2013 x64 wielu narzędzi wiersza polecenia

    -   VS2013 x64 natywnych narzędzi wiersza polecenia

    -   VS2013 x86 natywnych narzędzi wiersza polecenia

3.  Wybierz **Przypnij do ekranu startowego** lub **Przypnij do paska zadań**.

##  <a name="BKMK_Writing"></a> Pisanie kodu
 Pisz kod szybciej, korzystając z następujących funkcji.

-   **Użyj aplikacji przykładowych**. Można przyspieszyć opracowywanie aplikacji, pobierając i instalując aplikacje przykładowe z galerii kodu MSDN. Można także dowiesz się o określonej technologii lub koncepcji programowania, pobierając i przeglądając zestaw przykładów dotyczących danego obszaru.

-   **Korzystać z technologii IntelliSense**. Podczas wprowadzania kodu w edytorze, pojawi się informacje IntelliSense, takie jak lista członków, informacje o parametrach, szybkie informacje, pomoc podpisu i Dokończ wyraz. Funkcje te obsługują niepełne dopasowywanie tekstu. na przykład listy wyników dla List Members zawiera nie tylko wpisy, które rozpoczynają się od znaków czy zostały wprowadzone, ale także wpisy, które zawierają kombinacje znaków w dowolnym miejscu ich nazw. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).

-   **Zmień auto Wstawianie opcji IntelliSense podczas wpisywania kodu**. Przełączając IntelliSense do trybu sugestii, można określić, że opcje IntelliSense będą umieszczone tylko wtedy, gdy je samodzielnie wybierzesz.

     Aby włączyć tryb sugestia, wybierz klawisze Ctrl + Alt + spacja kluczy lub na pasku menu wybierz **Edytuj**, **IntelliSense**, **Przełącz tryb uzupełniania**.

-   **Używanie fragmentów kodu**. Można użyć wbudowanych fragmentów kodu lub utworzyć własne fragmenty kodu.

     Aby wstawić framgent kodu, na pasku menu wybierz **Edytuj**, **IntelliSense**, **Wstaw fragment kodu** lub Otwórz menu skrótów w pliku i wybierz pozycję **Wstaw fragment kodu** . Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).

-   **Rozwiązywanie błędów kodu w wierszu**. Tagi inteligentne są wyświetlane jako niebieskie lub czerwone pola pod wierszem kodu. Możesz wyświetlić opcje tagów inteligentnych, wskazując jedno z pól lub umieszczając kursor w wierszu kodu i wybierając Ctrl +. (okres) klucze.

     Niebieskich pola sugerują sposoby naprawienia błędy w kodzie.

     Rysunek 1: Błąd inteligentnych tagów

     ![Błąd tagi inteligentne sugestie](../ide/media/productivity-bluesmarttags.png "Productivity_BlueSmartTags")

     Czerwone pola sugerują sposoby Refaktoryzuj swój kod.

     Rysunek 2: Optymalizacja inteligentnych tagów

     ![Refaktoryzuj sugestii tagów inteligentnych](../ide/media/productivity-redsmarttags.png "Productivity_RedSmartTags")

-   **Pokaż i Edytuj definicję elementu kodu**. Można szybko wyświetlić i edytować ten moduł, w którym zdefiniowano element kodu, takich jak element członkowski, zmienna lub lokalnego lub.

     Aby otworzyć definicję w oknie podręcznym, zaznacz element i następnie wybierz polecenie klawisze Alt + F12 lub Otwórz menu skrótów dla elementu a następnie wybierz **Peek Definition**. Aby otworzyć definicję w oddzielnym oknie kodu, otwórz menu skrótów dla elementu, a następnie wybierz **przejdź do definicji**.

##  <a name="BKMK_Navigating"></a> Poruszanie się w obrębie kodu
 Aby znaleźć i Przenieś do określonych lokalizacji w kodzie szybciej, można użyć różnych technik przetwarzania.

-   **Zakładki linii kodu**. Można użyć zakładek, aby szybko przechodzić do określonych wierszy kodu w pliku.

     Aby ustawić zakładki, na pasku menu, wybierz **Edytuj**, **zakładki**, **Przełącz zakładkę**. Możesz wyświetlać wszystkie zakładki dla rozwiązania w **zakładki** okna. Aby uzyskać więcej informacji, zobacz [ustawienie zakładek w kodzie](../ide/setting-bookmarks-in-code.md).

-   **Wyszukaj definicje symbolu w pliku**. Możesz przeszukiwać rozwiązanie, aby zlokalizować definicje symboli i nazwy plików, ale wyniki wyszukiwania nie uwzględniają przestrzeni nazw lub zmiennych lokalnych.

     Aby skorzystać z tej funkcji, na pasku menu wybierz **Edytuj**, **przejdź do**.

-   **Przeglądaj ogólną strukturę kodu**. W **Eksploratora rozwiązań**, możesz wyszukiwać i przeglądać klasy i ich typów i członków w projektach. Można również wyszukiwać symbole, wyświetlać hierarchię wywoływania metody, znajdować odwołania do symboli i wykonywać inne zadania. Jeśli wybierzesz element kodu w **Eksploratora rozwiązań**, skojarzony plik zostanie otwarty w **Podgląd** kartę, a kursor przeniesie się do elementu w pliku. Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md).

##  <a name="BKMK_Finding"></a> Szybsze znajdowanie elementów
 Możesz dodatkowo przeszukiwać środowisko IDE dla poleceń, plików i opcji, oprócz filtrowania zawartości okien narzędziowych, aby wyświetlić tylko informacje odnoszące się do bieżącego zadania.

-   **Przefiltruj zawartość okna Narzędzie**. Możesz przeszukiwać zawartość wielu okien narzędziowych, takich jak **przybornika**, **właściwości** oknie i **Eksploratora rozwiązań**, ale Wyświetl tylko elementy, których nazwy zawiera znaki, które określisz.

-   **Wyświetlenie tylko błędów, które mają adres**. Jeśli wybierzesz **filtru** znajdujący się na **lista błędów** narzędzi, można zmniejszyć liczbę błędów, które pojawiają się w **lista błędów** okna. Możesz wyświetlić tylko błędy w plikach, które są otwarte w edytorze, tylko błędy w bieżącym pliku lub tylko błędy w bieżącym projekcie. Możesz też dokonać wyszukiwania w oknie Lista błędów, aby znaleźć określone błędy.

-   **Znajdowanie okien dialogowych, poleceń menu i opcji**. W [Szybkie uruchamianie, środowisko, okno dialogowe Opcje](../ide/reference/quick-launch-environment-options-dialog-box.md) wprowadź słowa kluczowe lub frazy dla elementów, które próbujesz znaleźć. Na przykład, poniższe opcje pojawiają się po wprowadzeniu `new project`:

     Rysunek 3: Szybkie uruchomieni lista dla `new project`

     ![Szybkie uruchamianie wyniki "nowy projekt"](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

     **Szybkie uruchamianie** Wyświetla łącza do **nowy projekt** okno dialogowe **Dodaj nowy element** okno dialogowe, a strony Projekty i rozwiązania w **opcje** okna dialogowego pole, między innymi. Szybkie uruchomieni może również obejmować pliki projektu i okna narzędzi.

##  <a name="BKMK_Debugging"></a> Debugowanie kodu
 Debugowanie może zajmować dużo czasu, ale poniższe porady mogą pomóc przyspieszyć proces.

-   **Testowanie strony, aplikacji lub witryny w różnych przeglądarkach**. Podczas debugowania kodu można łatwo przełączać się między przeglądarkami zainstalowanych w sieci web, w tym [narzędzie Page Inspector (Visual Studio)](http://msdn.microsoft.com/library/65880969-1ad2-47be-85b9-bb12c81bf209), bez konieczności otwierania **przeglądanie za pomocą** okno dialogowe. Możesz użyć **Debuguj element docelowy** listę, która znajduje się na **standardowa** pasku narzędzi obok pozycji **Rozpocznij debugowanie** przycisk, aby szybko sprawdzić, jakiej przeglądarki używasz podczas debugowania lub Wyświetlanie stron.

     ![Wybierz opcje debugowania w przeglądarce sieci Web](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")

-   **Ustaw tymczasowe punkty przerwania**. Można utworzyć tymczasowy punkt przerwania w bieżącym wierszu kodu i jednocześnie uruchomić debuger. Po osiągnięciu tego wiersza kodu debuger przechodzi w tryb podziału. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md).

     Aby użyć tej funkcji, wybierz klawisze Ctrl + F10 kluczy lub Otwórz menu skrótów dla wiersza kodu, na którym chcesz przerwać, a następnie wybierz **Uruchom do kursora**.

-   **Przenieś punkt wykonania podczas debugowania**. Można przenieść bieżący punkt wykonania do innej części kodu, a następnie ponownie uruchom debugowanie od tego momentu. Ta technika jest przydatna, jeśli chcesz debugować sekcję kodu bez konieczności ponownego przechodzenia przez wszystkie czynności, które są wymagane do uzyskania tej sekcji. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md).

     Aby przesunąć punkt wykonania, przeciągnij żółty grot do lokalizacji, w której chcesz ustawić następną instrukcję w tym samym pliku źródłowym, a następnie wybierz klawisz F5, aby kontynuować debugowanie.

-   **Przechwytywanie informacji o wartości dla zmiennych**. Możesz dodać etykietki danych do zmiennej w kodzie i przypiąć go, aby umożliwić dostęp ostatniej znanej wartości zmiennej po zakończeniu debugowania. Aby uzyskać więcej informacji, zobacz [wyświetlanie wartości danych w poradach dotyczących](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Aby dodać etykietki danych, debuger musi być w trybie przerwania. Umieść kursor w zmiennej, a następnie wybierz przycisk szpilki na się DataTip. Po zatrzymaniu debugowania w pliku źródłowym obok wiersza kodu, który zawiera zmienną pojawia się niebieska ikona szpilki. Jeśli wskażesz niebieską zakładkę, pojawi się wartość zmiennej z ostatniej sesji debugowania.

-   **Wyczyść okno bezpośrednie**. Możesz wymazać zawartość [bezpośrednim](../ide/reference/immediate-window.md) w czasie projektowania, wprowadzając `>cls` lub `>Edit.ClearAll`

     Aby uzyskać więcej informacji na temat dodatkowych poleceń, zobacz [Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

##  <a name="BKMK_Managing"></a> Zarządzanie plikami, paski narzędzi i Windows
 W dowolnym momencie może być działa w wielu plikach kodów i poruszać się między kilkoma oknami narzędzi, jak utworzyć aplikację. Możesz zachować zorganizowanym przy użyciu następujących wskazówek.

-   **Zachowaj pliki, które są często używane widoczne w edytorze**. Możesz przypiąć pliki po lewej stronie karty, by pozostały widoczne niezależnie od tego, ile plików jest otwarty w edytorze.

     Aby przypiąć plik, wybierz kartę pliku, a następnie wybierz **Przełącz stan przypięcia** przycisku.

-   **Przenoszenie dokumentów i okien na inne monitory**. Jeśli używasz więcej niż jednego monitora podczas opracowywania aplikacji, można pracować na porcjach aplikacji łatwiej, przenosząc pliki, które są otwarte w edytorze na inny monitor. Możesz również przesuwać, że okna narzędzi, takich jak okna debugera, do innego monitora i karty dokowanie okien dokumentu i narzędzi w celu utworzenia "tratwach". Aby uzyskać więcej informacji, zobacz [jak: Aranżowanie i dokowanie Windows](../misc/how-to-arrange-and-dock-windows.md).

     Można również zarządzać plikami łatwiej, tworząc inną instancję **Eksploratora rozwiązań** i przenosząc ją na inny monitor. Aby utworzyć inną instancję programu **Eksploratora rozwiązań**, otwórz menu skrótów na liście **Eksploratora rozwiązań**, a następnie wybierz **nowy widok Eksploratora rozwiązań**.

-   **Dostosowywanie czcionek, które są wyświetlane w programie Visual Studio**. Można zmienić krój czcionki, rozmiar i kolor, który jest używany dla tekstu w IDE. Na przykład możesz dostosować kolor elementów konkretnego kodu w edytorze i krój czcionki w narzędzie systemu windows lub w całej IDE. Aby uzyskać więcej informacji, zobacz [jak: Zmiana czcionek i kolorów](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) i [jak: Zmiana czcionek i kolorów w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz też
 [Domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) [jak: Dostosowywanie menu i pasków zadań](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md) [instruktażu: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [i porady dotyczące ułatwień dostępu](../ide/reference/accessibility-tips-and-tricks.md)
