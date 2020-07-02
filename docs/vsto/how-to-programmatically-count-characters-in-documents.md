---
title: 'Instrukcje: Programowane zliczanie znaków w dokumentach'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81ee7c3d798ae2c38ed80b261a6d87190daa59a2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546071"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Instrukcje: Programowane zliczanie znaków w dokumentach
  Pierwszy znak w dokumencie znajduje się na pozycji znaku 0, która reprezentuje punkt wstawiania. Ostatnia pozycja znaku jest równa łącznej liczbie znaków w dokumencie. Możesz określić liczbę znaków w dokumencie przy użyciu <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> właściwości <xref:Microsoft.Office.Interop.Word.Characters> kolekcji.

 Wszystkie znaki w dokumencie są zliczane, w tym spacje, znaczniki akapitu i inne znaki, które są normalnie ukryte. Nawet nowy pusty dokument zwraca liczbę jednego znaku, ponieważ zawiera znacznik akapitu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Aby wyświetlić liczbę znaków w dostosowaniu na poziomie dokumentu

1. Zaznacz cały dokument.

     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]

2. Wyświetl liczbę znaków w dokumencie w oknie komunikatu.

     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Aby wyświetlić liczbę znaków w dodatku narzędzi VSTO

1. Zaznacz cały dokument. Poniższy przykład wybiera aktywny dokument.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]

2. Wyświetl liczbę znaków w dokumencie w oknie komunikatu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: programowe pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
