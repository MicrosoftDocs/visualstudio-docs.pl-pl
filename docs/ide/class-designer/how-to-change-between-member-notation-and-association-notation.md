---
title: 'Instrukcje: Zmiana między notacją składowych i notacją skojarzeń (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0138ec1e2a36ce20b80982103ec408077502993a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913827"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Instrukcje: Zmiana między notacją składowych i notacją skojarzeń w Projektancie klas

W **projektanta klas**, możesz zmienić sposób diagram klas reprezentuje relacja skojarzenia między dwoma typami z notacją składowych notacją skojarzeń i na odwrót. Składowe wyświetlane jako linie asocjacji często zawierają użyteczne wizualizację jak typy są powiązane.

> [!NOTE]
> Skojarzenie relacji może być reprezentowana jako właściwość składowej lub pola. Aby zmienić notacją składowych notacją skojarzeń, jeden typ musi mieć członkiem innego typu. Aby zmienić notacją skojarzeń notacją składowych, dwa typy muszą być podłączone przez linia skojarzenia. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie skojarzeń typów bBetween](how-to-create-associations-between-types.md). Jeśli projekt zawiera wiele diagramów klas, zmiany wprowadzone w sposób skojarzenia relacje są wyświetlane na diagramie wpływa na tylko tego diagramu. Aby zmienić sposób innego diagramu zawiera relacje skojarzenia, Otwórz lub wyświetlania tego diagramu i wykonaj następujące kroki.

## <a name="to-change-member-notation-to-association-notation"></a>Aby zmienić notacją składowych i notacją skojarzeń

1.  W węźle projektu w Eksploratorze rozwiązań Otwórz plik diagramu klasy (.cd).

2.  Typ kształtu na diagramie klas, kliknij prawym przyciskiem myszy właściwość element członkowski lub pole reprezentujący skojarzenie, a następnie wybierz **wyświetlić jako skojarzenie**.

    > [!TIP]
    > Jeśli nie właściwości lub pola są widoczne w kształcie typu, mogą być zwinięte przedziałów w kształcie. Aby rozwinąć kształt typu, kliknij dwukrotnie nazwę przedziału lub kliknij prawym przyciskiem myszy kształt typu, a wybierz **rozwiń**.

    Element członkowski znika z przedziału w kształcie typu, a linia skojarzenia pojawi się połączyć z dwóch typów. Linia skojarzenia ma etykietę o nazwie właściwości lub pola.

## <a name="to-change-association-notation-to-member-notation"></a>Aby zmienić notacją skojarzeń notacją składowych

Na diagramie klas kliknij prawym przyciskiem myszy linia skojarzenia, a następnie wybierz **Pokaż jako właściwość** lub **Pokaż jako pole** odpowiednio. Linia asocjacji znika, i właściwość pojawią się w odpowiednich przedziału w ramach jego kształt typu na diagramie.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Instrukcje: Wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
- [Instrukcje: Wizualizacja skojarzenia kolekcji](how-to-visualize-a-collection-association.md)