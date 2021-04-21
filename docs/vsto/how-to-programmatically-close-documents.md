---
title: 'Pisano: Programowe zamykanie dokumentów'
description: Dowiedz się, jak zamknąć aktywny dokument lub określić dokument programu Microsoft Office Word do zamknięcia.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1b31a35ac1fa452f526d109dd93ca8264f78947b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825358"
---
# <a name="how-to-programmatically-close-documents"></a>Pisano: Programowe zamykanie dokumentów
  Możesz zamknąć aktywny dokument lub określić dokument do zamknięcia.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Zamykanie aktywnego dokumentu
 Istnieją dwie procedury zamykania aktywnego dokumentu: jedna dla dostosowań na poziomie dokumentu i jedna dla dodatków VSTO.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Aby zamknąć aktywny dokument w dostosowywaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.Close%2A> metodę klasy w `ThisDocument` projekcie, aby zamknąć dokument skojarzony z dostosowaniem. Aby użyć poniższego przykładu kodu, uruchom go z `ThisDocument` klasy .

    > [!NOTE]
    > W tym przykładzie <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość jest przekazujena do *parametru SaveChanges* w celu zamknięcia bez zapisywania zmian ani monitowania użytkownika.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet3":::

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Aby zamknąć aktywny dokument w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metodę właściwości , aby zamknąć aktywny <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> dokument. Aby użyć poniższego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

    > [!NOTE]
    > W tym przykładzie <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość jest przekazujena do *parametru SaveChanges* w celu zamknięcia bez zapisywania zmian ani monitowania użytkownika.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet3":::

## <a name="close-a-document-that-you-specify-by-name"></a>Zamykanie dokumentu, który został określony przez nazwę
 Sposób zamykania dokumentu, który jest określony przez nazwę, jest taki sam dla dodatków VSTO i dostosowań na poziomie dokumentu.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Aby zamknąć dokument określony przez nazwę

1. Określ nazwę dokumentu jako argument <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> kolekcji, a następnie wywołaj metodę <xref:Microsoft.Office.Interop.Word._Document.Close%2A> . W poniższym przykładzie kodu przyjęto założenie, że dokument o nazwie **NewDocument** jest otwarty w programie Word.

    > [!NOTE]
    > W tym przykładzie <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> wartość jest przekazujena do *parametru SaveChanges* w celu zamknięcia bez zapisywania zmian ani monitowania użytkownika.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet4":::

## <a name="see-also"></a>Zobacz też
- [2018: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [How to: Programowe zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
