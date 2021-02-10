---
title: 'Instrukcje: Dodawanie kontrolek XMLMappedRange do arkuszy'
description: Dowiedz się, że podczas mapowania elementu XML do komórki w Microsoft Office Excel program Visual Studio automatycznie doda do arkusza formant XmlMappedRange.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 065a904047630d15a8e9ed167a6a4a2764858387
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970325"
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
