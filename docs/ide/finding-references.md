---
title: Znajdowanie odwołań w kodzie
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4ef16ef88e871778fd4e0c755ffb156c374109
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592038"
---
# <a name="find-references-in-your-code"></a>Znajdowanie odwołań w kodzie

Można użyć **Znajdź wszystkie odwołania** polecenia, aby znaleźć, gdzie poszczególne elementy kodu są odwoływane w całej bazy kodu. Polecenie **Znajdź wszystkie odwołania** jest dostępne w menu kontekst (kliknij prawym przyciskiem myszy) elementu, do którego chcesz znaleźć odwołania. Lub, jeśli jesteś użytkownikiem klawiatury, naciśnij **klawisze Shift + F12**.

Wyniki są wyświetlane w ** \<** oknie narzędzia o nazwie element> odniesienia , gdzie *element* jest nazwą elementu, którego szukasz. Pasek narzędzi w oknie **odwołań** umożliwia:
- Zmień zakres wyszukiwania w polu listy rozwijanej. Możesz spojrzeć tylko w zmienionych dokumentach aż do całego rozwiązania.
- Skopiuj zaznaczony element, do którego istnieje odwołanie, wybierając przycisk **Kopiuj.**
- Wybierz przyciski, aby przejść do następnej lub poprzedniej lokalizacji na liście, lub naciśnij klawisze **F8** i **Shift + F8,** aby to zrobić.
- Usuń wszystkie filtry na zwróconych wynikach, wybierając przycisk **Wyczyść wszystkie filtry.**
- Zmień sposób grupowanie zwróconych elementów, wybierając ustawienie w polu listy rozwijanej **Grupa według:**
- Zachowaj bieżące okno wyników wyszukiwania, wybierając przycisk **Zachowaj wyniki.** Po wybraniu tego przycisku bieżące wyniki wyszukiwania pozostaną w tym oknie, a nowe wyniki wyszukiwania pojawią się w nowym oknie narzędzia.
- Wyszukaj ciągi w wynikach wyszukiwania, wprowadzając tekst w polu **tekstowym Wyszukaj wszystkie odwołania.**

Możesz również najechać kursorem myszy na dowolny wynik wyszukiwania, aby wyświetlić podgląd odwołania.

![Okno narzędzia Znajdź wszystkie odwołania](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Przejdź do odniesień
Aby przejść do odwołań w oknie **odwołań,** można użyć następujących metod:

- Naciśnij **klawisz F8,** aby przejść do następnego odwołania, lub **klawisze Shift + F8,** aby przejść do poprzedniego odwołania.
- Naciśnij klawisz **Enter** na odwołaniu lub kliknij go dwukrotnie, aby przejść do niego w kodzie.
- W menu po kliknięciu prawym przyciskiem myszy (menu kontekstowym) odwołania wybierz polecenie **Przejdź do poprzedniej lokalizacji** lub Przejdź do **następnej lokalizacji.**
- Wybierz **klawisze Strzałka w górę** i **Strzałka w dół** (jeśli są włączone w oknie dialogowym **Opcje).** Aby włączyć tę funkcję, na pasku menu wybierz pozycję Karty**środowiska** > **Opcje** >  **narzędzi** > i**Karta Podgląd****systemu Windows,** > a następnie wybierz pozycję **Zezwalaj na otwarcie nowych plików** na karcie Podgląd i Podgląd wybranych plików w polach Znajdź **wyniki.**

## <a name="change-reference-groupings"></a>Zmienianie grup odwołań
Domyślnie odwołania są pogrupowane według projektu, a następnie z definicji. Można jednak zmienić tę kolejność grupowania, zmieniając ustawienie w polu listy rozwijanej **Grupa według:** na pasku narzędzi. Na przykład można zmienić go z domyślnego ustawienia **programu Project, a następnie definicję** na **Definicję, a następnie projekt**, a także na inne ustawienia.

**Definicja** i **projekt** są dwoma domyślnymi grupami używanymi, ale można dodać inne, wybierając polecenie **Grupowanie** w menu prawym przyciskiem myszy lub w menu kontekstowym wybranego elementu. Dodanie większej liczby grup może być przydatne, jeśli rozwiązanie ma wiele plików i ścieżek.

## <a name="filter-by-reference-type-in-net"></a>Filtrowanie według typu odwołania w .NET
W języku C# lub Visual Basic okna Znajdź odwołania ma Kind kolumny, gdzie wyświetla listę, jaki typ odwołania znalazł. Ta kolumna może służyć do filtrowania według typu odwołania, klikając ikonę filtru, która pojawia się po umieszczeniu wskaźnika myszy nad nagłówkiem kolumny. Odwołania mogą być filtrowane według odczytu, zapisu, odwołania, nazwy, obszaru nazw i typu.

![Znajdź kolumny Rodzaj okna odwołań ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Zobacz też

- [Nawigowanie po kodzie](../ide/navigating-code.md)
