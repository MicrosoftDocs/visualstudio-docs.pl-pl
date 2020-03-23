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
ms.openlocfilehash: 781c9a6bc30f7d3a29bcb89e743600e6b29e6445
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585759"
---
# <a name="outlining"></a>Tworzenie konspektu

Można ukryć niektóre kod z widoku, zwijając obszar kodu, tak**+** aby pojawiał się pod znakiem plus ( ). Rozwijać zwinięty region, klikając znak plus. Jeśli jesteś użytkownikiem klawiatury, możesz wybrać **opcję Ctrl**+**M**+**M,** aby zwinąć i rozwinąć. Można również zwinąć region konspektu, klikając dwukrotnie dowolny wiersz w regionie na marginesie konspektu, który pojawia się po lewej stronie kodu. Zawartość zwiniętego regionu można wyświetlić jako etykietkę narzędzia po umieszczeniu wskaźnika myszy na zwiniętym regionie.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Edytor źródła (Visual Studio dla komputerów Mac).](/visualstudio/mac/source-editor)

Regiony na marginesie obliczania są również podświetlane po umieszczeniu wskaźnika myszy nad marginesem. Domyślny kolor podświetlania może wydawać się dość słaby w niektórych konfiguracjach kolorów. Można go zmienić w**opcjach** >  **narzędzi** > **Czcionki środowiska** > **i Kolory** > **zwijanego regionu**.

Podczas pracy w zarysie kodu, można rozwinąć sekcje, które chcesz pracować, zwinąć je po zakończeniu, a następnie przenieść do innych sekcji. Jeśli nie chcesz, aby wyświetlić konspekt, można użyć **polecenia Zatrzymaj konspekt,** aby usunąć informacje o konspekcie bez zakłócania kodu źródłowego.

Polecenia **Cofnij** i **Ponawiaj** w menu **Edycja** mają wpływ na te akcje. Operacje **kopiowania,** **wycinania,** wklejania i upuszczania zachowują informacje **przedstawiające,** ale nie stan zwijanego regionu. Na przykład podczas kopiowania regionu, który jest zwinięty, operacja **Wklej** wkleja skopiowany tekst jako rozwinięty region.

> [!CAUTION]
> Po zmianie regionu zarysowany, konspekt może zostać utracone. Na przykład usunięcia lub Znajdź i zamień operacje można wymazać koniec regionu.

Poniższe polecenia można znaleźć w podmenu **Edytuj** > **konspekt.**

|||
|-|-|
|Ukryj zaznaczenie|(**Ctrl**+**M**, **Ctrl**+**H**) - Zwija wybrany blok kodu, który normalnie nie byłby dostępny do konspektowania, na przykład `if` blok. Aby usunąć region niestandardowy, użyj **funkcji Zatrzymaj ukrywanie prądu** (lub **Ctrl**+**M**, **Ctrl**+**U**). Niedostępne w języku Visual Basic.|
|Przełączanie rozszerzania zwymiotowania|- Odwraca bieżący ukryty lub rozwinięty stan najbardziej wewnętrznej sekcji nakreślenia, gdy kursor znajduje się w zagnieżdżonej zwiniętej sekcji.|
|Przełączanie wszystkich kreślenia|(**Ctrl**+**M**, **Ctrl**+**L**) - Ustawia wszystkie regiony w tym samym stanie zwiniętego lub rozwiniętego. Jeśli niektóre regiony są rozwinięte, a niektóre zwinięte, zwinięte regiony zostaną rozwinięte.|
|Zatrzymaj tworzenie nakreślenia|(**Ctrl**+**M**, **Ctrl**+**P**) - Usuwa wszystkie informacje przedstawiające cały dokument.|
|Zatrzymaj ukrywanie prądu|(**Ctrl**+**M**, **Ctrl**+**U**) - Usuwa informacje o nakreśleniu dla aktualnie wybranego regionu zdefiniowanego przez użytkownika. Niedostępne w języku Visual Basic.|
|Zwiń do definicji|(**Ctrl**+**M**, **Ctrl**+**O**) - Zwija członków wszystkich typów.|
|Zwiń\<blok: logiczna> graniczna|(C++) Zwija region w funkcji zawierającej punkt wstawiania. Na przykład jeśli punkt wstawiania znajduje się wewnątrz pętli, pętla jest ukryta.|
|Zwiń \<wszystko w: struktury logiczne>|(C++) Zwija wszystkie struktury wewnątrz funkcji.|

Można również użyć visual studio SDK do definiowania regionów tekstu, które chcesz rozwinąć lub zwinąć. Zobacz [Przewodnik: Tworzenie nakreślenia](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Edytor źródłowy (Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor)
