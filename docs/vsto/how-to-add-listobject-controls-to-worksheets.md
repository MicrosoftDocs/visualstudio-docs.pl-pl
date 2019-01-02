---
title: 'Instrukcje: Dodawanie formantów ListObject do arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 891b7fbbc4f2bf0fc0fa40fe983435a19978d081
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909063"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Instrukcje: Dodawanie formantów ListObject do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek do arkusza programu Microsoft Office Excel, w czasie projektowania i w czasie wykonywania w projektach na poziomie dokumentu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Można również dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantów w czasie wykonywania w projektach dodatku narzędzi VSTO.  
  
 W tym temacie opisano następujące zadania:  
  
- [Dodawanie formantów ListObject w czasie projektowania](#designtime)  
  
- [Dodawanie formantów ListObject w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)  
  
- [Dodawanie formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.ListObject> formantów, zobacz [kontrolki ListObject](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Dodawanie formantów ListObject w czasie projektowania  
 Istnieje kilka sposobów, aby dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek do arkusza w projekcie na poziomie dokumentu, w czasie projektowania: Z programu Excel, programu Visual Studio **przybornika**i z **źródeł danych** okna.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-use-the-ribbon-in-excel"></a>Do użycia na Wstążce w programie Excel  
  
1.  Na **Wstaw** na karcie **tabel** grupy, kliknij przycisk **tabeli**.  
  
2.  Wybierz komórkę lub komórki, które mają zostać uwzględnione na liście, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-use-the-toolbox"></a>Aby użyć przybornika  
  
1.  Z **kontrolki programu Excel** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza.  
  
     **Dodaj kontrolkę ListObject** pojawi się okno dialogowe.  
  
2.  Wybierz komórkę lub komórki, które mają zostać uwzględnione na liście, a następnie kliknij przycisk **OK**.  
  
     Jeśli nie chcesz zachować nazwę domyślną, należy zmienić nazwę w **właściwości** okna.  
  
#### <a name="to-use-the-data-sources-window"></a>Aby korzystanie z okna źródeł danych  
  
1.  Otwórz **źródeł danych** okna i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
2.  Przeciągnij tabelę na podstawie **źródeł danych** okna do arkusza.  
  
     Powiązane z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> formant jest dodawany do arkusza. Aby uzyskać więcej informacji, zobacz [powiązanie danych oraz Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Dodawanie formantów ListObject w czasie wykonywania w projekcie na poziomie dokumentu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli dynamicznie w czasie wykonywania. Dzięki temu można utworzyć kontrolki hosta w odpowiedzi na zdarzenia. Dynamicznie utworzona lista obiektów nie są zachowywane w arkuszu zgodnie z kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolkę ListObject do arkusza  
  
1.  W <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> program obsługi zdarzeń `Sheet1`, Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę komórki **A1** za pośrednictwem **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Dodawanie formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki programowo dowolnego otwartego arkusza w projekcie dodatku narzędzi VSTO. Dynamicznie utworzona lista obiektów nie są zachowywane w arkuszu zgodnie z kontrolki hosta, jeśli arkusz zostanie zapisany i zamykane. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolkę ListObject do arkusza  
  
1.  Poniższy kod generuje element hosta arkusza, która opiera się na otwieranie arkusza, a następnie dodanie <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę komórki **A1** za pośrednictwem **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [ListObject — formant](../vsto/listobject-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Instrukcje: Zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
