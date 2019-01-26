---
title: Polecenia nawigacji kodu
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a2bb4bf9467000a792a728259d37f40e534ad3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039140"
---
# <a name="navigate-code"></a>Przechodzenie do kodu

Visual Studio zapewnia wiele sposobów nawigowania po kodzie w edytorze. Ten temat zawiera podsumowanie różnych sposobów na poruszanie się po kodzie i zawiera linki do tematów, w których sposoby te opisano bardziej szczegółowo.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Polecenia „Nawiguj wstecz” i „Nawiguj do przodu”

Możesz użyć przycisków **Nawiguj wstecz** (**Ctrl**+**-**) i **Nawiguj do przodu** ( **CTRL**+**Shift**+**-**) na pasku narzędzi, aby przesunąć punkt wstawiania do poprzednich lokalizacji lub powrócić do ostatniej lokalizacji z poprzedniej lokalizacji. Przyciski te zachowują ostatnich 20 lokalizacji. Polecenia te są również dostępne w menu **Widok** jako **Nawiguj wstecz** i **Nawiguj do przodu**.

![Przyciski nawigacji do przodu i do tyłu](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Pasek nawigacyjny

Za pomocą **paska nawigacyjnego** (rozwijanych pól u góry okna kodu) można przejść do kodu w bazie kodu. Po wybraniu typu lub elementu członkowskiego można przejść bezpośrednio do niego. Pasek nawigacyjny pojawia się, gdy edytujesz kod w bazie kodu Visual Basic, C# lub C++. W przypadku klasy częściowej elementy członkowskie zdefiniowane poza bieżącym plikiem kodu mogą być wyłączone (są wtedy wyświetlane na szaro).

 ![Pasek nawigacyjny kodu](../ide/media/vside_navigation_bar.png)

Można nawigować list rozwijanych w następujący sposób:

- Aby przejść do innego projektu, do którego należy bieżący plik, należy wybrać listę rozwijaną po lewej stronie.

- Aby przejść do klasy lub typu, wybierz je w środku listy rozwijanej.

- Aby przejść bezpośrednio do procedury lub innego członka klasy, należy wybrać odpowiednie listy rozwijanej.

- Aby przenieść fokus z okna kodu do paska nawigacji, naciśnij kombinację klawiszy skrótów **Ctrl**+**F2**.

- Aby przenieść fokus z pole, na pasku nawigacyjnym, naciśnij klawisz **kartę** klucza.

- Aby zaznaczyć element paska nawigacji, który ma fokus i powrócić do okna kodu, naciśnij **Enter** klucza.

- Powrót z paska nawigacji w kodzie bez zaznaczania żadnych, naciśnij klawisz **Esc** klucza.

Aby ukryć pasek nawigacyjny, należy zmienić **pasek nawigacyjny** opcji **Edytor tekstu wszystkie języki** ustawień (**narzędzia** > **opcje**  >  **Edytora tekstów** > **wszystkie języki**), lub zmienić ustawienia dla poszczególnych języków.

## <a name="find-all-references"></a>Znajdź wszystkie odwołania

Znajduje wszystkie odwołania do wybranego elementu w rozwiązaniu. Umożliwia to, aby sprawdzić efekty uboczne o dużych refaktoryzacji lub sprawdzić "nieużywany" kod. Naciśnij klawisz **F8** do przechodzenia między wynikami. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).

Dane wejściowe | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekst zawarty wewnątrz nazwy typu, a następnie naciśnij klawisz **Shift**+**F12**
**Myszy** | Wybierz **Znajdź wszystkie odwołania** z menu podręcznego

## <a name="reference-highlighting"></a>Wyróżnianie odwołań

Po kliknięciu symbolu w kodzie źródłowym, wszystkie wystąpienia tego symbolu zostaną wyróżnione w dokumencie. Wyróżnione symbole mogą zawierać oświadczenia i odwołania i wiele innych symboli, które **Znajdź wszystkie odwołania** zwróci. Należą do nich nazwy klas, obiektów, zmiennych, metod i właściwości. W kodzie języka Visual Basic słowa kluczowe dla wielu struktur sterowania są również wyróżnione. Aby przejść do następnego lub poprzedniego wyróżnionego symbolu, naciśnij **Ctrl**+**Shift**+**strzałkę w dół** lub **Ctrl** + **Shift**+**Strzałka w górę**. Można zmienić kolor podświetlenia w **narzędzia** > **opcje** > **środowiska** > **czcionek i Kolory** > **wyróżnione odwołanie**.

## <a name="go-to-commands"></a>Przejdź do polecenia

Przejdź do zawiera następujące polecenia, które są dostępne w **Edytuj** menu w obszarze **przejdź do**:

- **Przejdź do wiersza** (**Ctrl**+**G**): Przenieś do wiersza o określonym numerze w aktywnym dokumencie.

- **Przejdź do wszystkich** (**Ctrl**+**T** lub **Ctrl**+**,**): Przenieś do określonego wiersza, typu, plik, składnika lub symbol.

- **Go To File** (**Ctrl**+**1**, **Ctrl**+**F**): Przenieś do określonego pliku w rozwiązaniu.

- **Przejdź do niedawno używany plik** (**Ctrl**+**1**, **Ctrl**+**R**): Przenieś plik określony, przechodź do ostatnio wyświetlanych w rozwiązaniu (nowe w programie Visual Studio 2017 wersja 15.8).

- **Przejdź do typu** (**Ctrl**+**1**, **Ctrl**+**T**): Przejście do określonego typu w rozwiązaniu.

- **Przejdź do elementu członkowskiego** (**Ctrl**+**1**, **Ctrl**+**M**): Przejście do określonego elementu członkowskiego w rozwiązaniu.

- **Go To Symbol** (**Ctrl**+**1**, **Ctrl**+**S**): Przejście do określonego symbolu w rozwiązaniu.

W Visual Studio 2017 w wersji, należy zachować 15,8 lub nowszą wersją, następujące **przejdź do** nawigacji nie są również dostępne polecenia:

- **Przejdź do następnego problemu w pliku** (**Alt**+**PgDn**) i **przejdź na poprzedni problem w pliku** (**Alt** + **PgUp**)

- **Przejdź do ostatniego edytowanie lokalizacji** (**Ctrl**+**Shift**+**Backspace**)

Zobacz więcej informacji na temat tych poleceń w [Znajdowanie kodu za pomocą poleceń przejdź do](../ide/go-to.md) tematu.

## <a name="go-to-definition"></a>Przejdź do definicji

Przejdź do definicji powoduje przejście do definicji wybranego elementu. Aby uzyskać więcej informacji, zobacz [przejdź do definicji i zobacz definicję](../ide/go-to-and-peek-definition.md).

Dane wejściowe | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekst zawarty wewnątrz nazwy typu, a następnie naciśnij klawisz **F12**
**Myszy** | Kliknij prawym przyciskiem myszy nazwę typu, a następnie wybierz pozycję **przejdź do definicji** lub naciśnij **Ctrl** i kliknij nazwę typu (nowego programu Visual Studio 2017 wersji 15.4)

## <a name="peek-definition"></a>Zobacz definicję

Definicja zaznaczonego elementu w oknie wglądu Wyświetla definicji bez przechodzenia poza bieżącą lokalizację w edytorze kodu. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie i edytowanie kodu za pomocą funkcji zobacz definicję](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) i [przejdź do definicji i zobacz definicję](../ide/go-to-and-peek-definition.md).

Dane wejściowe | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekst zawarty wewnątrz nazwy typu, a następnie naciśnij klawisz **Alt**+**F12**
**Myszy** | Kliknij prawym przyciskiem myszy nazwę typu, a następnie wybierz pozycję **Peek Definition** lub naciśnij **Ctrl** i kliknij nazwę typu (Jeśli masz **Otwórz definicję w widoku podglądu** zaznaczoną opcją)

## <a name="go-to-implementation"></a>Przejdź do implementacji

Przy użyciu przejdź do implementacji, możesz przejść z klasy bazowej lub wpisz, aby ich implementacji. Jeśli istnieje wiele implementacji, zobaczysz je na liście **wyniki wyszukiwania symboli** okna:

Dane wejściowe | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekst zawarty wewnątrz nazwy typu, a następnie naciśnij klawisz **Ctrl**+**F12**
**Myszy** | Kliknij prawym przyciskiem myszy nazwę typu, a następnie wybierz pozycję **przejdź do implementacji**

## <a name="call-hierarchy"></a>Hierarchia wywołań

Możesz wyświetlić wywołania do i z metody w [hierarchię wywołań, okno](../ide/reference/call-hierarchy.md):

Dane wejściowe | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekst zawarty wewnątrz nazwy typu, a następnie naciśnij klawisz **Ctrl**+**K**, **Ctrl**+**T**
**Myszy** | Kliknij prawym przyciskiem myszy na nazwę elementu członkowskiego, a następnie wybierz pozycję **Pokaż hierarchię wywołań**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Kolejne polecenia metody i poprzedniej metody (Visual Basic)

W plikach kodu języka Visual Basic należy użyć tych poleceń, aby przenieść punkt wstawiania do różnych metod. Wybierz **Edytuj** > **Następna metoda** lub **Edytuj** > **Poprzednia metoda**.

## <a name="structure-visualizer"></a>Wizualizator struktury

Funkcja Wizualizator struktury w kodzie edytor *linie prowadnic struktury* -pionowa linia przerywana wiersze, które wskazują, dopasowywanie nawiasów klamrowych w bazie kodu. Dzięki temu je łatwiej zobaczyć, gdzie rozpocząć bloków logicznych i zakończenia.

![Wizualizator struktury](../ide/media/vside_structure_visualizer.png)

Aby wyłączyć linie prowadnic struktury, przejdź do **narzędzia** > **opcje** > **edytora tekstów** > **ogólne** i wyczyść **Pokaż linie prowadnic struktury** pole.

## <a name="enhanced-scroll-bar"></a>Rozszerzonego paska przewijania

Aby uzyskać ogólny widok kodu, można użyć rozszerzonego paska przewijania w oknie kodu. W trybie mapy widać podglądy kodu podczas przesuwania kursora w górę i w dół na pasku przewijania. Aby uzyskać więcej informacji, zobacz [jak: Śledzenie kodu przez dostosowania paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informacje o funkcji CodeLens

Można znaleźć informacje dotyczące konkretnego kodu, takich jak zmian i kto wprowadził te zmiany, odwołania, usterki, elementy robocze, przeglądy kodu i jednostki stan testu w przypadku korzystania z witryny CodeLens w edytorze kodu. CodeLens działa jak ekran projekcyjny, gdy używasz programu Visual Studio Enterprise z programem Team Foundation Server. Zobacz [znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Pokaż hierarchię wywołań](../ide/reference/call-hierarchy.md)
