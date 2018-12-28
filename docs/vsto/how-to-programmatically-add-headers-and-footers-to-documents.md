---
title: 'Instrukcje: Programowe Dodawanie nagłówków i stopek do dokumentów'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: d6baf57f8b34f6dc591a8e1a131bd665671322e9
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803379"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Instrukcje: Programowe Dodawanie nagłówków i stopek do dokumentów
  Możesz dodać tekst nagłówków i stopek w dokumencie za pomocą <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> właściwości i <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> właściwość <xref:Microsoft.Office.Interop.Word.Section>. Każda sekcja dokumentu zawiera trzy nagłówki i stopki:  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
  Procedury są inne w przypadku dostosowań na poziomie dokumentu i dodatków narzędzi VSTO.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów  
 Aby użyć poniższe przykłady kodu, należy uruchomić je z `ThisDocument` klasy w projekcie.  
  
### <a name="to-add-text-to-footers-in-the-document"></a>Aby dodać tekst stopki w dokumencie  
  
1.  Poniższy przykład kodu Ustawia czcionkę tekstu do wstawienia do głównej stopce każdej części dokumentu, a następnie wstawia tekst do stopki.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie  
  
1.  Poniższy przykład kodu dodaje pole do wyświetlenia na numer strony w każdy nagłówek w dokumencie, a następnie Ustawia wyrównanie akapitu, dzięki czemu tekst jest wyrównany do prawej strony nagłówka.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>Dodatków narzędzi VSTO  
 Aby użyć poniższe przykłady kodu, należy uruchomić je z `ThisAddIn` klasy w projekcie.  
  
### <a name="to-add-text-to-footers-in-a-document"></a>Aby dodać tekst stopki w dokumencie  
  
1.  Poniższy przykład kodu Ustawia czcionkę tekstu do wstawienia do głównej stopce każdej części dokumentu, a następnie wstawia tekst do stopki. Ten przykład kodu używa aktywnego dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie  
  
1.  Poniższy przykład kodu dodaje pole do wyświetlenia na numer strony w każdy nagłówek w dokumencie, a następnie Ustawia wyrównanie akapitu, dzięki czemu tekst jest wyrównany do prawej strony nagłówka. Ten przykład kodu używa aktywnego dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)   
 [Instrukcje: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Instrukcje: Programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   