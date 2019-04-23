---
title: 'Instrukcje: Zmiana rozmiaru formantów ListObject'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1ff4080b7b658af5911a0372562954899628bb92
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102682"
---
# <a name="how-to-resize-listobject-controls"></a>Instrukcje: Zmiana rozmiaru formantów ListObject
  Ustaw rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli po dodaniu go do programu Microsoft Office Excel; Jednakże, możesz chcieć zmienić jej rozmiar w późniejszym czasie. Na przykład można zmienić listę dwóch kolumn na trzy kolumny.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> formantów w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> formantów w czasie wykonywania w projekcie dodatku narzędzi VSTO.

 W tym temacie opisano następujące zadania:

- [Zmiana rozmiaru formantów ListObject w czasie projektowania](#designtime)

- [Zmiana rozmiaru formantów ListObject w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Zmiana rozmiaru formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.ListObject> formantów, zobacz [kontrolki ListObject](../vsto/listobject-control.md).

  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Dodawanie kolumn do obiekt listy powiązanych z danymi w czasie wykonywania? ](http://go.microsoft.com/fwlink/?LinkID=130318).

## <a name="designtime"></a> Zmienianie rozmiaru kontrolki ListObject w czasie projektowania
 Aby zmienić rozmiar listy, możesz kliknąć i przeciągnij jeden z uchwytów zmiany rozmiaru lub ponownie zdefiniować jej rozmiar w **Zmień rozmiar listy** okno dialogowe.

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Aby zmienić rozmiar listy za pomocą okna dialogowego Zmiana rozmiaru listy

1. Kliknij w dowolnym miejscu <xref:Microsoft.Office.Tools.Excel.ListObject> tabeli. **Narzędzia tabel** > **projektowania** zostanie wyświetlona karta na Wstążce.

2. W sekcji właściwości kliknij **Zmień rozmiar tabeli**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Wybierz nowy zakres danych w tabeli.

4. Kliknij przycisk **OK**.

## <a name="runtimedoclevel"></a> Zmienianie rozmiaru kontrolki ListObject w czasie wykonywania w projekcie na poziomie dokumentu
 Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> formantu w czasie wykonywania za pomocą <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> metody. Nie można użyć tej metody, aby przenieść <xref:Microsoft.Office.Tools.Excel.ListObject> formantu do nowej lokalizacji w arkuszu. Nagłówki muszą znajdować się w tym samym wierszu, a o zmienionym rozmiarze <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli może się nakładać na oryginalny obiekt listy. Po zmianie rozmiaru <xref:Microsoft.Office.Tools.Excel.ListObject> formant musi zawierać wiersz nagłówka i co najmniej jeden wiersz danych.

### <a name="to-resize-a-list-object-programmatically"></a>Aby zmienić rozmiar obiektu listy programowe

1. Tworzenie <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki, która obejmuje komórki **A1** za pośrednictwem **B3** na `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Zmień rozmiar na liście, aby zawierała komórki **A1** za pośrednictwem **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="runtimeaddin"></a> Zmień rozmiar ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki w dowolnym otwartego arkusza w czasie wykonywania. Aby uzyskać więcej informacji o sposobie dodawania <xref:Microsoft.Office.Tools.Excel.ListObject> sterowania do arkusza za pomocą dodatków narzędzi VSTO dla programów, zobacz [jak: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Aby zmienić rozmiar obiektu listy programowe

1. Tworzenie <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki, która obejmuje komórki **A1** za pośrednictwem **B3** na `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Zmień rozmiar na liście, aby zawierała komórki **A1** za pośrednictwem **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject — formant](../vsto/listobject-control.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: Zmiana rozmiaru formantów zakładki](../vsto/how-to-resize-bookmark-controls.md)
- [Instrukcje: Zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)
