---
title: Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania
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
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c7fa5073fca476159aa756b7a5527dd1007ab66b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075808"
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania
  Można dodać kontrolki do dokumentu Microsoft Office Word i Microsoft Office Excel skoroszyt w czasie wykonywania. Można również usunąć je w czasie wykonywania. Formanty, które są dodawane lub usuwane w czasie wykonywania są nazywane *kontrolek dynamicznych*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 W tym temacie opisano następujące czynności:

- [Zarządzanie formantów w czasie wykonywania za pomocą kolekcje kontrolek](#ControlsCollection).

- [Dodawanie hosta formantów do dokumentów](#HostControls).

- [Dodawanie kontrolek formularzy Windows Forms do dokumentów](#WindowsForms).

  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Dodawanie formantów do powierzchni dokument w czasie wykonywania? ](http://go.microsoft.com/fwlink/?LinkId=132782).

## <a name="ControlsCollection"></a> Zarządzanie formantów w czasie wykonywania za pomocą kolekcje kontrolek
 Aby dodać, pobrać lub usuwanie formantów w czasie wykonywania, należy użyć metody pomocnika <xref:Microsoft.Office.Tools.Excel.ControlCollection> i <xref:Microsoft.Office.Tools.Word.ControlCollection> obiektów.

 Sposób dostępu do tych obiektów zależy od typu projektu, które tworzysz:

- W projekcie na poziomie dokumentu dla programu Excel, należy użyć <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> właściwość `Sheet1`, `Sheet2`, i `Sheet3` klasy. Aby uzyskać więcej informacji na temat tych klas, zobacz [element hosta arkusza](../vsto/worksheet-host-item.md).

- W projekcie na poziomie dokumentu dla programu Word, użyj <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwość `ThisDocument` klasy. Aby uzyskać więcej informacji na temat tej klasy, zobacz [element hosta dokumentu](../vsto/document-host-item.md).

- W projekcie dodatku narzędzi VSTO dla programu Excel lub Word, użyj `Controls` właściwość <xref:Microsoft.Office.Tools.Excel.Worksheet> lub <xref:Microsoft.Office.Tools.Word.Document> generowane w czasie wykonywania. Aby uzyskać więcej informacji na temat generowania tych obiektów w czasie wykonywania, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="add-controls"></a>Dodawanie formantów
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> i <xref:Microsoft.Office.Tools.Word.ControlCollection> typy obejmują metody pomocnika, które służy do dodawania formantów hosta i wspólnych formantów Windows Forms do dokumentów i arkuszy. Każda nazwa metody ma format `Add` *kontrolować klasy*, gdzie *kontrolować klasy* jest nazwą klasy formantu, który chcesz dodać. Na przykład, aby dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki do dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> metody.

 Poniższy przykład kodu dodaje <xref:Microsoft.Office.Tools.Excel.NamedRange> do `Sheet1` w projekcie poziomie dokumentu dla programu Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Kontroli dostępu i delete
 Możesz użyć `Controls` właściwość <xref:Microsoft.Office.Tools.Excel.Worksheet> lub <xref:Microsoft.Office.Tools.Word.Document> do iteracji przez wszystkie formanty w dokumencie, w tym formantów dodanych w czasie projektowania. Formanty, które dodają w czasie projektowania są również nazywane *formantów statycznych*.

 Możesz usunąć kontrolek dynamicznych, wywołując `Delete` metody formantu lub przez wywołanie metody `Remove` metoda Każda kolekcja kontrolek. Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> metodę, aby usunąć <xref:Microsoft.Office.Tools.Excel.NamedRange> z `Sheet1` w projekcie poziomie dokumentu dla programu Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 Nie można usunąć formantów statycznych w czasie wykonywania. Jeśli spróbujesz użyć `Delete` lub `Remove` metodę, aby usunąć formant statyczny <xref:Microsoft.Office.Tools.CannotRemoveControlException> zostanie zgłoszony.

> [!NOTE]
>  Nie usuwaj programowo kontrolek w `Shutdown` programu obsługi zdarzeń dokumentu. Elementy interfejsu użytkownika w pliku nie są już dostępne podczas `Shutdown` zdarzenie jest wywoływane. Jeśli chcesz usunąć kontrolki przed zamknięciem dokumentu, Dodaj swój kod obsługi zdarzeń dla innego zdarzenia, takie jak <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> lub <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> dla programu Word, lub <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>, lub <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> dla programu Excel.

## <a name="HostControls"></a> Dodawanie hosta formantów do dokumentów

Po dodaniu programowego kontrolki hosta do dokumentów, musisz podać nazwę, która jednoznacznie identyfikuje formant. Ponadto musisz określić, gdzie można dodać kontrolki do dokumentu. Aby uzyskać szczegółowe instrukcje zobacz następujące tematy:

- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Instrukcje: Dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Instrukcje: Dodaj zawartość formantów do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Aby uzyskać więcej informacji na temat formantów hosta zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

Po zapisaniu dokumentu i następnie zamknięte, wszystkie formanty hosta dynamicznie utworzoną zostały odłączone od ich zdarzenia i utracą ich funkcji wiązania danych. Można dodać kod do rozwiązania, aby ponownie utworzyć kontrolki hosta po otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [kontrolek dynamicznych w dokumentach pakietu Office utrwalenia](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Metody pomocnicze nie są dostarczane dla następujących hostować formantów, ponieważ te kontrolki nie programowo dodać do dokumentów: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, i <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="WindowsForms"></a> Dodawanie kontrolek formularzy Windows Forms do dokumentów
 Po dodaniu programowo formantu Windows Forms do dokumentu, należy podać lokalizację i nazwę, która jednoznacznie identyfikuje formant kontrolki. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zapewnia metody pomocnika dla każdego formantu. Te metody są przeciążone, aby przekazać zakresu lub określonych współrzędnych lokalizacji kontrolki.

 Po zapisaniu dokumentu i następnie zamknięte, wszystkie kontrolki Windows Forms utworzony dynamicznie są usuwane z dokumentu. Można dodać kod do rozwiązania, aby ponownie utworzyć formanty, po otwarciu dokumentu. Jeśli tworzysz dynamiczne kontrolek Windows Forms przy użyciu dodatku narzędzi VSTO otoki ActiveX dla formantów są pozostawiane w dokumencie. Aby uzyskać więcej informacji, zobacz [kontrolek dynamicznych w dokumentach pakietu Office utrwalenia](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
>  Nie można programowo dodać kontrolek formularzy Windows Forms do dokumentów chronionych. Programowe wyłączanie dokumentu programu Word lub arkusza programu Excel, aby dodać kontrolkę, należy napisać dodatkowy kod, aby usunąć otoki ActiveX kontrolki gdy dokument zostanie zamknięty. Kontrolki ActiveX otoki nie zostanie automatycznie usunięta z chronionych dokumentów.

### <a name="add-custom-controls"></a>Dodaj formanty niestandardowe
 Jeśli chcesz dodać <xref:System.Windows.Forms.Control> nie jest obsługiwana przez metody pomocnika dostępne, takie jak formant użytkownika niestandardowego, należy użyć następujących metod:

- Dla programu Excel, użyj jednej z <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metody <xref:Microsoft.Office.Tools.Excel.ControlCollection> obiektu.

- Dla programu Word, użyj jednej z <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> metody <xref:Microsoft.Office.Tools.Word.ControlCollection> obiektu.

  Aby dodać kontrolkę, należy przekazać <xref:System.Windows.Forms.Control>lokalizację dla formantu i jego nazwę, która jednoznacznie identyfikuje formant `AddControl` metody. `AddControl` Metoda zwraca obiekt, który definiuje, jak kontrolka współdziała z arkusza kalkulacyjnego lub dokumentu. `AddControl` Metoda zwraca <xref:Microsoft.Office.Tools.Excel.ControlSite> (dla programu Excel) lub <xref:Microsoft.Office.Tools.Word.ControlSite> obiektu (dla programu Word).

  Poniższy przykład kodu demonstruje sposób używania <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metoda dynamicznie dodać formant użytkownika niestandardowego do arkusza w projekcie programu Excel z poziomu dokumentu. W tym przykładzie formant użytkownika nazwano `UserControl1`i <xref:Microsoft.Office.Interop.Excel.Range> nosi nazwę `range1`. Aby użyć tego przykładu, należy uruchomić go z `Sheet` *n* klasy w projekcie.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Użyj składowych kontrolek niestandardowych
 Po zakończeniu korzystania z jednego z `AddControl` metody, aby dodać formant do arkusza lub dokument, możesz teraz mieć dwa obiekty innej kontrolki:

- <xref:System.Windows.Forms.Control> Reprezentujący kontrolki niestandardowej.

- `ControlSite`, `OLEObject`, Lub `OLEControl` obiekt, który reprezentuje kontrolkę, po została dodana do arkusza lub dokumentu.

  Wiele właściwości i metody są udostępniane między tymi kontrolkami. Jest ważne, dostęp do tych elementów członkowskich przy użyciu właściwej opcji kontroli:

- Aby uzyskać dostęp do elementów członkowskich, które należą wyłącznie do kontrolki niestandardowej, należy użyć <xref:System.Windows.Forms.Control>.

- Aby uzyskać dostęp do elementów członkowskich, które są udostępniane przez formanty, należy użyć `ControlSite`, `OLEObject`, lub `OLEControl` obiektu.

  Jeśli masz dostępu do udostępnionego elementu członkowskiego z <xref:System.Windows.Forms.Control>, może się nie udać bez ostrzeżenia lub powiadomienie lub może utworzyć nieprawidłowe wyniki. Należy zawsze używać metody lub właściwości `ControlSite`, `OLEObject`, lub `OLEControl` obiektu, chyba że potrzebne metodę lub właściwość nie jest dostępna; dopiero wtedy należy odniesienia możesz <xref:System.Windows.Forms.Control>.

  Na przykład zarówno <xref:Microsoft.Office.Tools.Excel.ControlSite> klasy i <xref:System.Windows.Forms.Control> klasa ma `Top` właściwości. Aby pobrać lub ustawić odległość między górną krawędzią formantu a górnej części dokumentu, należy użyć <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> właściwość <xref:Microsoft.Office.Tools.Excel.ControlSite>, a nie <xref:System.Windows.Forms.Control.Top%2A> właściwość <xref:System.Windows.Forms.Control>.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]

## <a name="see-also"></a>Zobacz także
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Instrukcje: Dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
