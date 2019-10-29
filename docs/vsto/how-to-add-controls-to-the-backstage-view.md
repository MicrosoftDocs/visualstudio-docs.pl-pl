---
title: 'Instrukcje: Dodawanie kontrolek do widoku Backstage '
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
ms.openlocfilehash: 87cea877928baf52b0442ed9b0d952fcf649f155
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986009"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Instrukcje: Dodawanie kontrolek do widoku Backstage
  Za pomocą projektanta wstążki można dodać kontrolki do menu, które otwiera się po kliknięciu karty **plik** . Po uruchomieniu aplikacji, kontrolki dodawane do karty **plik** wyświetlają grupę o nazwie **Dodatki**.

 Nie można umieścić kontrolek przed ani po wbudowanych kontrolkach przy użyciu projektanta wstążki w programie Visual Studio. Wbudowana kontrolka to formant, który jest już wyświetlany w widoku Backstage. Jeśli chcesz umieścić formanty przed lub po wbudowanych kontrolkach, musisz użyć kodu XML wstążki. Aby uzyskać więcej informacji na temat **wstążki (XML)** , zobacz [kod XML wstążki](../vsto/ribbon-xml.md). Aby uzyskać więcej informacji na temat dostosowywania widoku Backstage, zobacz [wprowadzenie do widoku Backstage pakietu office 2010 dla deweloperów](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) i [Dostosuj widok backstage pakietu Office 2010 dla deweloperów](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Aby dodać formanty do widoku Backstage

1. Otwórz element wstążki w widok Projekt.

     Aby dowiedzieć się, jak dodać element **wstążki (projektant graficzny)** do projektu, zobacz [How to: wprowadzenie dostosowywanie wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. W Projektancie wstążki kliknij kartę **plik** .

     Zostanie wyświetlony Projektant menu. Ta powierzchnia projektowa nie zawiera żadnych kontrolek.

3. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku**Przeciągnij dowolną z następujących kontrolek do projektanta menu:

    - Przycisk

    - CheckBox

    - Galeria

    - Menu

    - Separator

    - SplitButton

    - ToggleButton

4. Przeciągnij kontrolki, aby przenieść je do nowych pozycji w menu.

## <a name="see-also"></a>Zobacz także
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Instrukcje: wprowadzenie dostosowywanie wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
