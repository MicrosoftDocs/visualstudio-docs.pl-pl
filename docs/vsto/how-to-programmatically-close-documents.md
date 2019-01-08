---
title: 'Instrukcje: Programowe zamykanie dokumentów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: cbe8e29ea42f92e072e3afffca95d6be59765434
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087051"
---
# <a name="how-to-programmatically-close-documents"></a>Instrukcje: Programowe zamykanie dokumentów
  Możesz zamknąć aktywny dokument, lub można określić dokumentu, aby zamknąć.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="close-the-active-document"></a>Zamyka aktywny dokument.  
 Istnieją dwie procedury zamykanie dokumentów aktywnych: jeden dla dostosowywania poziomie dokumentu i jeden dla dodatków narzędzi VSTO.  
  
### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Aby zamknąć aktywny dokument w dostosowaniu na poziomie dokumentu  
  
1.  Wywołaj <xref:Microsoft.Office.Tools.Word.Document.Close%2A> metody `ThisDocument` klasy w projekcie, aby zamknąć dokument służącej do dostosowywania. Aby użyć w poniższym przykładzie kodu, należy uruchomić go z `ThisDocument` klasy.  
  
    > [!NOTE]  
    >  Ten przykład przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość *SaveChanges* parametru, aby zamknąć bez zapisywania zmian lub monitowania użytkownika.  
  
     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]  
  
### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Aby zamknąć aktywnego dokumentu w dodatku narzędzi VSTO  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metody <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> właściwość, aby zamknąć aktywny dokument. Aby użyć w poniższym przykładzie kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.  
  
    > [!NOTE]  
    >  Ten przykład przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość *SaveChanges* parametru, aby zamknąć bez zapisywania zmian lub monitowania użytkownika.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]  
  
## <a name="close-a-document-that-you-specify-by-name"></a>Zamknij dokument, który określisz według nazwy  
 Sposób, w jaki Zamknij dokument, który określisz według nazwy jest taka sama dla dodatków narzędzi VSTO dla programów i dostosowań na poziomie dokumentu.  
  
### <a name="to-close-a-document-that-you-specify-by-name"></a>Aby zamknąć dokument, który określisz według nazwy  
  
1.  Określona nazwa dokumentu jako argument do <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> kolekcji, a następnie wywołania <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metody. Poniższy przykład kodu zakłada, że dokument o nazwie **NewDocument** jest otwarty w programie Word.  
  
    > [!NOTE]  
    >  Ten przykład przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość *SaveChanges* parametru, aby zamknąć bez zapisywania zmian lub monitowania użytkownika.  
  
     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Instrukcje: Programowe zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
