---
title: Polecenia nawigacji kodu
ms.date: 11/21/2019
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
author: TerryGLee
ms.author: tglee
manager: tglee
ms.workload:
- multiple
ms.openlocfilehash: 0216a71b675473d54aec9738ea7bdc85b7643841
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585824"
---
# <a name="navigate-code"></a>Nawigowanie po kodzie

Visual Studio oferuje wiele sposobów, aby poruszać się po kodzie w edytorze. W tym temacie podsumowano różne sposoby poruszania się po kodzie i zawiera łącza do tematów, które przejść do bardziej szczegółowych.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Nawigowanie do tyłu i nawigowanie do przodu poleceń

Za pomocą przycisków **Nawiguj wstecz** **(Ctrl)**+**-** i **Przejdź do przodu** **(Ctrl**+**Shift)**+**-** na pasku narzędzi można przenieść punkt wstawiania do poprzednich lokalizacji lub powrócić do nowszej lokalizacji z poprzedniej lokalizacji. Przyciski te zachowują ostatnie 20 lokalizacji punktu wstawiania. Polecenia te są również dostępne w menu **Widok** w obszarze **Nawigacja do tyłu** i **Nawiguj do przodu**.

![Przyciski nawigacyjne do przodu i do tyłu](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Pasek nawigacyjny

Można użyć **paska nawigacyjnego** (rozwijane pola w górnej części okna kodu), aby przejść do kodu w bazie kodu. Możesz wybrać typ lub element członkowski, aby przejść bezpośrednio do niego. Pasek nawigacyjny pojawia się podczas edytowania kodu w bazie kodu języka Visual Basic, C#lub C++. W klasie częściowej elementy członkowskie zdefiniowane poza bieżącym plikiem kodu mogą być wyłączone (są wyświetlane na szaro).

![Pasek nawigacyjny kodu](../ide/media/vside_navigation_bar.png)

Możesz poruszać się po polach rozwijanych w następujący sposób:

- Aby przejść do innego projektu, do którego należy bieżący plik, wybierz go z listy rozwijanej po lewej stronie.

- Aby przejść do klasy lub typu, wybierz ją w środkowej listy rozwijanej.

- Aby przejść bezpośrednio do procedury lub innego członka klasy, wybierz ją w prawym rozwijaniu.

- Aby przesunąć fokus z okna kodu na pasek nawigacyjny, naciśnij kombinację klawiszy skrótu **Ctrl**+**F2**.

- Aby przesunąć fokus z pola do pola na pasku nawigacyjnym, naciśnij klawisz **Tab.**

- Aby wybrać element paska nawigacyjnego, który ma fokus i powrócić do okna kodu, naciśnij klawisz **Enter.**

- Aby przywrócić fokus z paska nawigacyjnego do kodu bez wybierania czegokolwiek, naciśnij klawisz **Esc.**

Aby ukryć pasek nawigacyjny, zmień opcję **Pasek nawigacyjny** w **ustawieniach Edytora tekstu Wszystkie języki** **(Narzędzia** > **Opcje** > **Edytor tekstu Wszystkie** > **języki)** lub możesz zmienić ustawienia dla poszczególnych języków.

## <a name="find-all-references"></a>Znajdź wszystkie odwołania

Znajduje wszystkie odwołania do wybranego elementu w rozwiązaniu. Można użyć tego, aby sprawdzić możliwe skutki uboczne dużych refaktoryzacji lub zweryfikować "martwy" kod. Naciśnij **klawisz F8,** aby przejść między wynikami. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).

Dane wejściowe | Funkcja
------------ | ---
**Klawiatura** | Umieść kursor tekstu w środku nazwy typu i naciśnij **klawisz Shift**+**F12**
**Mysz** | Z menu po kliknięciu prawym przyciskiem myszy wybierz polecenie **Znajdź wszystkie odwołania**

## <a name="reference-highlighting"></a>Wyróżnianie odwołań

Po kliknięciu symbolu w kodzie źródłowym wszystkie wystąpienia tego symbolu są wyróżnione w dokumencie. Wyróżnione symbole mogą zawierać deklaracje i odwołania oraz wiele innych symboli, które **zwracają wszystkie odwołania.** Należą do nich nazwy klas, obiektów, zmiennych, metod i właściwości. W kodzie języka Visual Basic wyróżnione są również słowa kluczowe dla wielu struktur kontrolnych. Aby przejść do następnego lub poprzedniego wyróżnionego symbolu, naciśnij **klawisze Ctrl**+**Shift**+**Down Arrow** lub **Ctrl**+**Shift**+Up**Arrow**. Kolor wyróżniania można zmienić w obszarze**Opcje** >  **narzędzi** > **Czcionki środowiska** > **i kolory** > **wyróżnione .**

## <a name="go-to-commands"></a>Przejdź do poleceń

Przejdź do ma następujące polecenia, które są dostępne w menu **Edycja** w obszarze **Przejdź do**:

- **Przejdź do wiersza** (**Ctrl**+**G):** Przejdź do określonego numeru wiersza w aktywnym dokumencie.

- **Przejdź do wszystkich** **(Ctrl**+**T** lub **Ctrl**+**,**): Przejdź do określonego wiersza, typu, pliku, elementu członkowskiego lub symbolu.

- **Przejdź do pliku** **(Ctrl**+**1**, **Ctrl**+**F):** Przejdź do określonego pliku w rozwiązaniu.

- **Przejdź do ostatniego pliku** (**Ctrl**+**1**, **Ctrl**+**R):** Przejdź do określonego, ostatnio odsłanianego pliku w rozwiązaniu.

- **Przejdź do typu** **(Ctrl**+**1**, **Ctrl**+**T):** Przejdź do określonego typu w roztworze.

- **Przejdź do elementu członkowskiego** (**Ctrl**+**1**, **Ctrl**+**M):** Przejdź do określonego elementu członkowskiego w rozwiązaniu.

- **Przejdź do symbolu** **(Ctrl**+**1**, **Ctrl**+**S):** Przejdź do określonego symbolu w roztworze.

W programie Visual Studio 2017 w wersji 15.8 i nowszych dostępne są również następujące polecenia nawigacji **Przejdź do:**

- **Przejdź do następnego problemu w pliku** **(Alt**+**PgDn)** i **przejdź do poprzedniego wydania w pliku** **(Alt**+**PgUp**)

- **Przejdź do lokalizacji ostatniej edycji** **(Ctrl**+**Shift**+**Backspace)**

Więcej informacji na temat tych poleceń można znaleźć w temacie [Znajdź kod przy użyciu poleceń Przejdź do.](../ide/go-to.md)

## <a name="go-to-definition"></a>Przejdź do definicji

Przejdź do definicji prowadzi do definicji wybranego elementu. Aby uzyskać więcej informacji, zobacz [Przejdź do definicji i Zajrzeć do definicji](../ide/go-to-and-peek-definition.md).

Dane wejściowe | Funkcja
------------ | ---
**Klawiatura** | Umieść kursor tekstu w miejscu nazwy typu i naciśnij klawisz **F12**
**Mysz** | Kliknij prawym przyciskiem myszy nazwę typu i wybierz pozycję **Przejdź do definicji** lub naciśnij **klawisz Ctrl** i kliknij nazwę typu

## <a name="peek-definition"></a>Podejrzyj definicję

Definicja wglądu wyświetla definicję wybranego elementu w oknie bez nawigowania z dala od bieżącej lokalizacji w edytorze kodu. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie i edytowanie kodu przy użyciu funkcji Peek Definition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) i [Go To Definition and Peek Definition](../ide/go-to-and-peek-definition.md).

Dane wejściowe | Funkcja
------------ | ---
**Klawiatura** | Umieść kursor tekstu w środku nazwy typu i naciśnij klawisz **Alt**+**F12**
**Mysz** | Kliknij prawym przyciskiem myszy nazwę typu i wybierz **opcję Zerknij definicję** lub naciśnij **klawisz Ctrl** i kliknij nazwę typu (jeśli zaznaczono opcję **Otwórz definicję w widoku wglądu)**

## <a name="go-to-implementation"></a>Przejdź do implementacji

Za pomocą Przejdź do implementacji, można przejść z klasy podstawowej lub typu do jego implementacji. Jeśli istnieje wiele implementacji, zostaną wyświetlone w oknie **Znajdź wyniki symboli:**

Dane wejściowe | Funkcja
------------ | ---
**Klawiatura** | Umieść kursor tekstu w miejscu wewnątrz nazwy typu i naciśnij klawisz **Ctrl**+**F12**
**Mysz** | Kliknij prawym przyciskiem myszy nazwę typu i wybierz **pozycję Przejdź do implementacji**

## <a name="go-to-base"></a>Polecenie Go To Base (Przejdź do podstawy)

Za pomocą Przejdź do bazy, można poruszać się w górę łańcucha dziedziczenia wybranego elementu. Jeśli istnieje wiele wyników, zostaną wyświetlone w oknie **Przejdź do bazy:**

Dane wejściowe | Funkcja
------------ | ---
**Klawiatura** | Umieść kursor tekstu w miejscu nazwy typu i naciśnij klawisz **Alt**+**Home**
**Mysz** | Kliknij prawym przyciskiem myszy nazwę typu i wybierz **pozycję Przejdź do bazy**

## <a name="call-hierarchy"></a>Hierarchia wywołań

Można wyświetlić wywołania do i z metody w [oknie Hierarchia połączeń:](../ide/reference/call-hierarchy.md)

Dane wejściowe | Funkcja
------------ | ---
**Klawiatura** | Umieść kursor tekstu w miejscu wewnątrz nazwy typu i naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**T**
**Mysz** | Kliknij prawym przyciskiem myszy nazwę elementu członkowskiego i wybierz pozycję **Wyświetl hierarchię połączeń**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Polecenia Następna metoda i Poprzednia metoda (Visual Basic)

W plikach kodu języka Visual Basic użyj tych poleceń, aby przenieść punkt wstawiania do różnych metod. Wybierz **pozycję Edytuj** > **następną metodę** lub **Edytuj** > **poprzednią metodę**.

## <a name="structure-visualizer"></a>Wizualizator struktury

Funkcja Wizualizator struktury w edytorze kodu pokazuje *linie prowadzące strukturę* — pionowe linie przerywane, które wskazują pasujące nawiasy klamrowe w bazie kodu. Ułatwia to zobaczenie, gdzie zaczynają się i kończą bloki logiczne.

![Wizualizator struktury](../ide/media/vside_structure_visualizer.png)

Aby wyłączyć linie pomocnicze struktury, przejdź do**edytora** > tekstu**Opcje** >  **narzędzi** > **i** wyczyść pole Pokaż linie linii **linii pomocniczych struktury.**

## <a name="enhanced-scroll-bar"></a>Ulepszony pasek przewijania

Możesz użyć rozszerzonego paska przewijania w oknie kodu, aby uzyskać widok kodu z lotu ptaka. W trybie mapy można wyświetlić podglądy kodu po przesunięciu kursora w górę i w dół paska przewijania. Aby uzyskać więcej informacji, zobacz [Jak: Śledzenie kodu, dostosowując pasek przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informacje o kodzie KodLens

Informacje na temat określonego kodu, takie jak zmiany i kto dokonał tych zmian, odwołania, błędy, elementy robocze, przeglądy kodu i stan testu jednostkowego podczas korzystania z funkcji CodeLens w edytorze kodu. CodeLens działa jak wyświetlacz heads-up podczas korzystania z programu Visual Studio Enterprise z team foundation server. Zobacz [Znajdowanie zmian kodu i innych historii](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Wyświetlanie hierarchii połączeń](../ide/reference/call-hierarchy.md)
