---
title: 'Instrukcje: zmiana między notacją składowej i notacją skojarzenia (Projektant klas) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6a9a15b7284c647cb115c34b5655bdcaa7402ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663567"
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Porady: zmiana pomiędzy notacją członka i skojarzeniem notacji (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W Projektant klas można zmienić sposób, w jaki Diagram klas reprezentuje relację skojarzenia między dwoma typami z notacji elementu członkowskiego i odwrotnie. Elementy członkowskie wyświetlane jako linie kojarzenia często zapewniają przydatną wizualizację sposobu, w jaki są powiązane typy.

> [!NOTE]
> Relacje skojarzenia mogą być reprezentowane jako właściwość lub pole elementu członkowskiego. Aby zmienić notację elementu członkowskiego na notację skojarzenia, jeden typ musi mieć element członkowski innego typu. Aby zmienić notację skojarzenia na notację elementu członkowskiego, dwa typy muszą być połączone przez linię skojarzenia. Aby uzyskać więcej informacji, zobacz [jak: tworzenie skojarzeń między typami (Projektant klas)](../ide/how-to-create-associations-between-types-class-designer.md). Jeśli projekt zawiera wiele diagramów klas, zmiany wprowadzane do sposobu wyświetlania relacji skojarzenia mają wpływ tylko na ten diagram. Aby zmienić sposób wyświetlania relacji skojarzenia przez inny diagram, Otwórz lub Wyświetl ten diagram i wykonaj te kroki.

### <a name="to-change-member-notation-to-association-notation"></a>Aby zmienić notację elementu członkowskiego na notację skojarzenia

1. W węźle projektu w Eksplorator rozwiązań otwórz plik diagramu klas (. CD).

2. W kształcie typ na diagramie klas kliknij prawym przyciskiem myszy właściwość elementu członkowskiego lub pole reprezentujące skojarzenie, a następnie wybierz polecenie **Pokaż jako skojarzenie**.

    > [!TIP]
    > Jeśli w kształcie typu nie są widoczne żadne właściwości ani pola, przedziały w kształcie mogą być zwinięte. Aby rozwinąć kształt typu, kliknij dwukrotnie nazwę przedziału lub kliknij prawym przyciskiem myszy kształt typ, a następnie wybierz **Rozwiń**.

     Element członkowski znika z przedziału w kształcie typu, a linia skojarzenia zostanie wyświetlona, aby połączyć dwa typy. Wiersz skojarzenia jest oznaczony nazwą właściwości lub pola.

### <a name="to-change-association-notation-to-member-notation"></a>Aby zmienić notację skojarzenia z notacją składowej

- Na diagramie klas kliknij prawym przyciskiem myszy linię skojarzenia, a następnie wybierz polecenie **Pokaż jako właściwość** lub **Pokaż jako odpowiednie pole** .

     Wiersz skojarzenia znika, a właściwość jest wyświetlana w odpowiednim przedziale w obrębie kształtu typ na diagramie.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md) [instrukcje: wyświetlanie dziedziczenia między typami (Projektant klas)](../ide/how-to-view-inheritance-between-types-class-designer.md) [wyświetlanie typów i relacji (Projektant klas)](../ide/viewing-types-and-relationships-class-designer.md) [instrukcje: wizualizacja skojarzenia kolekcji (Projektant klas)](../ide/how-to-visualize-a-collection-association-class-designer.md)
