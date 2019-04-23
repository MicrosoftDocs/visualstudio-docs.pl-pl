---
title: 'Instrukcje: Implementowanie interfejsu (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e76aeea4c6779e97d882705e8680cd7a3b00d129
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087274"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Instrukcje: Implementowanie interfejsu w Projektancie klas

W **projektanta klas**, można zaimplementować interfejsu na diagramie klas łącząc je do klasy, która zawiera kod dla metody interfejsu. **Projektant klasy** generuje implementację interfejsu i wyświetla relacji między interfejsem i klasy relacji dziedziczenia. Można zaimplementować interfejs, za pomocą rysowania linii dziedziczenia między interfejsem i klasy lub przeciągnąć interfejs z widoku klasy.

> [!TIP]
> Można utworzyć taki sam sposób utworzyć inne typy interfejsów. Jeśli interfejs istnieje, ale nie jest wyświetlane na diagramie klasy, następnie najpierw wyświetlamy go. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie typów za pomocą projektanta klas](how-to-create-types.md) i [jak: Wyświetlanie istniejących typów](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Aby zaimplementować interfejs, za pomocą rysowania linię dziedziczenia

1. Na diagramie klas wyświetlić interfejs i klasa, która będzie implementować interfejs.

2. Rysuj linię dziedziczenia z klasy i interfejsu.

     Lizak pojawia się dołączony do klasy i etykietę o nazwie interfejsu identyfikuje relacji dziedziczenia. Program Visual Studio generuje namiastki dla wszystkich członków interfejsu.

Aby uzyskać więcej informacji, zobacz [jak: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Aby zaimplementować interfejs w oknie widoku klas

1. Na diagramie klasy można wyświetlić klasę, która ma zostać zaimplementowany interfejs.

2. Otwórz **Widok klas** i Znajdź interfejsu.

    > [!TIP]
    > Jeśli **Widok klas** nie jest otwarty, otwórz **Widok klas** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Shift** + **C**.

3. Przeciągnij węzeł interfejsu klasa kształt na diagramie.

     Lizak pojawia się dołączony do klasy i etykietę o nazwie interfejsu identyfikuje relacji dziedziczenia. Program Visual Studio generuje namiastki dla wszystkich członków interfejsu; w tym momencie interfejs jest implementowany.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie typów za pomocą Projektanta klas](how-to-create-types.md)
- [Instrukcje: Wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Instrukcje: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Refaktoryzacja klas i typów](refactoring-classes-and-types.md)