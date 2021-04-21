---
title: Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania
description: Dowiedz się, jak dodawać kontrolki do Microsoft Office programu Word i Microsoft Office programu Excel w czasie uruchamiania.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 64a4d4dcd2e6115a3b8093a0a9338cb126f49a28
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825137"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania
  Kontrolki można dodawać do dokumentu Microsoft Office Word i Microsoft Office programu Excel w czasie uruchamiania. Można je również usunąć w czasie uruchamiania. Kontrolki, które dodajesz lub usuwasz w czasie uruchamiania, są nazywane *kontrolkami dynamicznymi*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 W tym temacie opisano następujące kwestie:

- [Zarządzaj kontrolkami w czasie uruchamiania przy użyciu kolekcji kontrolek.](#ControlsCollection)

- [Dodaj kontrolki hosta do dokumentów](#HostControls).

- [Dodaj Windows Forms kontrolki do dokumentów](#WindowsForms).

## <a name="manage-controls-at-run-time-by-using-control-collections"></a><a name="ControlsCollection"></a> Zarządzanie kontrolkami w czasie uruchamiania przy użyciu kolekcji kontrolek
 Aby dodać, pobrać lub usunąć kontrolki w czasie działania, użyj metod pomocnika <xref:Microsoft.Office.Tools.Excel.ControlCollection> obiektów <xref:Microsoft.Office.Tools.Word.ControlCollection> i .

 Sposób uzyskiwania dostępu do tych obiektów zależy od typu projektu, który opracowujesz:

- W projekcie na poziomie dokumentu dla programu Excel użyj <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> właściwości klas , i `Sheet1` `Sheet2` `Sheet3` . Aby uzyskać więcej informacji na temat tych klas, zobacz [Element hosta arkusza](../vsto/worksheet-host-item.md).

- W projekcie na poziomie dokumentu dla programu Word użyj <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości `ThisDocument` klasy . Aby uzyskać więcej informacji na temat tej klasy, zobacz [Dokument elementu hosta](../vsto/document-host-item.md).

- W projekcie dodatku VSTO dla programu Excel lub Word użyj właściwości `Controls` lub <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> wygenerowanej w czasie uruchamiania. Aby uzyskać więcej informacji na temat generowania tych obiektów w czasie działania, zobacz Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatekach [VSTO w czasie uruchamiania.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="add-controls"></a>Dodawanie kontrolek
 Typy <xref:Microsoft.Office.Tools.Excel.ControlCollection> i obejmują metody pomocników, których można używać do dodawania kontrolek hosta i popularnych kontrolek Windows Forms kontrolek do dokumentów <xref:Microsoft.Office.Tools.Word.ControlCollection> i arkuszy. Każda nazwa metody ma `Add` *klasę kontrolek formatu*, gdzie *klasa sterowania* jest nazwą klasy kontrolki, którą chcesz dodać. Aby na przykład dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> metody .

 Poniższy przykład kodu dodaje do <xref:Microsoft.Office.Tools.Excel.NamedRange> w `Sheet1` projekcie na poziomie dokumentu dla programu Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb" id="Snippet3":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs" id="Snippet3":::


### <a name="access-and-delete-controls"></a>Kontrolki dostępu i usuwania
 Możesz użyć właściwości lub , aby iterować po wszystkich kontrolkach w dokumencie, w tym kontrolkach dodanych `Controls` <xref:Microsoft.Office.Tools.Excel.Worksheet> w czasie <xref:Microsoft.Office.Tools.Word.Document> projektowania. Kontrolki, które dodajesz w czasie projektowania, są również nazywane *kontrolkami statycznych*.

 Kontrolki dynamiczne można usunąć, wywołując metodę kontrolki `Delete` lub wywołując `Remove` metodę każdej kolekcji Controls. W poniższym przykładzie kodu użyto metody , aby usunąć z pliku w <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> `Sheet1` projekcie na poziomie dokumentu dla programu Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs" id="Snippet4":::


 Nie można usunąć kontrolek statycznych w czasie uruchamiania. Jeśli spróbujesz użyć metody `Delete` lub w celu usunięcia `Remove` statycznej kontrolki, zostanie <xref:Microsoft.Office.Tools.CannotRemoveControlException> zgłoszony wyjątek .

> [!NOTE]
> Nie usuwaj programowo kontrolek w `Shutdown` programie obsługi zdarzeń dokumentu. Elementy interfejsu użytkownika dokumentu nie są już dostępne po `Shutdown` zdarzeniu. Jeśli chcesz usunąć kontrolki przed zamknięciem dokumentu, dodaj kod do procedury obsługi zdarzeń dla innego zdarzenia, takiego jak lub dla programu <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> Word lub , lub dla programu <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose> <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> Excel.

## <a name="add-host-controls-to-documents"></a><a name="HostControls"></a> Dodawanie kontrolek hosta do dokumentów

Podczas programowego dodawania kontrolek hosta do dokumentów należy podać nazwę jednoznacznie identyfikującą kontrolkę i określić, gdzie dodać kontrolkę do dokumentu. Aby uzyskać szczegółowe instrukcje, zobacz następujące tematy:

- [2017: Dodawanie kontrolek ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [2017: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [2019: Dodawanie kontrolek wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [How to: Add Content controls to Word documents (2.03.2017: Dodawanie kontrolek zawartości do](../vsto/how-to-add-content-controls-to-word-documents.md)

- [How to: Add Bookmark controls to Word documents (Jak dodać kontrolki zakładek do dokumentów programu Word)](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Aby uzyskać więcej informacji na temat kontrolek hosta, zobacz [Host items and host controls overview (Elementy hosta i kontrolki hosta — omówienie).](../vsto/host-items-and-host-controls-overview.md)

Gdy dokument zostanie zapisany, a następnie zamknięty, wszystkie dynamicznie utworzone kontrolki hosta zostaną odłączone od zdarzeń i utracą funkcjonalność powiązania danych. Możesz dodać kod do rozwiązania, aby ponownie utworzyć kontrolki hosta po ponownym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

> [!NOTE]
> Metody pomocnika nie są dostępne dla następujących kontrolek hosta, ponieważ tych kontrolek nie można dodać programowo do dokumentów: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Word.XMLNode> , i <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="add-windows-forms-controls-to-documents"></a><a name="WindowsForms"></a> Dodawanie Windows Forms kontrolek do dokumentów
 Podczas programowego dodawania kontrolki Windows Forms do dokumentu należy podać lokalizację kontrolki i nazwę, która jednoznacznie identyfikuje kontrolkę. Metoda [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] udostępnia metody pomocnika dla każdej kontrolki. Te metody są przeciążone, dzięki czemu można przekazać zakres lub określone współrzędne dla lokalizacji kontrolki.

 Po zapisaniu i zamknięciu dokumentu wszystkie dynamicznie Windows Forms są usuwane z dokumentu. Możesz dodać kod do rozwiązania, aby ponownie utworzyć kontrolki po ponownym otwarciu dokumentu. Jeśli tworzysz dynamiczne kontrolki Windows Forms za pomocą dodatku VSTO, otoki ActiveX dla kontrolek zostaną pozostawione w dokumencie. Aby uzyskać więcej informacji, zobacz [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

> [!NOTE]
> Windows Forms nie można programowo dodawać do chronionych dokumentów. Jeśli programowo nie chcesz chronić dokumentu programu Word lub arkusza programu Excel w celu dodania kontrolki, musisz napisać dodatkowy kod, aby usunąć otokę ActiveX kontrolki po zamknięciu dokumentu. Otoka ActiveX kontrolki nie jest automatycznie usuwana z chronionych dokumentów.

### <a name="add-custom-controls"></a>Dodaj formanty niestandardowe
 Jeśli chcesz dodać kontrolkę , która nie jest obsługiwana przez dostępne metody pomocnika, takie jak niestandardowa kontrolka <xref:System.Windows.Forms.Control> użytkownika, użyj następujących metod:

- W przypadku programu Excel użyj <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> jednej z metod obiektu <xref:Microsoft.Office.Tools.Excel.ControlCollection> .

- W przypadku programu Word użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> jednej z metod obiektu <xref:Microsoft.Office.Tools.Word.ControlCollection> .

  Aby dodać kontrolkę, przekaż do metody lokalizację kontrolki oraz nazwę, która jednoznacznie identyfikuje <xref:System.Windows.Forms.Control> `AddControl` kontrolkę. Metoda zwraca obiekt , który definiuje sposób interakcji `AddControl` kontrolki z arkuszem lub dokumentem. Metoda `AddControl` zwraca <xref:Microsoft.Office.Tools.Excel.ControlSite> obiekt (dla programu Excel) <xref:Microsoft.Office.Tools.Word.ControlSite> lub obiekt (dla programu Word).

  Poniższy przykład kodu przedstawia sposób użycia metody w celu dynamicznego dodawania niestandardowej kontrolki użytkownika do arkusza w projekcie programu <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> Excel na poziomie dokumentu. W tym przykładzie kontrolka użytkownika ma nazwę `UserControl1` , a <xref:Microsoft.Office.Interop.Excel.Range> kontrolka ma nazwę `range1` . Aby użyć tego przykładu, uruchom go z `Sheet` *n* klasy w projekcie.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet2":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet2":::

### <a name="use-members-of-custom-controls"></a>Używanie elementów członkowskich kontrolek niestandardowych
 Po użyciu jednej z metod dodawania kontrolki do arkusza lub dokumentu `AddControl` masz teraz dwa różne obiekty sterujące:

- Kontrolka <xref:System.Windows.Forms.Control> reprezentująca kontrolkę niestandardową.

- Obiekt `ControlSite` `OLEObject` , lub `OLEControl` reprezentujący kontrolkę po dodaniu jej do arkusza lub dokumentu.

  Między tymi kontrolkami jest współdzielonych wiele właściwości i metod. Ważne jest, aby uzyskać dostęp do tych elementów członkowskich za pomocą odpowiedniej kontrolki:

- Aby uzyskać dostęp do elementów członkowskich należących tylko do kontrolki niestandardowej, użyj kontrolki <xref:System.Windows.Forms.Control> .

- Aby uzyskać dostęp do elementów członkowskich, które są współużytkują kontrolki, użyj `ControlSite` `OLEObject` obiektu , lub `OLEControl` .

  Jeśli uzyskujesz dostęp do udostępnionego członka z folderu , może to się nie powieść bez ostrzeżenia lub powiadomienia <xref:System.Windows.Forms.Control> albo może dawać nieprawidłowe wyniki. Zawsze używaj metod lub właściwości obiektu , lub , chyba że potrzebna metoda lub właściwość nie jest dostępna. Tylko wtedy należy odwołać się `ControlSite` `OLEObject` do obiektu `OLEControl` <xref:System.Windows.Forms.Control> .

  Na przykład zarówno <xref:Microsoft.Office.Tools.Excel.ControlSite> klasa , jak i klasa mają właściwość <xref:System.Windows.Forms.Control> `Top` . Aby uzyskać lub ustawić odległość między górnej części kontrolki i górnej części dokumentu, użyj właściwości , a nie <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> <xref:Microsoft.Office.Tools.Excel.ControlSite> właściwości <xref:System.Windows.Forms.Control.Top%2A> <xref:System.Windows.Forms.Control> .

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet3":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet3":::

## <a name="see-also"></a>Zobacz też
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [How to: Add ListObject controls to worksheets (Jak dodać kontrolki ListObject do arkuszy)](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Jak dodać kontrolki NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Jak dodać kontrolki wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [How to: Add content controls to Word documents (Jak dodać kontrolki zawartości do dokumentów programu Word)](../vsto/how-to-add-content-controls-to-word-documents.md)
- [How to: Add Bookmark controls to Word documents (Jak dodać kontrolki zakładek do dokumentów programu Word)](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Windows Forms kontroli w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Jak dodać kontrolki Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
