---
title: 'Instrukcje: zmiana rozmiaru kontrolek NamedRange'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7762e67b1676f72030cae8d958bef19c501660c3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545824"
---
# <a name="how-to-resize-namedrange-controls"></a>Instrukcje: zmiana rozmiaru kontrolek NamedRange
  Możesz ustawić rozmiar <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki, gdy dodasz ją Microsoft Office do dokumentu programu Microsoft Excel. można jednak zmienić jego rozmiar w późniejszym czasie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Można zmienić rozmiar nazwanego zakresu w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Możesz również zmienić rozmiar nazwanych zakresów w czasie wykonywania w dodatkach VSTO na poziomie aplikacji.

 W tym temacie opisano następujące zadania:

- [Zmiana rozmiaru kontrolek NamedRange w czasie projektowania](#designtime)

- [Zmiana rozmiaru kontrolek NamedRange w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Zmiana rozmiaru kontrolek NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a>Zmiana rozmiaru kontrolek NamedRange w czasie projektowania
 Można zmienić rozmiar nazwanego zakresu przez ponowne zdefiniowanie jego rozmiaru w oknie dialogowym **Definiowanie nazwy** .

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Aby zmienić rozmiar nazwanego zakresu przy użyciu okna dialogowego Definiowanie nazwy

1. Kliknij prawym przyciskiem myszy <xref:Microsoft.Office.Tools.Excel.NamedRange> formant.

2. Kliknij pozycję **Zarządzaj nazwanymi zakresami** w menu skrótów.

     Zostanie wyświetlone okno dialogowe **Definiowanie nazwy** .

3. Wybierz nazwany zakres, którego rozmiar chcesz zmienić.

4. Usuń zaznaczenie pola **odwołuje się do** .

5. Zaznacz komórki, których chcesz użyć do zdefiniowania rozmiaru nazwanego zakresu.

6. Kliknij przycisk **OK**.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a>Zmiana rozmiaru kontrolek NamedRange w czasie wykonywania w projekcie na poziomie dokumentu
 Można zmienić rozmiar nazwanego zakresu programowo przy użyciu <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> właściwości.

> [!NOTE]
> W oknie **Właściwości** <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> Właściwość jest oznaczona jako tylko do odczytu.

### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwanego zakresu

1. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę w komórce **a1** `Sheet1` .

     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]

2. Zmień rozmiar nazwanego zakresu, aby uwzględnić komórkę **B1**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>Zmiana rozmiaru kontrolek NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Można zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w dowolnym otwartym arkuszu w czasie wykonywania. Aby uzyskać więcej informacji na temat dodawania <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki do arkusza przy użyciu dodatku VSTO, zobacz [How to: Add NamedRange Controls to arkuszs](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwanego zakresu

1. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę w komórce **a1** `Sheet1` .

     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]

2. Zmień rozmiar nazwanego zakresu, aby uwzględnić komórkę **B1**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]

## <a name="see-also"></a>Zobacz też
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Instrukcje: zmiana rozmiaru kontrolek zakładek](../vsto/how-to-resize-bookmark-controls.md)
- [Instrukcje: Zmienianie rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)
