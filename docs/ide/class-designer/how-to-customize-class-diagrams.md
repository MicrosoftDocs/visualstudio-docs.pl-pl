---
title: 'Porady: dostosowywanie diagramów klasy (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4c55204983f9e7a546867621ec21070c8d69645
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590166"
---
# <a name="how-to-customize-class-diagrams"></a>Instrukcje: Dostosowywanie diagramów klas

Można zmienić sposób wyświetlania informacji na diagramach klas. Można dostosować cały diagram lub poszczególne typy na powierzchni projektowej.

Na przykład, można dostosować poziom powiększenia całego diagramu klasy, zmienić grupowanie i sortowanie poszczególnych składowych typu, ukrywać lub pokazywać relacje i przenieść pojedyncze typy lub zestawy typów w dowolne miejsce na diagramie.

> [!NOTE]
> Dostosowywanie sposobu wyświetlania kształtów na diagramie nie zmienia podstawowego kodu dla typów reprezentowanych na diagramie.

Sekcje, które zawierają składowe typu, takie jak sekcja **Właściwości** w klasie, są nazywane przedziałami. Można ukryć lub pokazać poszczególne przedziały i elementy członkowskie typu.

## <a name="zoom-in-and-out-of-the-class-diagram"></a>Powiększanie i pomniejszanie diagramu klasy

1. Otwórz i wybierz plik diagramu klas w **Projektant klas**.

2. Na pasku narzędzi **Projektant klas** kliknij przycisk **Powiększ** lub **Pomniejsz** , aby zmienić poziom powiększenia powierzchni projektanta.

     lub

     Określ konkretną wartość stopnia powiększenia. Możesz użyć listy rozwijanej **powiększenie** lub wpisać prawidłowy poziom powiększenia (prawidłowy zakres to od 10% do 400%).

    > [!NOTE]
    > Zmiana powiększenia nie wpływa na skalę wydruku diagramu klasy.

## <a name="customize-grouping-and-sorting-of-type-members"></a>Dostosowywanie grupowania i sortowania elementów członkowskich typu

1. Otwórz i wybierz plik diagramu klas w **Projektant klas**.

2. Kliknij prawym przyciskiem myszy pusty obszar na powierzchni projektowej i wskaż **elementy członkowskie grupy**.

3. Wybierz jedną z dostępnych opcji:

    - **Grupuj według rodzaju** oddziela poszczególne elementy członkowskie typu do pogrupowanej listy właściwości, metod, zdarzeń i pól. Pojedyncze grupy zależą od definicji jednostki: na przykład, klasa nie wyświetli żadnej grupy zdarzeń, jeśli nie istnieją jeszcze żadne zdarzenia zdefiniowane dla tej klasy.

    - **Grupuj według dostępu** oddziela poszczególne elementy członkowskie typu do listy grupowanej na podstawie modyfikatorów dostępu elementu członkowskiego. Na przykład, publiczne i prywatne.

    - **Sortuj alfabetycznie** wyświetla elementy tworzące jednostkę jako pojedynczą listę z alfabetem. Lista jest sortowana w kolejności rosnącej.

## <a name="hide-compartments-on-a-type"></a>Ukrywanie przedziałów w danym typie

1. Otwórz i wybierz plik diagramu klas w **Projektant klas**.

2. Kliknij prawym przyciskiem myszy kategorię składowej w typie, który chcesz dostosować (na przykład wybierz węzeł **metody** w klasie.

3. Kliknij pozycję **Ukryj przedział**.

     Wybrany przedział znika z kontenera typu.

## <a name="hide-individual-members-on-a-type"></a>Ukrywanie poszczególnych elementów członkowskich w danym typie

1. Otwórz i wybierz plik diagramu klas w **Projektant klas**.

2. Kliknij prawym przyciskiem myszy element członkowski w typie, który chcesz ukryć.

3. Kliknij przycisk **Ukryj**.

     Wybrany element członkowski znika z kontenera typu.

## <a name="show-hidden-compartments-and-members-on-a-type"></a>Pokazywanie ukrytych przedziałów i elementów członkowskich w danym typie

1. Otwórz i wybierz plik diagramu klas w **Projektant klas**.

2. Kliknij prawym przyciskiem myszy nazwę typu z ukrytym przedziałem.

3. Kliknij pozycję **Pokaż wszystkie elementy członkowskie**.

     Wszystkie ukryte przedziały i elementy członkowskie pojawiają się w kontenerze typu.

## <a name="hide-relationships"></a>{1&gt;Ukrywanie relacji&lt;1}

1. Otwórz i wybierz plik diagramu klas w **Projektant klas**.

2. Kliknij prawym przyciskiem myszy linię skojarzenia lub dziedziczenia, którą chcesz ukryć.

3. Kliknij przycisk **Ukryj** dla linii skojarzenia, a następnie kliknij przycisk **Ukryj linię dziedziczenia** dla linii dziedziczenia.

4. Kliknij pozycję **Pokaż wszystkie elementy członkowskie**.

     Wszystkie ukryte przedziały i elementy członkowskie pojawiają się w kontenerze typu.

## <a name="show-hidden-relationships"></a>Pokazywanie ukrytych relacji

1. Otwórz i wybierz plik diagramu klas w **Projektant klas**.

2. Kliknij prawym przyciskiem myszy typ z ukrytym skojarzeniem lub dziedziczeniem.

   Kliknij pozycję **Pokaż wszystkie elementy członkowskie** dla linii skojarzenia, a następnie kliknij pozycję **Pokaż klasę bazową** lub **Pokaż klasy pochodne** dla linii dziedziczenia.

## <a name="remove-a-shape-from-a-class-diagram"></a>Usuwanie kształtu z diagramu klasy
Możesz usunąć kształt typu z diagramu klasy bez wpływu na podstawowy kod typu. Usuwanie kształtów typu z diagramu klasy dotyczy tylko tego diagramu: podstawowy kod, który określa typ, i inne diagramy, które wyświetlają typ, nie są modyfikowane.

1. Na diagramie klasy zaznacz kształt typu, który chcesz usunąć z diagramu.

2. W menu **Edycja** wybierz polecenie **Usuń z diagramu**.

     Kształt typu i wszystkie linie skojarzeń lub dziedziczenia połączone z kształtem nie są już wyświetlane na diagramie.

## <a name="delete-a-type-shape-and-its-underlying-code"></a>Usuwanie kształtu typu i jego kodu podstawowego

1. Kliknij prawym przyciskiem myszy kształt na powierzchni projektowej.

2. Wybierz pozycję **Usuń kod** z menu kontekstowego.

     Kształt zostanie usunięty z diagramu, a jego podstawowy kod zostanie usunięty z projektu.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: zmiana między notacją składowej i notacją skojarzenia](how-to-change-between-member-notation-and-association-notation.md)
- [Instrukcje: wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
