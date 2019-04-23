---
title: 'Instrukcje: Dostosowywanie diagramów klas (Projektant klas) | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 442181aa78e539471aa35feb96ec7503e09a97ec
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065834"
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Instrukcje: Dostosowywanie diagramów klas (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić sposób wyświetlania informacji na diagramach klas. Można dostosować cały diagram lub poszczególne typy na powierzchni projektowej.  
  
 Na przykład, można dostosować poziom powiększenia całego diagramu klasy, zmienić grupowanie i sortowanie poszczególnych składowych typu, ukrywać lub pokazywać relacje i przenieść pojedyncze typy lub zestawy typów w dowolne miejsce na diagramie.  
  
> [!NOTE]
>  Dostosowywanie sposobu wyświetlania kształtów na diagramie nie zmienia podstawowego kodu dla typów reprezentowanych na diagramie.  
  
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
  
## <a name="ZoomInOut"></a> Powiększanie i pomniejszanie diagramu klasy  
  
1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2. Kliknij na pasku narzędzi projektanta klas **Powiększ** lub **Pomniejsz** przycisk, aby zmienić poziom powiększenia powierzchni projektowej.  
  
     lub  
  
     Określ konkretną wartość stopnia powiększenia. Możesz użyć **powiększenia** listy rozwijanej lub wpisać prawidłowy poziom powiększenia (prawidłowy zakres to od 10% do 400%).  
  
    > [!NOTE]
    >  Zmiana powiększenia nie wpływa na skalę wydruku diagramu klasy.  
  
## <a name="CustomizeGroupingSorting"></a> Dostosowywanie grupowania i sortowania elementów członkowskich typu  
  
1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2. Kliknij prawym przyciskiem myszy pusty obszar na powierzchni projektowej i wskaż **członków grupy**.  
  
3. Wybierz jedną z dostępnych opcji:  
  
    1. **Grupuj według rodzaju** dzieli poszczególne elementy członkowskie typu na pogrupowaną listę właściwości, metod, zdarzeń i pól. Pojedyncze grupy zależą od definicji jednostki: na przykład, klasa nie wyświetli żadnej grupy zdarzeń, jeśli nie istnieją jeszcze żadne zdarzenia zdefiniowane dla tej klasy.  
  
    2. **Grupuj według typu dostępu** modyfikatorach dostępu dzieli poszczególne elementy członkowskie typu na pogrupowaną listę oparty na elemencie członkowskim. Na przykład, publiczne i prywatne.  
  
    3. **Sortuj alfabetycznie** Wyświetla elementy tworzące jednostkę jako pojedynczą listę alfabetyczną. Lista jest sortowana w kolejności rosnącej.  
  
## <a name="HideCompartments"></a> Ukrywanie przedziałów w danym typie  
  
1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2. Kliknij prawym przyciskiem myszy kategorię składowej w typie, który chcesz dostosować (na przykład wybierz **metody** węzła w klasie.  
  
3. Kliknij przycisk **Ukryj przedział**.  
  
     Wybrany przedział znika z kontenera typu.  
  
## <a name="HideMembers"></a> Ukrywanie poszczególnych elementów członkowskich w danym typie  
  
1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2. Kliknij prawym przyciskiem myszy element członkowski w typie, który chcesz ukryć.  
  
3. Kliknij przycisk **Ukryj**.  
  
     Wybrany element członkowski znika z kontenera typu.  
  
## <a name="DisplayHiddenCompartmentsAndMemberrs"></a> Pokazywanie ukrytych przedziałów i elementów członkowskich w danym typie  
  
1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2. Kliknij prawym przyciskiem myszy nazwę typu z ukrytym przedziałem.  
  
3. Kliknij przycisk **Pokaż wszystkie elementy członkowskie**.  
  
     Wszystkie ukryte przedziały i elementy członkowskie pojawiają się w kontenerze typu.  
  
## <a name="HideAssociationAndInheritance"></a> Ukrywanie relacji  
  
1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2. Kliknij prawym przyciskiem myszy linię skojarzenia lub dziedziczenia, którą chcesz ukryć.  
  
3. Kliknij przycisk **Ukryj** linii skojarzeń, a następnie kliknij przycisk **Ukryj linię dziedziczenia** dla linii dziedziczenia.  
  
4. Kliknij przycisk **Pokaż wszystkie elementy członkowskie**.  
  
     Wszystkie ukryte przedziały i elementy członkowskie pojawiają się w kontenerze typu.  
  
## <a name="DisplayAssociationAndInheritance"></a> Pokazywanie ukrytych relacji  
  
1. Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2. Kliknij prawym przyciskiem myszy typ z ukrytym skojarzeniem lub dziedziczeniem.  
  
   Kliknij przycisk **Pokaż wszystkie elementy członkowskie** linii skojarzeń, a następnie kliknij przycisk **Pokaż klasy podstawowe** lub **Pokaż klasy pochodne** dla linii dziedziczenia.  
  
## <a name="RemoveCodeAndShape"></a> Usuwanie kształtu z diagramu klasy  
 Możesz usunąć kształt typu z diagramu klasy bez wpływu na podstawowy kod typu. Usuwanie kształtów typu z diagramu klasy dotyczy tylko tego diagramu: podstawowy kod, który określa typ, i inne diagramy, które wyświetlają typ, nie są modyfikowane.  
  
1. Na diagramie klasy zaznacz kształt typu, który chcesz usunąć z diagramu.  
  
2. Na **Edytuj** menu, wybierz **Usuń z diagramu**.  
  
     Kształt typu i wszystkie linie skojarzeń lub dziedziczenia połączone z kształtem nie są już wyświetlane na diagramie.  
  
## <a name="DeleteTypeShapeAndCode"></a> Usuwanie kształtu typu i jego kodu podstawowego  
  
1. Kliknij prawym przyciskiem myszy kształt na powierzchni projektowej.  
  
2. Wybierz **Usuń kod** z menu kontekstowego.  
  
     Kształt zostanie usunięty z diagramu, a jego podstawowy kod zostanie usunięty z projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md)   
 [Instrukcje: Zmiana między notacją składowych i notacją skojarzeń (Projektant klas)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)   
 [Instrukcje: Wyświetlanie istniejących typów (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md)   
 [Wyświetlanie typów i relacji (Projektant klas)](../ide/viewing-types-and-relationships-class-designer.md)
