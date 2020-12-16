---
title: 'Instrukcje: Programowane formatowanie tekstu w dokumentach'
description: Dowiedz się, jak można użyć obiektu Range do programistycznego formatowania tekstu w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 931991529b160fedfe65a92e8243183792abf518
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525728"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Instrukcje: Programowane formatowanie tekstu w dokumentach
  Można użyć <xref:Microsoft.Office.Interop.Word.Range> obiektu do formatowania tekstu w Microsoft Office dokumencie programu Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Poniższy przykład wybiera pierwszy akapit w dokumencie i zmienia rozmiar czcionki, nazwę czcionki i wyrównanie. Następnie wybiera zakres i wyświetla okno komunikatu, aby wstrzymać przed wykonaniem kolejnej sekcji kodu. Następna sekcja wywołuje metodę Undo <xref:Microsoft.Office.Tools.Word.Document> elementu hosta (dla dostosowania na poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Document> klasy (dla dodatku VSTO) trzy razy. Stosuje standardowy styl wcięcia i wyświetla okno komunikatu, aby wstrzymać kod. Następnie kod wywołuje <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> metodę jednokrotnie i wyświetla okno komunikatu.

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="to-format-text-using-a-document-level-customization"></a>Aby sformatować tekst przy użyciu dostosowania na poziomie dokumentu

1. Poniższy przykład może służyć do dostosowywania na poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Aby sformatować tekst przy użyciu dodatku VSTO

1. Poniższy przykład może być używany w dodatku VSTO. Ten przykład używa aktywnego dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowane wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Instrukcje: programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
