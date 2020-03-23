---
title: Zmiana między notacją skojarzenia & elementami członkowskimi (Projektant klas)
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592272"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Jak: Zmiana notacji elementu członkowskiego i notacji skojarzenia w Projektancie klas

W **Projektancie klas**można zmienić sposób, w jaki diagram klasy reprezentuje relację skojarzenia między dwoma typami, od notacji elementu członkowskiego do notacji skojarzenia i odwrotnie. Elementy członkowskie wyświetlane jako linie skojarzenia często zapewniają użyteczną wizualizację sposobu powiązanych typów.

> [!NOTE]
> Relacje skojarzeń mogą być reprezentowane jako właściwość lub pole członkowskie. Aby zmienić notację elementu członkowskiego na notację skojarzenia, jeden typ musi mieć element członkowski innego typu. Aby zmienić notację skojarzenia na notację elementu członkowskiego, oba typy muszą być połączone linią skojarzenia. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie skojarzeń bBetween typów](how-to-create-associations-between-types.md). Jeśli projekt zawiera wiele diagramów klas, zmiany wprowadzone w sposób diagramu wyświetla relacje skojarzenia wpływ tylko na ten diagram. Aby zmienić sposób, w jaki inny diagram wyświetla relacje skojarzeń, otwórz lub wyświetl ten diagram i wykonaj te kroki.

## <a name="to-change-member-notation-to-association-notation"></a>Aby zmienić notację elementu członkowskiego na notację skojarzenia

1. W węźle projektu w Eksploratorze rozwiązań otwórz plik diagramu klasy (cd).

2. W kształcie typu na diagramie klasy kliknij prawym przyciskiem myszy właściwość lub pole członkowskie reprezentujące skojarzenie, a następnie wybierz polecenie **Pokaż jako skojarzenie**.

    > [!TIP]
    > Jeśli w kształcie tekstu nie są widoczne żadne właściwości lub pola, przedziały w kształcie mogą być zwinięte. Aby rozwinąć kształt tekstu, kliknij dwukrotnie nazwę przedziału lub kliknij kształt tekstu prawym przyciskiem myszy, a następnie wybierz polecenie **Rozwiń**.

    Element członkowski znika z przedziału w kształcie typu i pojawi się linia skojarzenia, aby połączyć dwa typy. Wiersz skojarzenia jest oznaczony nazwą właściwości lub pola.

## <a name="to-change-association-notation-to-member-notation"></a>Aby zmienić notację skojarzenia na notację elementu członkowskiego

Na diagramie klas kliknij prawym przyciskiem myszy wiersz skojarzenia i wybierz polecenie **Pokaż jako właściwość** lub **Pokaż jako pole.** Linia skojarzenia znika, a właściwość jest wyświetlana w odpowiednim przedziale w kształcie typu na diagramie.

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Jak: Wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
- [Jak: Wizualizacja skojarzenia kolekcji](how-to-visualize-a-collection-association.md)
