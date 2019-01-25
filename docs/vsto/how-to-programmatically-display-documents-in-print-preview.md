---
title: 'Instrukcje: Programowe wyświetlanie dokumentów w podglądzie wydruku'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0907db7e616f0b342f2810c32af8e06d6bc730f7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873941"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Instrukcje: Programowe wyświetlanie dokumentów w podglądzie wydruku
  Jeśli rozwiązanie generuje raport, można wyświetlić raport do użytkownika w trybie podglądu wydruku.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procedury w przypadku dostosowań na poziomie dokumentu  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku przez wywołanie metody printpreview —  
  
1.  Wywołaj <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> metody <xref:Microsoft.Office.Tools.Word.Document> klasy. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku, ustawiając właściwość printpreview —  
  
1.  Ustaw <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> obiekt **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procedury dotyczące dodatków narzędzi VSTO  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku przez wywołanie metody printpreview —  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> metody <xref:Microsoft.Office.Interop.Word.Document> , którą chcesz wyświetlić podgląd. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku, ustawiając właściwość printpreview —  
  
1.  Ustaw <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> obiekt **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md)   
 [Instrukcje: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Instrukcje: Programowe tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)  
