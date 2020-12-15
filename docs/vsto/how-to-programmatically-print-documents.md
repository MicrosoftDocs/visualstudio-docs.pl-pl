---
title: 'Instrukcje: Programowane drukowanie dokumentów'
description: Dowiedz się, w jaki sposób można wydrukować cały dokument programu Microsoft Word lub część dokumentu na drukarce domyślnej.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e17976c86a519db3c5edcd60c426b5d20e84b526
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523922"
---
# <a name="how-to-programmatically-print-documents"></a>Instrukcje: Programowane drukowanie dokumentów
  Do drukarki domyślnej można wydrukować cały dokument programu Microsoft Office Word lub część dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Drukowanie dokumentu, który jest częścią dostosowania na poziomie dokumentu

### <a name="to-print-the-entire-document"></a>Aby wydrukować cały dokument

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> metodę `ThisDocument` klasy w projekcie, aby wydrukować cały dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` klasy.

     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]

### <a name="to-print-the-current-page-of-the-document"></a>Aby wydrukować bieżącą stronę dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> metodę `ThisDocument` klasy w projekcie i określ, że jedna kopia bieżącej strony ma być drukowana. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` klasy.

     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]

## <a name="print-a-document-by-using-a-vsto-add-in"></a>Drukowanie dokumentu przy użyciu dodatku VSTO

### <a name="to-print-an-entire-document"></a>Aby wydrukować cały dokument

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> metodę <xref:Microsoft.Office.Interop.Word.Document> obiektu, który chcesz wydrukować. Poniższy przykład kodu Drukuje aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]

### <a name="to-print-the-current-page-of-a-document"></a>Aby wydrukować bieżącą stronę dokumentu

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> metodę obiektu, <xref:Microsoft.Office.Interop.Word.Document> który chcesz wydrukować, i określ, że jedna kopia bieżącej strony ma być drukowana. Poniższy przykład kodu Drukuje aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]

## <a name="see-also"></a>Zobacz też
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
