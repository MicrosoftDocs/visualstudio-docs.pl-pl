---
title: Zwijać i rozwijać regiony kodu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6451e835e44af23fbd41c9c1573e0bc5daed115
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952349"
---
# <a name="outlining"></a>Tworzenie konspektu

Możesz ukryć jakiś kod w widoku, zwijając obszar kodu, aby była ona wyświetlana w obszarze znak plus (**+**). Zwinięty region jest rozwiniesz, klikając znak plus. Jeśli jesteś użytkownikiem klawiatury, można wybrać **Ctrl**+**M**+**M** można zwijać i rozwijać. Można również zwinąć konspektu region przez dwukrotne kliknięcie każdego wiersza w regionie na marginesie konspektu, który jest wyświetlany z lewej strony kodu. Jako etykietka narzędzia można wyświetlić zawartość Zwinięty region, po najechaniu kursorem na zwinięty region.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [Edytor źródła (program Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor).

Regiony na marginesie konspektu są również wyróżnione po najechaniu kursorem na marginesie za pomocą myszy. Domyślny kolor wyróżnienia, może wydawać się zamiast Blade, w niektórych konfiguracjach kolorów. Można zmienić w **narzędzia** > **opcje** > **środowiska** > **czcionki i kolory**  >  **Region zwijany**.

Podczas pracy w kodzie schemat można rozszerzyć sekcje, które chcesz pracować nad, zwijając, gdy będzie gotowe, a następnie przenieść do innej sekcji. Jeśli chcesz, aby Tworzenie konspektu wyświetlane, można użyć **Zatrzymaj tworzenie konspektu** polecenie, aby usunąć informacje konspektu bez zakłócania działania kodu bazowego.

**Cofnij** i **wykonaj ponownie** polecenia na **Edytuj** menu mają wpływ na te akcje. **Kopiowania**, **Wytnij**, **Wklej**, i operacji przeciągania i upuszczania zachowywanie informacji konspektu, ale nie stan region zwijany. Na przykład podczas kopiowania region, który jest zwinięte, **Wklej** operacji będzie Wklej skopiowany tekst jako rozwinięty region.

> [!CAUTION]
> Po zmianie konturu region konspekt mogą zostać utracone. Na przykład usunięcia lub operacji Znajdź i Zamień może wymazać koniec regionu.

Następujące polecenia można znaleźć na **Edytuj** > **konspekt** podmenu.

|||
|-|-|
|Ukryj zaznaczenie|(**Ctrl**+**M**, **Ctrl**+**H**)-zwija wybranego bloku kodu, który zwykle nie jest dostępne dla konspektu, na przykład `if` bloku. Aby usunąć niestandardowy regionie, użyj **Zatrzymaj ukrywanie bieżącego** (lub **Ctrl**+**M**, **Ctrl** + **U**). Nie jest dostępna w języku Visual Basic.|
|Przełącz rozszerzanie konspektu|-Odwraca bieżący stan ukryte lub rozszerzona najbardziej wewnętrzną funkcją zwijanie sekcji, gdy kursor znajduje się w zagnieżdżonych zwiniętą sekcję.|
|Przełącz wszystkie konspekty|(**Ctrl**+**M**, **Ctrl**+**L**) — zestawy we wszystkich regionach do tej samej zwijania i rozwijania stanu. Jeśli niektóre regiony są rozszerzane, a niektóre zwinięte, następnie zwinięte regiony są rozwijane.|
|Przestań tworzyć konspekt|(**Ctrl**+**M**, **Ctrl**+**P**) — usuwa wszystkie informacje konspektu dla całego dokumentu.|
|Zatrzymaj ukrywanie bieżącego|(**Ctrl**+**M**, **Ctrl**+**U**)-usuwa konspektu informacje dotyczące aktualnie wybranego region zdefiniowany przez użytkownika. Nie jest dostępna w języku Visual Basic.|
|Zwiń do definicji|(**Ctrl**+**M**, **Ctrl**+**O**)-Zwija wszystkie typy elementów członkowskich.|
|Zwiń blok:\<logiczne granic >|(Visual C++) Zwija regionu w funkcji znajduje się punkt wstawiania. Na przykład jeśli punkt wstawiania znajduje się wewnątrz pętli, pętla jest ukryta.|
|Zwiń wszystkie w: \<logicznej struktury >|(Visual C++) Zwija wszystkie struktury wewnątrz funkcji.|

Aby zdefiniować regionów tekst, który chcesz rozwinąć lub zwinąć umożliwia także zestawu SDK programu Visual Studio. Zobacz [instruktażu: Konspekt](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Edytor źródła (program Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor)