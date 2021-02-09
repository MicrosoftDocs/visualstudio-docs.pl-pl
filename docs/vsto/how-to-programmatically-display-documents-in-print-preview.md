---
title: 'Instrukcje: Programowane wyświetlanie dokumentów w podglądzie wydruku'
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
ms.openlocfilehash: 14005f465fd4394e86450017530de457a97b3d4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885550"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Instrukcje: Programowane wyświetlanie dokumentów w podglądzie wydruku
  Jeśli rozwiązanie generuje raport, możesz chcieć wyświetlić raport dla użytkownika w trybie Podgląd wydruku.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Procedury dostosowywania na poziomie dokumentu

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku przez wywołanie metody PrintPreview

1. Wywoływanie <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> metody <xref:Microsoft.Office.Tools.Word.Document> klasy. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku przez ustawienie właściwości PrintPreview

1. Ustaw <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> Właściwość <xref:Microsoft.Office.Interop.Word.Application> obiektu na **wartość true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="procedures-for-vsto-add-ins"></a>Procedury dotyczące dodatków narzędzi VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku przez wywołanie metody PrintPreview

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> metodę, którą <xref:Microsoft.Office.Interop.Word.Document> chcesz wyświetlić w wersji zapoznawczej. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku przez ustawienie właściwości PrintPreview

1. Ustaw <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> Właściwość <xref:Microsoft.Office.Interop.Word.Application> obiektu na **wartość true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md)
- [Instrukcje: programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Instrukcje: Programowane tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)
