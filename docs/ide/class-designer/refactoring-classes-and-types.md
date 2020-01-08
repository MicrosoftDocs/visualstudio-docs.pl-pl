---
title: Zmień nazwę i Przenieś klasy i typy w Projektant klas
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e060f044af666f5a4357e527819286d3bd87267
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590751"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Klasy i typy refaktoryzacji w Projektant klas

W przypadku refaktoryzacji kodu można ułatwić zrozumienie, konserwację i wydajniejsze działanie poprzez zmianę jego wewnętrznej struktury i sposobu, w jaki obiekty są zaprojektowane, a nie z zachowaniem zewnętrznym. Użyj Projektant klas i okna Szczegóły klasy, aby zmniejszyć ilość pracy, którą trzeba wykonać, i szansę wprowadzenia usterek podczas refaktoryzacji C#, Visual Basic lub C++ kodu w projekcie programu Visual Studio.

> [!NOTE]
> Pliki projektu mogą być tylko do odczytu, ponieważ projekt znajduje się pod kontrolą kodu źródłowego i nie jest wyewidencjonowany, jest to projekt, do którego istnieje odwołanie, lub jego pliki są oznaczone jako tylko do odczytu na dysku. Podczas pracy w projekcie w jednym z tych stanów będą prezentowane różne sposoby zapisywania pracy w zależności od stanu projektu. Dotyczy to również kodu refaktoryzacji i kodu, który można zmienić w inny sposób, na przykład jego bezpośredniej edycji.

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Zawartość pomocnicza|
|----------| - |
|**Klasy refaktoryzacji:** Operacji refaktoryzacji można użyć do podziału klasy na klasy częściowe lub w celu zaimplementowania abstrakcyjnej klasy bazowej.|-   [instrukcje: dzielenie klasy na klasy częściowe](how-to-split-a-class-into-partial-classes.md)|
|**Praca z interfejsami:** W Projektant klas można zaimplementować interfejs na diagramie klas, łącząc go z klasą, która dostarcza kod dla metod interfejsu.|-   [: implementowanie interfejsu](how-to-implement-an-interface.md)|
|**Typy refaktoryzacji, elementy członkowskie typu i parametry:** Za pomocą Projektant klas można zmienić nazwy typów, zastąpić elementy typu lub przenieść je z jednego typu do drugiego. Można również tworzyć Typy dopuszczające wartości null.|-   [Zmień nazwy typów i składowych typu](#rename-types-and-type-members)<br />-   [przenieść składowe typu z jednego typu na inny](#move-type-members-from-one-type-to-another)<br />-   [instrukcje: Tworzenie typu dopuszczającego wartość null](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Zmień nazwy typów i składowych typu

W Projektant klas można zmienić nazwę typu lub elementu członkowskiego typu na diagramie klasy lub w oknie **Właściwości** . W oknie **Szczegóły klasy** można zmienić nazwę elementu członkowskiego, ale nie typ. Zmiana nazwy typu lub składowej typu jest propagowana do wszystkich okien i lokalizacji kodu, w których pojawiła się stara nazwa.

### <a name="rename-in-the-class-designer"></a>Zmień nazwę w Projektant klas

1. Na diagramie klasy wybierz typ lub element członkowski i wybierz nazwę.

     Nazwa elementu członkowskiego można edytować.

2. Wpisz nową nazwę typu lub elementu członkowskiego typu

### <a name="rename-in-the-class-details-window"></a>Zmień nazwę w oknie Szczegóły klasy

1. Aby wyświetlić okno **Szczegóły klasy** , kliknij prawym przyciskiem myszy typ lub element członkowski typu i wybierz pozycję **Szczegóły klasy**.

     Zostanie wyświetlone okno **Szczegóły klasy** .

2. W kolumnie **Nazwa** Zmień nazwę elementu członkowskiego typu

3. Aby przenieść fokus z komórki, naciśnij klawisz **Enter** lub kliknij poza komórką.

    > [!NOTE]
    > W oknie **Szczegóły klasy** można zmienić nazwę elementu członkowskiego, ale nie typ.

### <a name="rename-in-the-properties-window"></a>Zmień nazwę w okno Właściwości

1. Na diagramie klasy lub w oknie **Szczegóły klasy** , kliknij prawym przyciskiem myszy typ lub element członkowski, a następnie wybierz polecenie **Właściwości**.

     Zostanie wyświetlone okno **Właściwości** , w którym są wyświetlane właściwości typu lub elementu członkowskiego typu.

2. W właściwości **name (nazwa** ) Zmień nazwę typu lub składowej typu.

     Nowa nazwa jest propagowana do wszystkich okien i lokalizacji kodu w bieżącym projekcie, w których pojawiła się stara nazwa.

## <a name="move-type-members-from-one-type-to-another"></a>Przenoszenie elementów członkowskich typu z jednego typu do innego

Za pomocą **Projektant klas**, można przenieść składową typu z jednego typu na inny typ. Oba typy muszą być widoczne na bieżącym diagramie klas.

1. W typie widocznym na powierzchni projektowej kliknij prawym przyciskiem myszy element członkowski, który chcesz przenieść do innego typu, a następnie wybierz polecenie **Wytnij**.

2. Kliknij prawym przyciskiem myszy typ docelowy i wybierz polecenie **Wklej**.

     Właściwość jest usuwana z typu źródłowego i pojawia się w typie docelowym.

## <a name="see-also"></a>Zobacz także

- [Projektowanie klas i typów](designing-and-viewing-classes-and-types.md)
