---
title: 'Instrukcje: Zmień rozmiar kontrolek NamedRange'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 80a7fd251d525541b6894c757d7acd148900047c
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252052"
---
# <a name="how-to-resize-namedrange-controls"></a>Instrukcje: Zmień rozmiar kontrolek NamedRange
  Możesz ustawić rozmiar <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki, gdy dodasz ją Microsoft Office do dokumentu programu Microsoft Excel. można jednak zmienić jego rozmiar w późniejszym czasie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Można zmienić rozmiar nazwanego zakresu w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Możesz również zmienić rozmiar nazwanych zakresów w czasie wykonywania w dodatkach VSTO na poziomie aplikacji.

 W tym temacie opisano następujące zadania:

- [Zmiana rozmiaru kontrolek NamedRange w czasie projektowania](#designtime)

- [Zmiana rozmiaru kontrolek NamedRange w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Zmiana rozmiaru kontrolek NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

## <a name="designtime"></a>Zmiana rozmiaru kontrolek NamedRange w czasie projektowania
 Można zmienić rozmiar nazwanego zakresu przez ponowne zdefiniowanie jego rozmiaru w oknie dialogowym **Definiowanie nazwy** .

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Aby zmienić rozmiar nazwanego zakresu przy użyciu okna dialogowego Definiowanie nazwy

1. Kliknij prawym przyciskiem <xref:Microsoft.Office.Tools.Excel.NamedRange> myszy formant.

2. Kliknij pozycję **Zarządzaj nazwanymi zakresami** w menu skrótów.

     Zostanie wyświetlone okno dialogowe **Definiowanie nazwy** .

3. Wybierz nazwany zakres, którego rozmiar chcesz zmienić.

4. Usuń zaznaczenie pola **odwołuje się do** .

5. Zaznacz komórki, których chcesz użyć do zdefiniowania rozmiaru nazwanego zakresu.

6. Kliknij przycisk **OK**.

## <a name="runtimedoclevel"></a>Zmiana rozmiaru kontrolek NamedRange w czasie wykonywania w projekcie na poziomie dokumentu
 Można zmienić rozmiar nazwanego zakresu programowo przy użyciu <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> właściwości.

> [!NOTE]
> W <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> oknie **Właściwości** właściwość jest oznaczona jako tylko do odczytu.

### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwanego zakresu

1. Utwórz kontrolkę w komórce **a1** `Sheet1`. <xref:Microsoft.Office.Tools.Excel.NamedRange>

     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]

2. Zmień rozmiar nazwanego zakresu, aby uwzględnić komórkę **B1**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]

## <a name="runtimeaddin"></a>Zmiana rozmiaru kontrolek NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Można zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w dowolnym otwartym arkuszu w czasie wykonywania. Aby uzyskać więcej informacji na temat dodawania <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki do arkusza przy użyciu dodatku VSTO, zobacz [How to: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwanego zakresu

1. Utwórz kontrolkę w komórce **a1** `Sheet1`. <xref:Microsoft.Office.Tools.Excel.NamedRange>

     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]

2. Zmień rozmiar nazwanego zakresu, aby uwzględnić komórkę **B1**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]

## <a name="see-also"></a>Zobacz także
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Instrukcje: Zmień rozmiar kontrolek zakładek](../vsto/how-to-resize-bookmark-controls.md)
- [Instrukcje: Zmień rozmiar formantów ListObject](../vsto/how-to-resize-listobject-controls.md)
