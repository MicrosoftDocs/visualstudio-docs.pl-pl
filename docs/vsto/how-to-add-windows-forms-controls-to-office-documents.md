---
title: 'Instrukcje: Dodawanie kontrolek formularzy Windows forms do dokumentów pakietu Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba2d1f46a16724f120d3e3ac788dfc8f2e290474
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899918"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office
  Możesz dodać kontrolek formularzy Windows Forms do programu Microsoft Office Excel i Microsoft Office Word dokumentów w czasie projektowania w projektach na poziomie dokumentu. W czasie wykonywania można dodawać formanty w dostosowaniach na poziomie dokumentu i dodatków narzędzi VSTO. Na przykład można dodać <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> sterowania do arkusza, co użytkownicy mogą wybrać z listy opcji.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 W tym temacie opisano następujące zadania:  
  
- [Dodawanie formantów w czasie projektowania](#designtime)  
  
- [Dodawanie formantów w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
- [Dodawanie formantów w czasie wykonywania w dodatkach VSTO](#runtimeaddin)  
  
  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Dodawanie formantów do powierzchni dokument w czasie wykonywania? ](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Dodawanie formantów w czasie projektowania  
 Istnieje kilka sposobów, aby dodać kontrolek formularzy Windows Forms do dokumentów w projekcie na poziomie dokumentu w czasie projektowania.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Przeciągnij formant programu Windows Forms do dokumentów  
  
1.  Utwórz lub Otwórz skoroszyt programu Excel, projektu lub projektu dokument programu Word w programie Visual Studio, tak aby dokument był widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **wspólnych formantów** karcie **przybornika**, kliknij kontrolkę, którą chcesz dodać i przeciągnij go do dokumentu.  
  
    > [!NOTE]  
    >  Po wybraniu kontrolki w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest wymagane i nie powinny być usuwane.  
  
### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Rysowanie formantu Windows Forms w dokumencie  
  
1.  Utwórz lub Otwórz skoroszyt programu Excel, projektu lub projektu dokument programu Word w programie Visual Studio, tak aby dokument był widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **wspólnych formantów** karcie **przybornika**, kliknij kontrolkę, którą chcesz dodać.  
  
3.  W dokumencie kliknij w miejscu lewego górnego rogu kontrolki można znaleźć i przeciągnij w odpowiednie miejsce prawym dolnym rogu formantu w zlokalizowanym.  
  
     Formant jest dodawany do dokumentu z określonej lokalizacji i rozmiaru.  
  
    > [!NOTE]  
    >  Po wybraniu kontrolki w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest wymagane i nie powinny być usuwane.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Aby dodać formant programu Windows Forms do dokumentu przez pojedyncze kliknięcie formantu  
  
1.  Utwórz lub Otwórz skoroszyt programu Excel, projektu lub projektu dokument programu Word w programie Visual Studio, tak aby dokument był widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **wspólnych formantów** karcie **przybornika**, kliknij kontrolkę, którą chcesz dodać  
  
3.  Jeden dokument, kliknij w miejscu formant, który ma zostać dodana.  
  
     Formant jest dodawany do dokumentu z domyślnego rozmiaru.  
  
    > [!NOTE]  
    >  Po wybraniu kontrolki w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest wymagane i nie powinny być usuwane.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Aby dodać formant programu Windows Forms do dokumentu przez dwukrotne kliknięcie formantu  
  
1.  Utwórz lub Otwórz skoroszyt programu Excel, projektu lub projektu dokument programu Word w programie Visual Studio, tak aby dokument był widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **wspólnych formantów** karcie **przybornika**, kliknij dwukrotnie formant, którego chcesz dodać.  
  
     Formant jest dodawany do dokumentu w środkowej części dokumentu lub aktywne okienko.  
  
    > [!NOTE]  
    >  Po wybraniu kontrolki w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest wymagane i nie powinny być usuwane.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Aby dodać formant programu Windows Forms w dokumencie, naciskając klawisz Enter  
  
1.  Utwórz lub Otwórz skoroszyt programu Excel, projektu lub projektu dokument programu Word w programie Visual Studio, tak aby dokument był widoczny w projektancie. Aby uzyskać informacje dotyczące tworzenia projektów, zobacz [jak: Tworzenie projektów Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **wspólnych formantów** karcie **przybornika**, kliknij kontrolkę chcesz dodać, a następnie naciśnij klawisz **Enter** klucza.  
  
     Formant jest dodawany do dokumentu w środkowej części dokumentu lub aktywne okienko.  
  
    > [!NOTE]  
    >  Po wybraniu kontrolki w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest wymagane i nie powinny być usuwane.  
  
##  <a name="runtimedoclevel"></a> Dodawanie formantów w czasie wykonywania w projektach na poziomie dokumentu  
 Możesz programowo dodać kontrolek formularzy Windows Forms do dokumentu w czasie wykonywania. W programie Word, należy użyć metod <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> właściwość `ThisDocument` klasy. W programie Excel, należy użyć metod <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> właściwość `Sheet` *n* klasy. Każda metoda ma kilka przeciążeń, które pozwalają określić położenie formantu w różny sposób.  
  
 Po dodaniu kontrolki Windows Forms do dokumentów w czasie wykonywania, formant nie jest trwały dokumentu, gdy dokument zostanie zamknięty. Można ponownie utworzyć formant przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Aby dodać formant programu Windows Forms w czasie wykonywania  
  
1.  Użyj metody o tej nazwie Dodaj\<*kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu Windows Forms, którą chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
     Poniższy przykład kodu demonstruje sposób dodawania <xref:Microsoft.Office.Tools.Excel.Controls.Button> do komórki **C5** z `Sheet1` w projekcie poziomie dokumentu dla programu Excel.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a> Dodawanie formantów w czasie wykonywania w dodatkach VSTO  
 Możesz programowo dodać kontrolek formularzy Windows Forms dowolnego otwartego dokumentu w czasie wykonywania. Najpierw Generuj element hosta, która jest oparta na otwartym dokumencie lub arkuszu. Następnie w programie Word, użyj metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości nowego elementu host. W programie Excel, należy użyć metod <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> właściwości nowego elementu host. Każda metoda ma kilka przeciążeń, które pozwalają określić położenie formantu w różny sposób.  
  
 Po dodaniu kontrolki Windows Forms do dokumentów w czasie wykonywania, formant nie jest trwały dokumentu, gdy dokument zostanie zamknięty. Można ponownie utworzyć formant przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatku narzędzi VSTO dla programów, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Aby dodać formant programu Windows Forms w czasie wykonywania  
  
1.  Użyj metody o tej nazwie Dodaj\<*kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu Windows Forms, którą chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
    > [!NOTE]  
    >  W dodatku narzędzi VSTO dla projektów, których celem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, należy dodać odwołanie do *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* lub *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* zestawu w celu uzyskania dostępu Dodaj\<*kontrolować klasy*> metody.  
  
     Poniższy przykład kodu demonstruje sposób dodawania <xref:Microsoft.Office.Tools.Word.Controls.Button> do pierwszego akapitu aktywnego dokumentu za pomocą dodatków narzędzi VSTO programu Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>Zobacz także  
 [Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Instrukcje: Zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
