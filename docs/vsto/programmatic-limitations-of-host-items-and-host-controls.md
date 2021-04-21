---
title: Ograniczenia programowe elementów hosta i kontrolek hosta
description: Poznaj podstawowe różnice między zachowaniem elementów hosta i kontrolek hosta a natywnymi obiektami pakietu Office w czasie uruchamiania.
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
ms.openlocfilehash: 463543a40ac9443959b06cf9f65dad4c99c52ee3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828829"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Ograniczenia programowe elementów hosta i kontrolek hosta
  Każdy element hosta i kontrolka hosta są zaprojektowane tak, aby zachowywały się jak odpowiadające im natywne Microsoft Office programu Word lub Microsoft Office Excel z dodatkowymi funkcjami. Istnieją jednak pewne podstawowe różnice między zachowaniem elementów hosta i kontrolek hosta a natywnymi obiektami pakietu Office w czasie działania.

 Aby uzyskać ogólne informacje na temat elementów hosta i kontrolek hosta, zobacz [Host items and host controls overview (Elementy hosta i kontrolki hosta — omówienie).](../vsto/host-items-and-host-controls-overview.md)

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Programowe tworzenie elementów hosta
 W przypadku programowego tworzenia lub otwierania dokumentu, skoroszytu lub arkusza w czasie uruchamiania przy użyciu modelu obiektów programu Word lub Excel element nie jest elementem hosta. Zamiast tego nowy obiekt jest natywnym obiektem pakietu Office. Jeśli na przykład użyjemy metody do utworzenia nowego dokumentu programu Word w czasie działania, będzie to obiekt natywny, <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> <xref:Microsoft.Office.Interop.Word.Document> a nie element <xref:Microsoft.Office.Tools.Word.Document> hosta. Podobnie podczas tworzenia nowego arkusza w czasie działania przy użyciu metody otrzymasz obiekt natywny, <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> <xref:Microsoft.Office.Interop.Excel.Worksheet> a nie element <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta.

 W projektach na poziomie dokumentu nie można tworzyć elementów hosta w czasie uruchamiania. Elementy hosta można tworzyć tylko w czasie projektowania w projektach na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [Document host item (Element hosta dokumentu),](../vsto/document-host-item.md) [Workbook host item (Element hosta skoroszytu)](../vsto/workbook-host-item.md) [i Worksheet host item (Element hosta arkusza).](../vsto/worksheet-host-item.md)

 W projektach dodatków VSTO można tworzyć <xref:Microsoft.Office.Tools.Word.Document> elementy <xref:Microsoft.Office.Tools.Excel.Workbook> , lub <xref:Microsoft.Office.Tools.Excel.Worksheet> hostować je w czasie uruchamiania. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

## <a name="programmatically-create-host-controls"></a>Programowe tworzenie kontrolek hosta
 Kontrolki hosta można programowo dodawać do elementu <xref:Microsoft.Office.Tools.Word.Document> hosta lub w czasie <xref:Microsoft.Office.Tools.Excel.Worksheet> uruchamiania. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Nie można dodać kontrolek hosta do natywnego <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet> .

> [!NOTE]
> Następujących kontrolek hosta nie można dodać programowo do arkuszy lub dokumentów: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Word.XMLNode> , i <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Opis różnic typu między elementami hosta, kontrolkami hosta i natywnymi obiektami pakietu Office
 Dla każdego elementu hosta i kontrolki hosta istnieje podstawowy natywny obiekt programu Word Microsoft Office lub Microsoft Office Excel. Dostęp do bazowego obiektu można uzyskać za pomocą właściwości InnerObject elementu hosta lub kontrolki hosta. Nie ma jednak możliwości rzutowania natywnego obiektu pakietu Office na odpowiedni element hosta lub kontrolkę hosta. Jeśli spróbujesz rzutować natywny obiekt pakietu Office na typ elementu hosta lub kontrolki hosta, <xref:System.InvalidCastException> zgłaszany jest element .

 Istnieje kilka scenariuszy, w których różnice między typami elementów hosta i kontrolek hosta a bazowymi natywnymi obiektami pakietu Office mogą mieć wpływ na kod.

### <a name="pass-host-controls-to-methods-and-properties"></a>Przekaż kontrolki hosta do metod i właściwości
 W programie Word nie można przekazać kontrolki hosta do metody lub właściwości, która wymaga natywnego obiektu word jako parametru. Należy użyć właściwości InnerObject kontrolki hosta, aby zwrócić źródłowy obiekt macierzysty programu Word. Na przykład można przekazać obiekt do metody, przekazując właściwość <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki hosta do metody .

 W programie Excel należy użyć właściwości InnerObject kontrolki hosta, aby przekazać kontrolkę hosta do metody lub właściwości, gdy metoda lub właściwość oczekuje bazowego obiektu programu Excel.

 Poniższy przykład tworzy <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę i przekazuje ją do <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody . Kod używa właściwości nazwanego zakresu w celu zwrócenia podstawowego pakietu <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> <xref:Microsoft.Office.Interop.Excel.Range> Office, który jest wymagany przez <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodę .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet28":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet28":::

### <a name="return-types-of-native-office-methods-and-properties"></a>Zwraca typy natywnych metod i właściwości pakietu Office
 Większość metod i właściwości elementów hosta zwraca bazowy natywny obiekt pakietu Office, na którym bazuje element hosta. Na przykład właściwość <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> kontrolki hosta w <xref:Microsoft.Office.Tools.Excel.NamedRange> programie Excel zwraca <xref:Microsoft.Office.Interop.Excel.Worksheet> obiekt, a nie <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta. Podobnie właściwość <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> kontrolki hosta w <xref:Microsoft.Office.Tools.Word.RichTextContentControl> programie Word zwraca <xref:Microsoft.Office.Interop.Word.Document> obiekt, a nie <xref:Microsoft.Office.Tools.Word.Document> element hosta.

### <a name="access-collections-of-host-controls"></a>Uzyskiwanie dostępu do kolekcji kontrolek hosta
 Nie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zapewnia poszczególnych kolekcji dla każdego typu kontrolki hosta. Zamiast tego użyj właściwości Controls elementu hosta, aby iterować po wszystkich kontrolkach zarządzanych (zarówno kontrolkach hosta, jak i kontrolkach Windows Forms) w dokumencie lub arkuszu, a następnie poszukaj elementów, które pasują do typu kontrolki hosta, która Cię interesuje. Poniższy przykład kodu sprawdza każdą kontrolkę w dokumencie programu Word i określa, czy kontrolka jest <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolką .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet10":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet10":::

 Aby uzyskać więcej informacji na temat właściwości Kontrolki elementów hosta, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Modele obiektów programów Word i Excel obejmują właściwości, które uwidoczniają kolekcje natywnych kontrolek w dokumentach i arkuszach. Przy użyciu tych właściwości nie można uzyskać dostępu do kontrolek zarządzanych. Na przykład nie można wyliczyć każdej kontrolki hosta w dokumencie przy użyciu właściwości lub <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> właściwości <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> <xref:Microsoft.Office.Tools.Word.Document> . Te właściwości obejmują tylko <xref:Microsoft.Office.Interop.Word.Bookmark> kontrolki w dokumencie; nie zawierają kontrolek <xref:Microsoft.Office.Tools.Word.Bookmark> hosta w dokumencie.

## <a name="see-also"></a>Zobacz też
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
