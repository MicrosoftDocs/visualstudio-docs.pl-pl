---
title: Zmiana między notacją skojarzenia & elementu członkowskiego (Projektant klas)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f706acfbaee7c6170f74bc655f9172ff6bdd3b4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592272"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Instrukcje: zmiana między notacją składowej i notacją skojarzenia w Projektant klas

W **Projektant klas**można zmienić sposób, w jaki Diagram klas reprezentuje relację skojarzenia między dwoma typami z notacji elementu członkowskiego i odwrotnie. Elementy członkowskie wyświetlane jako linie kojarzenia często zapewniają przydatną wizualizację sposobu, w jaki są powiązane typy.

> [!NOTE]
> Relacje skojarzenia mogą być reprezentowane jako właściwość lub pole elementu członkowskiego. Aby zmienić notację elementu członkowskiego na notację skojarzenia, jeden typ musi mieć element członkowski innego typu. Aby zmienić notację skojarzenia na notację elementu członkowskiego, dwa typy muszą być połączone przez linię skojarzenia. Aby uzyskać więcej informacji, zobacz [How to: Create Association bBetween Types](how-to-create-associations-between-types.md). Jeśli projekt zawiera wiele diagramów klas, zmiany wprowadzane do sposobu wyświetlania relacji skojarzenia mają wpływ tylko na ten diagram. Aby zmienić sposób wyświetlania relacji skojarzenia przez inny diagram, Otwórz lub Wyświetl ten diagram i wykonaj te kroki.

## <a name="to-change-member-notation-to-association-notation"></a>Aby zmienić notację elementu członkowskiego na notację skojarzenia

1. W węźle projektu w Eksplorator rozwiązań otwórz plik diagramu klas (. CD).

2. W kształcie typ na diagramie klas kliknij prawym przyciskiem myszy właściwość elementu członkowskiego lub pole reprezentujące skojarzenie, a następnie wybierz polecenie **Pokaż jako skojarzenie**.

    > [!TIP]
    > Jeśli w kształcie typu nie są widoczne żadne właściwości ani pola, przedziały w kształcie mogą być zwinięte. Aby rozwinąć kształt typu, kliknij dwukrotnie nazwę przedziału lub kliknij prawym przyciskiem myszy kształt typ, a następnie wybierz **Rozwiń**.

    Element członkowski znika z przedziału w kształcie typu, a linia skojarzenia zostanie wyświetlona, aby połączyć dwa typy. Wiersz skojarzenia jest oznaczony nazwą właściwości lub pola.

## <a name="to-change-association-notation-to-member-notation"></a>Aby zmienić notację skojarzenia z notacją składowej

Na diagramie klas kliknij prawym przyciskiem myszy linię skojarzenia, a następnie wybierz polecenie **Pokaż jako właściwość** lub **Pokaż jako odpowiednie pole** . Wiersz skojarzenia znika, a właściwość jest wyświetlana w odpowiednim przedziale w obrębie kształtu typ na diagramie.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Instrukcje: wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
- [Instrukcje: wizualizacja skojarzenia kolekcji](how-to-visualize-a-collection-association.md)
