---
title: 'Instrukcje: Dodawanie formantów do widoku Backstage '
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bb038fdebdfefeb5f401860c17b5567028c3bb77
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621347"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Instrukcje: Dodawanie formantów do widoku Backstage
  Można użyć projektanta wstążki, aby dodać formanty do menu otwieranego po kliknięciu **pliku** kartę. Po uruchomieniu aplikacji, formanty, które dodajesz do **pliku** karta pojawi się grupa o nazwie **Add-ins**.

 Nie możesz umieścić formantów przed ani po wbudowanych formantach przy użyciu projektanta wstążki w programie Visual Studio. Wbudowany formant jest formant, który już występuje w widoku Backstage. Jeśli chcesz umieścić formanty przed lub po formantach wbudowanych, należy użyć składni XML wstążki. Aby uzyskać więcej informacji na temat **wstążki (XML)**, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md). Aby uzyskać więcej informacji na temat dostosowywania widoku Backstage, zobacz [wprowadzenie do widoku widoku Backstage programu Office 2010 dla programistów](http://go.microsoft.com/fwlink/?LinkId=182189) i [dostosować widok widoku Backstage programu Office 2010 dla programistów](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Aby dodać formanty do widoku Backstage

1.  Otwórz element wstążki w widoku Projekt.

     Aby uzyskać informacje dotyczące sposobu dodawania **Wstążka (Projektant graficzny)** elementu do projektu, zobacz [jak: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

2.  W Projektancie Wstążki kliknij **pliku** kartę.

     Projektant menu pojawia się. Tę powierzchnię projektu nie zawiera żadnych formantów.

3.  Z **formanty wstążki Office** karcie **przybornika**, przeciągnij dowolny z następujących formantów w Projektancie menu:

    -   Przycisk

    -   CheckBox

    -   Galeria

    -   Menu

    -   Separator

    -   SplitButton

    -   ToggleButton

4.  Przeciągnij formanty, aby przenieść je do nowej pozycji menu.

## <a name="see-also"></a>Zobacz także
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
