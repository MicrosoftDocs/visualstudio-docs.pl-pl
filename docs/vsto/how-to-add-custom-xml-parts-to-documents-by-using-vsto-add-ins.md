---
title: 'Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c3b7d214f7793540aafafcac195635e4f2fc9c0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605981"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO
  Dane XML można przechowywać w następujące typy dokumentów, tworząc z niestandardowym elementem XML w dodatku VSTO:

- Skoroszyt programu Microsoft Office Excel.

- Dokument programu Microsoft Office Word.

- Prezentacja Microsoft PowerPoint pakietu Office.

  Aby uzyskać więcej informacji, zobacz [przegląd części niestandardowy plik XML](../vsto/custom-xml-parts-overview.md).

  **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów na poziomie aplikacji dla programów Excel, PowerPoint i Word. Aby uzyskać więcej informacji, zobacz [funkcje, które są dostępne przez typ aplikacji i projektów pakietu Office](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Aby dodać niestandardowe części XML do skoroszytu programu Excel

1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> obiekt <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> kolekcji w skoroszycie. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w skoroszycie.

     Poniższy przykład kodu dodaje z niestandardowym elementem XML do określonego skoroszytu.

     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]

2.  Dodaj `AddCustomXmlPartToWorkbook` metody `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.

3.  Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, kiedy użytkownik otwiera skoroszyt, wywołać metodę z programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> zdarzeń.

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Aby dodać niestandardowe części XML do dokumentu programu Word

1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> obiekt <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> kolekcji w dokumencie. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w dokumencie.

     Poniższy przykład kodu dodaje z niestandardowym elementem XML do określonego dokumentu.

     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]

2.  Dodaj `AddCustomXmlPartToDocument` metody `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Word.

3.  Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, kiedy użytkownik otwiera dokument, wywołać metodę z programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń.

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Aby dodać niestandardowe części XML do prezentacji programu PowerPoint

1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> obiekt [Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) kolekcji w prezentacji. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w prezentacji.

     Poniższy przykład kodu dodaje z niestandardowym elementem XML do określonego prezentacji.

     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]

2.  Dodaj `AddCustomXmlPartToPresentation` metody `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu PowerPoint.

3.  Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, gdy użytkownik otworzy prezentacji, wywołać metodę z programu obsługi zdarzeń dla [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) zdarzeń.

## <a name="robust-programming"></a>Skuteczne programowanie
 Dla uproszczenia w tym przykładzie użyto ciągu XML, który jest zdefiniowany jako zmienna lokalna w metodzie. Zazwyczaj należy uzyskać plik XML z zewnętrznego źródła, takich jak plik lub bazy danych.

## <a name="see-also"></a>Zobacz także
- [Niestandardowe części XML ― omówienie](../vsto/custom-xml-parts-overview.md)
- [Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
