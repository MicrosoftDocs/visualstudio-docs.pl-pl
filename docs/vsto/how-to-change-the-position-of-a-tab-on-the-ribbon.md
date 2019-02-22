---
title: 'Instrukcje: Zmiana położenia zakładki na Wstążce'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc628ffd37cd67c080bfd544c77d6189e6eca21a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641108"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Instrukcje: Zmiana położenia zakładki na Wstążce
  Można zmienić kolejność niestandardowych kart na Wstążce za pomocą **Edotor kolekcji zakładek**. Można określić położenie niestandardowych kart przed lub po wbudowanej karcie na Wstążce. Wbudowana karty to karta, która jest już na Wstążce aplikacji Microsoft Office. Na przykład **danych** karty to karta wbudowana w programie Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Aby zmienić kolejność kart na Wstążce

1.  Wybierz plik kodu wstążki (*.vb* lub *.cs* pliku) w **Eksploratora rozwiązań**.

2.  Na **widoku** menu, kliknij przycisk **projektanta**.

3.  Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij przycisk **właściwości**.

4.  W **właściwości** wybierz **karty** właściwości, a następnie kliknij przycisk wielokropka (![przenośnych elipsy projektanta ASP.NET](../sharepoint/media/mwellipsis.gif "przenośnych ASP.NET Projektant elipsy")).

     **Edotor kolekcji zakładek** pojawia się.

5.  W **Edotor kolekcji zakładek**w **członków** listy, wybierz kartę, aby przenieść i kliknij w górę lub strzałkę w dół, aby zmienić kolejność tabulacji.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Aby umieścić na karcie przed lub po wbudowanej karcie na Wstążce

1.  W Projektancie wstążki wybierz kartę niestandardową.

2.  W **właściwości** okna, rozwiń węzeł **ControlId** właściwości, a następnie upewnij się, że wartość **ControlIdType** właściwość jest ustawiona na **niestandardowe**.

3.  W **właściwości** okna, rozwiń węzeł **pozycji** właściwości.

4.  Ustaw **PositionType** właściwość do odpowiedniej wartości:

    -   **BeforeOfficeId** umieszcza grupy przed określonym wbudowanej karty.

    -   **AfterOfficeId** umieszcza grupy po określonym wbudowanej karty.

5.  Ustaw **OfficeId** właściwości Identyfikator kontrolki wbudowanej karty.

     Aby uzyskać listę kontroli identyfikatorów, zobacz [pliki Pomocy pakietu Office 2010: Identyfikatory kontrolki interfejsu użytkownika fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).

## <a name="see-also"></a>Zobacz także
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
