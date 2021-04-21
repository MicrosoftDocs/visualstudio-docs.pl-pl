---
title: 'How to: Resize ListObject controls ( Jak zmienić rozmiar kontrolek ListObject)'
description: Dowiedz się, jak za pomocą Visual Studio programowo zmienić rozmiar kontrolek ListObject w skoroszycie programu Microsoft Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a2fd0b8ce46ba15066ab4cf070807e2457c21e70
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828959"
---
# <a name="how-to-resize-listobject-controls"></a>How to: Resize ListObject controls ( Jak zmienić rozmiar kontrolek ListObject)
  Rozmiar kontrolki można ustawić podczas dodawania jej do skoroszytu programu Excel Microsoft Office, ale możesz zmienić jej rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> w późniejszym czasie. Na przykład możesz zmienić listę dwu kolumnową na trzy kolumny.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Rozmiar kontrolek <xref:Microsoft.Office.Tools.Excel.ListObject> można zmieniać w czasie projektowania lub w czasie uruchamiania w projektach na poziomie dokumentu. Kontrolki można <xref:Microsoft.Office.Tools.Excel.ListObject> zmieniać w czasie uruchamiania w projekcie dodatku VSTO.

 W tym temacie opisano następujące zadania:

- [Zmienianie rozmiaru kontrolek ListObject w czasie projektowania](#designtime)

- [Zmienianie rozmiaru kontrolek ListObject w czasie uruchamiania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Zmienianie rozmiaru kontrolek ListObject w czasie uruchamiania w projekcie dodatku VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na <xref:Microsoft.Office.Tools.Excel.ListObject> temat kontrolek, zobacz [ListObject, kontrolka](../vsto/listobject-control.md).

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Zmienianie rozmiaru kontrolki ListObject w czasie projektowania
 Aby zmienić rozmiar listy, możesz kliknąć i przeciągnąć jeden z uchwytów zmiany rozmiaru lub ponownie zdefiniować jej rozmiar w oknie **dialogowym Zmienianie** rozmiaru listy.

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Aby zmienić rozmiar listy przy użyciu okna dialogowego Zmienianie rozmiaru listy

1. Kliknij dowolne miejsce w  <xref:Microsoft.Office.Tools.Excel.ListObject> tabeli. Zostanie **wyświetlona**  >  **karta Projektowanie narzędzi** tabel na wstążce.

2. W sekcji Właściwości kliknij pozycję Zmień **rozmiar tabeli.**

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Wybierz nowy zakres danych dla tabeli.

4. Kliknij przycisk **OK**.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Zmienianie rozmiaru kontrolki ListObject w czasie uruchamiania w projekcie na poziomie dokumentu
 Rozmiar kontrolki <xref:Microsoft.Office.Tools.Excel.ListObject> można zmienić w czasie działania przy użyciu metody <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Tej metody nie można użyć do przeniesienia <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki do nowej lokalizacji w arkuszu. Nagłówki muszą pozostać w tym samym wierszu, a kontrolka o zmienionym rozmiarze <xref:Microsoft.Office.Tools.Excel.ListObject> musi nakładać się na oryginalny obiekt listy. Kontrolka o <xref:Microsoft.Office.Tools.Excel.ListObject> zmienionym rozmiarze musi zawierać wiersz nagłówka i co najmniej jeden wiersz danych.

### <a name="to-resize-a-list-object-programmatically"></a>Aby programowo zmienić rozmiar obiektu listy

1. Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę, która obejmuje komórkę **od A1** do **B3 na** . `Sheet1`

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet6":::

2. Zmień rozmiar listy, aby zawierała komórki **od A1** do **C5**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Zmienianie rozmiaru projektu ListObject w czasie uruchamiania w projekcie dodatku VSTO
 Rozmiar kontrolki można <xref:Microsoft.Office.Tools.Excel.ListObject> zmienić w dowolnym otwartym arkuszu w czasie uruchamiania. Aby uzyskać więcej informacji na temat sposobu dodawania kontrolki do arkusza za pomocą dodatku VSTO, zobacz Temat Jak dodać kontrolki <xref:Microsoft.Office.Tools.Excel.ListObject> [ListObject do arkuszy.](../vsto/how-to-add-listobject-controls-to-worksheets.md)

### <a name="to-resize-a-list-object-programmatically"></a>Aby programowo zmienić rozmiar obiektu listy

1. Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę, która obejmuje komórkę **od A1** do **B3 na** . `Sheet1`

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet12":::

2. Zmień rozmiar listy, aby zawierała komórki **od A1** do **C5**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject, kontrolka](../vsto/listobject-control.md)
- [How to: Add ListObject controls to worksheets (Jak dodać kontrolki ListObject do arkuszy)](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Jak zmienić rozmiar kontrolek zakładki](../vsto/how-to-resize-bookmark-controls.md)
- [Jak zmienić rozmiar formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)
