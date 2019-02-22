---
title: 'Instrukcje: Dostosowywanie wbudowanej karty'
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
ms.openlocfilehash: 26f17e863900eb1d1aa6414d28a7de0cee8f3c10
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639547"
---
# <a name="how-to-customize-a-built-in-tab"></a>Instrukcje: Dostosowywanie wbudowanej karty
  Grupy i formanty można dodać do wbudowanej karty. Wbudowana karty to karta, która jest już na Wstążce aplikacji Microsoft Office. Na przykład **danych** karty to karta wbudowana w programie Excel. Podczas tworzenia grup niestandardowych, zostanie wyświetlone ostatnie na karcie, ale można przenieść grupy dowolne miejsce na karcie.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
>  Można dodać grupy do wbudowanej karty, ale nie można usunąć wbudowanych grup z wbudowanej karty.

### <a name="to-add-groups-to-a-built-in-tab"></a>Aby dodać grupy do wbudowanej karty

1.  Kliknij prawym przyciskiem myszy plik kodu wstążki w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Projektant widoków**.

    > [!NOTE]
    >  Jeśli nie ma plik kodu wstążki **Eksploratora rozwiązań**, należy dodać **element wstążki** do projektu. Zobacz [jak: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

2.  Kliknij prawym przyciskiem myszy dowolną kartę w Projektancie wstążki, a następnie kliknij przycisk **właściwości**.

3.  W **właściwości** okna, rozwiń węzeł **ControlId** właściwości, a następnie ustaw **ControlIdType** właściwości **Office**.

4.  Ustaw **OfficeId** właściwości *identyfikator formantu* wbudowane karty, który chcesz dostosować.

     Identyfikator kontrolki to nazwa, która unikatowo identyfikuje karty, grupy i formanty, które są wbudowane w aplikacji Microsoft Office.

     Aby uzyskać listę kontroli identyfikatorów, zobacz [pliki Pomocy pakietu Office 2010: Identyfikatory kontrolki interfejsu użytkownika fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).

5.  Z **formanty wstążki Office** karcie **przybornika**, przeciągnij grupy na karcie.

    > [!NOTE]
    >  Wbudowane grupy nie są wyświetlane w projektancie. W związku z tym, jedynym sposobem ustalenia, czy użytkownik korzysta z wbudowanej karty jest zbadanie **ControlId** właściwości karty.

### <a name="to-position-groups-on-a-built-in-tab"></a>Aby zmienić położenie grupy na karcie wbudowanej

1.  W Projektancie wstążki wybierz grupę niestandardową.

2.  W **właściwości** okna, rozwiń węzeł **pozycji** właściwości.

3.  Ustaw **PositionType** właściwość do odpowiedniej wartości:

    -   **BeforeOfficeId** umieszcza grupy przed określonej grupy wbudowane.

    -   **AfterOfficeId** umieszcza grupy po określonej grupy wbudowane.

4.  Ustaw **OfficeId** właściwości Identyfikator kontrolki wbudowanej grupy.

     Aby uzyskać listę kontroli identyfikatorów, zobacz [pliki Pomocy pakietu Office 2010: Identyfikatory kontrolki interfejsu użytkownika fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).

## <a name="see-also"></a>Zobacz także
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Instrukcje: Zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Instrukcje: Dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Instrukcje: Pokaż błędy interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
