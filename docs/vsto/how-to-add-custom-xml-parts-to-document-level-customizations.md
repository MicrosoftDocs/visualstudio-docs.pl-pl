---
title: 'Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 22c4a3346de4dac78fd4fcb7c566827cd6ed5a79
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602744"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu
  Dane XML można przechowywać w skoroszycie programu Microsoft Office Excel lub dokumentu programu Microsoft Office Word, tworząc z niestandardowym elementem XML w dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [przegląd części niestandardowy plik XML](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
>  Program Visual Studio nie zapewnia projektów na poziomie dokumentu dla programu Microsoft PowerPoint pakietu Office. Aby dowiedzieć się, jak dodawanie niestandardowych części XML do prezentacji programu PowerPoint przy użyciu dodatku narzędzi VSTO, zobacz [jak: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Aby dodać niestandardowe części XML do skoroszytu programu Excel

1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> obiekt <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w skoroszycie. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w skoroszycie.

     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]

2.  Dodaj `AddCustomXmlPartToWorkbook` metody `ThisWorkbook` klasy w projekcie poziomie dokumentu dla programu Excel.

3.  Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, kiedy użytkownik otwiera skoroszyt, wywołaj metodę z `ThisWorkbook_Startup` programu obsługi zdarzeń.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Aby dodać niestandardowe części XML do dokumentu programu Word

1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> obiekt <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w dokumencie. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w dokumencie.

     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]

2.  Dodaj `AddCustomXmlPartToDocument` metody `ThisDocument` klasy w projekcie poziomie dokumentu dla programu Word.

3.  Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, kiedy użytkownik otwiera dokument, wywołaj metodę z `ThisDocument_Startup` programu obsługi zdarzeń.

## <a name="robust-programming"></a>Skuteczne programowanie
 Dla uproszczenia w tym przykładzie użyto ciągu XML, który jest zdefiniowany jako zmienna lokalna w metodzie. Zazwyczaj należy uzyskać plik XML z zewnętrznego źródła, takich jak plik lub bazy danych.

## <a name="see-also"></a>Zobacz także
- [Niestandardowe części XML ― omówienie](../vsto/custom-xml-parts-overview.md)
- [Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
