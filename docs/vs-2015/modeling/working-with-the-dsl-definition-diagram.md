---
title: Praca z diagramem definicji DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 14e365d6bbe99634135bfad133d840b98e22e3b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663040"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Praca z diagramem definicji DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagram definicji [!INCLUDE[dsl](../includes/dsl-md.md)] jest ważnym narzędziem do definiowania języka specyficznego dla domeny. Można dodawać elementy do modelu domeny i definiować relacje na diagramie. można także zmodyfikować układ diagramu, aby zwiększyć jego czytelność.

## <a name="the-layout-of-the-diagram"></a>Układ diagramu
 Diagram definicji [!INCLUDE[dsl](../includes/dsl-md.md)] ma dwie partycje, partycje **klas i relacji** oraz partycję **elementów diagramu** . Partycje **klasy i relacje** wyświetlają klasy domen, relacje domen i dziedziczenie. Partycja **elementów diagramu** zawiera klasy kształtu, klasy łączników, klasy toru i wygenerowany diagram projektanta.

 Klasy domeny mogą znajdować się w wielu lokalizacjach w partycjach **klas i relacji** . Definicja klasy domeny wyświetla drzewo dziedziczenia, jeśli jest klasą bazową dla innych klas domeny i drzewo relacji, jeśli jest to źródło relacji osadzania lub odwołań. Symbole zastępcze klas domen są wyświetlane jako elementy docelowe relacji osadzania lub odwołań. Domyślnie elementy zastępcze są wyświetlane z zwiniętym przedziałem **właściwości domeny** . Nie pokazuje dziedziczenia ani relacji osadzania ani odwołań.

 Po dodaniu klasy domeny pojawia się ona w dolnej części partycji **klasy i relacje** . Po dodaniu relacji osadzania lub odwołania jest ona rysowana w obszarze i po prawej stronie klasy domeny źródłowej.

 Podczas dodawania klas domen i relacji może być trudno zlokalizować konkretną klasę domeny. Klasę domeny można znaleźć, klikając ją prawym przyciskiem myszy w **Eksploratorze DSL** , a następnie klikając pozycję **Znajdź na diagramie**.

 W poniższych sekcjach opisano, jak można zmienić wygląd diagramu, aby ułatwić jego odczytywanie.

## <a name="copying-elements"></a>Kopiowanie elementów
 Można użyć kopiowania, wycinać i wklejać elementów na diagramie definicji DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Powiększanie lub pomniejszanie na diagramie
 Możesz powiększyć lub pomniejszyć diagram za pomocą paska narzędzi **Projektant DSL** , aby ustawić poziom powiększenia.

## <a name="hiding-map-lines"></a>Ukrywanie linii mapy
 Linie mapy to linie rysowane między klasą domeny lub relacją domeny a kształtem lub łącznikiem, do którego jest zamapowany. Linie mapy można ukryć, klikając przycisk **Pokaż linie mapy** na pasku narzędzi **Projektant DSL** . Aby wyświetlić wiersze, kliknij przycisk ponownie.

## <a name="changing-the-diagram-layout"></a>Zmiana układu diagramu
 Układ **klas i partycji relacji** można zmienić w następujący sposób.

### <a name="expandcollapse"></a>Rozwiń/Zwiń
 Można zmniejszyć rozmiar elementu kształtu przedziału, który reprezentuje klasę domeny lub kształt, klikając go prawym przyciskiem myszy, a następnie klikając przycisk **Zwiń**. Spowoduje to ukrycie przedziału **właściwości domeny** kształtu. Aby ponownie wyświetlić przedział **właściwości domeny** , kliknij prawym przyciskiem myszy kształt, a następnie kliknij przycisk **Rozwiń**.

### <a name="move-updown"></a>Przenieś w górę/w dół
 Możesz przenieść klasę domeny lub element diagramu w górę lub w dół na partycji, klikając prawym przyciskiem myszy element, a następnie klikając pozycję **Przenieś w górę** lub **Przenieś w dół**. Jeśli przeniesiesz element zastępczy, który jest wyświetlany jako obiekt docelowy relacji osadzania lub odwołania, relacja zostanie przeniesiona z nią.

### <a name="expandcollapse-relationships-tree"></a>Rozwiń/Zwiń drzewo relacji
 Jeśli klasa domeny odgrywa rolę źródłową w osadzaniu lub relacji odwołania z innymi klasami domeny, można ukryć relacje, klikając prawym przyciskiem myszy definicję klasy domeny, a następnie klikając polecenie **Zwiń relacje drzewa**. Aby wyświetlić relacje, kliknij prawym przyciskiem myszy element definicji, a następnie kliknij **Rozwiń drzewo relacje**.

### <a name="expandcollapse-inheritance-tree"></a>Rozwiń/Zwiń drzewo dziedziczenia
 Jeśli klasa domeny jest klasą bazową innych klas domen, drzewo dziedziczenia można ukryć, klikając prawym przyciskiem myszy definicję klasy domeny, a następnie klikając polecenie **Zwiń drzewo dziedziczenia**. Aby wyświetlić drzewo dziedziczenia, kliknij prawym przyciskiem myszy element definicji, a następnie kliknij polecenie **Rozwiń drzewo dziedziczenia**.

### <a name="bring-tree-here"></a>Wyświetl drzewo tutaj
 Aby skonsolidować diagram, kliknij prawym przyciskiem myszy klasę zastępczą domeny, a następnie kliknij pozycję **przesuń drzewo tutaj**. Zastępcza Klasa domeny stał się elementem definicji i wyświetla drzewa dziedziczenia i relacje. Dawno element definicji jest symbolem zastępczym, jeśli jest obiektem docelowym relacji lub elementu podrzędnego w relacji dziedziczenia; w przeciwnym razie zniknie.

### <a name="split-tree"></a>Podziel drzewo
 Można rozdzielić drzewa dziedziczenia lub relacje, klikając prawym przyciskiem myszy definicję klasy domeny, która wyświetla je, a następnie klikając polecenie **Podziel drzewo**. Element definicji zmieni się na element zastępczy, a Klasa domeny definicji wraz z drzewami dziedziczenia i relacji jest teraz wyświetlana u dołu partycji.

### <a name="show-as-class"></a>Pokaż jako klasę
 Jeśli relacja domeny ma relacje pochodne lub jeśli ma relacje osadzania lub odwołania z innymi relacjami domeny, można wyświetlić relację jako klasę, klikając prawym przyciskiem myszy relację, a następnie klikając polecenie **Pokaż jako klasę**. Relacja będzie wyświetlana z przedziałem **właściwości domeny** i będzie zawierać drzewa dziedziczenia i relacje.

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
