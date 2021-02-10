---
title: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO
description: Dowiedz się, jak przechowywać dane XML w następujących typach dokumentów, tworząc niestandardową część XML w dodatku VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fbba5c629807815a306221368d00b7d759dcc294
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954231"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO
  Dane XML można przechowywać w następujących typach dokumentów, tworząc niestandardową część XML w dodatku VSTO:

- Skoroszyt programu Excel Microsoft Office.

- Dokument programu Microsoft Office Word.

- Prezentacja programu PowerPoint Microsoft Office.

  Aby uzyskać więcej informacji, zobacz temat [niestandardowe składniki XML — Omówienie](../vsto/custom-xml-parts-overview.md).

  **Dotyczy:** Informacje przedstawione w tym temacie mają zastosowanie do projektów na poziomie aplikacji dla programów Excel, PowerPoint i Word. Aby uzyskać więcej informacji, zobacz [dostępność funkcji według aplikacji pakietu Office i typów projektów](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Aby dodać niestandardową część XML do skoroszytu programu Excel

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> kolekcji w skoroszycie. <xref:Microsoft.Office.Core.CustomXMLPart>Zawiera ciąg XML, który ma być przechowywany w skoroszycie.

     Poniższy przykład kodu dodaje niestandardową część XML do określonego skoroszytu.

     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]

2. Dodaj `AddCustomXmlPartToWorkbook` metodę do `ThisAddIn` klasy w projekcie dodatku VSTO dla programu Excel.

3. Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardową część XML, gdy użytkownik otwiera skoroszyt, wywołaj metodę z procedury obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> zdarzenia.

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Aby dodać niestandardową część XML do dokumentu programu Word

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> kolekcji w dokumencie. <xref:Microsoft.Office.Core.CustomXMLPart>Zawiera ciąg XML, który ma być przechowywany w dokumencie.

     Poniższy przykład kodu dodaje niestandardową część XML do określonego dokumentu.

     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]

2. Dodaj `AddCustomXmlPartToDocument` metodę do `ThisAddIn` klasy w projekcie dodatku VSTO dla programu Word.

3. Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardową część XML, gdy użytkownik otwiera dokument, wywołaj metodę z procedury obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzenia.

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Aby dodać niestandardową część XML do prezentacji programu PowerPoint

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do kolekcji [Microsoft.Office.Interop.PowerPoint._Presentation. CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) w prezentacji. <xref:Microsoft.Office.Core.CustomXMLPart>Zawiera ciąg XML, który ma być przechowywany w prezentacji.

     Poniższy przykład kodu dodaje niestandardową część XML do określonej prezentacji.

     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]

2. Dodaj `AddCustomXmlPartToPresentation` metodę do `ThisAddIn` klasy w projekcie dodatku VSTO dla programu PowerPoint.

3. Wywołaj metodę z innego kodu w projekcie. Na przykład, aby utworzyć niestandardową część XML, gdy użytkownik otwiera prezentację, wywołaj metodę z procedury obsługi zdarzeń dla zdarzenia [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) .

## <a name="robust-programming"></a>Niezawodne programowanie
 Dla uproszczenia w tym przykładzie użyto ciągu XML, który jest definiowany jako zmienna lokalna w metodzie. Zazwyczaj należy uzyskać kod XML ze źródła zewnętrznego, takiego jak plik lub baza danych.

## <a name="see-also"></a>Zobacz też
- [Niestandardowe części XML — Omówienie](../vsto/custom-xml-parts-overview.md)
- [Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
