---
title: 'Instrukcje: Zmień rozmiar formantów ListObject'
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
ms.openlocfilehash: d7dac99088dc57b538f7a26ffbd0bdc0e3e05b5a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252128"
---
# <a name="how-to-resize-listobject-controls"></a>Porady: Zmień rozmiar formantów ListObject
  Można ustawić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki, gdy dodasz ją do Microsoft Office skoroszytu programu Excel. można jednak zmienić jej rozmiar w późniejszym czasie. Na przykład możesz chcieć zmienić listę dwóch kolumn na trzy kolumny.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Można zmieniać rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Można zmieniać rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek w czasie wykonywania w projekcie dodatku VSTO.

 W tym temacie opisano następujące zadania:

- [Zmień rozmiar formantów ListObject w czasie projektowania](#designtime)

- [Zmień rozmiar formantów ListObject w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Zmiana rozmiaru formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji <xref:Microsoft.Office.Tools.Excel.ListObject> na temat kontrolek, zobacz [ListObject Control](../vsto/listobject-control.md).

  ![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby zapoznać się z pokrewną [prezentacją wideo, zobacz Jak mogę: Czy dodać kolumny do obiektu listy powiązanego z danymi w czasie wykonywania? ](http://go.microsoft.com/fwlink/?LinkID=130318).

## <a name="designtime"></a>Zmień rozmiar kontrolki ListObject w czasie projektowania
 Aby zmienić rozmiar listy, można kliknąć i przeciągnąć jeden z uchwytów zmiany rozmiaru lub zmienić jego rozmiar w oknie dialogowym **Zmień rozmiar listy** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Aby zmienić rozmiar listy przy użyciu okna dialogowego Zmienianie rozmiaru listy

1. Kliknij gdziekolwiek w <xref:Microsoft.Office.Tools.Excel.ListObject> tabeli. Zostanie wyświetlona karta**projektowanie** **narzędzi** > tabel na Wstążce.

2. W sekcji Właściwości kliknij pozycję **Zmień rozmiar tabeli**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Wybierz nowy zakres danych dla tabeli.

4. Kliknij przycisk **OK**.

## <a name="runtimedoclevel"></a>Zmień rozmiar kontrolki ListObject w czasie wykonywania w projekcie na poziomie dokumentu
 Można zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki w czasie wykonywania przy <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> użyciu metody. Nie można użyć tej metody, aby przenieść <xref:Microsoft.Office.Tools.Excel.ListObject> formant do nowej lokalizacji w arkuszu. Nagłówki muszą pozostać w tym samym wierszu, a <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolka o zmienionym rozmiarze musi nakładać się na oryginalny obiekt listy. <xref:Microsoft.Office.Tools.Excel.ListObject> Kontrolka o zmienionym rozmiarze musi zawierać wiersz nagłówka i co najmniej jeden wiersz danych.

### <a name="to-resize-a-list-object-programmatically"></a>Aby programowo zmienić rozmiar obiektu listy

1. Utwórz kontrolkę obejmującą komórki **a1** do **B3** na `Sheet1`. <xref:Microsoft.Office.Tools.Excel.ListObject>

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Zmień rozmiar listy tak, aby obejmowała komórki **a1** do **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="runtimeaddin"></a>Zmiana rozmiaru listy w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Można zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki w dowolnym otwartym arkuszu w czasie wykonywania. Aby uzyskać więcej informacji na temat dodawania <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki do arkusza przy użyciu dodatku VSTO, zobacz [How to: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Aby programowo zmienić rozmiar obiektu listy

1. Utwórz kontrolkę obejmującą komórki **a1** do **B3** na `Sheet1`. <xref:Microsoft.Office.Tools.Excel.ListObject>

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Zmień rozmiar listy tak, aby obejmowała komórki **a1** do **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Zobacz także
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject — formant](../vsto/listobject-control.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: Zmień rozmiar kontrolek zakładek](../vsto/how-to-resize-bookmark-controls.md)
- [Instrukcje: Zmień rozmiar kontrolek NamedRange](../vsto/how-to-resize-namedrange-controls.md)
