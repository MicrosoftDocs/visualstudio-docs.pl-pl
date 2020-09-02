---
title: Refaktoryzacja klas i typów (Projektant klas) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5803b720ae1271d8319310820d1f0dc159db8bf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670275"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refaktoryzacja klas i typów (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku refaktoryzacji kodu można ułatwić zrozumienie, konserwację i wydajniejsze działanie poprzez zmianę jego wewnętrznej struktury i sposobu, w jaki obiekty są zaprojektowane, a nie z zachowaniem zewnętrznym. Użyj Projektant klas i okna Szczegóły klasy, aby zmniejszyć ilość pracy, którą trzeba wykonać, i szansę wprowadzenia usterek w przypadku refaktoryzacji kodu Visual C# .NET, Visual Basic .NET lub C++ w projekcie programu Visual Studio.

> [!NOTE]
> Pliki projektu mogą być tylko do odczytu, ponieważ projekt znajduje się pod kontrolą kodu źródłowego i nie jest wyewidencjonowany; jest to przywoływany projekt; lub jego pliki są oznaczone jako tylko do odczytu na dysku. Podczas pracy w projekcie w jednym z tych stanów będą prezentowane różne sposoby zapisywania pracy w zależności od stanu projektu. Dotyczy to również kodu refaktoryzacji i kodu, który można zmienić w inny sposób, na przykład jego bezpośredniej edycji. Aby uzyskać więcej informacji, zobacz [Wyświetlanie informacji tylko do odczytu (Projektant klas)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pomocnicza|
|----------|------------------------|
|**Klasy refaktoryzacji:** Operacji refaktoryzacji można użyć do podziału klasy na klasy częściowe lub w celu zaimplementowania abstrakcyjnej klasy bazowej.|-   [Instrukcje: dzielenie klasy na klasy częściowe (Projektant klas)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|
|**Praca z interfejsami:** W Projektant klas można zaimplementować interfejs na diagramie klas, łącząc go z klasą, która dostarcza kod dla metod interfejsu.|-   [Instrukcje: implementowanie interfejsu (Projektant klas)](../ide/how-to-implement-an-interface-class-designer.md)|
|**Typy refaktoryzacji, elementy członkowskie typu i parametry:** Za pomocą Projektant klas można zmienić nazwy typów, zastąpić elementy typu lub przenieść je z jednego typu do drugiego. Można również tworzyć Typy dopuszczające wartości null.|-   [Zmiana nazw typów i składowych typu](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Przeniesienie elementów członkowskich typu z jednego typu do innego](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Instrukcje: Tworzenie typu dopuszczającego wartość null (Projektant klas)](../ide/how-to-create-a-nullable-type-class-designer.md)|

### <a name="renaming-types-and-type-members"></a><a name="RenamingTypesAndMembers"></a> Zmiana nazw typów i składowych typu
 W Projektant klas można zmienić nazwę typu lub elementu członkowskiego typu na diagramie klasy lub w okno Właściwości. W oknie Szczegóły klasy można zmienić nazwę elementu członkowskiego, ale nie typ. Zmiana nazwy typu lub składowej typu jest propagowana do wszystkich okien i lokalizacji kodu, w których pojawiła się stara nazwa.

##### <a name="to-rename-a-name-in-the-class-designer"></a>Aby zmienić nazwę w Projektant klas

1. Na diagramie klasy wybierz typ lub element członkowski, a następnie kliknij nazwę.

     Nazwa elementu członkowskiego można edytować.

2. Wpisz nową nazwę typu lub elementu członkowskiego typu

##### <a name="to-rename-a-name-in-the-class-details-window"></a>Aby zmienić nazwę w Okno szczegółów klasy

1. Aby wyświetlić okno Szczegóły klasy, kliknij prawym przyciskiem myszy typ lub element członkowski typu, a następnie kliknij pozycję **Szczegóły klasy**.

     Zostanie wyświetlone okno Szczegóły klasy.

2. W kolumnie **Nazwa** Zmień nazwę elementu członkowskiego typu

3. Aby przenieść fokus z komórki, naciśnij klawisz **Enter** lub kliknij poza komórką.

    > [!NOTE]
    > W oknie Szczegóły klasy można zmienić nazwę elementu członkowskiego, ale nie typ.

##### <a name="to-rename-a-name-in-the-properties-window"></a>Aby zmienić nazwę w okno Właściwości

1. Na diagramie klasy lub w oknie Szczegóły klasy, kliknij prawym przyciskiem myszy typ lub element członkowski, a następnie kliknij polecenie **Właściwości**.

     Okno Właściwości pojawia się i wyświetla właściwości typu lub elementu członkowskiego typu.

2. W właściwości **name (nazwa** ) Zmień nazwę typu lub składowej typu.

     Nowa nazwa jest propagowana do wszystkich okien i lokalizacji kodu w bieżącym projekcie, w których pojawiła się stara nazwa.

### <a name="moving-type-members-from-one-type-to-another"></a><a name="MovingTypeMembers"></a> Przeniesienie elementów członkowskich typu z jednego typu do innego
 Za pomocą **Projektant klas**, można przenieść składową typu z jednego typu na inny, jeśli oba są widoczne na bieżącym diagramie klas.

##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Aby przenieść element członkowski typu z jednego typu do innego

1. W typie widocznym na powierzchni projektowej kliknij prawym przyciskiem myszy element członkowski, który chcesz przenieść do innego typu, a następnie kliknij pozycję **Wytnij**.

2. Kliknij prawym przyciskiem myszy typ docelowy, a następnie kliknij przycisk **Wklej**.

     Właściwość jest usuwana z typu źródłowego i pojawia się w typie docelowym.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wyświetlanie typów i relacji (Projektant klas)](../ide/viewing-types-and-relationships-class-designer.md)||
|[Projektowanie klas i typów (Projektant klas)](../ide/designing-classes-and-types-class-designer.md)||
