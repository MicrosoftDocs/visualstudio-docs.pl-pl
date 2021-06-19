---
title: Praca z diagramem definicji DSL
description: Dowiedz się, że diagram definicji narzędzi DSL jest ważnym narzędziem do definiowania języka specyficznego dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f401fe0509fc425fff873a7dc224c69359156861
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388077"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Praca z diagramem definicji DSL
Diagram definicji jest ważnym narzędziem do definiowania języka [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] specyficznego dla domeny. Możesz dodawać elementy do modelu domeny i definiować relacje na diagramie, a także modyfikować układ diagramu, aby był bardziej czytelny.

## <a name="the-layout-of-the-diagram"></a>Układ diagramu
 Diagram [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definicji ma dwie partycje: **partycję Klasy i relacje** oraz **partycję Elementy diagramu.** Partycja **Klasy i relacje** wyświetla klasy domeny, relacje domeny i dziedziczenie. Partycja **Elementy diagramu** wyświetla klasy kształtów, klasy łączników, klasy torów i wygenerowany diagram projektanta.

 Klasy domen mogą być wyświetlane w wielu lokalizacjach w **partycjach Klasy i** relacje. Definicja klasy domeny wyświetla drzewo dziedziczenia, jeśli jest klasą bazową dla innych klas domeny, oraz drzewo relacji, jeśli jest źródłem osadzania lub odwoływać się do relacji. Symbole zastępcze klasy domeny są wyświetlane jako elementy docelowe osadzania lub odwoływać się do relacji. Domyślnie elementy zastępcze są wyświetlane ze zwiniętym **przedziałem Właściwości** domeny. Nie pokazują dziedziczenia, osadzania ani odwoływać się do relacji.

 Po dodaniu klasy domeny pojawia się ona w dolnej części partycji **Klasy i** relacje. Po dodaniu relacji osadzania lub odwołania jest ona rysowana w obszarze i po prawej stronie klasy domeny źródłowej.

 W przypadku dodawania klas domeny i relacji znalezienie określonej klasy domeny może okazać się trudne. Klasę domeny można znaleźć, klikając ją prawym przyciskiem myszy w Eksploratorze **DSL,** a następnie klikając polecenie **Zlokalizuj w diagramie**.

 W poniższych sekcjach opisano, jak można zmienić wygląd diagramu, aby ułatwić jego odczytywanie.

## <a name="copying-elements"></a>Kopiowanie elementów
 Możesz użyć kopiowania, wycinania i wklejania elementów w diagramie definicji DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Powiększanie lub pomniejszanie diagramu
 Możesz powiększać lub pomniejszać diagram przy użyciu paska **projektant DSL,** aby ustawić poziom powiększenia.

## <a name="hiding-map-lines"></a>Ukrywanie linii mapy
 Linie mapy to linie rysowane między klasą domeny lub relacją domeny a kształtem lub łącznikiem, na który jest mapowany. Linie mapy można ukryć, klikając przycisk **Pokaż linie mapy** na pasku **projektant DSL** mapy. Aby wyświetlić wiersze, kliknij przycisk ponownie.

## <a name="changing-the-diagram-layout"></a>Zmienianie układu diagramu
 Układ partycji Klasy i relacje można zmienić **w** następujący sposób.

### <a name="expandcollapse"></a>Rozwijanie/zwijanie
 Rozmiar elementu kształtu przedziału reprezentującego klasę domeny lub kształt można zmniejszyć, klikając go prawym przyciskiem myszy, a następnie klikając polecenie **Zwiń**. Pozwala to ukryć **przedział Właściwości** domeny kształtu. Aby ponownie wyświetlić **przedział Właściwości domeny,** kliknij prawym przyciskiem myszy kształt, a następnie kliknij polecenie **Rozwiń.**

### <a name="move-updown"></a>Przenoszenie w górę/w dół
 Klasę domeny lub element diagramu można przenieść w górę lub w dół partycji, klikając prawym przyciskiem myszy element , a następnie klikając polecenie **Przenieś** w górę lub **Przenieś w dół.** Jeśli przeniesiesz element zastępczy, który jest wyświetlany jako element docelowy osadzania lub relacji odwołania, relacja zostanie z nim przenosowana.

### <a name="expandcollapse-relationships-tree"></a>Rozwijanie/zwijanie drzewa relacji
 Jeśli klasa domeny odgrywa rolę źródłową w osadzaniu lub relacjach odwołania z innymi klasami domen, możesz ukryć relacje, klikając prawym przyciskiem myszy definicję klasy domeny, a następnie klikając polecenie **Zwiń drzewo relacji.** Aby wyświetlić relacje, kliknij prawym przyciskiem myszy element definicji, a następnie kliknij polecenie **Rozwiń drzewo relacji.**

### <a name="expandcollapse-inheritance-tree"></a>Rozwijanie/zwijanie drzewa dziedziczenia
 Jeśli klasa domeny jest klasą bazową innych klas domeny, możesz ukryć drzewo dziedziczenia, klikając prawym przyciskiem myszy definicję klasy domeny, a następnie klikając polecenie **Zwiń drzewo dziedziczenia.** Aby wyświetlić drzewo dziedziczenia, kliknij prawym przyciskiem myszy element definicji, a następnie kliknij polecenie **Rozwiń drzewo dziedziczenia**.

### <a name="bring-tree-here"></a>Wyświetl drzewo tutaj
 Diagram można skonsolidować, klikając prawym przyciskiem myszy klasę domeny zastępczej, a następnie klikając polecenie Bring Tree Here (Przynieź **drzewo tutaj).** Klasa domeny zastępczej staje się elementem definicji i wyświetla drzewa dziedziczenia i relacji. Poprzedni element definicji staje się elementem zastępczym, jeśli jest obiektem docelowym relacji lub elementem podrzędnym w relacji dziedziczenia; w przeciwnym razie znika.

### <a name="split-tree"></a>Podziel drzewo
 Drzewa dziedziczenia lub relacji można podzielić, klikając prawym przyciskiem myszy definicję klasy domeny, która je wyświetla, a następnie klikając pozycję **Podziel drzewo.** Element definicji staje się elementem zastępczym, a klasa domeny definicji wraz z drzewami dziedziczenia i relacji jest teraz wyświetlana w dolnej części partycji.

### <a name="show-as-class"></a>Pokaż jako klasę
 Jeśli relacja domeny ma relacje pochodne lub zawiera osadzanie lub odwołania do relacji z innymi relacjami domeny, możesz wyświetlić relację jako klasę, klikając relację prawym przyciskiem myszy, a następnie klikając polecenie Pokaż jako **klasę**. Relacja zostanie wyświetlona z **przedziałem Właściwości domeny** i będzie pokazywać drzewa dziedziczenia i relacji.

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))