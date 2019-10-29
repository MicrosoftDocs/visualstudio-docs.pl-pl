---
title: 'Instrukcje: dostosowywanie wbudowanej karty'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3550c3bd48a02d5daf4ef7156960e8a8fab3b93a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985944"
---
# <a name="how-to-customize-a-built-in-tab"></a>Instrukcje: dostosowywanie wbudowanej karty
  Do wbudowanej karty można dodać grupy i kontrolki. Karta wbudowana to karta, która znajduje się już na Wstążce aplikacji Microsoft Office. Na przykład karta **dane** jest wbudowaną kartą w programie Excel. Po utworzeniu grupy niestandardowej pojawia się ona jako Ostatnia na karcie, ale można ją przenieść w dowolnym miejscu na karcie.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Można dodać grupy do wbudowanej karty, ale nie można usunąć wbudowanych grup z wbudowanej karty.

### <a name="to-add-groups-to-a-built-in-tab"></a>Aby dodać grupy do wbudowanej karty

1. Kliknij prawym przyciskiem myszy plik kodu wstążki w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Projektant widoków**.

    > [!NOTE]
    > Jeśli plik kodu wstążki nie pojawia się w **Eksplorator rozwiązań**, należy dodać **element wstążki** do projektu. Zobacz [jak to zrobić: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Kliknij prawym przyciskiem myszy dowolną kartę w Projektancie wstążki, a następnie kliknij polecenie **Właściwości**.

3. W oknie **Właściwości** rozwiń Właściwość **ControlID** , a następnie ustaw właściwość **ControlIdType** na **Office**.

4. Ustaw właściwość **OfficeId** na *Identyfikator formantu* wbudowanej karty, która ma zostać dostosowana.

     Identyfikator kontrolki to nazwa, która jednoznacznie identyfikuje karty, grupy i kontrolki, które są wbudowane w Microsoft Office aplikacji.

     Aby uzyskać listę identyfikatorów sterowania, zobacz [pliki pomocy pakietu office 2010: identyfikatory formantów interfejsu użytkownika pakietu Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

5. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku**przeciągnij grupy na kartę.

    > [!NOTE]
    > Wbudowane grupy nie są wyświetlane w projektancie. W związku z tym jedynym sposobem ustalenia, czy pracujesz z wbudowaną kartą, jest sprawdzenie właściwości **ControlID** karty.

### <a name="to-position-groups-on-a-built-in-tab"></a>Aby umieścić grupy na karcie wbudowanej

1. W Projektancie wstążki wybierz grupę niestandardową.

2. W oknie **Właściwości** rozwiń Właściwość **Position** .

3. Ustaw właściwość **PositionType** na odpowiednią wartość:

    - **BeforeOfficeId** umieszcza grupę przed określoną grupą wbudowaną.

    - **AfterOfficeId** ustawia grupę po określonej wbudowanej grupie.

4. Ustaw właściwość **OfficeId** na identyfikator formantu wbudowanej grupy.

     Aby uzyskać listę identyfikatorów sterowania, zobacz [pliki pomocy pakietu office 2010: identyfikatory formantów interfejsu użytkownika pakietu Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Zobacz także
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Instrukcje: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Instrukcje: zmiana położenia karty na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Instrukcje: Dodawanie kontrolek do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Instrukcje: pokazywanie błędów interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
