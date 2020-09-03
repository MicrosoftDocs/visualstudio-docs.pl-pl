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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07ad01726b57073cad3a5a2876a4b22667d3770a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545447"
---
# <a name="outlining"></a>Tworzenie konspektu

Można ukryć jakiś kod z widoku, zwijając region kodu, tak aby pojawił się pod znakiem plus ( **+** ). Aby rozwinąć zwinięty region, kliknij znak plus. Jeśli jesteś użytkownikiem z klawiatury, możesz wybrać opcję **Ctrl** + **m** + **m** , aby zwinąć i rozwinąć. Możesz również zwinąć region konspektu, klikając dwukrotnie dowolny wiersz w regionie na marginesie tworzenia konspektu, który pojawia się po lewej stronie kodu. Zawartość zwiniętego regionu można zobaczyć po umieszczeniu wskaźnika myszy na zwiniętym regionie.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz temat [Edytor źródła (Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor).

Regiony na marginesie tworzenia konspektu są również podświetlane po umieszczeniu wskaźnika myszy na marginesie przy użyciu myszki. Domyślny kolor wyróżnienia może wydawać się raczej słaby w niektórych konfiguracjach kolorów. Można ją zmienić w opcji **Narzędzia**  >  **Options**  >  **Environment**  >  **czcionki i kolory**środowiska  >  **zwijane**.

Gdy Pracujesz w kodzie konspektu, możesz rozwinąć sekcje, nad którymi chcesz pracować, zwinąć je po zakończeniu, a następnie przejść do innych sekcji. Jeśli nie chcesz wyświetlać konspektów, możesz użyć polecenia **Zatrzymaj tworzenie** konspektu, aby usunąć informacje o konspekcie bez zakłócania kodu źródłowego.

Polecenia **Cofnij** i **Wykonaj ponownie** w menu **Edycja** mają wpływ na te akcje. Operacje **kopiowania**, **wycinania**, **wklejania**oraz przeciągania i upuszczania zachowują informacje z konspektu, ale nie stan regionu zwijanego. Na przykład podczas kopiowania regionu, który jest zwinięty, operacja **wklejania** spowoduje wklejenie skopiowanego tekstu jako rozwiniętego regionu.

> [!CAUTION]
> Po zmianie regionu obramowania może dojść do utraty konspektu. Na przykład operacje usuwania lub znajdowania i zamieniania mogą wymazać koniec regionu.

Poniższe polecenia można znaleźć w podmenu **Edytuj**  >  **Konspekt** .

|Nazwa|Opis|
|-|-|
|Ukryj zaznaczenie|(**Ctrl** + **M**, **Ctrl** + **H**) — zwija wybrany blok kodu, który zwykle nie jest dostępny do tworzenia konspektu, na przykład `if` blok. Aby usunąć region niestandardowy, Użyj przycisk **Zatrzymaj ukrywanie bieżące** (lub **Ctrl** + **M**, **Ctrl** + **U**). Niedostępne w Visual Basic.|
|Przełącz rozszerzanie konspektu|-Odwraca bieżący ukryty lub rozwinięty stan wewnętrznej sekcji tworzenia konspektu, gdy kursor znajduje się w zagnieżdżonej zwijanej sekcji.|
|Przełącz wszystkie konspekty|(**Ctrl** + **M**, **Ctrl** + **L**) — ustawia wszystkie regiony na ten sam stan zwinięte lub rozwinięte. Jeśli niektóre regiony są rozwinięte i zwinięte, zwijane regiony są rozwinięte.|
|Zatrzymaj tworzenie konspektu|(**Ctrl** + **M**, **Ctrl** + **P**) — usuwa wszystkie informacje dotyczące tworzenia konspektu dla całego dokumentu.|
|Przestań ukrywać bieżące|(**Ctrl** + **M**, **Ctrl** + **U**) — usuwa informacje z konspektu dla aktualnie wybranego regionu zdefiniowanego przez użytkownika. Niedostępne w Visual Basic.|
|Zwiń do definicji|(**Ctrl** + **M**, **Ctrl** + **O**) — zwija elementy członkowskie wszystkich typów.|
|Zwiń blok:\<logical boundary>|Języków Zwija region w funkcji zawierającej punkt wstawiania. Na przykład, jeśli punkt wstawiania leży wewnątrz pętli, pętla jest ukryta.|
|Zwiń wszystko w: \<logical structures>|Języków Zwija wszystkie struktury wewnątrz funkcji.|

Możesz również użyć zestawu Visual Studio SDK, aby zdefiniować regiony tekstu, które mają zostać rozwinięte lub zwinięte. Zobacz [Przewodnik: Tworzenie konspektu](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Edytor źródła (Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor)
