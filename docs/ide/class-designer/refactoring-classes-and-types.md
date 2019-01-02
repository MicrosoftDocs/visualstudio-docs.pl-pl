---
title: Zmień nazwę i przenieść klas i typów w Projektancie klas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e85c4b760bab242ba5aa43f0e1aab0936565af33
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891469"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Refaktoryzacja klas i typów w Projektancie klas

Refaktoryzacja kodu możesz ułatwić zrozumienie, obsługa i bardziej wydajne, zmieniając jego wewnętrzną strukturę i sposób jej obiektów są zaprojektowane nie jego zachowanie zewnętrznych. Korzystanie z projektanta klas i w oknie Szczegóły klasy, aby zmniejszyć prac, które należy wykonać oraz ryzyko wprowadzenia błędów, Refaktoryzacja C#, Visual Basic lub C++ możesz pisać kod w projekcie programu Visual Studio.

> [!NOTE]
> Pliki projektu może być tylko do odczytu, ponieważ projekt jest pod kontrolą kodu źródłowego i nie został wyewidencjonowany, jest przywoływany projekt lub jego pliki są oznaczone jako tylko do odczytu na dysku. Podczas pracy w projekcie w jeden z tych stanów, zostaną wyświetlone różne sposoby, aby zapisać swoją pracę w zależności od stanu projektu. Dotyczy to refaktoryzacji kodu, a także kod, który możesz zmienić w inny sposób, na przykład bezpośrednio edytując ją.

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Zawartość pomocnicza|
|----------| - |
|**Refaktoryzacja klas:** Można użyć operacji refaktoryzacji, podział klasy na klasy częściowe lub Implementowanie abstrakcyjnych klas podstawowych.|-   [Jak: Podział klasy na klasy częściowe](how-to-split-a-class-into-partial-classes.md)|
|**Praca z interfejsów:** W Projektancie klas można zaimplementować interfejsu na diagramie klas, łącząc je do klasy, która zawiera kod dla metody interfejsu.|-   [Jak: Implementowanie interfejsu](how-to-implement-an-interface.md)|
|**Refaktoryzacja, typy, elementy członkowskie typu i parametry:** Za pomocą projektanta klas, można zmienić nazwy typów, Przesłoń składowe typu lub przenieść je z jednego typu na inny. Można również utworzyć typy dopuszczające wartości null.|-   [Zmiana nazwy, typy i elementy członkowskie typu](#rename-types-and-type-members)<br />-   [Przenoszenie elementów członkowskich typu z jednego typu na inny](#move-type-members-from-one-type-to-another)<br />-   [Jak: Tworzenie typu dopuszczającego wartość null](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Zmiana nazwy, typy i elementy członkowskie typu

W Projektancie klas, możesz zmienić nazwę typu lub składowej typu na diagramie klasy lub w **właściwości** okna. W **szczegóły klasy** okna, możesz zmienić nazwę elementu członkowskiego, ale nie jest typem. Zmiana nazwy typu lub składowej typu propaguje do wszystkich okien i lokalizacji kodu, w których pojawiły się starej nazwy.

### <a name="rename-in-the-class-designer"></a>Zmień nazwę w Projektancie klas

1. Na diagramie klasy zaznacz typ lub element członkowski, a następnie wybierz nazwę.

     Nazwa elementu członkowskiego staje się edytowalna.

2. Wpisz nową nazwę dla typu lub składowej typu

### <a name="rename-in-the-class-details-window"></a>Zmień nazwę w oknie Szczegóły klasy

1. Aby wyświetlić **szczegóły klasy** okna, kliknij prawym przyciskiem myszy typ lub składowa typu i wybierz **szczegóły klasy**.

     **Szczegóły klasy** zostanie wyświetlone okno.

2. W **nazwa** kolumny, zmienić nazwę elementu członkowskiego typu

3. Aby przenieść fokus od komórki, naciśnij klawisz **Enter** klucza, lub kliknij przycisk od komórki.

    > [!NOTE]
    > W **szczegóły klasy** okna, możesz zmienić nazwę elementu członkowskiego, ale nie jest typem.

### <a name="rename-in-the-properties-window"></a>Zmień nazwę w oknie dialogowym właściwości

1. Na diagramie klasy lub **szczegóły klasy** okna, kliknij prawym przyciskiem myszy typ lub element członkowski, a następnie wybierz pozycję **właściwości**.

     **Właściwości** okna pojawi się i wyświetla właściwości dla typu lub składowej typu.

2. W **nazwa** właściwości, Zmień nazwę typu lub typ elementu członkowskiego.

     Nowa nazwa propaguje do wszystkich okien i lokalizacji kodu w bieżącym projekcie, gdzie znajdowały się starej nazwy.

## <a name="move-type-members-from-one-type-to-another"></a>Przenoszenie elementów członkowskich typu z jednego typu na inny

Za pomocą **projektanta klas**, można przenieść elementu członkowskiego typu z jednego typu na inny typ. Oba typy muszą być widoczne w bieżącym diagramie klas.

1. W typie, który jest wyświetlany na powierzchni projektowej, kliknij prawym przyciskiem myszy składnik, który chcesz przenieść do innego typu, a następnie wybierz **Wytnij**.

2. Kliknij prawym przyciskiem myszy docelowy typ, a następnie wybierz pozycję **Wklej**.

     Właściwość zostanie usunięta z typu źródłowego i pojawia się w typie docelowym.

## <a name="see-also"></a>Zobacz także

- [Projektowanie klas i typów](designing-and-viewing-classes-and-types.md)