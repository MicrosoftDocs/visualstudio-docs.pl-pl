---
title: 'Instrukcje: Zmienianie rozmiaru formantów ListObject'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 68a9841d8471189538959a311bf9349199d55f78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545837"
---
# <a name="how-to-resize-listobject-controls"></a>Instrukcje: Zmienianie rozmiaru formantów ListObject
  Można ustawić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki, gdy dodasz ją do Microsoft Office skoroszytu programu Excel. można jednak zmienić jej rozmiar w późniejszym czasie. Na przykład możesz chcieć zmienić listę dwóch kolumn na trzy kolumny.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Można zmieniać rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Można zmieniać rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek w czasie wykonywania w projekcie dodatku VSTO.

 W tym temacie opisano następujące zadania:

- [Zmień rozmiar formantów ListObject w czasie projektowania](#designtime)

- [Zmień rozmiar formantów ListObject w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Zmiana rozmiaru formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek, zobacz [ListObject Control](../vsto/listobject-control.md).

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Zmień rozmiar kontrolki ListObject w czasie projektowania
 Aby zmienić rozmiar listy, można kliknąć i przeciągnąć jeden z uchwytów zmiany rozmiaru lub zmienić jego rozmiar w oknie dialogowym **Zmień rozmiar listy** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Aby zmienić rozmiar listy przy użyciu okna dialogowego Zmienianie rozmiaru listy

1. Kliknij gdziekolwiek w  <xref:Microsoft.Office.Tools.Excel.ListObject> tabeli. **Table Tools**  >  Zostanie wyświetlona karta**projektowanie** narzędzi tabel na Wstążce.

2. W sekcji Właściwości kliknij pozycję **Zmień rozmiar tabeli**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Wybierz nowy zakres danych dla tabeli.

4. Kliknij przycisk **OK**.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Zmień rozmiar kontrolki ListObject w czasie wykonywania w projekcie na poziomie dokumentu
 Można zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki w czasie wykonywania przy użyciu <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> metody. Nie można użyć tej metody, aby przenieść <xref:Microsoft.Office.Tools.Excel.ListObject> formant do nowej lokalizacji w arkuszu. Nagłówki muszą pozostać w tym samym wierszu, a kontrolka o zmienionym rozmiarze <xref:Microsoft.Office.Tools.Excel.ListObject> musi nakładać się na oryginalny obiekt listy. Kontrolka o zmienionym rozmiarze <xref:Microsoft.Office.Tools.Excel.ListObject> musi zawierać wiersz nagłówka i co najmniej jeden wiersz danych.

### <a name="to-resize-a-list-object-programmatically"></a>Aby programowo zmienić rozmiar obiektu listy

1. Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę obejmującą komórki **a1** do **B3** na `Sheet1` .

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Zmień rozmiar listy tak, aby obejmowała komórki **a1** do **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Zmiana rozmiaru listy w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Można zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki w dowolnym otwartym arkuszu w czasie wykonywania. Aby uzyskać więcej informacji na temat dodawania <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki do arkusza przy użyciu dodatku VSTO, zobacz [How to: Add ListObject Controls to arkuszs](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Aby programowo zmienić rozmiar obiektu listy

1. Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę obejmującą komórki **a1** do **B3** na `Sheet1` .

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Zmień rozmiar listy tak, aby obejmowała komórki **a1** do **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Zobacz też
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject — formant](../vsto/listobject-control.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: zmiana rozmiaru kontrolek zakładek](../vsto/how-to-resize-bookmark-controls.md)
- [Instrukcje: zmiana rozmiaru kontrolek NamedRange](../vsto/how-to-resize-namedrange-controls.md)
