---
title: Jak zmienić rozmiar formantów NamedRange
description: Dowiedz się, jak za pomocą Visual Studio programowo zmienić rozmiar kontrolek NamedRange w skoroszycie programu Microsoft Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3b70b34de222c35903a4f08b95d9efe8d8f896d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826463"
---
# <a name="how-to-resize-namedrange-controls"></a>Jak zmienić rozmiar formantów NamedRange
  Rozmiar kontrolki można ustawić podczas dodawania jej do dokumentu programu Microsoft Office Excel, ale możesz zmienić jej rozmiar <xref:Microsoft.Office.Tools.Excel.NamedRange> w późniejszym czasie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W projektach na poziomie dokumentu można zmienić rozmiar nazwanego zakresu w czasie projektowania lub w czasie uruchamiania. Można również zmienić rozmiar nazwanych zakresów w czasie uruchamiania w dodatki VSTO na poziomie aplikacji.

 W tym temacie opisano następujące zadania:

- [Zmienianie rozmiaru kontrolek NamedRange w czasie projektowania](#designtime)

- [Zmienianie rozmiaru kontrolek NamedRange w czasie uruchamiania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Zmienianie rozmiaru kontrolek NamedRange w czasie uruchamiania w projekcie dodatku VSTO](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a> Zmienianie rozmiaru kontrolek NamedRange w czasie projektowania
 Rozmiar nazwanego zakresu można zmienić, ponownie definiując jego rozmiar w **oknie dialogowym Definiowanie** nazwy.

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Aby zmienić rozmiar nazwanego zakresu przy użyciu okna dialogowego Definiowanie nazwy

1. Kliknij prawym przyciskiem myszy <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę.

2. Kliknij **pozycję Zarządzaj nazwanych zakresów** w menu skrótów.

     Zostanie **wyświetlone okno dialogowe Definiowanie** nazwy.

3. Wybierz nazwany zakres, którego rozmiar chcesz zmienić.

4. Wyczyść pole **Odwołuje się** do.

5. Wybierz komórki, których chcesz użyć do zdefiniowania rozmiaru nazwanego zakresu.

6. Kliknij przycisk **OK**.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Zmienianie rozmiaru kontrolek NamedRange w czasie uruchamiania w projekcie na poziomie dokumentu
 Nazwany zakres można zmienić programowo, używając <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> właściwości .

> [!NOTE]
> W **oknie** Właściwości właściwość <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> jest oznaczona jako tylko do odczytu.

### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwanego zakresu

1. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę w **komórce A1** . `Sheet1`

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet4":::

2. Zmień rozmiar nazwanego zakresu, aby uwzględnić **komórkę B1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet5":::

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Zmienianie rozmiaru kontrolek NamedRange w czasie uruchamiania w projekcie dodatku VSTO
 Rozmiar kontrolki można <xref:Microsoft.Office.Tools.Excel.NamedRange> zmienić w dowolnym otwartym arkuszu w czasie uruchamiania. Aby uzyskać więcej informacji na temat sposobu dodawania kontrolki do arkusza za pomocą dodatku VSTO, zobacz Temat Jak dodać kontrolki <xref:Microsoft.Office.Tools.Excel.NamedRange> [NamedRange do arkuszy.](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwanego zakresu

1. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę w **komórce A1** . `Sheet1`

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet10":::

2. Zmień rozmiar nazwanego zakresu, aby uwzględnić **komórkę B1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet11":::

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [2017: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Jak zmienić rozmiar kontrolek zakładki](../vsto/how-to-resize-bookmark-controls.md)
- [How to: Resize ListObject controls (2017: Zmienianie rozmiaru kontrolek ListObject)](../vsto/how-to-resize-listobject-controls.md)
