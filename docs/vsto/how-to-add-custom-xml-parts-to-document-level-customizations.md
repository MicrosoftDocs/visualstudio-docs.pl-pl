---
title: 'How to: Add custom XML parts to document-level customizations (Jak dodać niestandardowe części XML do dostosowań na poziomie dokumentu)'
description: Dowiedz się, jak przechowywać dane XML w skoroszycie programu Excel Microsoft Office excel lub w Microsoft Office Word, tworząc niestandardową część XML w dostosowywaniu na poziomie dokumentu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 99374a2daded3c4b49b60053a69cd1ff7c4dffe8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827698"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>How to: Add custom XML parts to document-level customizations (Jak dodać niestandardowe części XML do dostosowań na poziomie dokumentu)
  Dane XML można przechowywać w skoroszycie programu Excel Microsoft Office excel lub w Microsoft Office word, tworząc niestandardową część XML w dostosowywaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [Omówienie niestandardowych części XML.](../vsto/custom-xml-parts-overview.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio nie zapewnia projektów na poziomie dokumentu dla Microsoft Office PowerPoint. Aby uzyskać informacje na temat dodawania niestandardowej części XML do prezentacji programu PowerPoint przy użyciu dodatku VSTO, zobacz Jak dodać niestandardowe części XML do dokumentów przy użyciu dodatków [VSTO.](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Aby dodać niestandardową część XML do skoroszytu programu Excel

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w skoroszycie. Obiekt <xref:Microsoft.Office.Core.CustomXMLPart> zawiera ciąg XML, który ma być zapisywany w skoroszycie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb" id="Snippet1":::

2. Dodaj metodę `AddCustomXmlPartToWorkbook` do klasy `ThisWorkbook` w projekcie na poziomie dokumentu dla programu Excel.

3. Wywołaj metodę z innego kodu w projekcie. Aby na przykład utworzyć niestandardową część XML, gdy użytkownik otworzy skoroszyt, wywołaj metodę z `ThisWorkbook_Startup` procedury obsługi zdarzeń.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Aby dodać niestandardową część XML do dokumentu programu Word

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w dokumencie. Obiekt <xref:Microsoft.Office.Core.CustomXMLPart> zawiera ciąg XML, który ma być zapisywany w dokumencie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs" id="Snippet1":::

2. Dodaj `AddCustomXmlPartToDocument` metodę do klasy `ThisDocument` w projekcie na poziomie dokumentu dla programu Word.

3. Wywołaj metodę z innego kodu w projekcie. Aby na przykład utworzyć niestandardową część XML, gdy użytkownik otworzy dokument, wywołaj metodę z `ThisDocument_Startup` procedury obsługi zdarzeń.

## <a name="robust-programming"></a>Niezawodne programowanie
 Dla uproszczenia w tym przykładzie użyto ciągu XML zdefiniowanego jako zmienna lokalna w metodzie . Zazwyczaj kod XML należy uzyskać ze źródła zewnętrznego, takiego jak plik lub baza danych.

## <a name="see-also"></a>Zobacz też
- [Omówienie niestandardowych części XML](../vsto/custom-xml-parts-overview.md)
- [How to: Add custom XML parts to documents by using VSTO Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
