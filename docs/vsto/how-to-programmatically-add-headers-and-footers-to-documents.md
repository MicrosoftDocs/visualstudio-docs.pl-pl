---
title: 'How to: Programowe dodawanie nagłówków i stopek do dokumentów'
description: Dowiedz się, jak dodawać tekst do nagłówków i stopek w dokumencie przy użyciu właściwości Headers i Footers sekcji.
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
ms.openlocfilehash: 73844d19ef6bb85c623706ab0d359836e42a3b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828750"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>How to: Programowe dodawanie nagłówków i stopek do dokumentów
  Tekst można dodać do nagłówków i stopek w dokumencie przy użyciu właściwości <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> i <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> właściwości <xref:Microsoft.Office.Interop.Word.Section> . Każda sekcja dokumentu zawiera trzy nagłówki i stopki:

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Procedury są różne w przypadku dostosowań na poziomie dokumentu i dodatków VSTO.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów
 Aby użyć poniższych przykładów kodu, uruchom je z `ThisDocument` klasy w projekcie.

### <a name="to-add-text-to-footers-in-the-document"></a>Aby dodać tekst do stopek w dokumencie

1. Poniższy przykład kodu ustawia czcionkę tekstu, który ma zostać wstawiony do podstawowej stopki każdej sekcji dokumentu, a następnie wstawia tekst do stopki.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie

1. Poniższy przykład kodu dodaje pole w celu pokazania numeru strony w każdym nagłówku w dokumencie, a następnie ustawia wyrównanie akapitu tak, aby tekst był wyrównany do prawej strony nagłówka.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet116":::

## <a name="vsto-add-ins"></a>Dodatki VSTO
 Aby użyć poniższych przykładów kodu, uruchom je z `ThisAddIn` klasy w projekcie.

### <a name="to-add-text-to-footers-in-a-document"></a>Aby dodać tekst do stopek w dokumencie

1. Poniższy przykład kodu ustawia czcionkę tekstu, który ma zostać wstawiony do podstawowej stopki każdej sekcji dokumentu, a następnie wstawia tekst do stopki. W tym przykładzie kodu jest używany aktywny dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Aby dodać tekst do nagłówków w dokumencie

1. Poniższy przykład kodu dodaje pole w celu pokazania numeru strony w każdym nagłówku w dokumencie, a następnie ustawia wyrównanie akapitu tak, aby tekst był wyrównany do prawej strony nagłówka. W tym przykładzie kodu jest używany aktywny dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet116":::

## <a name="see-also"></a>Zobacz też
- [How to: Programmatically create new documents (Tworzyć programowo nowe dokumenty)](../vsto/how-to-programmatically-create-new-documents.md)
- [Pisano: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [How to: Programmatically loop through found items in documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
