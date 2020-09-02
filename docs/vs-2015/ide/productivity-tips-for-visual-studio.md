---
title: Porady dotyczące produktywności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a5b2f2e2dc00eda388b2a2d075924fa72f9eff1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670310"
---
# <a name="productivity-tips-for-visual-studio"></a>Visual Studio — wskazówki dotyczące produktywności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Postępując zgodnie z tymi wskazówkami, można szybciej i wydajnie pisać, nawigować i debugować kod w programie Visual Studio. Aby uzyskać więcej informacji na temat typowych skrótów klawiaturowych, zobacz [porady i wskazówki](../ide/tips-and-tricks-for-visual-studio.md). Aby zapoznać się z bardziej kompletną listą, zobacz temat [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) oraz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Ten temat zawiera następujące sekcje:

 [Uzyskiwanie dostępu Visual Studio Tools](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)

 [Pisanie kodu](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)

 [Nawigowanie w kodzie](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)

 [Szybsze znajdowanie elementów](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)

 [Kod debugowania](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)

 [Zarządzanie plikami, paskami narzędzi i oknami](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)

## <a name="accessing-visual-studio-tools"></a><a name="BKMK_Access"></a> Uzyskiwanie dostępu Visual Studio Tools
 Można łatwiej uzyskać dostęp do wiersz polecenia dla deweloperów lub innego narzędzia, jeśli przypinasz je do ekranu startowego lub na pasku zadań.

1. Na ekranie startowym wpisz `Visual Studio Tools` , a następnie wybierz klawisz ENTER.

2. W **Eksploratorze plików**Otwórz menu skrótów dla elementu, który chcesz:

    - Powiadomienia kompilacji

    - Menedżer pakietów możliwością debugowania

    - wiersz polecenia dla deweloperów VS2013

    - Microsoft Feedback Client 2013

    - Wiersz polecenia narzędzi VS2013 ARM Cross Tools

    - Wiersz polecenia narzędzi VS2013 x64 Cross Tools

    - VS2013 wiersz polecenia narzędzi x64 Native Tools

    - VS2013 wiersz polecenia narzędzi x86 Native Tools

3. Wybierz pozycję **Przypnij do menu Start** lub **Przypnij do paska zadań**.

## <a name="writing-code"></a><a name="BKMK_Writing"></a> Pisanie kodu
 Szybsze pisanie kodu przy użyciu następujących funkcji.

- **Korzystaj z przykładowych aplikacji**. Można przyspieszyć tworzenie aplikacji, pobierając i instalując przykładowe aplikacje z galerii kodu MSDN. Możesz również poznać konkretną technikę lub koncepcję programowania, pobierając i eksplorowanie przykładowego pakietu dla tego obszaru.

- **Użyj funkcji IntelliSense**. Podczas wprowadzania kodu w edytorze informacje o technologii IntelliSense, takie jak elementy członkowskie listy, informacje o parametrach, szybkie informacje, pomoc podpisu i pełny wyraz, pojawiają się. Funkcje te obsługują rozmyte dopasowywanie tekstu; na przykład listy wyników dla członków listy zawierają nie tylko wpisy, które zaczynają się od znaków wprowadzonych, ale także wpisy, które zawierają kombinację znaków w dowolnym miejscu nazwy. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md).

- **Zmień Autouzupełnianie opcji IntelliSense podczas wprowadzania kodu**. Przełączając funkcję IntelliSense do trybu sugestii, można określić, że opcje IntelliSense są wstawiane tylko wtedy, gdy użytkownik jawnie je wybiera.

     Aby włączyć tryb sugestii, wybierz klawisze Ctrl + Alt + spacje lub na pasku menu wybierz kolejno opcje **Edytuj**, **IntelliSense**i **Przełącz tryb uzupełniania**.

- **Użyj fragmentów kodu**. Możesz użyć wbudowanych fragmentów kodu lub utworzyć własne fragmenty kodu.

     Aby wstawić fragment kodu, na pasku menu wybierz polecenie **Edycja**, **IntelliSense**, **Wstaw fragment kodu** lub Otwórz menu skrótów w pliku i wybierz **Wstaw fragment kodu**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).

- **Naprawianie błędów kodu w tekście**. Tagi inteligentne są wyświetlane jako niebieskie lub czerwone pola w wierszu kodu. Możesz wyświetlić opcje tagów inteligentnych, wskazując jedno z pól lub przez umieszczenie kursora w wierszu kodu i wybranie kombinacji klawiszy CTRL +. (okres) klucze.

     Niebieskie pola sugerują sposoby naprawienia błędów w kodzie.

     Rysunek 1. Tagi inteligentne błędów

     ![Sugestie dotyczące tagów inteligentnych błędów](../ide/media/productivity-bluesmarttags.png "Productivity_BlueSmartTags")

     Czerwone pola sugerują sposoby refaktoryzacji kodu.

     Rysunek 2. Refaktoryzacja tagów inteligentnych

     ![Sugestie tagów inteligentnych refaktoryzacji](../ide/media/productivity-redsmarttags.png "Productivity_RedSmartTags")

- **Pokaż i Edytuj definicję elementu kodu**. Można szybko wyświetlać i edytować moduł, w którym zdefiniowano element kodu, taki jak element członkowski, zmienna lub wartość lokalna.

     Aby otworzyć definicję w oknie podręcznym, zaznacz element, a następnie wybierz klawisze Alt + F12 lub Otwórz menu skrótów dla elementu, a następnie wybierz polecenie **Podgląd definicji**. Aby otworzyć definicję w osobnym oknie kodu, otwórz menu skrótów dla elementu, a następnie wybierz **Przejdź do definicji**.

## <a name="navigating-within-your-code"></a><a name="BKMK_Navigating"></a> Nawigowanie w kodzie
 Możesz użyć różnych technik, aby szybciej znajdować i przechodzić do określonych lokalizacji w kodzie.

- **Zakładki wierszy kodu**. Przy użyciu zakładek można szybko przechodzić do określonych wierszy kodu w pliku.

     Aby ustawić zakładkę, na pasku menu wybierz kolejno opcje **Edytuj**, **zakładki**i **Przełącz zakładkę**. Wszystkie zakładki rozwiązania można wyświetlić w oknie **zakładek** . Aby uzyskać więcej informacji, zobacz [Ustawianie zakładek w kodzie](../ide/setting-bookmarks-in-code.md).

- **Wyszukaj definicje symboli w pliku**. Możesz wyszukać w rozwiązaniu, aby zlokalizować definicje symboli i nazwy plików, ale wyniki wyszukiwania nie obejmują przestrzeni nazw ani zmiennych lokalnych.

     Aby uzyskać dostęp do tej funkcji, na pasku menu wybierz pozycję **Edytuj**, a następnie **Przejdź do**.

- **Przeglądaj ogólną strukturę kodu**. W **Eksplorator rozwiązań**można wyszukiwać i przeglądać klasy oraz ich typy i członków w projektach. Możesz również wyszukiwać symbole, wyświetlać hierarchię wywołań metody, znajdować odwołania do symboli i wykonywać inne zadania. Jeśli wybierzesz element kodu w **Eksplorator rozwiązań**, skojarzony plik zostanie otwarty na karcie **podglądu** , a kursor zostanie przeniesiony do elementu w pliku. Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md).

## <a name="finding-items-faster"></a><a name="BKMK_Finding"></a> Szybsze znajdowanie elementów
 Oprócz filtrowania zawartości okien narzędzi można przeszukiwać w środowisku IDE, aby wyświetlić tylko odpowiednie informacje dotyczące bieżącego zadania.

- **Filtrowanie zawartości okien narzędzi**. Można wyszukiwać zawartość wielu okien narzędzi, takich jak **Przybornik**, okno **Właściwości** i **Eksplorator rozwiązań**, ale wyświetlane są tylko elementy, których nazwy zawierają określone znaki.

- **Wyświetl tylko błędy, które chcesz rozwiązać**. Jeśli wybierzesz przycisk **Filtr** na pasku narzędzi **Lista błędów** , możesz zmniejszyć liczbę błędów, które pojawiają się w oknie **Lista błędów** . Można wyświetlić tylko błędy w plikach, które są otwarte w edytorze, tylko błędy w bieżącym pliku lub tylko błędy w bieżącym projekcie. Możesz również wyszukać w oknie Lista błędów, aby znaleźć konkretne błędy.

- **Znajdowanie okien dialogowych, poleceń menu i opcji**. W oknie [dialogowym szybkie uruchamianie, środowisko, opcje](../ide/reference/quick-launch-environment-options-dialog-box.md) Wprowadź słowa kluczowe lub frazy dla elementów, które próbujesz znaleźć. Na przykład następujące opcje są wyświetlane, jeśli wprowadzisz `new project` :

     Rysunek 3. Lista wyników szybkiego uruchamiania dla `new project`

     ![Wyniki szybkiego uruchamiania dla "nowy projekt"](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

     Przycisk **szybkiego uruchamiania** wyświetla linki do okna dialogowego **Nowy projekt** , okno dialogowe **Dodaj nowy element** i strony projekty i rozwiązania w oknie dialogowym **Opcje** , między innymi. Wyniki szybkiego uruchamiania mogą również obejmować pliki projektu i okna narzędzi.

## <a name="debugging-code"></a><a name="BKMK_Debugging"></a> Kod debugowania
 Debugowanie może zużywać dużo czasu, ale poniższe porady mogą pomóc przyspieszyć proces.

- **Przetestuj tę samą stronę, aplikację lub witrynę w różnych przeglądarkach**. Podczas debugowania kodu można łatwo przełączać się między zainstalowanymi przeglądarkami sieci Web, w tym [inspektorem stron (Visual Studio)](https://msdn.microsoft.com/library/65880969-1ad2-47be-85b9-bb12c81bf209)bez konieczności otwierania okna dialogowego **przeglądanie za pomocą** . Możesz użyć listy **obiektów docelowych debugowania** , która znajduje się na **standardowym** pasku narzędzi obok przycisku **Rozpocznij debugowanie** , aby szybko sprawdzić, która przeglądarka jest używana podczas debugowania lub wyświetlania stron.

     ![Wybierz opcje debugowania przeglądarki sieci Web](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")

- **Ustaw tymczasowe punkty przerwania**. Można utworzyć tymczasowy punkt przerwania w bieżącym wierszu kodu i uruchomić debuger jednocześnie. Po trafieniu tego wiersza kodu debuger przechodzi w tryb przerwania. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

     Aby użyć tej funkcji, wybierz klawisze CTRL + F10 lub Otwórz menu skrótów dla wiersza kodu, na którym chcesz przerwać, a następnie wybierz polecenie **Uruchom do kursora**.

- **Przenieś punkt wykonywania podczas debugowania**. Bieżący punkt wykonywania można przenieść do innej sekcji kodu, a następnie ponownie uruchomić debugowanie od tego momentu. Ta technika jest przydatna, jeśli chcesz debugować sekcję kodu bez konieczności ponownego tworzenia wszystkich kroków wymaganych w celu uzyskania dostępu do tej sekcji. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

     Aby przenieść punkt wykonywania, przeciągnij żółtą grot strzałki do lokalizacji, w której chcesz ustawić następną instrukcję w tym samym pliku źródłowym, a następnie wybierz klawisz F5, aby kontynuować debugowanie.

- **Przechwyć informacje o wartości dla zmiennych**. Można dodać etykietki danych do zmiennej w kodzie i przypiąć ją, aby można było uzyskać dostęp do ostatniej znanej wartości zmiennej po zakończeniu debugowania. Aby uzyskać więcej informacji, zobacz [Wyświetlanie wartości danych w etykietkach danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Aby dodać etykietki danych, debuger musi być w trybie przerwania. Umieść kursor na zmiennej, a następnie wybierz przycisk Przypnij na wyświetlonej etykietki danych. Po zatrzymaniu debugowania w pliku źródłowym obok wiersza kodu, który zawiera zmienną, pojawia się niebieska ikona pinezki. Jeśli wskażesz niebieski numer PIN, zostanie wyświetlona wartość zmiennej z ostatniej sesji debugowania.

- **Wyczyść okno bezpośrednie**. Możesz wymazać zawartość [okna bezpośredniego](../ide/reference/immediate-window.md) w czasie projektowania, wprowadzając `>cls` lub `>Edit.ClearAll`

     Aby uzyskać więcej informacji na temat dodatkowych poleceń, zobacz [Visual Studio — Aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

## <a name="managing-files-toolbars-and-windows"></a><a name="BKMK_Managing"></a> Zarządzanie plikami, paskami narzędzi i oknami
 W dowolnym momencie możesz pracować w wielu plikach kodu i poruszać się po kilku oknach narzędzi podczas opracowywania aplikacji. Możesz zachować swoją organizację, korzystając z poniższych wskazówek.

- **Zachowaj rzadko używane pliki w edytorze**. Możesz przypinać pliki do lewej strony z karty, aby były widoczne niezależnie od tego, ile plików jest otwartych w edytorze.

     Aby przypiąć plik, wybierz kartę plik, a następnie wybierz przycisk **Przełącz stan przypięcia** .

- **Przenieś dokumenty i okna do innych monitorów**. Jeśli używasz więcej niż jednego monitora podczas opracowywania aplikacji, możesz łatwiej pracować nad częściami aplikacji, przenosząc pliki, które są otwarte w edytorze, do innego monitora. Możesz również przenieść okna narzędzi, takie jak okna debugera, do innego monitora i Zadokuj okna dokumentów i narzędzi, aby utworzyć "tratwy". Aby uzyskać więcej informacji, zobacz [How to: Rozmieoć i Docking Windows](../misc/how-to-arrange-and-dock-windows.md).

     Można również łatwiej zarządzać plikami, tworząc inne wystąpienie **Eksplorator rozwiązań** i przenosząc je do innego monitora. Aby utworzyć inne wystąpienie **Eksplorator rozwiązań**, otwórz menu skrótów w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Nowy widok Eksplorator rozwiązań**.

- **Dostosuj czcionki, które pojawiają się w programie Visual Studio**. Można zmienić krój, rozmiar i kolor czcionki używany dla tekstu w IDE. Na przykład można dostosować kolor określonych elementów kodu w edytorze i krój czcionki w oknach narzędzi lub w środowisku IDE. Aby uzyskać więcej informacji, zobacz [How to: Change Fonts and Colors](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) i [How to: Change Fonts and Colors in the Editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz też
 [Domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) [: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md) [Przewodnik: Tworzenie proste](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [porady i wskazówki dotyczące ułatwień dostępu](../ide/reference/accessibility-tips-and-tricks.md) aplikacji
