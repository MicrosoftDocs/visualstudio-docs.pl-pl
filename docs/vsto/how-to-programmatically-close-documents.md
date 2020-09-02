---
title: 'Instrukcje: programowe Zamykanie dokumentów'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18dc4099f4c1df17efbe2dd3c213332bb73b52c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547462"
---
# <a name="how-to-programmatically-close-documents"></a>Instrukcje: programowe Zamykanie dokumentów
  Możesz zamknąć aktywny dokument lub określić dokument do zamknięcia.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Zamknij aktywny dokument
 Istnieją dwie procedury zamykania aktywnego dokumentu: jeden dla dostosowań na poziomie dokumentu i jeden dla dodatków narzędzi VSTO.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Aby zamknąć aktywny dokument w dostosowaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.Close%2A> metodę `ThisDocument` klasy w projekcie, aby zamknąć dokument skojarzony z dostosowaniem. Aby użyć następującego przykładu kodu, uruchom go z `ThisDocument` klasy.

    > [!NOTE]
    > Ten przykład przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość do parametru *metody SaveChanges* , aby zamknąć bez zapisywania zmian lub monitowania użytkownika.

     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Aby zamknąć aktywny dokument w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metodę właściwości, <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> Aby zamknąć aktywny dokument. Aby użyć następującego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

    > [!NOTE]
    > Ten przykład przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość do parametru *metody SaveChanges* , aby zamknąć bez zapisywania zmian lub monitowania użytkownika.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]

## <a name="close-a-document-that-you-specify-by-name"></a>Zamknij dokument określony przez nazwę
 Sposób zamykania dokumentu określonego za pomocą nazwy jest taki sam dla dodatków narzędzi VSTO i dostosowań na poziomie dokumentu.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Aby zamknąć dokument określony przez nazwę

1. Określ nazwę dokumentu jako argument <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> kolekcji, a następnie Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metodę. W poniższym przykładzie kodu założono, że dokument o nazwie **NewDocument** jest otwarty w programie Word.

    > [!NOTE]
    > Ten przykład przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość do parametru *metody SaveChanges* , aby zamknąć bez zapisywania zmian lub monitowania użytkownika.

     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Instrukcje: programowe zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
