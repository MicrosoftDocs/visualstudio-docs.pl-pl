---
title: Zmienianie nazw i przenoszenie klas i typów w Projektancie klas
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590751"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Klasy i typy refaktoryzacji w Projektancie klas

Podczas refaktoryzacji kodu, można ułatwić zrozumienie, utrzymanie i bardziej wydajne, zmieniając jego wewnętrznej struktury i jak jego obiekty są zaprojektowane, a nie jego zachowanie zewnętrzne. Użyj Projektanta klas i okna Szczegóły klasy, aby zmniejszyć pracę, którą należy wykonać i możliwość wprowadzenia błędów podczas refaktoryzacji kodu C#, Visual Basic lub C++ w projekcie programu Visual Studio.

> [!NOTE]
> Pliki projektu mogą być tylko do odczytu, ponieważ projekt jest pod kontrolą kodu źródłowego i nie jest wyewidencjonowany, jest to projekt, do którego istnieje odwołanie, lub jego pliki są oznaczone jako tylko do odczytu na dysku. Podczas pracy w projekcie w jednym z tych stanów, zostanie przedstawiony z różnych sposobów, aby zapisać swoją pracę w zależności od stanu projektu. Dotyczy to refaktoryzacji kodu, a także kodu, który można zmienić w inny sposób, na przykład bezpośrednio edytować go.

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pomocnicza|
|----------| - |
|**Klasy refaktoryzacji:** Operacji refaktoryzacji można użyć do dzielenia klasy na klasy częściowe lub do zaimplementowania abstrakcyjnej klasy podstawowej.|-   [Jak: Podziel klasę na klasy częściowe](how-to-split-a-class-into-partial-classes.md)|
|**Praca z interfejsami:** W Projektancie klas można zaimplementować interfejs na diagramie klasy, łącząc go z klasą, która udostępnia kod dla metod interfejsu.|-   [Jak: Implementowanie interfejsu](how-to-implement-an-interface.md)|
|**Refaktoryzowanie typów, typów elementów członkowskich i parametrów:** Za pomocą Projektanta klas, można zmienić nazwy typów, zastąpić elementy członkowskie typu lub przenieść je z jednego typu do drugiego. Można również utworzyć typy nullable.|-   [Zmienianie nazw typów i typów elementów członkowskich](#rename-types-and-type-members)<br />-   [Przenoszenie elementów członkowskich typu z jednego typu na inny](#move-type-members-from-one-type-to-another)<br />-   [Jak: Tworzenie typu nullable](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Zmienianie nazw typów i typów elementów członkowskich

W Projektancie klas można zmienić nazwę typu lub elementu członkowskiego typu na diagramie klasy lub w oknie **Właściwości.** W oknie **Szczegóły klasy** można zmienić nazwę elementu członkowskiego, ale nie typ. Zmiana nazwy typu lub typu elementu członkowskiego propaguje do wszystkich okien i lokalizacji kodu, w których pojawiła się stara nazwa.

### <a name="rename-in-the-class-designer"></a>Zmiana nazwy w Projektancie klas

1. Na diagramie klas wybierz typ lub element członkowski i wybierz nazwę.

     Nazwa członka staje się edytowalna.

2. Wpisz nową nazwę typu lub elementu członkowskiego typu

### <a name="rename-in-the-class-details-window"></a>Zmiana nazwy w oknie Szczegóły klasy

1. Aby wyświetlić okno **Szczegóły klasy,** kliknij prawym przyciskiem myszy element członkowski typu lub typu i wybierz polecenie **Szczegóły klasy**.

     Zostanie wyświetlene okno **Szczegóły klasy.**

2. W kolumnie **Nazwa** zmień nazwę elementu członkowskiego typu

3. Aby odsunąć fokus od komórki, naciśnij klawisz **Enter** lub kliknij od niej.

    > [!NOTE]
    > W oknie **Szczegóły klasy** można zmienić nazwę elementu członkowskiego, ale nie typ.

### <a name="rename-in-the-properties-window"></a>Zmiana nazwy w oknie Właściwości

1. Na diagramie klasy lub w oknie **Szczegóły klasy** kliknij prawym przyciskiem myszy typ lub element członkowski, a następnie wybierz polecenie **Właściwości**.

     Zostanie **wyświetlone** okno Właściwości i zostanie wyświetlone właściwości typu lub elementu członkowskiego typu.

2. We właściwości **Name** zmień nazwę typu lub typu elementu członkowskiego.

     Nowa nazwa jest propagowane do wszystkich okien i lokalizacji kodu w bieżącym projekcie, w którym pojawiła się stara nazwa.

## <a name="move-type-members-from-one-type-to-another"></a>Przenoszenie elementów członkowskich typu z jednego typu na inny

Za pomocą **projektanta klas**można przenieść element członkowski typu z jednego typu do innego typu. Oba typy muszą być widoczne na bieżącym diagramie klasy.

1. W typie widocznym na powierzchni projektowej kliknij prawym przyciskiem myszy element członkowski, który chcesz przenieść do innego typu, a następnie wybierz polecenie **Wytnij**.

2. Kliknij prawym przyciskiem myszy typ miejsca docelowego i wybierz polecenie **Wklej**.

     Właściwość jest usuwany z typu źródłowego i pojawia się w typie docelowym.

## <a name="see-also"></a>Zobacz też

- [Projektowanie klas i typów](designing-and-viewing-classes-and-types.md)
