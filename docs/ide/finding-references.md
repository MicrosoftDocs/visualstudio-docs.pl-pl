---
title: Znajdowanie odwołań w kodzie
description: Dowiedz się więcej o poleceniu Znajdź wszystkie odwołania, aby znaleźć odwołania do określonych elementów kodu w kodzie.
ms.custom: SEO-VS-2020
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cc7702ae07c83c5798945c4a9bb2ab787fc9cd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945568"
---
# <a name="find-references-in-your-code"></a>Znajdowanie odwołań w kodzie

Możesz użyć polecenia **Znajdź wszystkie odwołania** , aby znaleźć, gdzie poszczególne elementy kodu są przywoływane w bazie kodu. Polecenie **Znajdź wszystkie odwołania** jest dostępne w menu kontekstowym (kliknij prawym przyciskiem myszy) elementu, do którego chcesz znaleźć odwołania. Lub, jeśli jesteś użytkownikiem klawiatury, naciśnij klawisze **Shift + F12**.

Wyniki pojawiają się w oknie narzędzia o nazwie **\<element> References**, gdzie *element* to nazwa wyszukiwanego elementu. Pasek narzędzi w oknie **odwołania** umożliwia:
- Zmień zakres wyszukiwania w polu listy rozwijanej. Możesz wyszukać tylko zmienione dokumenty, tak samo jak w całym rozwiązaniu.
- Skopiuj wybrany element, do którego istnieje odwołanie, wybierając przycisk **Kopiuj** .
- Wybierz przyciski, aby przejść do następnej lub poprzedniej lokalizacji na liście, lub naciśnij klawisze **F8** i **Shift + F8** , aby to zrobić.
- Usuń wszystkie filtry dla zwracanych wyników, wybierając przycisk **Wyczyść wszystkie filtry** .
- Zmień sposób grupowania zwracanych elementów przez wybranie ustawienia w polu listy rozwijanej **Grupuj według:** .
- Zachowaj bieżące okno wyników wyszukiwania, wybierając przycisk **Zachowaj wyniki** . Po wybraniu tego przycisku bieżące wyniki wyszukiwania pozostają w tym oknie, a nowe wyniki wyszukiwania pojawiają się w nowym oknie narzędzi.
- Wyszukaj ciągi w wynikach wyszukiwania, wprowadzając tekst w polu tekstowym **wyszukiwania Znajdź wszystkie odwołania** .

Możesz również ustawić wskaźnik myszy nad dowolnym wynikiem wyszukiwania, aby zobaczyć podgląd odwołania.

![Okno narzędzia Znajdowanie wszystkich odwołań](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Przejdź do odwołań
Aby przejść do odwołań w oknie **odwołania** , można użyć następujących metod:

- Naciśnij klawisz **F8** , aby przejść do następnego odwołania, lub **klawisze Shift + F8** , aby przejść do poprzedniego odwołania.
- Naciśnij klawisz **Enter** , aby uzyskać odwołanie, lub kliknij go dwukrotnie, aby przejść do niego w kodzie.
- W menu rozwijanym prawym przyciskiem myszy (menu kontekstowe) odwołania wybierz polecenie **Przejdź do poprzedniej lokalizacji** lub **Przejdź do następnej lokalizacji** polecenia.
- Wybierz klawisze **Strzałka w górę** i **Strzałka w dół** (jeśli są włączone w oknie dialogowym **Opcje** ). Aby włączyć tę funkcję, na pasku menu wybierz kolejno   >  **Opcje** narzędzia  >    >  **karty środowiska i Podgląd systemu Windows**  >  , a następnie zaznacz pole wyboru **Zezwalaj na otwieranie nowych plików na karcie Podgląd** i **Wyświetl podgląd wybranych plików w polu Wyniki wyszukiwania** .

## <a name="change-reference-groupings"></a>Zmień grupowanie odwołań
Domyślnie odwołania są pogrupowane według projektu, a następnie według definicji. Można jednak zmienić tę kolejność grupowania, zmieniając ustawienie w polu listy rozwijanej **Grupuj według:** na pasku narzędzi. Można na przykład zmienić to ustawienie z domyślnego ustawienia **projekt, a następnie definicja** na projekt, **a** także inne ustawienia.

**Definicja** i **projekt** to dwie domyślne grupy, które są używane, ale możesz dodać inne, wybierając polecenie **grupowania** na prawym kliknięciu lub menu kontekstowym wybranego elementu. Dodanie większej liczby grup może być przydatne, jeśli rozwiązanie ma wiele plików i ścieżek.

## <a name="filter-by-reference-type-in-net"></a>Filtrowanie według typu odwołania w programie .NET
W języku C# lub Visual Basic okno Znajdowanie odwołań zawiera kolumnę rodzajową, w której znajduje się lista informacji o rodzaju znalezionych odwołań. Ta kolumna może służyć do filtrowania według typu referencyjnego, klikając ikonę filtru, która pojawia się po umieszczeniu wskaźnika myszy na nagłówku kolumny. Odwołania można filtrować według odczytu, zapisu, odwołania, nazwy, przestrzeni nazw i typu.

![Znajdowanie kolumny rodzaju okna odwołań ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Zobacz też

- [Nawigowanie po kodzie](../ide/navigating-code.md)
