---
title: Ograniczenia programowe elementów hosta i kontrolek hosta
description: Zapoznaj się z podstawowymi różnicami między zachowaniem elementów hosta i formantów hosta oraz natywnymi obiektami pakietu Office w czasie wykonywania.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fbc3258f3ea7e0b3cc93a2887dfff5a3bfefb19d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891894"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Ograniczenia programowe elementów hosta i kontrolek hosta
  Każdy element hosta i formant hosta są zaprojektowane tak, aby zachowywały się jak odpowiadający mu Microsoft Office natywny obiekt programu Word lub Microsoft Office programu Excel, z dodatkowymi funkcjami. Istnieją jednak podstawowe różnice między zachowaniem elementów hosta i formantów hosta oraz natywnymi obiektami pakietu Office w czasie wykonywania.

 Aby uzyskać ogólne informacje na temat elementów hosta i kontrolek hosta, zobacz temat [elementy hosta i kontrolki](../vsto/host-items-and-host-controls-overview.md)hosta.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Programowe tworzenie elementów hosta
 W przypadku programistycznego tworzenia lub otwierania dokumentu, skoroszytu lub arkusza w czasie wykonywania przy użyciu modelu obiektów programu Word lub Excel element nie jest elementem hosta. Zamiast tego nowy obiekt jest natywnym obiektem pakietu Office. Na przykład, jeśli używasz <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metody do tworzenia nowego dokumentu programu Word w czasie wykonywania, będzie on obiektem macierzystym, <xref:Microsoft.Office.Interop.Word.Document> a nie <xref:Microsoft.Office.Tools.Word.Document> elementem hosta. Podobnie podczas tworzenia nowego arkusza w czasie wykonywania przy użyciu <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody uzyskuje się obiekt macierzysty, <xref:Microsoft.Office.Interop.Excel.Worksheet> a nie <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta.

 W projektach na poziomie dokumentu nie można tworzyć elementów hosta w czasie wykonywania. Elementy hosta mogą być tworzone tylko w czasie projektowania w projektach na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [dokument](../vsto/document-host-item.md)element hosta, [element hosta skoroszytu](../vsto/workbook-host-item.md)i [element hosta arkusza](../vsto/worksheet-host-item.md).

 W projektach dodatku VSTO można tworzyć <xref:Microsoft.Office.Tools.Word.Document> , <xref:Microsoft.Office.Tools.Excel.Workbook> lub <xref:Microsoft.Office.Tools.Excel.Worksheet> hostować elementy w czasie wykonywania. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Programistyczne Tworzenie formantów hosta
 Można programowo dodać kontrolki hosta do <xref:Microsoft.Office.Tools.Word.Document> elementu lub <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Nie można dodać formantów hosta do natywnych <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet> .

> [!NOTE]
> Następujących kontrolek hosta nie można dodać programowo do arkuszy lub dokumentów: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , <xref:Microsoft.Office.Tools.Word.XMLNode> i <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Zrozumienie różnic między elementami hosta, kontrolkami hosta i natywnymi obiektami pakietu Office
 Dla każdego elementu hosta i kontrolki hosta istnieje podstawowe natywne Microsoft Office Word lub Microsoft Office obiektu programu Excel. Możesz uzyskać dostęp do bazowego obiektu za pomocą właściwości InnerObject elementu hosta lub formantu hosta. Nie istnieje jednak możliwość rzutowania natywnego obiektu pakietu Office do odpowiadającego mu elementu hosta lub kontrolki hosta. Jeśli spróbujesz rzutować natywny obiekt pakietu Office na typ elementu hosta lub kontrolki hosta, <xref:System.InvalidCastException> zostanie zgłoszony.

 Istnieje kilka scenariuszy, w których różnice między typami elementów hosta i kontrolek hosta oraz bazowymi obiektami natywnych pakietu Office mogą mieć wpływ na kod.

### <a name="pass-host-controls-to-methods-and-properties"></a>Przekaż kontrolki hosta do metod i właściwości
 W programie Word nie można przekazać kontrolki hosta do metody lub właściwości, która wymaga natywnego obiektu programu Word jako parametru. Musisz użyć właściwości InnerObject kontrolki hosta, aby zwrócić bazowego obiektu programu Word. Na przykład można przekazać <xref:Microsoft.Office.Interop.Word.Bookmark> obiekt do metody przez przekazanie <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki hosta do metody.

 W programie Excel, musisz użyć właściwości Wewnętrznejobject kontrolki hosta, aby przekazać formant hosta do metody lub właściwości, gdy metoda lub właściwość oczekuje bazowego obiektu programu Excel.

 Poniższy przykład tworzy <xref:Microsoft.Office.Tools.Excel.NamedRange> formant i przekazuje go do <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody. Kod używa <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> Właściwości nazwanego zakresu do zwrócenia bazowego biura <xref:Microsoft.Office.Interop.Excel.Range> , który jest wymagany przez <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodę.

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>Zwracane typy natywnych metod i właściwości pakietu Office
 Większość metod i właściwości elementów hosta zwraca podstawowy natywny obiekt pakietu Office, na którym jest oparty element hosta. Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> Właściwość <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki hosta w programie Excel zwraca <xref:Microsoft.Office.Interop.Excel.Worksheet> obiekt, a nie <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta. Podobnie <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> Właściwość <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kontrolki hosta w programie Word zwraca <xref:Microsoft.Office.Interop.Word.Document> obiekt, a nie <xref:Microsoft.Office.Tools.Word.Document> element hosta.

### <a name="access-collections-of-host-controls"></a>Dostęp do kolekcji formantów hosta
 Nie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] udostępnia pojedynczych kolekcji dla każdego typu formantu hosta. Zamiast tego należy użyć właściwości Controls elementu hosta, aby wykonać iterację wszystkich zarządzanych formantów (zarówno formantów hosta, jak i formantów Windows Forms) w dokumencie lub arkuszu, a następnie poszukać elementów pasujących do typu kontrolki hosta, która Cię interesuje. Poniższy przykład kodu sprawdza każdy formant w dokumencie programu Word i określa, czy formant jest <xref:Microsoft.Office.Tools.Word.Bookmark> .

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 Aby uzyskać więcej informacji na temat właściwości kontrolek elementów hosta, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Modele obiektów programów Word i Excel zawierają właściwości, które uwidaczniają kolekcje natywnych kontrolek dokumentów i arkuszy. Nie można uzyskać dostępu do formantów zarządzanych przy użyciu tych właściwości. Na przykład nie można wyliczyć każdej <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki hosta w dokumencie przy użyciu <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> właściwości <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> właściwości <xref:Microsoft.Office.Tools.Word.Document> . Te właściwości zawierają tylko <xref:Microsoft.Office.Interop.Word.Bookmark> kontrolki w dokumencie. nie zawierają one <xref:Microsoft.Office.Tools.Word.Bookmark> formantów hosta w dokumencie.

## <a name="see-also"></a>Zobacz też
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
