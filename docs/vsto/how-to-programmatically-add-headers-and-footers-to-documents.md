---
title: 'Instrukcje: programowe Dodawanie nagłówków i stopek do dokumentów'
description: Dowiedz się, jak dodać tekst do nagłówków i stopek w dokumencie przy użyciu właściwości nagłówki i stopek w sekcji.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 63b50e020efa549993e36dbd5b43504467e554a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908611"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Instrukcje: programowe Dodawanie nagłówków i stopek do dokumentów
  Możesz dodać tekst do nagłówków i stopek w dokumencie przy użyciu <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> właściwości i <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> właściwości <xref:Microsoft.Office.Interop.Word.Section> . Każda sekcja dokumentu zawiera trzy nagłówki i stopki:

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Procedury te różnią się w przypadku dostosowań na poziomie dokumentu i dodatków narzędzi VSTO.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów
 Aby użyć następujących przykładów kodu, uruchom je z `ThisDocument` klasy w projekcie.

### <a name="to-add-text-to-footers-in-the-document"></a>Aby dodać tekst do stopek w dokumencie

1. Poniższy przykład kodu ustawia czcionkę tekstu, który ma zostać wstawiony do podstawowej stopki każdej sekcji dokumentu, a następnie wstawia tekst do stopki.

     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie

1. Poniższy przykład kodu dodaje pole, aby wyświetlić numer strony w każdym nagłówku dokumentu, a następnie ustawia wyrównanie akapitu tak, aby tekst wyrównany do prawej krawędzi nagłówka.

     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]

## <a name="vsto-add-ins"></a>Dodatki narzędzi VSTO
 Aby użyć następujących przykładów kodu, uruchom je z `ThisAddIn` klasy w projekcie.

### <a name="to-add-text-to-footers-in-a-document"></a>Aby dodać tekst do stopek w dokumencie

1. Poniższy przykład kodu ustawia czcionkę tekstu, który ma zostać wstawiony do podstawowej stopki każdej sekcji dokumentu, a następnie wstawia tekst do stopki. Ten przykład kodu używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie

1. Poniższy przykład kodu dodaje pole, aby wyświetlić numer strony w każdym nagłówku dokumentu, a następnie ustawia wyrównanie akapitu tak, aby tekst wyrównany do prawej krawędzi nagłówka. Ten przykład kodu używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)
- [Instrukcje: Programowane poszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
