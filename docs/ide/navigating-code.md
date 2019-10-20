---
title: Polecenia nawigacji kodu
ms.date: 08/14/2018
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1fcfd69e2de9a174c708da1c4f5eaedd397722e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667014"
---
# <a name="navigate-code"></a>Nawiguj po kodzie

Program Visual Studio zapewnia wiele sposobów nawigowania po kodzie w edytorze. Ten temat zawiera podsumowanie różnych sposobów nawigowania po kodzie i zawiera linki do tematów, które zawierają bardziej szczegółowe informacje.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Przejdź wstecz i Nawiguj do przodu poleceń

Możesz użyć przycisku **Nawiguj wstecz** (**Ctrl** + **-** ) i **przejdź do przodu** (**Ctrl** +**SHIFT** + **1**) na pasku narzędzi, aby przenieść punkt wstawiania do poprzedniego lokalizacje lub aby powrócić do nowszej lokalizacji z poprzedniej lokalizacji. Przyciski te zachowują ostatnie 20 lokalizacji punktu wstawiania. Te polecenia są również dostępne w menu **Widok** , w obszarze **Nawigacja wstecz** i **Przejdź do przodu**.

![Przyciski nawigacji do przodu i do tyłu](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Pasek nawigacyjny

Możesz użyć **paska nawigacyjnego** (pola rozwijane w górnej części okna kod), aby przejść do kodu w kodzie bazowym. Możesz wybrać typ lub element członkowski, aby przejść bezpośrednio do niego. Pasek nawigacyjny pojawia się, gdy edytujesz kod w Visual Basic C#lub C++ w bazie kodu. W klasie częściowej, elementy członkowskie zdefiniowane poza bieżącym plikiem kodu mogą być wyłączone (są wyświetlane w kolorze szarym).

![Pasek nawigacyjny kodu](../ide/media/vside_navigation_bar.png)

Możesz nawigować wokół pól rozwijanych w następujący sposób:

- Aby przejść do innego projektu, do którego należy bieżący plik, wybierz go na liście rozwijanej po lewej stronie.

- Aby przejść do klasy lub typu, wybierz ją z listy rozwijanej Środkowo.

- Aby przejść bezpośrednio do procedury lub innego elementu członkowskiego klasy, wybierz ją z listy rozwijanej po prawej stronie.

- Aby przenieść fokus z okna kod na pasek nawigacyjny, naciśnij kombinację klawiszy skrótu **Ctrl** +**F2**.

- Aby przenieść fokus z pola do pola na pasku nawigacyjnym, naciśnij klawisz **Tab** .

- Aby wybrać element paska nawigacyjnego, który ma fokus i powrócić do okna kod, naciśnij klawisz **Enter** .

- Aby zwrócić fokus z paska nawigacyjnego do kodu bez zaznaczania niczego, naciśnij klawisz **ESC** .

Aby ukryć pasek nawigacyjny, należy zmienić **opcję Pasek nawigacyjny** w **ustawieniach Edytor tekstu wszystkie języki** (**Narzędzia**  > **Opcje**  > **edytorze tekstów**  > **wszystkie języki**) lub można zmienić ustawienia dla poszczególnych języków.

## <a name="find-all-references"></a>Znajdź wszystkie odwołania

Znajduje wszystkie odwołania do wybranego elementu w rozwiązaniu. Można go użyć do sprawdzenia możliwych efektów ubocznych dużego refaktoryzacji lub do zweryfikowania "martwego" kodu. Naciśnij klawisz **F8** , aby przeskoczyć między wynikami. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).

Dane wejściowe | Funkcja
------------ | ---
**Klawiatury** | Umieść kursor tekstowy w miejscu wewnątrz nazwy typu, a następnie naciśnij klawisz **Shift** +**F12**
**Wskaźnik** | Wybierz pozycję **Znajdź wszystkie odwołania z menu dostępnego** po kliknięciu prawym przyciskiem myszy

## <a name="reference-highlighting"></a>Wyróżnianie odwołań

Gdy klikniesz symbol w kodzie źródłowym, wszystkie wystąpienia tego symbolu zostaną wyróżnione w dokumencie. Wyróżnione symbole mogą zawierać deklaracje i odwołania, a wiele innych symboli, które będą zwracać **wszystkie odwołania** . Obejmują one nazwy klas, obiektów, zmiennych, metod i właściwości. W kodzie Visual Basic są również wyróżnione słowa kluczowe dla wielu struktur kontroli. Aby przejść do następnego lub poprzedniego wyróżnionego symbolu, naciśnij klawisz **Ctrl** +**SHIFT** +**strzałkę w dół** lub **Ctrl** +**SHIFT** +**strzałkę w górę**. Kolor podświetlania można zmienić w obszarze **narzędzia**  > **opcje**  > **środowisku**  > **czcionki i kolory**  > **wyróżnione odwołanie**.

## <a name="go-to-commands"></a>Przejdź do poleceń

Polecenie Przejdź do zawiera następujące polecenia, które są dostępne w menu **Edytuj** w sekcji **Przejdź do**:

- **Przejdź do wiersza** (**Ctrl** +**G**): przenosi do określonego numeru wiersza w aktywnym dokumencie.

- **Przejdź do wszystkich** (**Ctrl** +**t** lub **Ctrl** + **,** ): Przenieś do określonego wiersza, typu, pliku, elementu członkowskiego lub symbolu.

- **Przejdź do pliku** (**Ctrl** +**1**, **Ctrl** +**F**): Przenieś do określonego pliku w rozwiązaniu.

- **Przejdź do ostatniego pliku** (**Ctrl** +**1**, **Ctrl** +**R**): Przejdź do określonego, ostatnio odwiedzonego pliku w rozwiązaniu.

- **Przejdź do typu** (**Ctrl** +**1**, **Ctrl** +**t**): Przenieś do określonego typu w rozwiązaniu.

- **Przejdź do elementu członkowskiego** (**Ctrl** +**1**, **Ctrl** +**M**): Przenieś do określonego elementu członkowskiego w rozwiązaniu.

- **Przejdź do symbolu** (**Ctrl** +**1**, **Ctrl** +**S**): Przenieś do określonego symbolu w rozwiązaniu.

W programie Visual Studio 2017 w wersji 15,8 i nowszych dostępne są również następujące **polecenia nawigacyjne** :

- **Przejdź do następnego problemu w pliku** (**Alt** +**PgDn**) i **Przejdź do poprzedniego problemu w pliku** (**Alt** +**PgUp**)

- **Przejdź do ostatniej edycji lokalizacji** (**Ctrl** +**SHIFT** +**Backspace**)

Więcej informacji na temat tych poleceń można znaleźć w temacie [Find Code using go to Commands](../ide/go-to.md) .

## <a name="go-to-definition"></a>Przejdź do definicji

Przejdź do definicji przeprowadzi Cię do definicji wybranego elementu. Aby uzyskać więcej informacji, zobacz [Przejdź do definicji i wglądu definicji](../ide/go-to-and-peek-definition.md).

Dane wejściowe | Funkcja
------------ | ---
**Klawiatury** | Umieść kursor tekstowy w miejscu wewnątrz nazwy typu, a następnie naciśnij klawisz **F12**
**Wskaźnik** | Kliknij prawym przyciskiem myszy nazwę typu i wybierz pozycję **Przejdź do definicji** lub naciśnij klawisz **Ctrl** i kliknij nazwę typu

## <a name="peek-definition"></a>Definicja wglądu

Funkcja wglądu definicja wyświetla definicję wybranego elementu w oknie bez nawigowania do bieżącej lokalizacji w edytorze kodu. Aby uzyskać więcej informacji, zobacz [How to: wyświetlanie i edytowanie kodu za pomocą definicji wglądu](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) i [Przejdź do definicji i wglądu do definicji](../ide/go-to-and-peek-definition.md).

Dane wejściowe | Funkcja
------------ | ---
**Klawiatury** | Umieść kursor tekstowy w miejscu wewnątrz nazwy typu, a następnie naciśnij klawisz **Alt** +**F12**
**Wskaźnik** | Kliknij prawym przyciskiem myszy nazwę typu i wybierz opcję **wgląd do definicji** lub naciśnij klawisz **Ctrl** i kliknij nazwę typu (Jeśli zaznaczono opcję **Otwórz definicję w widoku wglądu** )

## <a name="go-to-implementation"></a>Przejdź do implementacji

Korzystając z funkcji przejdź do implementacji, można nawigować z klasy bazowej lub typu do ich implementacji. Jeśli istnieje wiele implementacji, zostaną one wyświetlone w oknie **Wyszukiwanie wyników symboli** :

Dane wejściowe | Funkcja
------------ | ---
**Klawiatury** | Umieść kursor tekstowy w miejscu wewnątrz nazwy typu, a następnie naciśnij klawisz **Ctrl** +**F12**
**Wskaźnik** | Kliknij prawym przyciskiem myszy nazwę typu i wybierz pozycję **Przejdź do implementacji**

## <a name="call-hierarchy"></a>Hierarchia wywołań

Można wyświetlić wywołania do i z metody w [oknie hierarchia wywołań](../ide/reference/call-hierarchy.md):

Dane wejściowe | Funkcja
------------ | ---
**Klawiatury** | Umieść kursor tekstowy w miejscu wewnątrz nazwy typu, a następnie naciśnij **klawisze ctrl** +**K**, **Ctrl** +**t**
**Wskaźnik** | Kliknij prawym przyciskiem myszy nazwę elementu członkowskiego i wybierz pozycję **Wyświetl hierarchię wywołań**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Polecenia Next i Previous metody (Visual Basic)

W Visual Basic pliki kodu Użyj tych poleceń, aby przenieść punkt wstawiania do różnych metod. Wybierz pozycję **edytuj**  > **Następna metoda** lub **Edytuj**  > **poprzednią metodę**.

## <a name="structure-visualizer"></a>Wizualizator struktury

Funkcja wizualizator struktury w edytorze kodu pokazuje *linie prowadnic struktury* — pionowe linie kreskowane wskazujące pasujące nawiasy klamrowe w bazie kodu. Ułatwia to sprawdzenie, gdzie bloki logiczne zaczynają się i kończą.

![Wizualizator struktury](../ide/media/vside_structure_visualizer.png)

Aby wyłączyć linie prowadnic struktury, przejdź do pozycji **narzędzia**  > **Opcje**  > **Edytor tekstów**  > **Ogólne** i wyczyść pole wyboru **Pokaż linie prowadnicy struktury** .

## <a name="enhanced-scroll-bar"></a>Udoskonalony pasek przewijania

Możesz użyć rozszerzonego paska przewijania w oknie kodu, aby uzyskać wgląd w swój kod w oczy. W trybie mapy można zobaczyć podgląd kodu po przesunięciu kursora w górę i w dół paska przewijania. Aby uzyskać więcej informacji, zobacz [jak: śledzić kod przez dostosowanie paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informacje CodeLens

W edytorze kodu można znaleźć informacje o konkretnym kodzie, takie jak zmiany i osoby, które wprowadziły te zmiany, odwołania, błędy, elementy robocze, przeglądy kodu i stan testu jednostkowego. CodeLens działa jak w przypadku wyświetlania głowic w przypadku używania Visual Studio Enterprise z Team Foundation Server. Zobacz [Znajdowanie zmian w kodzie i innych historii](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Wyświetl hierarchię wywołań](../ide/reference/call-hierarchy.md)
