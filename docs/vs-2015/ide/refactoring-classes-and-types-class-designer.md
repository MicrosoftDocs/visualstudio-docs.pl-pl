---
title: Refaktoryzacja klas i typów (Projektant klas) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eaee3dae25f5f2e5544a2521a7bce0201b45a3e2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441157"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refaktoryzacja klas i typów (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refaktoryzacja kodu możesz ułatwić zrozumienie, obsługa i bardziej wydajne, zmieniając jego wewnętrzną strukturę i sposób jej obiektów są zaprojektowane nie jego zachowanie zewnętrznych. Umożliwia ograniczenie prac, które należy wykonać i ryzyko wprowadzenia błędów podczas refaktoryzacji kodu języka Visual C# .NET, Visual Basic .NET lub C++ w projekcie programu Visual Studio w Projektancie klas i oknie Szczegóły klasy.  
  
> [!NOTE]
> Pliki projektu może być tylko do odczytu, ponieważ projekt jest pod kontrolą kodu źródłowego i nie został wyewidencjonowany; jest to projekt odwołania; lub jego pliki są oznaczone jako tylko do odczytu na dysku. Podczas pracy w projekcie w jeden z tych stanów, zostaną wyświetlone różne sposoby, aby zapisać swoją pracę w zależności od stanu projektu. Dotyczy to refaktoryzacji kodu, a także kod, który możesz zmienić w inny sposób, na przykład bezpośrednio edytując ją. Aby uzyskać więcej informacji, zobacz [wyświetlanie informacji tylko do odczytu (Projektant klas)](http://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pomocnicza|  
|----------|------------------------|  
|**Refaktoryzacja klas:** Można użyć operacji refaktoryzacji, podział klasy na klasy częściowe lub Implementowanie abstrakcyjnych klas podstawowych.|-   [Jak: Podział klas na klasy częściowe (Projektant klas)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|  
|**Praca z interfejsów:** W Projektancie klas można zaimplementować interfejsu na diagramie klas, łącząc je do klasy, która zawiera kod dla metody interfejsu.|-   [Jak: Implementowanie interfejsu (Projektant klas)](../ide/how-to-implement-an-interface-class-designer.md)|  
|**Refaktoryzacja, typy, elementy członkowskie typu i parametry:** Za pomocą projektanta klas, można zmienić nazwy typów, Przesłoń składowe typu lub przenieść je z jednego typu na inny. Można również utworzyć typy dopuszczające wartości null.|-   [Zmiana nazwy, typy i elementy członkowskie typu](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Przenoszenie elementów członkowskich typu z jednego typu na inny](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Jak: Tworzenie typu zerowalnego (Projektant klas)](../ide/how-to-create-a-nullable-type-class-designer.md)|  
  
### <a name="RenamingTypesAndMembers"></a> Zmiana nazwy, typy i elementy członkowskie typu  
 W Projektancie klas możesz zmienić nazwę typu lub składowej typu na diagramie klasy lub w oknie dialogowym właściwości. W oknie Szczegóły klasy można zmienić nazwę elementu członkowskiego, ale nie jest typem. Zmiana nazwy typu lub składowej typu propaguje do wszystkich okien i lokalizacji kodu, w których pojawiły się starej nazwy.  
  
##### <a name="to-rename-a-name-in-the-class-designer"></a>Aby zmienić nazwę w Projektancie klas  
  
1. Na diagramie klasy wybierz typ lub element członkowski, a następnie kliknij nazwę.  
  
     Nazwa elementu członkowskiego staje się edytowalna.  
  
2. Wpisz nową nazwę dla typu lub składowej typu  
  
##### <a name="to-rename-a-name-in-the-class-details-window"></a>Aby zmienić nazwę w oknie Szczegóły klasy  
  
1. Aby wyświetlić okno Szczegóły klasy, kliknij prawym przyciskiem myszy typ lub składowa typu, a następnie kliknij przycisk **szczegóły klasy**.  
  
     Zostanie wyświetlone okno Szczegóły klasy.  
  
2. W **nazwa** kolumny, zmienić nazwę elementu członkowskiego typu  
  
3. Aby przenieść fokus od komórki, naciśnij klawisz **ENTER** klucza, lub kliknij przycisk od komórki.  
  
    > [!NOTE]
    > W oknie Szczegóły klasy można zmienić nazwę elementu członkowskiego, ale nie jest typem.  
  
##### <a name="to-rename-a-name-in-the-properties-window"></a>Aby zmienić nazwę w oknie dialogowym właściwości  
  
1. Na diagramie klasy lub w oknie Szczegóły klasy, kliknij prawym przyciskiem myszy typ lub element członkowski, a następnie kliknij przycisk **właściwości**.  
  
     W oknie właściwości, pojawia się i wyświetla właściwości dla typu lub składowej typu.  
  
2. W **nazwa** właściwości, Zmień nazwę typu lub typ elementu członkowskiego.  
  
     Nowa nazwa propaguje do wszystkich okien i lokalizacji kodu w bieżącym projekcie, gdzie znajdowały się starej nazwy.  
  
### <a name="MovingTypeMembers"></a> Przenoszenie elementów członkowskich typu z jednego typu na inny  
 Za pomocą **projektanta klas**, można przenieść elementu członkowskiego typu z jednego typu do innego typu, jeśli obie są widoczne w bieżącym diagramie klas.  
  
##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Aby przenieść jeden typ elementu członkowskiego typu  
  
1. W typie, który jest wyświetlany na powierzchni projektowej, kliknij prawym przyciskiem myszy składnik, który chcesz przenieść do innego typu, a następnie kliknij przycisk **Wytnij**.  
  
2. Kliknij prawym przyciskiem myszy docelowy typ, a następnie kliknij przycisk **Wklej**.  
  
     Właściwość zostanie usunięta z typu źródłowego i pojawia się w typie docelowym.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wyświetlanie typów i relacji (Projektant klas)](../ide/viewing-types-and-relationships-class-designer.md)||  
|[Projektowanie klas i typów (Projektant klas)](../ide/designing-classes-and-types-class-designer.md)||
