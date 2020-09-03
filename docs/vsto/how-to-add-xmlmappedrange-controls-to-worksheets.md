---
title: 'Instrukcje: Dodawanie kontrolek XMLMappedRange do arkuszy'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1d69e705e8f537ba3636422ad6883a7633e03322
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544888"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Instrukcje: Dodawanie kontrolek XMLMappedRange do arkuszy
  Po zmapowaniu elementu XML do komórki w Microsoft Office Excel program Visual Studio automatycznie dodaje <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontrolkę do arkusza.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Kontrolka jest niedostępna w **przyborniku** lub oknie **źródła danych** . Ponadto nie można programowo tworzyć <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontrolek.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Aby dodać formant XMLMappedRange do arkusza

1. Otwórz skoroszyt programu Excel w projektancie programu Visual Studio.

2. Otwórz arkusz, w którym chcesz dodać formant.

3. Na karcie **deweloper** kliknij pozycję **Źródło**.

    > [!NOTE]
    > Jeśli na Wstążce nie jest widoczna karta **deweloper** , należy ją włączyć. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Zostanie wyświetlone okienko zadania **Źródło XML** .

4. W okienku zadania **Źródło XML** kliknij pozycję **mapy XML**.

5. W oknie dialogowym **mapy XML** kliknij przycisk **Dodaj**.

     Zostanie wyświetlone okno dialogowe **Źródło XML** .

6. Wybierz schemat XML ze **źródła XML** okno dialogowe i kliknij przycisk **Otwórz**.

     Schemat zostanie dodany do okna dialogowego **mapy XML** .

7. W oknie dialogowym **mapy XML** kliknij przycisk **OK**.

8. Przeciągnij element ze źródłowego okienka zadań **XML** do komórki w arkuszu.

     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Zostanie utworzony i dodany do projektu.

    > [!NOTE]
    > Jeśli przeciągniesz element nadrzędny z okienka zadań **Źródło XML** , <xref:Microsoft.Office.Tools.Excel.ListObject> zostanie utworzony formant.

## <a name="see-also"></a>Zobacz też
- [XmlMappedRange — formant](../vsto/xmlmappedrange-control.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Instrukcje: mapowanie schematów do arkuszy w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
