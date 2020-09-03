---
title: Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44bf1de5d550a264a63ba7293fe1bdc0c9630aee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986323"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania
  Możesz dodać kontrolki do Microsoft Office dokumentu programu Word i Microsoft Office skoroszytu programu Excel w czasie wykonywania. Można je również usunąć w czasie wykonywania. Kontrolki dodawane lub usuwane w czasie wykonywania są nazywane *kontrolkami dynamicznymi*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 W tym temacie opisano następujące zagadnienia:

- [Zarządzanie kontrolkami w czasie wykonywania przy użyciu kolekcji kontrolek](#ControlsCollection).

- [Dodaj formanty hosta do dokumentów](#HostControls).

- [Dodawanie formantów Windows Forms do dokumentów](#WindowsForms).

## <a name="manage-controls-at-run-time-by-using-control-collections"></a><a name="ControlsCollection"></a> Zarządzanie kontrolkami w czasie wykonywania przy użyciu kolekcji kontrolek
 Aby dodać, pobrać lub usunąć kontrolki w czasie wykonywania, należy użyć metod pomocniczych <xref:Microsoft.Office.Tools.Excel.ControlCollection> <xref:Microsoft.Office.Tools.Word.ControlCollection> obiektów i.

 Sposób uzyskiwania dostępu do tych obiektów zależy od typu projektu, który tworzysz:

- W projekcie na poziomie dokumentu dla programu Excel Użyj <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> właściwości `Sheet1` `Sheet2` klasy,, i `Sheet3` . Aby uzyskać więcej informacji na temat tych klas, zobacz [arkusz elementów hosta](../vsto/worksheet-host-item.md).

- W projekcie na poziomie dokumentu dla programu Word, użyj <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości `ThisDocument` klasy. Aby uzyskać więcej informacji na temat tej klasy, zobacz [dokument element hosta](../vsto/document-host-item.md).

- W projekcie dodatku VSTO dla programu Excel lub Word Użyj `Controls` właściwości <xref:Microsoft.Office.Tools.Excel.Worksheet> lub <xref:Microsoft.Office.Tools.Word.Document> , która jest generowana w czasie wykonywania. Aby uzyskać więcej informacji na temat generowania tych obiektów w czasie wykonywania, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="add-controls"></a>Dodawanie kontrolek
 <xref:Microsoft.Office.Tools.Excel.ControlCollection>Typy i <xref:Microsoft.Office.Tools.Word.ControlCollection> zawierają metody pomocnika, których można użyć do dodawania formantów hosta i wspólnych formantów Windows Forms do dokumentów i arkuszy. Każda nazwa metody ma `Add` *klasę kontrolki*format, gdzie *Klasa sterowania* jest nazwą klasy kontrolki, która ma zostać dodana. Na przykład, aby dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formant do dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> metody.

 Poniższy przykład kodu dodaje <xref:Microsoft.Office.Tools.Excel.NamedRange> do `Sheet1` w projekcie na poziomie dokumentu dla programu Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Kontrolki dostępu i usuwania
 Można użyć `Controls` właściwości <xref:Microsoft.Office.Tools.Excel.Worksheet> lub, <xref:Microsoft.Office.Tools.Word.Document> Aby wykonać iterację wszystkich kontrolek w dokumencie, w tym kontrolek dodanych w czasie projektowania. Kontrolki dodawane w czasie projektowania są również nazywane *kontrolkami statycznymi*.

 Można usunąć kontrolki dynamiczne `Delete` , wywołując metodę kontrolki lub wywołując `Remove` metodę każdej kolekcji formantów. Poniższy przykład kodu używa <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> metody do usuwania <xref:Microsoft.Office.Tools.Excel.NamedRange> z `Sheet1` w projekcie na poziomie dokumentu dla programu Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 Nie można usunąć kontrolek statycznych w czasie wykonywania. Jeśli spróbujesz użyć `Delete` `Remove` metody lub, aby usunąć formant statyczny, <xref:Microsoft.Office.Tools.CannotRemoveControlException> zostanie zgłoszony.

> [!NOTE]
> Nie należy programistycznie usuwać formantów w programie `Shutdown` obsługi zdarzeń dokumentu. Elementy interfejsu użytkownika dokumentu nie są już dostępne, gdy `Shutdown` zdarzenie jest zgłaszane. Jeśli chcesz usunąć formanty przed zamknięciem dokumentu, Dodaj kod do programu obsługi zdarzeń dla innego zdarzenia, takiego jak <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> lub <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> dla programu Word lub dla <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose> <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> programu Excel.

## <a name="add-host-controls-to-documents"></a><a name="HostControls"></a> Dodawanie formantów hosta do dokumentów

Przy programistycznym dodawaniu formantów hosta do dokumentów, należy podać nazwę, która jednoznacznie identyfikuje kontrolkę, i należy określić miejsce dodania kontrolki do dokumentu. Aby uzyskać szczegółowe instrukcje, zobacz następujące tematy:

- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Instrukcje: Dodawanie kontrolek wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Aby uzyskać więcej informacji na temat kontrolek hosta, zobacz temat [elementy hosta i kontrolki hosta](../vsto/host-items-and-host-controls-overview.md).

Po zapisaniu i zamknięciu dokumentu wszystkie dynamicznie utworzone formanty hosta są odłączone od ich zdarzeń i tracą funkcjonalność powiązania danych. Możesz dodać kod do rozwiązania, aby ponownie utworzyć kontrolki hosta po ponownym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Nie podano metod pomocniczych dla następujących kontrolek hosta, ponieważ te kontrolki nie mogą być dodane programowo do dokumentów: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , <xref:Microsoft.Office.Tools.Word.XMLNode> i <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="add-windows-forms-controls-to-documents"></a><a name="WindowsForms"></a> Dodawanie formantów Windows Forms do dokumentów
 Gdy programowo dodasz kontrolkę Windows Forms do dokumentu, musisz podać lokalizację kontrolki i nazwę, która jednoznacznie identyfikuje formant. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Zapewnia metody pomocnika dla każdej kontrolki. Te metody są przeciążone, aby można było przekazać zakres lub określone współrzędne dla lokalizacji formantu.

 Po zapisaniu i zamknięciu dokumentu wszystkie dynamicznie tworzone kontrolki Windows Forms są usuwane z dokumentu. Możesz dodać kod do rozwiązania, aby ponownie utworzyć kontrolki po ponownym otwarciu dokumentu. Jeśli utworzysz kontrolki dynamiczne Windows Forms przy użyciu dodatku VSTO, otoki ActiveX dla kontrolek pozostaną w dokumencie. Aby uzyskać więcej informacji, zobacz [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Formantów Windows Forms nie można programistycznie dodać do chronionych dokumentów. Jeśli program programowo nie chroni dokumentu programu Word lub arkusza programu Excel w celu dodania kontrolki, należy napisać dodatkowy kod, aby usunąć otokę ActiveX kontrolki po zamknięciu dokumentu. Otoka ActiveX kontrolki nie jest automatycznie usuwana z chronionych dokumentów.

### <a name="add-custom-controls"></a>Dodaj formanty niestandardowe
 Jeśli chcesz dodać element <xref:System.Windows.Forms.Control> , który nie jest obsługiwany przez dostępne metody pomocnika, takie jak niestandardowa kontrolka użytkownika, użyj następujących metod:

- Dla programu Excel Użyj jednej z <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metod <xref:Microsoft.Office.Tools.Excel.ControlCollection> obiektu.

- Dla programu Word Użyj jednej z <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> metod <xref:Microsoft.Office.Tools.Word.ControlCollection> obiektu.

  Aby dodać kontrolkę, Przekaż <xref:System.Windows.Forms.Control> , lokalizację dla kontrolki i nazwę, która jednoznacznie identyfikuje kontrolkę do `AddControl` metody. `AddControl`Metoda zwraca obiekt, który definiuje sposób interakcji kontrolki z arkuszem lub dokumentem. `AddControl`Metoda zwraca <xref:Microsoft.Office.Tools.Excel.ControlSite> (dla programu Excel) lub <xref:Microsoft.Office.Tools.Word.ControlSite> obiekt (dla programu Word).

  Poniższy przykład kodu demonstruje, jak używać <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metody do dynamicznego dodawania niestandardowej kontrolki użytkownika do arkusza w projekcie programu Excel na poziomie dokumentu. W tym przykładzie kontrolka użytkownika ma nazwę `UserControl1` i <xref:Microsoft.Office.Interop.Excel.Range> ma nazwę `range1` . Aby użyć tego przykładu, należy uruchomić go z `Sheet` klasy *n* w projekcie.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Użyj członków formantów niestandardowych
 Po użyciu jednej z `AddControl` metod, aby dodać kontrolkę do arkusza lub dokumentu, istnieją teraz dwa różne obiekty sterujące:

- <xref:System.Windows.Forms.Control>Reprezentuje kontrolkę niestandardową.

- `ControlSite`, `OLEObject` , Lub `OLEControl` obiekt, który reprezentuje kontrolkę po dodaniu do arkusza lub dokumentu.

  Między tymi kontrolkami są współdzielone wiele właściwości i metod. Ważne jest, aby uzyskać dostęp do tych członków za pomocą odpowiedniej kontrolki:

- Aby uzyskać dostęp do elementów członkowskich, które należą tylko do kontrolki niestandardowej, użyj <xref:System.Windows.Forms.Control> .

- Aby uzyskać dostęp do elementów członkowskich, które są współużytkowane przez formanty, użyj `ControlSite` `OLEObject` obiektu, lub `OLEControl` .

  Jeśli uzyskujesz dostęp do udostępnionego elementu członkowskiego z programu <xref:System.Windows.Forms.Control> , może to zakończyć się niepowodzeniem bez ostrzeżenia lub powiadomienia lub może wygenerować nieprawidłowe wyniki. Zawsze używaj metod lub właściwości `ControlSite` `OLEObject` obiektu, `OLEControl` chyba że wymagana Metoda lub właściwość nie jest dostępna; tylko wtedy należy odwołać się do <xref:System.Windows.Forms.Control> .

  Na przykład <xref:Microsoft.Office.Tools.Excel.ControlSite> Klasa i <xref:System.Windows.Forms.Control> Klasa mają `Top` Właściwość. Aby uzyskać lub ustawić odległość między górną częścią kontrolki a górą dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> właściwości <xref:Microsoft.Office.Tools.Excel.ControlSite> , a nie <xref:System.Windows.Forms.Control.Top%2A> właściwości <xref:System.Windows.Forms.Control> .

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]

## <a name="see-also"></a>Zobacz też
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Instrukcje: Dodawanie kontrolek wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Kontrolki Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
