---
title: Zwijanie i rozwijanie regionów kodu
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 791663c04d1c1e79eebaed39d339d8d118ffeaae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748864"
---
# <a name="outlining"></a>Tworzenie konspektu

Można ukryć jakiś kod z widoku, zwijając region kodu, tak aby pojawił się pod znakiem plusa ( **+** ). Aby rozwinąć zwinięty region, kliknij znak plus. Jeśli jesteś użytkownikiem z klawiatury, możesz wybrać pozycję **Ctrl** +**m** +**m** , aby zwinąć i rozwinąć. Możesz również zwinąć region konspektu, klikając dwukrotnie dowolny wiersz w regionie na marginesie tworzenia konspektu, który pojawia się po lewej stronie kodu. Zawartość zwiniętego regionu można zobaczyć po umieszczeniu wskaźnika myszy na zwiniętym regionie.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz temat [Edytor źródła (Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor).

Regiony na marginesie tworzenia konspektu są również podświetlane po umieszczeniu wskaźnika myszy na marginesie przy użyciu myszki. Domyślny kolor wyróżnienia może wydawać się raczej słaby w niektórych konfiguracjach kolorów. Można ją zmienić w obszarze **narzędzia**  > **opcje**  > **środowisku**  > **czcionki i kolory**  > **zwijany region**.

Gdy Pracujesz w kodzie konspektu, możesz rozwinąć sekcje, nad którymi chcesz pracować, zwinąć je po zakończeniu, a następnie przejść do innych sekcji. Jeśli nie chcesz wyświetlać konspektów, możesz użyć polecenia **Zatrzymaj tworzenie** konspektu, aby usunąć informacje o konspekcie bez zakłócania kodu źródłowego.

Polecenia **Cofnij** i **Wykonaj ponownie** w menu **Edycja** mają wpływ na te akcje. Operacje **kopiowania**, **wycinania**, **wklejania**oraz przeciągania i upuszczania zachowują informacje z konspektu, ale nie stan regionu zwijanego. Na przykład podczas kopiowania regionu, który jest zwinięty, operacja **wklejania** spowoduje wklejenie skopiowanego tekstu jako rozwiniętego regionu.

> [!CAUTION]
> Po zmianie regionu obramowania może dojść do utraty konspektu. Na przykład operacje usuwania lub znajdowania i zamieniania mogą wymazać koniec regionu.

Poniższe polecenia można znaleźć w podmenu **edytuj**  >  tworzenia**konspektu** .

|||
|-|-|
|Ukryj zaznaczenie|(**Ctrl** +**M**, **Ctrl** +**H**) — zwija wybrany blok kodu, który zwykle nie jest dostępny do tworzenia konspektu, na przykład blok `if`. Aby usunąć region niestandardowy, Użyj przycisk **Zatrzymaj ukrywanie bieżące** (lub **Ctrl** +**M**, **Ctrl** +**U**). Niedostępne w Visual Basic.|
|Przełącz rozszerzanie konspektu|-Odwraca bieżący ukryty lub rozwinięty stan wewnętrznej sekcji tworzenia konspektu, gdy kursor znajduje się w zagnieżdżonej zwijanej sekcji.|
|Przełącz wszystkie konspekty|(**Ctrl** +**M**, **Ctrl** +**L**) — ustawia wszystkie regiony do tego samego zwinięte lub rozwiniętego stanu. Jeśli niektóre regiony są rozwinięte i zwinięte, zwijane regiony są rozwinięte.|
|Zatrzymaj tworzenie konspektu|(**Ctrl** +**M**, **Ctrl** +**P**) — usuwa wszystkie informacje dotyczące tworzenia konspektu dla całego dokumentu.|
|Przestań ukrywać bieżące|(**Ctrl** +**M**, **Ctrl** +**U**) — usuwa informacje dotyczące tworzenia konspektu dla aktualnie wybranego regionu zdefiniowanego przez użytkownika. Niedostępne w Visual Basic.|
|Zwiń do definicji|(**Ctrl** +**M**, **Ctrl** +**O**) — zwija elementy członkowskie wszystkich typów.|
|Zwiń blok: \<logical granicy >|(C++) Zwija region w funkcji zawierającej punkt wstawiania. Na przykład, jeśli punkt wstawiania leży wewnątrz pętli, pętla jest ukryta.|
|Zwiń wszystko w: struktury \<logical >|(C++) Zwija wszystkie struktury wewnątrz funkcji.|

Możesz również użyć zestawu Visual Studio SDK, aby zdefiniować regiony tekstu, które mają zostać rozwinięte lub zwinięte. Zobacz [Przewodnik: Tworzenie konspektu](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Edytor źródła (Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor)