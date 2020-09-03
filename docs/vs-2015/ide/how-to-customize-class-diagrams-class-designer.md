---
title: 'Instrukcje: Dostosowywanie diagramów klas (Projektant klas) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ff78bea6759359d3703f5fed6157f051c89befb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668009"
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Porady: dostosowywanie diagramów klasy (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić sposób wyświetlania informacji na diagramach klas. Można dostosować cały diagram lub poszczególne typy na powierzchni projektowej.

 Na przykład, można dostosować poziom powiększenia całego diagramu klasy, zmienić grupowanie i sortowanie poszczególnych składowych typu, ukrywać lub pokazywać relacje i przenieść pojedyncze typy lub zestawy typów w dowolne miejsce na diagramie.

> [!NOTE]
> Dostosowywanie sposobu wyświetlania kształtów na diagramie nie zmienia podstawowego kodu dla typów reprezentowanych na diagramie.

 Sekcje, które zawierają składowe typu, na przykład sekcja Właściwości w klasie, są nazywane przedziałami. Można ukryć lub pokazać poszczególne przedziały i elementy członkowskie typu.

 **W tym temacie**

- [Powiększanie i pomniejszanie diagramu klasy](../ide/how-to-customize-class-diagrams-class-designer.md#ZoomInOut)

- [Dostosowywanie grupowania i sortowania elementów członkowskich typu](../ide/how-to-customize-class-diagrams-class-designer.md#CustomizeGroupingSorting)

- [Ukrywanie przedziałów w danym typie](../ide/how-to-customize-class-diagrams-class-designer.md#HideCompartments)

- [Ukrywanie poszczególnych elementów członkowskich w danym typie](../ide/how-to-customize-class-diagrams-class-designer.md#HideMembers)

- [Pokazywanie ukrytych przedziałów i elementów członkowskich w danym typie](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayHiddenCompartmentsAndMemberrs)

- [Ukrywanie relacji](../ide/how-to-customize-class-diagrams-class-designer.md#HideAssociationAndInheritance)

- [Pokazywanie ukrytych relacji](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayAssociationAndInheritance)

- [Usuwanie kształtu z diagramu klasy](../ide/how-to-customize-class-diagrams-class-designer.md#RemoveCodeAndShape)

- [Usuwanie kształtu typu i jego kodu podstawowego](../ide/how-to-customize-class-diagrams-class-designer.md#DeleteTypeShapeAndCode)

## <a name="zoom-in-and-out-of-the-class-diagram"></a><a name="ZoomInOut"></a> Powiększanie i pomniejszanie diagramu klas

1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.

2. Na pasku narzędzi Projektant klas kliknij przycisk **Powiększ** lub **Pomniejsz** , aby zmienić poziom powiększenia powierzchni projektanta.

     lub

     Określ konkretną wartość stopnia powiększenia. Możesz użyć listy rozwijanej **powiększenie** lub wpisać prawidłowy poziom powiększenia (prawidłowy zakres to od 10% do 400%).

    > [!NOTE]
    > Zmiana powiększenia nie wpływa na skalę wydruku diagramu klasy.

## <a name="customize-grouping-and-sorting-of-type-members"></a><a name="CustomizeGroupingSorting"></a> Dostosowywanie grupowania i sortowania elementów członkowskich typu

1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.

2. Kliknij prawym przyciskiem myszy pusty obszar na powierzchni projektowej i wskaż **elementy członkowskie grupy**.

3. Wybierz jedną z dostępnych opcji:

    1. **Grupuj według rodzaju** oddziela poszczególne elementy członkowskie typu do pogrupowanej listy właściwości, metod, zdarzeń i pól. Pojedyncze grupy zależą od definicji jednostki: na przykład, klasa nie wyświetli żadnej grupy zdarzeń, jeśli nie istnieją jeszcze żadne zdarzenia zdefiniowane dla tej klasy.

    2. **Grupuj według dostępu** oddziela poszczególne elementy członkowskie typu do listy grupowanej na podstawie modyfikatorów dostępu elementu członkowskiego. Na przykład, publiczne i prywatne.

    3. **Sortuj alfabetycznie** wyświetla elementy tworzące jednostkę jako pojedynczą listę z alfabetem. Lista jest sortowana w kolejności rosnącej.

## <a name="hide-compartments-on-a-type"></a><a name="HideCompartments"></a> Ukryj przedziały w typie

1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.

2. Kliknij prawym przyciskiem myszy kategorię składowej w typie, który chcesz dostosować (na przykład wybierz węzeł **metody** w klasie.

3. Kliknij pozycję **Ukryj przedział**.

     Wybrany przedział znika z kontenera typu.

## <a name="hide-individual-members-on-a-type"></a><a name="HideMembers"></a> Ukrywanie poszczególnych elementów członkowskich w typie

1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.

2. Kliknij prawym przyciskiem myszy element członkowski w typie, który chcesz ukryć.

3. Kliknij przycisk **Ukryj**.

     Wybrany element członkowski znika z kontenera typu.

## <a name="show-hidden-compartments-and-members-on-a-type"></a><a name="DisplayHiddenCompartmentsAndMemberrs"></a> Pokaż ukryte przedziały i elementy członkowskie w typie

1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.

2. Kliknij prawym przyciskiem myszy nazwę typu z ukrytym przedziałem.

3. Kliknij pozycję **Pokaż wszystkie elementy członkowskie**.

     Wszystkie ukryte przedziały i elementy członkowskie pojawiają się w kontenerze typu.

## <a name="hide-relationships"></a><a name="HideAssociationAndInheritance"></a> Ukryj relacje

1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.

2. Kliknij prawym przyciskiem myszy linię skojarzenia lub dziedziczenia, którą chcesz ukryć.

3. Kliknij przycisk **Ukryj** dla linii skojarzenia, a następnie kliknij przycisk **Ukryj linię dziedziczenia** dla linii dziedziczenia.

4. Kliknij pozycję **Pokaż wszystkie elementy członkowskie**.

     Wszystkie ukryte przedziały i elementy członkowskie pojawiają się w kontenerze typu.

## <a name="show-hidden-relationships"></a><a name="DisplayAssociationAndInheritance"></a> Pokaż ukryte relacje

1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.

2. Kliknij prawym przyciskiem myszy typ z ukrytym skojarzeniem lub dziedziczeniem.

   Kliknij pozycję **Pokaż wszystkie elementy członkowskie** dla linii skojarzenia, a następnie kliknij pozycję **Pokaż klasę bazową** lub **Pokaż klasy pochodne** dla linii dziedziczenia.

## <a name="remove-a-shape-from-a-class-diagram"></a><a name="RemoveCodeAndShape"></a> Usuwanie kształtu z diagramu klas
 Możesz usunąć kształt typu z diagramu klasy bez wpływu na podstawowy kod typu. Usuwanie kształtów typu z diagramu klasy dotyczy tylko tego diagramu: podstawowy kod, który określa typ, i inne diagramy, które wyświetlają typ, nie są modyfikowane.

1. Na diagramie klasy zaznacz kształt typu, który chcesz usunąć z diagramu.

2. W menu **Edycja** wybierz polecenie **Usuń z diagramu**.

     Kształt typu i wszystkie linie skojarzeń lub dziedziczenia połączone z kształtem nie są już wyświetlane na diagramie.

## <a name="delete-a-type-shape-and-its-underlying-code"></a><a name="DeleteTypeShapeAndCode"></a> Usuwanie kształtu typu i jego kodu źródłowego

1. Kliknij prawym przyciskiem myszy kształt na powierzchni projektowej.

2. Wybierz pozycję **Usuń kod** z menu kontekstowego.

     Kształt zostanie usunięty z diagramu, a jego podstawowy kod zostanie usunięty z projektu.

## <a name="see-also"></a>Zobacz też
 [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md) [instrukcje: zmiana między notacją składowej a notacją skojarzenia (Projektant klas)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md) [instrukcje: wyświetlanie](../ide/how-to-view-existing-types-class-designer.md) [typów i relacji typu](../ide/viewing-types-and-relationships-class-designer.md) (Projektant klas) przeglądanie istniejących typów (Projektant klas)
