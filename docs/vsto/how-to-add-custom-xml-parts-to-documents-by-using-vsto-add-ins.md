---
title: Dodawanie niestandardowych części XML do dokumentów przy użyciu dodatków VSTO
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
ms.openlocfilehash: 31c2364213d3b4dae16558f395ad7bdd93231787
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827867"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Jak dodać niestandardowe części XML do dokumentów za pomocą dodatków VSTO
  Dane XML można przechowywać w następujących typach dokumentów, tworząc niestandardową część XML w dodatku VSTO:

- Skoroszyt Microsoft Office programu Excel.

- Dokument Microsoft Office Word.

- Prezentacja Microsoft Office PowerPoint.

  Aby uzyskać więcej informacji, zobacz [Omówienie niestandardowych części XML.](../vsto/custom-xml-parts-overview.md)

  **Dotyczy:** Informacje zawarte w tym temacie dotyczą projektów na poziomie aplikacji dla programów Excel, PowerPoint i Word. Aby uzyskać więcej informacji, zobacz [Funkcje dostępne według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Aby dodać niestandardową część XML do skoroszytu programu Excel

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> kolekcji w skoroszycie. Obiekt <xref:Microsoft.Office.Core.CustomXMLPart> zawiera ciąg XML, który ma być zapisywany w skoroszycie.

     Poniższy przykład kodu dodaje niestandardową część XML do określonego skoroszytu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs" id="Snippet1":::

2. Dodaj metodę `AddCustomXmlPartToWorkbook` do klasy `ThisAddIn` w projekcie dodatku VSTO dla programu Excel.

3. Wywołaj metodę z innego kodu w projekcie. Aby na przykład utworzyć niestandardową część XML, gdy użytkownik otworzy skoroszyt, wywołaj metodę z procedury obsługi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> zdarzeń dla zdarzenia.

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Aby dodać niestandardową część XML do dokumentu programu Word

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> kolekcji w dokumencie. Obiekt <xref:Microsoft.Office.Core.CustomXMLPart> zawiera ciąg XML, który ma być zapisywany w dokumencie.

     Poniższy przykład kodu dodaje niestandardową część XML do określonego dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs" id="Snippet1":::

2. Dodaj `AddCustomXmlPartToDocument` metodę do klasy `ThisAddIn` w projekcie dodatku VSTO dla programu Word.

3. Wywołaj metodę z innego kodu w projekcie. Aby na przykład utworzyć niestandardową część XML, gdy użytkownik otworzy dokument, wywołaj metodę z procedury obsługi <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń dla zdarzenia.

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Aby dodać niestandardową część XML do prezentacji programu PowerPoint

1. Dodaj nowy <xref:Microsoft.Office.Core.CustomXMLPart> obiekt do [kolekcji Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) w prezentacji. Obiekt <xref:Microsoft.Office.Core.CustomXMLPart> zawiera ciąg XML, który ma być zapisywany w prezentacji.

     Poniższy przykład kodu dodaje niestandardową część XML do określonej prezentacji.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb" id="Snippet1":::

2. Dodaj `AddCustomXmlPartToPresentation` metodę do klasy `ThisAddIn` w projekcie dodatku VSTO dla programu PowerPoint.

3. Wywołaj metodę z innego kodu w projekcie. Aby na przykład utworzyć niestandardową część XML, gdy użytkownik otworzy prezentację, wywołaj metodę z procedury obsługi zdarzeń dla zdarzenia [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen.](/previous-versions/office/developer/office-2010/ff762843(v=office.14))

## <a name="robust-programming"></a>Niezawodne programowanie
 Dla uproszczenia w tym przykładzie użyto ciągu XML zdefiniowanego jako zmienna lokalna w metodzie . Zazwyczaj kod XML należy uzyskać ze źródła zewnętrznego, takiego jak plik lub baza danych.

## <a name="see-also"></a>Zobacz też
- [Omówienie niestandardowych części XML](../vsto/custom-xml-parts-overview.md)
- [How to: Add custom XML parts to document-level customizations (3.03.2017: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentu)](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
