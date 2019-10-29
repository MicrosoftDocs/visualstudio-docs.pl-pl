---
title: 'Instrukcje: zmiana położenia karty na Wstążce'
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
ms.openlocfilehash: bf943f9df4499b30e294e4d7e8bf48b25aa52eab
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985986"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Instrukcje: zmiana położenia karty na Wstążce
  Można zmienić kolejność kart niestandardowych na Wstążce przy użyciu **edytora kolekcji kart**. Możesz umieścić karty niestandardowe przed lub po karcie wbudowanej na Wstążce. Karta wbudowana to karta, która znajduje się już na Wstążce aplikacji Microsoft Office. Na przykład karta **dane** jest wbudowaną kartą w programie Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Aby zmienić kolejność kart na Wstążce

1. Wybierz plik kodu wstążki (plik*VB* lub *cs* ) w **Eksplorator rozwiązań**.

2. W menu **Widok** kliknij pozycję **Projektant**.

3. Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij polecenie **Właściwości**.

4. W oknie **Właściwości** wybierz właściwość **tabulatory** , a następnie kliknij przycisk wielokropka (![ASP.net Mobile Designer Elipsa](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")).

     Zostanie wyświetlony **Edytor kolekcji kart** .

5. W **edytorze kolekcji kart**na liście **Członkowie** wybierz kartę, którą chcesz przenieść, a następnie kliknij strzałkę w górę lub w dół, aby zmienić kolejność tabulacji.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Aby umieścić kartę przed lub po karcie wbudowanej na Wstążce

1. W Projektancie wstążki wybierz kartę niestandardową.

2. W oknie **Właściwości** rozwiń Właściwość **ControlID** , a następnie upewnij się, że właściwość **ControlIdType** ma wartość **Custom**.

3. W oknie **Właściwości** rozwiń Właściwość **Position** .

4. Ustaw właściwość **PositionType** na odpowiednią wartość:

    - **BeforeOfficeId** umieszcza grupę przed określoną wbudowaną kartą.

    - **AfterOfficeId** ustawia grupę po określonej wbudowanej karcie.

5. Ustaw właściwość **OfficeId** na identyfikator formantu wbudowanej karty.

     Aby uzyskać listę identyfikatorów sterowania, zobacz [pliki pomocy pakietu office 2010: identyfikatory formantów interfejsu użytkownika pakietu Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Zobacz także
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
