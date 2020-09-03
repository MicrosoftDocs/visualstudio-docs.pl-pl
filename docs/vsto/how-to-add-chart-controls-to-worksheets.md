---
title: 'Instrukcje: Dodawanie kontrolek wykresu do arkuszy'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fdb1f738fe6e68f7470ae65e6ce08b2f3be0ef6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546240"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Instrukcje: Dodawanie kontrolek wykresu do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki do Microsoft Office arkusza programu Excel w czasie projektowania i w czasie wykonywania w przypadku dostosowań na poziomie dokumentu. Możesz również dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki w czasie wykonywania w dodatkach narzędzi VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W tym temacie opisano następujące zadania:

- [Dodaj kontrolki wykresu w czasie projektowania](#designtime)

- [Dodawanie kontrolek wykresu w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek wykresu w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.Chart> kontrolek, zobacz [formant wykresu](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Dodaj kontrolki wykresu w czasie projektowania
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> formant do arkusza w taki sam sposób, jak dodać wykres z poziomu aplikacji.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.Chart>Kontrolka jest niedostępna z **przybornika** lub okna **źródła danych** .

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Aby dodać kontrolkę hosta wykresu do arkusza w programie Excel

1. Na karcie **Wstawianie** w grupie **wykresy** kliknij pozycję **kolumna**, kliknij kategorię wykresów, a następnie kliknij żądany typ wykresu.

2. W oknie dialogowym **Wstawianie wykresu** kliknij przycisk **OK**.

3. Na karcie **projekt** w grupie **dane** kliknij przycisk **Wybierz dane**.

4. W oknie dialogowym **Wybierz źródło danych** kliknij pole **zakres danych** **wykresu** i wyczyść wszystkie wybrane ustawienia domyślne.

5. W arkuszu **dane dla wykresu** wybierz zakres komórek zawierający dane wykresu (komórki **a5** do **D8**).

6. W oknie dialogowym **Wybierz źródło danych** kliknij przycisk **OK**.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek wykresu w czasie wykonywania w projekcie na poziomie dokumentu
 Formant można dodać <xref:Microsoft.Office.Tools.Excel.Chart> dynamicznie w czasie wykonywania. Utworzone dynamicznie wykresy nie są utrwalane w dokumencie jako formanty hosta, gdy dokument jest zamknięty. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formant wykresu do arkusza

1. W programie <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obsługi zdarzeń programu `Sheet1` Wstaw poniższy kod, aby dodać <xref:Microsoft.Office.Tools.Excel.Chart> formant.

     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie kontrolek wykresu w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Formant można dodać <xref:Microsoft.Office.Tools.Excel.Chart> programowo do dowolnego otwartego arkusza w projekcie dodatku VSTO. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

 Dynamicznie tworzone kontrolki wykresu nie są utrwalane w arkuszu jako kontrolki hosta, gdy arkusz jest zamknięty. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formant wykresu do arkusza

1. Poniższy kod generuje element hosta arkusza, który jest oparty na otwartym arkuszu, a następnie dodaje <xref:Microsoft.Office.Tools.Excel.Chart> kontrolkę.

     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład ma następujące wymagania:

- Dane do wykresu, przechowywane w zakresie od A5 do D8 w arkuszu.

## <a name="see-also"></a>Zobacz też
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Kontrolka wykresu](../vsto/chart-control.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
