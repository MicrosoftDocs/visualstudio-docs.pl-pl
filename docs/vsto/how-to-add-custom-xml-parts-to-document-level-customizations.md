---
title: 'Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 92148a6f084a4cc04b4587781e750e4fd0df133f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538336"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu
  Dane XML można przechowywać w Microsoft Office skoroszycie programu Excel lub w Microsoft Office dokumencie programu Word, tworząc niestandardową część XML w dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz temat [niestandardowe składniki XML — Omówienie](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Program Visual Studio nie udostępnia projektów na poziomie dokumentu dla programu Microsoft Office PowerPoint. Aby uzyskać informacje na temat dodawania niestandardowej części XML do prezentacji programu PowerPoint przy użyciu dodatku VSTO, zobacz [How to: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Aby dodać niestandardową część XML do skoroszytu programu Excel

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w skoroszycie. <xref:Microsoft.Office.Core.CustomXMLPart>Zawiera ciąg XML, który ma być przechowywany w skoroszycie.

     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]

2. Dodaj `AddCustomXmlPartToWorkbook` metodę do `ThisWorkbook` klasy w projekcie na poziomie dokumentu dla programu Excel.

3. Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardową część XML, gdy użytkownik otworzy skoroszyt, wywołaj metodę z `ThisWorkbook_Startup` procedury obsługi zdarzeń.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Aby dodać niestandardową część XML do dokumentu programu Word

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w dokumencie. <xref:Microsoft.Office.Core.CustomXMLPart>Zawiera ciąg XML, który ma być przechowywany w dokumencie.

     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]

2. Dodaj `AddCustomXmlPartToDocument` metodę do `ThisDocument` klasy w projekcie na poziomie dokumentu dla programu Word.

3. Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardową część XML, gdy użytkownik otwiera dokument, wywołaj metodę z `ThisDocument_Startup` procedury obsługi zdarzeń.

## <a name="robust-programming"></a>Niezawodne programowanie
 Dla uproszczenia w tym przykładzie użyto ciągu XML, który jest definiowany jako zmienna lokalna w metodzie. Zazwyczaj należy uzyskać kod XML ze źródła zewnętrznego, takiego jak plik lub baza danych.

## <a name="see-also"></a>Zobacz także
- [Niestandardowe części XML — Omówienie](../vsto/custom-xml-parts-overview.md)
- [Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
