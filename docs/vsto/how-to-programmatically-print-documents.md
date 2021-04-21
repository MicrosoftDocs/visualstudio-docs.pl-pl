---
title: Jak programowo drukować dokumenty
description: Dowiedz się, jak wydrukować cały dokument programu Microsoft Word lub jego część na drukarce domyślnej.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47f295a6259b8d722c9c3c714b62fe648bdea1c6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827204"
---
# <a name="how-to-programmatically-print-documents"></a>Jak programowo drukować dokumenty
  Możesz wydrukować całą zawartość Microsoft Office programu Word lub część dokumentu, na drukarce domyślnej.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Drukowanie dokumentu, który jest częścią dostosowania na poziomie dokumentu

### <a name="to-print-the-entire-document"></a>Aby wydrukować cały dokument

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> metodę klasy w `ThisDocument` projekcie, aby wydrukować cały dokument. Aby użyć tego przykładu, uruchom kod z `ThisDocument` klasy .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-the-document"></a>Aby wydrukować bieżącą stronę dokumentu

1. Wywołaj metodę klasy w projekcie i określ, że ma zostać wydrukowana <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> `ThisDocument` jedna kopia bieżącej strony. Aby użyć tego przykładu, uruchom kod z `ThisDocument` klasy .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet12":::

## <a name="print-a-document-by-using-a-vsto-add-in"></a>Drukowanie dokumentu przy użyciu dodatku VSTO

### <a name="to-print-an-entire-document"></a>Aby wydrukować cały dokument

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> metodę <xref:Microsoft.Office.Interop.Word.Document> obiektu, który chcesz wydrukować. Poniższy przykład kodu drukuje aktywny dokument. Aby użyć tego przykładu, uruchom kod z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-a-document"></a>Aby wydrukować bieżącą stronę dokumentu

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> metodę obiektu, który chcesz wydrukować, i określ, że ma zostać wydrukowana <xref:Microsoft.Office.Interop.Word.Document> jedna kopia bieżącej strony. Poniższy przykład kodu drukuje aktywny dokument. Aby użyć tego przykładu, uruchom kod z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet12":::

## <a name="see-also"></a>Zobacz też
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
