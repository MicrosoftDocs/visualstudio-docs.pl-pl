---
title: 'Instrukcje: Dodawanie formantów wykresu do arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 577c0531e73ad5586386c478611e57daa7e651d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967469"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Instrukcje: Dodawanie formantów wykresu do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolek do arkusza programu Microsoft Office Excel, w czasie projektowania i w czasie wykonywania w dostosowaniach na poziomie dokumentu. Można również dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantów w czasie wykonywania w dodatkach VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 W tym temacie opisano następujące zadania:  
  
- [Dodawanie formantów wykresu w czasie projektowania](#designtime)  
  
- [Dodawanie formantów wykresu w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)  
  
- [Dodawanie formantów wykresu w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.Chart> formantów, zobacz [wykresu kontroli](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Dodawanie formantów wykresu w czasie projektowania  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> formantu do arkusza w taki sam sposób, należy dodać wykres z poziomu aplikacji.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> Formant nie jest dostępny z **przybornika** lub **źródeł danych** okna.  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Aby dodać kontrolki hosta wykresu do arkusza programu Excel  
  
1.  Na **Wstaw** na karcie **wykresy** grupy, kliknij przycisk **kolumny**, kliknij kategorię wykresów, a następnie kliknij typ wykresu.  
  
2.  W **Wstaw wykres** okno dialogowe, kliknij przycisk **OK**.  
  
3.  Na **projektowania** na karcie **danych** grupy, kliknij przycisk **wybierz dane**.  
  
4.  W **wybierz źródło danych** okno dialogowe, kliknij przycisk w **wykresu** **zakres danych** i wyczyść wszystkie wybór domyślny.  
  
5.  W **danych wykresu** arkusz, zaznacz zakres komórek, która zawiera dane wykresu (komórek **A5** za pośrednictwem **D8**).  
  
6.  W **wybierz źródło danych** okno dialogowe, kliknij przycisk **OK**.  
  
##  <a name="runtimedoclevel"></a> Dodawanie formantów wykresu w czasie wykonywania w projekcie na poziomie dokumentu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontroli dynamicznie w czasie wykonywania. Utworzony dynamicznie wykresy nie są zachowywane w dokumencie jako host decyduje, gdy dokument zostanie zamknięty. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formant wykresu do arkusza  
  
1.  W <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> program obsługi zdarzeń `Sheet1`, Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontroli.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Dodawanie formantów wykresu w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki programowo dowolnego otwartego arkusza w projekcie dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Formanty dynamicznie utworzony wykres nie zostaną utrwalone w arkuszu zgodnie z kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodać formanty do pakietu Office, dokumenty w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formant wykresu do arkusza  
  
1.  Poniższy kod generuje element hosta arkusza, która opiera się na otwieranie arkusza, a następnie dodanie <xref:Microsoft.Office.Tools.Excel.Chart> kontroli.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 W tym przykładzie ma następujące wymagania:  
  
-   Dane na wykresie, przechowywane w zakresie od A5 do D8 w arkuszu.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Kontrolka wykresu](../vsto/chart-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
