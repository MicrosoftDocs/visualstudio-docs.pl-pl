---
title: 'How to: Programmatically display documents in Print Preview'
description: Dowiedz się, jak programowo wyświetlać dokumenty w podglądzie wydruku w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90979fbc7cd0b46329b8d9e9bc142e8cf0066db0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825891"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>How to: Programmatically display documents in Print Preview
  Jeśli rozwiązanie generuje raport, może być konieczne wyświetlenie raportu użytkownikowi w trybie podglądu wydruku.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Procedury dostosowywania na poziomie dokumentu

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku, wywołując metodę PrintPreview

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> metodę <xref:Microsoft.Office.Tools.Word.Document> klasy . Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku, ustawiając właściwość PrintPreview

1. Ustaw właściwość <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> obiektu na wartość <xref:Microsoft.Office.Interop.Word.Application> **true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="procedures-for-vsto-add-ins"></a>Procedury dotyczące dodatków VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku, wywołując metodę PrintPreview

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> metodę metody , którą chcesz wyświetlić w wersji <xref:Microsoft.Office.Interop.Word.Document> zapoznawczej. Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku, ustawiając właściwość PrintPreview

1. Ustaw właściwość <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> obiektu na wartość <xref:Microsoft.Office.Interop.Word.Application> **true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo drukować dokumenty](../vsto/how-to-programmatically-print-documents.md)
- [Pisano: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Jak programowo tworzyć nowe dokumenty](../vsto/how-to-programmatically-create-new-documents.md)
