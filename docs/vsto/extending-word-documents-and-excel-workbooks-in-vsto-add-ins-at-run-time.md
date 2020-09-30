---
title: Rozszerzone dokumenty programu Word & skoroszyty programu Excel w dodatkach narzędzi VSTO w czasie wykonywania
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e2227aa2db4943ab132a8b2e2f9fc3a6f0ec4096
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585448"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania
  Dodatku VSTO można użyć do dostosowania dokumentów programu Word i skoroszytów programu Excel w następujący sposób:

- Dodaj zarządzane formanty do dowolnego otwartego dokumentu lub arkusza.

- Przekonwertuj istniejący obiekt listy w arkuszu programu Excel na rozszerzony <xref:Microsoft.Office.Tools.Excel.ListObject> , który uwidacznia zdarzenia i można powiązać z danymi przy użyciu modelu powiązań danych Windows Forms.

- Dostęp do zdarzeń na poziomie aplikacji, które są udostępniane przez programy Word i Excel, dla określonych dokumentów, skoroszytów i arkuszy.

  Aby użyć tej funkcji, należy wygenerować obiekt w czasie wykonywania, który rozszerza dokument lub skoroszyt.

  **Dotyczy:** Informacje zawarte w tym artykule dotyczą projektów dodatku VSTO dla następujących aplikacji: Excel i Word. Aby uzyskać więcej informacji, zobacz [dostępność funkcji według aplikacji pakietu Office i typów projektów](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="generate-extended-objects-in-vsto-add-ins"></a>Generowanie obiektów rozszerzonych w dodatkach narzędzi VSTO
 *Obiekty rozszerzone* to wystąpienia typów zapewniane przez Visual Studio Tools pakietu Office Runtime, które dodają funkcje do obiektów, które znajdują się natywnie w modelu obiektów Word lub Excel (nazywane *natywnymi obiektami pakietu Office*). Aby wygenerować rozszerzony obiekt dla obiektu programu Word lub Excel, użyj `GetVstoObject` metody. Przy pierwszym wywołaniu `GetVstoObject` metody dla określonego obiektu Word lub Excel zwraca nowy obiekt, który rozszerza określony obiekt. Za każdym razem, gdy wywołasz metodę i określisz ten sam obiekt Word lub Excel, zwraca ten sam obiekt rozszerzony.

 Typ obiektu rozszerzonego ma taką samą nazwę jak typ natywnego obiektu pakietu Office, ale typ jest zdefiniowany w <xref:Microsoft.Office.Tools.Excel> <xref:Microsoft.Office.Tools.Word> przestrzeni nazw lub. Na przykład, jeśli wywołasz `GetVstoObject` metodę w celu poszerzenia <xref:Microsoft.Office.Interop.Word.Document> obiektu, metoda zwraca <xref:Microsoft.Office.Tools.Word.Document> obiekt.

 `GetVstoObject`Metody są przeznaczone głównie do użytku w projektach dodatku VSTO. Można również użyć tych metod w projektach na poziomie dokumentu, ale zachowują się one inaczej i mają mniej użycia.

 Aby określić, czy rozszerzony obiekt został już wygenerowany dla określonego natywnego obiektu pakietu Office, użyj `HasVstoObject` metody. Aby uzyskać więcej informacji, zobacz [Określanie, czy obiekt pakietu Office został rozszerzony](#HasVstoObject).

### <a name="generate-host-items"></a>Generuj elementy hosta
 W przypadku korzystania z programu `GetVstoObject` w celu poszerzenia obiektu poziomu dokumentu (czyli, <xref:Microsoft.Office.Interop.Excel.Workbook> <xref:Microsoft.Office.Interop.Excel.Worksheet> lub <xref:Microsoft.Office.Interop.Word.Document> ) zwracany obiekt jest nazywany *elementem hosta*. Element hosta to typ, który może zawierać inne obiekty, w tym inne rozszerzone obiekty i kontrolki. Jest on podobny do odpowiedniego typu w podstawowym zestawie międzyoperacyjnym programu Word lub Excel, ale zawiera dodatkowe funkcje. Aby uzyskać więcej informacji na temat elementów hosta, zobacz [Omówienie elementów hosta i formantów hosta](../vsto/host-items-and-host-controls-overview.md).

 Po wygenerowaniu elementu hosta można go użyć do dodania formantów zarządzanych do dokumentu, skoroszytu lub arkusza. Aby uzyskać więcej informacji, zobacz [Dodawanie formantów zarządzanych do dokumentów i arkuszy](#AddControls).

#### <a name="to-generate-a-host-item-for-a-word-document"></a>Aby wygenerować element hosta dla dokumentu programu Word

- Poniższy przykład kodu demonstruje, jak wygenerować element hosta dla aktywnego dokumentu.

     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]

#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Aby wygenerować element hosta dla skoroszytu programu Excel

- Poniższy przykład kodu demonstruje, jak wygenerować element hosta dla aktywnego skoroszytu.

     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]

#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Aby wygenerować element hosta dla arkusza programu Excel

- Poniższy przykład kodu demonstruje, jak wygenerować element hosta dla aktywnego arkusza w projekcie.

     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]

### <a name="generate-listobject-host-controls"></a>Generowanie formantów hosta ListObject
 Gdy używasz `GetVstoObject` metody do rozszerania <xref:Microsoft.Office.Interop.Excel.ListObject> , metoda zwraca <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject>Ma wszystkie funkcje oryginału <xref:Microsoft.Office.Interop.Excel.ListObject> . Ma także dodatkowe funkcje i może być powiązane z danymi przy użyciu modelu powiązań danych Windows Forms. Aby uzyskać więcej informacji, zobacz [formant ListObject](../vsto/listobject-control.md).

#### <a name="to-generate-a-host-control-for-a-listobject"></a>Aby wygenerować formant hosta dla ListObject

- Poniższy przykład kodu demonstruje, jak wygenerować jako <xref:Microsoft.Office.Tools.Excel.ListObject> pierwszy <xref:Microsoft.Office.Interop.Excel.ListObject> w aktywnym arkuszu w projekcie.

     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]

### <a name="add-managed-controls-to-documents-and-worksheets"></a><a name="AddControls"></a> Dodawanie formantów zarządzanych do dokumentów i arkuszy
 Po wygenerowaniu <xref:Microsoft.Office.Tools.Word.Document> lub można <xref:Microsoft.Office.Tools.Excel.Worksheet> dodać kontrolki do dokumentu lub arkusza, które reprezentują te obiekty rozszerzone. Aby dodać kontrolki, użyj `Controls` właściwości <xref:Microsoft.Office.Tools.Word.Document> lub <xref:Microsoft.Office.Tools.Excel.Worksheet> . Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Można dodać kontrolki Windows Forms lub *formanty hosta*. Formant hosta jest formantem dostarczanym przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] program, który otacza odpowiednią kontrolkę w podstawowym zestawie międzyoperacyjnym programu Word lub Excel. Kontrolka hosta uwidacznia wszystkie zachowania bazowego natywnego obiektu pakietu Office. Wywołuje również zdarzenia i może być powiązane z danymi przy użyciu modelu powiązań danych Windows Forms. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

> [!NOTE]
> Nie można dodać <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontrolki do arkusza lub <xref:Microsoft.Office.Tools.Word.XMLNode> <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki lub do dokumentu przy użyciu dodatku VSTO. Tych formantów hosta nie można dodać programowo. Aby uzyskać więcej informacji, zobacz Ograniczenia programowe [elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="persist-and-remove-controls"></a>Utrwalanie i usuwanie kontrolek
 Po dodaniu formantów zarządzanych do dokumentu lub arkusza formanty nie są utrwalane, gdy dokument zostanie zapisany, a następnie zamknięty. Wszystkie kontrolki hosta są usuwane, dzięki czemu tylko bazowe natywne obiekty pakietu Office są pozostawione w tle. Na przykład a <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Interop.Excel.ListObject> . Wszystkie kontrolki Windows Forms są również usuwane, ale otoki ActiveX dla formantów są pozostawione w dokumencie. Musisz dołączyć kod w dodatku VSTO, aby wyczyścić kontrolki, lub odtworzyć kontrolki przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

## <a name="access-application-level-events-on-documents-and-workbooks"></a>Dostęp do zdarzeń na poziomie aplikacji w dokumentach i skoroszytach
 Niektóre zdarzenia dokumentów, skoroszytów i arkuszy w natywnych modelach programów Word i Excel są wywoływane tylko na poziomie aplikacji. Na przykład <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenie jest zgłaszane, gdy dokument zostanie otwarty w programie Word, ale to zdarzenie jest definiowane w <xref:Microsoft.Office.Interop.Word.Application> klasie, a nie w <xref:Microsoft.Office.Interop.Word.Document> klasie.

 Jeśli używasz tylko natywnych obiektów pakietu Office w dodatku VSTO, musisz obsłużyć te zdarzenia na poziomie aplikacji, a następnie napisać dodatkowy kod, aby określić, czy dokument, który spowodował zdarzenie, został dostosowany. Elementy hosta zapewniają te zdarzenia na poziomie dokumentu, dzięki czemu można łatwiej obsłużyć zdarzenia dla określonego dokumentu. Można wygenerować element hosta, a następnie obsłużyć zdarzenie dla tego elementu hosta.

### <a name="example-that-uses-native-word-objects"></a>Przykład używający natywnych obiektów programu Word
 Poniższy przykład kodu demonstruje, jak obsłużyć zdarzenie na poziomie aplikacji dla dokumentów programu Word. `CreateDocument`Metoda tworzy nowy dokument, a następnie definiuje <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> program obsługi zdarzeń, który uniemożliwia zapisanie tego dokumentu. Zdarzenie jest zdarzeniem na poziomie aplikacji, które jest zgłaszane dla <xref:Microsoft.Office.Interop.Word.Application> obiektu, a program obsługi zdarzeń musi porównać `Doc` parametr z `document1` obiektem, aby określić, czy `document1` reprezentuje zapisany dokument.

 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]

### <a name="examples-that-use-a-host-item"></a>Przykłady korzystające z elementu hosta
 Poniższe przykłady kodu upraszczają ten proces przez obsługę <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> zdarzenia <xref:Microsoft.Office.Tools.Word.Document> elementu hosta. `CreateDocument2`Metoda w tych przykładach generuje, <xref:Microsoft.Office.Tools.Word.Document> że rozszerza `document2` obiekt, a następnie definiuje <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> procedurę obsługi zdarzeń, która uniemożliwia zapisanie dokumentu. Procedura obsługi zdarzeń jest wywoływana tylko wtedy `document2` , gdy jest zapisywana, i może anulować akcję zapisu bez wykonywania dodatkowych czynności w celu sprawdzenia, który dokument został zapisany.

 Poniższy przykład kodu demonstruje to zadanie.

 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]

## <a name="determine-whether-an-office-object-has-been-extended"></a><a name="HasVstoObject"></a> Określanie, czy obiekt pakietu Office został rozszerzony
 Aby określić, czy rozszerzony obiekt został już wygenerowany dla określonego natywnego obiektu pakietu Office, użyj `HasVstoObject` metody. Ta metoda zwraca **wartość true** , jeśli rozszerzony obiekt został już wygenerowany.

 Użyj metody `Globals.Factory.HasVstoMethod`. Przekaż obiekt macierzysty programu Word lub programu Excel, taki jak <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet> , który ma zostać przetestowany dla rozszerzonego obiektu.

 `HasVstoObject`Metoda jest przydatna, gdy chcesz uruchomić kod tylko wtedy, gdy określony obiekt pakietu Office ma rozszerzony obiekt. Na przykład jeśli masz dodatek narzędzi VSTO dla programu Word, który obsługuje zdarzenie, <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> Aby usunąć formanty zarządzane z dokumentu przed jego zapisaniem, użyj `HasVstoObject` metody w celu ustalenia, czy dokument został rozszerzony. Jeśli dokument nie został rozszerzony, nie może mieć zarządzanych formantów i program obsługi zdarzeń może zwrócić bez próby oczyszczenia formantów w dokumencie.

## <a name="see-also"></a>Zobacz też
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
