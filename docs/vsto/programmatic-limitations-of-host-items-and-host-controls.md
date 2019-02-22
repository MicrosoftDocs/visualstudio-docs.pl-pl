---
title: Ograniczenia programowe elementów hosta i kontrolek hosta
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 488551d9b86ec7bd09adadd92d515cac1a53e841
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596154"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Ograniczenia programowe elementów hosta i kontrolek hosta
  Każdy element hosta i kontrolki hosta jest przeznaczony do zachowują się jak odpowiedni natywnego Microsoft Office Word lub obiektu programu Microsoft Office Excel z dodatkowymi funkcjami. Istnieją jednak pewne podstawowe różnice między zachowanie elementów hosta i kontrolek hosta i natywnego obiektów pakietu Office w czasie wykonywania.

 Aby uzyskać ogólne informacje dotyczące elementów hosta i kontrolek hosta, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Programowe tworzenie elementów hosta
 Gdy programowo utworzyć lub otworzyć dokumentu, skoroszytu lub arkusza w czasie wykonywania za pomocą modelu obiektów programu Word lub Excel, element nie jest element hosta. Zamiast tego nowy obiekt jest obiektem natywnych pakietu Office. Na przykład, jeśli używasz <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodę, aby utworzyć nowy dokument programu Word w czasie wykonywania, będzie ona natywny <xref:Microsoft.Office.Interop.Word.Document> obiektu zamiast <xref:Microsoft.Office.Tools.Word.Document> element hosta. Podobnie, po utworzeniu nowego arkusza w czasie wykonywania za pomocą <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody, otrzymasz macierzystej <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu zamiast <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta.

 W projektach na poziomie dokumentu nie można utworzyć elementów hosta w czasie wykonywania. Obiekty hosta mogą być tworzone tylko w czasie projektowania w projektach na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [element hosta dokumentu](../vsto/document-host-item.md), [element hosta skoroszytu](../vsto/workbook-host-item.md), i [element hosta arkusza](../vsto/worksheet-host-item.md).

 W projektach dodatku narzędzi VSTO dla programów, można utworzyć <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, lub <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementy w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Programowe tworzenie kontrolek hosta
 Możesz programowo dodane formanty hosta do <xref:Microsoft.Office.Tools.Word.Document> lub <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Nie można dodać kontrolki hosta do macierzystej <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet>.

> [!NOTE]
>  Następujące kontrolki hosta nie można programowo dodać do arkuszy lub dokumenty: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, i <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Opis typu różnic między elementów hosta, formanty hosta i natywnego obiektów pakietu Office
 Dla każdego elementu hosta i kontrolki hosta istnieje podstawowych natywnych obiektów Microsoft Office Word lub Microsoft Office Excel. Obiekt źródłowy dostęp za pomocą właściwości InnerObject elementu hosta lub kontrolki hosta. Jednak nie ma możliwości można rzutować natywnego obiektu pakietu Office, na jej odpowiadający element hosta lub kontrolki hosta. Jeśli zostanie podjęta próba rzutowania natywnych obiektów pakietu Office do typu element hosta lub kontrolki hosta <xref:System.InvalidCastException> zgłaszany.

 Istnieje kilka scenariuszy, w którym różnice między typami elementów hosta i kontrolek hosta i natywnego obiektów pakietu Office może mieć wpływ na kod.

### <a name="pass-host-controls-to-methods-and-properties"></a>Formanty hosta — dostęp próbny do metod i właściwości
 W programie Word nie można przekazać formant hosta, metody lub właściwości, która wymaga natywnego obiektu Word jako parametr. Właściwość InnerObject kontrolki hosta musi być zwracają obiekt natywny programu Word. Na przykład, można przekazać <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu do metody przez przekazanie <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> właściwość <xref:Microsoft.Office.Tools.Word.Bookmark> hostować kontrolę do metody.

 W programie Excel musi być właściwością InnerObject kontrolki hosta przekazać do metody lub właściwości kontrolki hosta, gdy metoda lub właściwość oczekuje obiektu źródłowego programu Excel.

 Poniższy przykład tworzy <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli i przekazuje go do <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody. Kod używa <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> właściwość nazwany zakres do zwrócenia bazowego Office <xref:Microsoft.Office.Interop.Excel.Range> jest to wymagane <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody.

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>Zwracane typy natywne Office metod i właściwości
 Większość metod i właściwości elementów hosta Zwróć natywnych Office obiektu źródłowego podstawie element hosta. Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> właściwość <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w programie Excel zwraca hosta <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu zamiast <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta. Podobnie <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> właściwość <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kontrolki w programie Word zwraca hosta <xref:Microsoft.Office.Interop.Word.Document> obiektu zamiast <xref:Microsoft.Office.Tools.Word.Document> element hosta.

### <a name="access-collections-of-host-controls"></a>Dostęp do kolekcji kontrolki hosta
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Nie dostarcza poszczególnych kolekcji dla każdego typu formantu hosta. Zamiast tego należy użyć do iteracji przez wszystkie formanty zarządzanego (formanty hosta i kontrolek formularzy Windows Forms) w dokumencie lub arkuszu właściwości kontrolki elementu hosta, a następnie Wyszukaj elementy, które jest zgodny z typem formantu hosta, który Cię interesuje. Poniższy przykład kodu sprawdza każdego formantu w dokumencie programu Word i określa, czy kontrolka jest <xref:Microsoft.Office.Tools.Word.Bookmark>.

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 Aby uzyskać więcej informacji na temat właściwości kontrolek elementów hosta, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Modele obiektów programu Word i Excel zawierają właściwości, które uwidaczniają kolekcje natywne kontrolki na dokumenty i arkusze. Zarządzane formanty nie może uzyskać dostępu, używając tych właściwości. Na przykład nie jest możliwe wyliczenie każdego <xref:Microsoft.Office.Tools.Word.Bookmark> hostować kontroli w dokumencie przy użyciu <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> właściwość <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> właściwość <xref:Microsoft.Office.Tools.Word.Document>. Te właściwości obejmują tylko <xref:Microsoft.Office.Interop.Word.Bookmark> kontrolek w dokumencie; nie zawierają <xref:Microsoft.Office.Tools.Word.Bookmark> hostowania kontrolek w dokumencie.

## <a name="see-also"></a>Zobacz także
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
