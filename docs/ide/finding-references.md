---
title: Trwa znajdowanie odwołań w kodzie
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df3eb6577c72aa421f2a22d93b3109f63548cc96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793506"
---
# <a name="find-references-in-your-code"></a>Znajdowanie odwołań w kodzie

Możesz użyć **Znajdź wszystkie odwołania** polecenie, aby dowiedzieć się, gdzie elementy określonego kodu do których istnieją odwołania w całej bazie kodu. **Znajdź wszystkie odwołania** polecenie jest dostępne w menu kontekstowym (kliknij prawym przyciskiem myszy), które ma zostać odnaleziona odwołania do elementu. Lub, jeśli jesteś użytkownikiem klawiatury, naciśnij klawisz **Shift + F12**.

Wyniki są wyświetlane w oknie narzędzi o nazwie  **\<element > odwołania**, gdzie *elementu* jest nazwa elementu, którego szukasz. Pasek narzędzi w **odwołania** okno umożliwia:
- Zmień zakres wyszukiwania w polu listy rozwijanej. Można szukać tylko zmienione dokumenty do całego rozwiązania.
- Kopiuj wybrany element odwołania, wybierając **kopiowania** przycisku.
- Wybierz przyciski, aby przejść do następnej lub poprzedniej lokalizacji na liście lub naciśnij **F8** i **Shift + F8** kluczy, aby to zrobić.
- Usuń wszystkie filtry na zwróconych wynikach, wybierając **wyczyść wszystkie filtry** przycisku.
- Zmień sposób zwrócone elementy są grupowane, wybierając ustawienia w **Grupuj według:** pole listy rozwijanej.
- Zachowaj bieżące okno wyników wyszukiwania, wybierając **Zachowaj wyniki** przycisku. Po wybraniu tego przycisku, pozostają aktualne wyniki wyszukiwania, w tym oknie, a nowe wyniki wyszukiwania są wyświetlane w nowym oknie narzędzia.
- Wyszukaj ciąg w wynikach wyszukiwania, wprowadzając tekst w **wyszukiwania Znajdź wszystkie odwołania** pola tekstowego.

Możesz również umieścić kursor myszy dowolny wynik wyszukiwania, aby wyświetlić podgląd odwołania.

![Znajdź wszystkie odwołania do okna narzędzi](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Przejdź do odwołania
Można użyć następujących metod można przejść do odwołań w **odwołania** okna:

- Naciśnij klawisz **F8** można przejść do następnego odwołanie, lub **Shift + F8** można przejść do poprzedniej odwołania.
- Naciśnij klawisz **Enter** klucz odwołanie lub kliknij dwukrotnie, aby przejść do niego w kodzie.
- W menu kliknij prawym przyciskiem myszy (menu kontekstowe) odwołanie, wybierz **przejdź do poprzedniej lokalizacji** lub **przejdź do następnej lokalizacji** poleceń.
- Wybierz **Strzałka w górę** i **strzałkę w dół** kluczy (jeśli są one włączone w **opcje** okno dialogowe). Aby włączyć tę funkcję, na pasku menu wybierz **narzędzia** > **opcje** > **środowiska**  >   **Karty i Windows** > **karcie podglądu**, a następnie wybierz pozycję **Zezwalaj na nowe pliki były otwierane w karcie podglądu** i **Podgląd zaznaczonych plików w Znajdź wyniki** pola.

## <a name="change-reference-groupings"></a>Zmień odwołania grupowania
Domyślnie odwołania są pogrupowane według projektu, następnie zgodnie z definicją. Jednak ta kolejność grupowania można zmienić, zmieniając ustawienie w **Grupuj według:** pole listy rozwijanej na pasku narzędzi. Na przykład można zmienić go z ustawieniem domyślnym **projekt, a następnie definicja** do **definicja, a następnie projekt**, jak również do innych ustawień.

**Definicja** i **projektu** są używane dwie domyślne grupowania, ale możesz dodać inne, wybierając **grupowanie** polecenia menu kliknij prawym przyciskiem myszy lub kontekst wybranego elementu. Dodawanie więcej grupowań mogą być przydatne, jeśli rozwiązanie ma wiele plików i ścieżek.

## <a name="filter-by-reference-type-in-net"></a>Filtruj według typu odwołania na platformie .NET
W C# lub Visual Basic okno Znajdź odwołania zawiera rodzaj kolumny, których wymieniono znaleziono typ odwołania. Ta kolumna może służyć do filtrowania według typu odwołania, klikając ikonę filtru, który pojawia się po najechaniu kursorem na nagłówek kolumny. Odwołania można filtrować według odczytu, zapisu, odwołania i NameOnly.

![Znajdź rodzaj okna odwołania do kolumny ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Zobacz także

- [Nawigowanie po kodzie](../ide/navigating-code.md)
