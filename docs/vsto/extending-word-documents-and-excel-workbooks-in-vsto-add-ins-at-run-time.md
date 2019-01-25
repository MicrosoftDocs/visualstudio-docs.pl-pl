---
title: Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania
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
ms.openlocfilehash: 8c3527070c1934c723b6038c93347f1a78ac948a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864881"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-runtime"></a>Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania
  Dodatku narzędzi VSTO służy do dostosowywania dokumentów programu Word i skoroszytów programu Excel w następujący sposób:  
  
- Dodawanie formantów zarządzanego do dowolnego otwartego dokumentu lub arkusza.  
  
- Konwertowanie istniejącego obiektu listy programu Excel do rozszerzonego <xref:Microsoft.Office.Tools.Excel.ListObject> który uwidacznia zdarzenia i może być powiązana z danymi za pomocą modelu powiązanie danych formularzy Windows.  
  
- Zdarzenia dodatku poziomu aplikacji dostępu, które są dostępne w programach Word i Excel dla określonych dokumentów, skoroszytów i arkuszy.  
  
  Aby używać tej funkcji, musisz wygenerować obiektu w czasie wykonywania, który rozszerza dokument lub skoroszyt.  
  
  **Dotyczy:** Informacje przedstawione w tym artykule mają zastosowanie do projektów dodatku VSTO dla następujących aplikacji: Program Excel i Word. Aby uzyskać więcej informacji, zobacz [funkcje, które są dostępne przez typ aplikacji i projektów pakietu Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="generate-extended-objects-in-vsto-add-ins"></a>Generowanie rozszerzonych obiektów w dodatków narzędzi VSTO  
 *Obiekty rozszerzone* wystąpień typów przy użyciu programu Visual Studio Tools dla pakietu Office runtime, które dodają funkcje do obiektów, które istnieją w sposób natywny w modele obiektów programu Word lub Excel (o nazwie *natywnych obiektów pakietu Office*). Aby wygenerować rozszerzonego obiektu dla obiektu programu Word lub Excel, należy użyć `GetVstoObject` metody. Przy pierwszym wywołaniu `GetVstoObject` obiektu metodę dla określonego programu Word lub Excel, zwraca nowy obiekt, który rozszerza określony obiekt. Każdorazowo, wywołaj metodę i określić tego samego programu Word lub Excel obiektu, zwraca ten sam obiekt rozszerzonej.  
  
 Typ obiektu rozszerzonych ma taką samą nazwę jak typ natywny obiektów pakietu Office, ale typ jest zdefiniowany w <xref:Microsoft.Office.Tools.Excel> lub <xref:Microsoft.Office.Tools.Word> przestrzeni nazw. Na przykład, jeśli wywołasz `GetVstoObject` metodę, aby rozszerzyć <xref:Microsoft.Office.Interop.Word.Document> obiektu, metoda zwraca <xref:Microsoft.Office.Tools.Word.Document> obiektu.  
  
 `GetVstoObject` Metody są przeznaczone do użycia głównie w projektach dodatku narzędzi VSTO. Można również użyć tych metod w projektach na poziomie dokumentu, ale będą działały inaczej i mają mniejszą liczbę zastosowań.  
  
 Aby ustalić, czy obiekt rozszerzonych został już wygenerowany dla danego obiektu macierzystego pakietu Office, należy użyć `HasVstoObject` metody. Aby uzyskać więcej informacji, zobacz [ustalić, czy obiekt pakietu Office zostały rozszerzone](#HasVstoObject).  
  
### <a name="generate-host-items"></a>Generowanie elementów hosta  
 Kiedy używasz `GetVstoObject` rozszerzenie obiektu poziomu dokumentu (oznacza to, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, lub <xref:Microsoft.Office.Interop.Word.Document>), zwróconego obiektu jest wywoływana *element hosta*. Element hosta to typ, który może zawierać inne obiekty, w tym inne obiekty rozszerzone i formantów. Jest on podobny odpowiedni typ w programie Word lub Excel podstawowego zestawu międzyoperacyjnego, ale ma dodatkowych funkcji. Aby uzyskać więcej informacji na temat elementów hosta, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).  
  
 Po wygenerowaniu elementu hosta służy do dodawania formantów zarządzanego do dokumentu, skoroszytu lub arkusza. Aby uzyskać więcej informacji, zobacz [Dodaj zarządzany formantów do dokumentów i arkuszy](#AddControls).  
  
#### <a name="to-generate-a-host-item-for-a-word-document"></a>Aby wygenerować element hosta dokumentu programu Word  
  
-   Poniższy przykład kodu demonstruje sposób generowania elementu hosta dla aktywnego dokumentu.  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Aby wygenerować element hosta skoroszytu programu Excel  
  
-   Poniższy przykład kodu demonstruje sposób generowania elementu hosta dla aktywnego skoroszytu.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Aby wygenerować element hosta arkusza programu Excel  
  
-   Poniższy przykład kodu demonstruje sposób generowania elementu hosta dla aktywnego arkusza w projekcie.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generate-listobject-host-controls"></a>Generowanie kontrolki hosta ListObject  
 Kiedy używasz `GetVstoObject` metodę, aby rozszerzyć <xref:Microsoft.Office.Interop.Excel.ListObject>, metoda zwraca <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Zawiera wszystkie funkcje oryginalny <xref:Microsoft.Office.Interop.Excel.ListObject>. Ponadto udostępnia dodatkowe funkcje i może być powiązana z danymi za pomocą modelu powiązanie danych formularzy Windows. Aby uzyskać więcej informacji, zobacz [kontrolki ListObject](../vsto/listobject-control.md).  
  
#### <a name="to-generate-a-host-control-for-a-listobject"></a>W celu wygenerowania kontrolki hosta dla ListObject  
  
-   Poniższy przykład kodu demonstruje sposób generowania <xref:Microsoft.Office.Tools.Excel.ListObject> pierwszy <xref:Microsoft.Office.Interop.Excel.ListObject> w aktywnym arkuszu w projekcie.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
###  <a name="AddControls"></a> Dodawanie formantów zarządzanego do dokumentów i arkuszy  
 Po wygenerowaniu <xref:Microsoft.Office.Tools.Word.Document> lub <xref:Microsoft.Office.Tools.Excel.Worksheet>, można dodać kontrolki do dokumentu lub arkusz kalkulacyjny, który rozszerzone te obiekty reprezentują. Aby dodać formanty, należy użyć `Controls` właściwość <xref:Microsoft.Office.Tools.Word.Document> lub <xref:Microsoft.Office.Tools.Excel.Worksheet>. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Można dodać kontrolek formularzy Windows Forms lub *hostowania kontrolek*. Kontrolki hosta jest formantem, dostarczone przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] to opakowuje odpowiedni formant w programie Word lub Excel podstawowego zestawu międzyoperacyjnego. Kontrolki hosta uwidacznia wszystkie zachowania obiektu bazowego natywnych pakietu Office. Ponadto wywołuje zdarzenia i może być powiązana z danymi za pomocą modelu powiązanie danych formularzy Windows. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  Nie można dodać <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontrolki w arkuszu lub <xref:Microsoft.Office.Tools.Word.XMLNode> lub <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki do dokumentu, za pomocą dodatku narzędzi VSTO. Te kontrolki hosta nie można dodać programowo. Aby uzyskać więcej informacji, zobacz [ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="persist-and-remove-controls"></a>Zostaną zachowane, a usuwanie kontrolek  
 Po dodaniu zarządzane formanty w dokumencie lub arkuszu formanty nie są zachowywane po zapisaniu dokumentu i następnie zamknięty. Wszystkie formanty hosta zostaną usunięte, tak aby tylko podstawowy natywnych obiektów pakietu Office są pozostawione. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject> staje się <xref:Microsoft.Office.Interop.Excel.ListObject>. Wszystkie kontrolki Windows Forms są również usuwane, ale otoki ActiveX dla formantów są pozostawione w dokumencie. Należy dołączyć kod dodatku narzędzi VSTO dla programów wyczyścić kontrolki lub ponownie utworzyć formanty przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [kontrolek dynamicznych w dokumentach pakietu Office utrwalenia](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## <a name="access-application-level-events-on-documents-and-workbooks"></a>Zdarzenia dodatku poziomu aplikacji dostęp do dokumentów i skoroszytów  
 Niektóre zdarzenia dokumentu, skoroszytu i arkuszy w macierzystym modele obiektów programu Word i Excel są wywoływane tylko na poziomie aplikacji. Na przykład <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenie jest wywoływane, gdy dokument zostanie otwarty w programie Word, ale to zdarzenie jest zdefiniowany w <xref:Microsoft.Office.Interop.Word.Application> klasy, a nie <xref:Microsoft.Office.Interop.Word.Document> klasy.  
  
 Gdy używasz tylko natywny obiektów pakietu Office w dodatku narzędzi VSTO dla programów, należy obsługę następujących zdarzeń na poziomie aplikacji, a następnie wpisz dodatkowy kod w celu ustalenia, czy dokument, który podniósł zdarzenie jest taki, który został dostosowany. Obiekty hosta oferuje te zdarzenia na poziomie dokumentu, dlatego jest łatwiejsze do obsługi zdarzeń dla określonego dokumentu. Można wygenerować element hosta, a następnie obsługi zdarzeń dla tego elementu hosta.  
  
### <a name="example-that-uses-native-word-objects"></a>Przykład, który używa natywnych obiektów programu Word  
 Poniższy przykład kodu pokazuje, jak obsługiwać zdarzenia dodatku poziomu aplikacji dla dokumentów programu Word. `CreateDocument` Metoda tworzy nowy dokument, a następnie definiuje <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> program obsługi zdarzeń, który uniemożliwia są zapisywane w tym dokumencie. Zdarzenie jest zdarzenie dodatku poziomu aplikacji, które jest wywoływane dla <xref:Microsoft.Office.Interop.Word.Application> obiektu i program obsługi zdarzeń musi porównywać `Doc` parametrem `document1` obiektu, aby ustalić, czy `document1` reprezentuje zapisany dokument.  
  
 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>Przykłady z zastosowaniem element hosta  
 Poniższe przykłady kodu upraszcza ten proces obsługi <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> zdarzenia <xref:Microsoft.Office.Tools.Word.Document> element hosta. `CreateDocument2` Generuje metodę w tych przykładach <xref:Microsoft.Office.Tools.Word.Document> rozszerzający `document2` obiektu, a następnie definiuje <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> program obsługi zdarzeń, który uniemożliwia zapisanie dokumentu. Program obsługi zdarzeń jest wywoływany tylko wtedy, gdy `document2` jest zapisywana i może anulować zapisu akcji bez wykonywania dodatkowych działań, aby sprawdzić, który dokument został zapisany.  
  
 Poniższy przykład kodu demonstruje tego zadania.  
  
 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> Określić, czy obiekt pakietu Office został rozszerzony  
 Aby ustalić, czy obiekt rozszerzonych został już wygenerowany dla danego obiektu macierzystego pakietu Office, należy użyć `HasVstoObject` metody. Ta metoda zwraca **true** Jeśli rozszerzonej obiekt został już wygenerowany.  
  
 Użyj `Globals.Factory.HasVstoMethod` metody. Przekaż w natywnych obiektów programu Word lub Excel, takich jak <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet>, który chcesz przetestować rozszerzonego obiektu.  
  
 `HasVstoObject` Metoda jest przydatna, gdy użytkownik chce uruchomić kod, tylko wtedy, gdy określony obiekt Office ma obiektu rozszerzonego. Na przykład, jeśli masz dodatku narzędzi VSTO programu Word, który obsługuje <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenie, aby usunąć zarządzane formanty z dokumentu, zanim zostaną zapisane, użyj `HasVstoObject` metodę pozwala ustalić, czy dokument został rozszerzony. Jeśli dokument nie został rozszerzony, nie mogą mieć zarządzane formanty i program obsługi zdarzeń mogą powrócić bez próby wyczyścić kontrolki do dokumentu.  
  
## <a name="see-also"></a>Zobacz także  
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)  
