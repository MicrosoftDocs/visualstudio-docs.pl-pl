---
title: Tworzenie konspektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 907d075f597799edd582c9f2bae693eac92c0b2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544966"
---
# <a name="outlining"></a>Tworzenie konspektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można ukryć jakiś kod z widoku, zwijając region kodu, tak aby pojawił się pod znakiem plus (+). Aby rozwinąć zwinięty region, kliknij znak plus. (Lub naciśnij klawisze CTRL + M + M, aby zwinąć region, a następnie CTRL + M + M, aby rozwinąć go ponownie). Możesz również zwinąć region konspektu, klikając dwukrotnie dowolny wiersz w regionie na marginesie tworzenia konspektu, który pojawia się po lewej stronie kodu. Zawartość zwiniętego regionu można zobaczyć po umieszczeniu wskaźnika myszy na zwiniętym regionie.

 Regiony na marginesie tworzenia konspektu są również podświetlane po umieszczeniu wskaźnika myszy na marginesie przy użyciu myszki. Domyślny kolor wyróżnienia może wydawać się raczej słaby w niektórych konfiguracjach kolorów. Można ją zmienić w obszarze **Narzędzia/Opcje/środowisko/czcionki i kolory/zwijany region**.

 Gdy Pracujesz w kodzie konspektu, możesz rozwinąć sekcje, nad którymi chcesz pracować, zwinąć je po zakończeniu, a następnie przejść do innych sekcji. Jeśli nie chcesz wyświetlać konspektów, możesz użyć polecenia **Zatrzymaj tworzenie** konspektu, aby usunąć informacje o konspekcie bez zakłócania kodu źródłowego.

 Polecenia **Cofnij** i **Wykonaj ponownie** w menu **Edycja** mają wpływ na te akcje. Operacje **kopiowania**, **wycinania**, **wklejania**oraz przeciągania i upuszczania zachowują informacje z konspektu, ale nie stan regionu zwijanego. Na przykład podczas kopiowania regionu, który jest zwinięty, operacja **wklejania** spowoduje wklejenie skopiowanego tekstu jako rozwiniętego regionu.

> [!CAUTION]
> Po zmianie regionu obramowania może dojść do utraty konspektu. Na przykład operacje usuwania lub znajdowania i zamieniania mogą wymazać koniec regionu.

 Poniższe polecenia można znaleźć w podmenu **Edytuj/konspekt** .

|Polecenie|Opis|
|-|-|
|Ukryj zaznaczenie|(CTRL + M, CTRL + H) — zwija wybrany blok kodu, który zwykle nie jest dostępny do tworzenia konspektu, na przykład `if` blok. Aby usunąć region niestandardowy, użyj **Zatrzymaj ukrywanie bieżącego** (lub Ctrl + M, Ctrl + U). Niedostępne w Visual Basic.|
|Przełącz rozszerzanie konspektu|-Odwraca bieżący ukryty lub rozwinięty stan wewnętrznej sekcji tworzenia konspektu, gdy kursor znajduje się w zagnieżdżonej zwijanej sekcji.|
|Przełącz wszystkie konspekty|(CTRL + M, CTRL + L) — ustawia wszystkie regiony na ten sam stan zwinięte lub rozwinięte. Jeśli niektóre regiony są rozwinięte i zwinięte, zwijane regiony są rozwinięte.|
|Zatrzymaj tworzenie konspektu|(CTRL + M, CTRL + P) — usuwa wszystkie informacje dotyczące tworzenia konspektu dla całego dokumentu.|
|Przestań ukrywać bieżące|(CTRL + M, CTRL + U) — usuwa informacje z tworzenia konspektu dla aktualnie wybranego regionu zdefiniowanego przez użytkownika. Niedostępne w Visual Basic.|
|Zwiń do definicji|(CTRL + M, CTRL + O) — zwija elementy członkowskie wszystkich typów.|
|Zwiń blok:\<logical boundary>|(Visual C++) Zwija region w funkcji zawierającej punkt wstawiania. Na przykład, jeśli punkt wstawiania leży wewnątrz pętli, pętla jest ukryta.|
|Zwiń wszystko w: \<logical structures>|(Visual C++) Zwija wszystkie struktury wewnątrz funkcji.|

 Możesz również użyć zestawu Visual Studio SDK, aby zdefiniować regiony tekstu, które mają zostać rozwinięte lub zwinięte. Zobacz [Przewodnik: Tworzenie konspektu](../extensibility/walkthrough-outlining.md).
